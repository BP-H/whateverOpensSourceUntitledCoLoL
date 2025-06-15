
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE KARMA-POWERED REMIX ECONOMY AGENT (README_8 Protocol)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic into a definitive, production-ready agent.

This agent implements:
- Karma Gating & Exponential Onboarding: New users must earn karma to mint content.
  The threshold starts at 100,000 and halves with each successful mint, creating a
  fair but challenging path to full participation.
- Advanced Fairness Mechanics: A multi-layered system of diminishing returns (per-user,
  per-day) and viral decay (per-coin) prevents spam and ensures economic stability.
- Attribution-First Architecture: Enhanced data structures and hooks for tracking
  and rewarding external scientific and artistic references.
- Fortified Governance: A comprehensive, hash-chained audit log (`LogChain`), a
  modular content filter (`Vaccine`), and a rigorous consent framework.
- Extensibility: Designed with clear interfaces and placeholder hooks for future
  features, including advanced governance and the multi-species vision.
- The 33.3333% Split Law: The inviolable economic heart of the protocol, ensuring
  fair value distribution for every creative action.

This code is the contract. It is designed to be forked, remixed, and improved upon.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
"""

import re
import sys
import json
import random
import datetime
import hashlib
from collections import defaultdict, deque

# === UTILITY FUNCTIONS ===
def ts():
    """Returns the current UTC timestamp in ISO 8601 format."""
    return datetime.datetime.utcnow().isoformat() + "Z"

def sha(s):
    """Computes the SHA-256 hash of a given string."""
    return hashlib.sha256(s.encode()).hexdigest()

def today():
    """Returns the current date in YYYY-MM-DD format."""
    return datetime.date.today().isoformat()

# === IMMUNE SYSTEM (VACCINE) ===
# In a production environment, these patterns would be loaded from an external config file.
VAX_PATTERNS = {
    "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b"],
    "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b"],
    "medium":   [r"\bpolitics\b", r"\bsurveillance\b", r"\bpropaganda\b", r"\bmanipulate\b"],
}
class Vaccine:
    """
    Scans content for forbidden patterns and blocks actions if found.
    Acts as the protocol's immune system against malicious content.
    """
    def __init__(self):
        self.block_counts = defaultdict(int)

    def scan(self, text):
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        lower_text = text.lower()
        for level, patterns in VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    # Log the blocked content for audit purposes.
                    with open("vaccine.log", "a") as f:
                        f.write(json.dumps({"ts": ts(), "severity": level, "pattern": p, "snippet": text[:88]}) + "\n")
                    print(f"🚫 VACCINE BLOCK [{level}]: Forbidden pattern '{p}' detected.")
                    return False
        return True

# === IMMUTABLE AUDIT LOG (LOGCHAIN) ===
class LogChain:
    """
    Implements an immutable, append-only audit log. Each entry is cryptographically
    chained to the previous one, ensuring a tamper-evident record of all events.
    """
    def __init__(self, filename="logchain.log", capacity=50000):
        self.filename = filename
        self.entries = deque(maxlen=capacity)
        try:
            with open(self.filename, "r") as f:
                for line in f:
                    self.entries.append(line.rstrip())
        except FileNotFoundError:
            pass

    def add(self, event):
        """Adds a new event (dict) to the log with a chained hash."""
        entry_json = json.dumps(event, sort_keys=True)
        prev_hash = self.entries[-1].split("||")[-1] if self.entries else ""
        # The new hash is a function of the new entry and the previous hash.
        chain_hash = sha(entry_json + prev_hash)
        self.entries.append(entry_json + "||" + chain_hash)
        self._save()

    def _save(self):
        """Writes the current log chain to the file."""
        with open(self.filename, "w") as fh:
            fh.write("\n".join(self.entries))

    def show(self, filter_str=None):
        """Displays log events, with an optional filter."""
        print("📜 AUDIT LOG:")
        count = 0
        for i, line in enumerate(self.entries, 1):
            if filter_str and filter_str.lower() not in line.lower():
                continue
            data = json.loads(line.split("||"))
            print(f"{i}. {data.get('ts','')} - {data.get('event','')}")
            count += 1
        if count == 0:
            print(" (no matching entries)")

    def verify(self):
        """Verifies the integrity of the entire logchain."""
        print("🔐 Verifying logchain integrity...")
        prev_hash = ""
        for idx, line in enumerate(self.entries, 1):
            try:
                entry, stored_hash = line.split("||")
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {idx}.")
                return False
            
            calculated_hash = sha(entry + prev_hash)
            if calculated_hash!= stored_hash:
                print(f"❌ TAMPER DETECTED: Chain break at entry {idx}. Hash mismatch.")
                return False
            prev_hash = stored_hash
        print("✅ Logchain integrity verified.")
        return True

# === CORE DATA MODELS ===
class User:
    """
    Represents a user in the protocol. This class encapsulates all user-specific
    state, including karma, consent, and minting status.
    """
    def __init__(self, name, is_genesis=False, consent=True):
        self.name = name
        self.is_genesis = is_genesis
        self.karma = 0.0
        self.consent = consent
        self.coins =
        self.minted_count = 0
        self.mint_threshold = 100000.0 if not is_genesis else 0.0
        self.daily_actions = defaultdict(int)
        self.last_action_date = today()

    def __repr__(self):
        return f"User(name='{self.name}', karma={self.karma:.2f}, is_genesis={self.is_genesis})"

class Coin:
    """
    Represents a unit of creative content (a "coin"). This class is enhanced to
    support the attribution-first framework.
    """
    def __init__(self, root, tag="single", value=1.0, ancestors=None, references=None, fields=None):
        self.root = root  # The original creator(s) of the content.
        self.tag = tag
        self.value = value
        self.ancestors = ancestors or  # List of parent coin IDs for remixes.
        self.references = references or  # Structured list of external attributions.
        self.fields = fields or  # Metadata tags (e.g., "science", "art").
        self.reactions =  # Log of (user, emoji, timestamp) tuples.

    def to_dict(self):
        """Serializes the coin object to a dictionary for logging or storage."""
        def fix_tuples(obj):
            if isinstance(obj, (list, tuple)):
                return [fix_tuples(x) for x in obj]
            return obj
        return {
            "root": fix_tuples(self.root),
            "tag": self.tag,
            "value": self.value,
            "ancestors": self.ancestors,
            "references": self.references,
            "fields": self.fields,
            "reactions": fix_tuples(self.reactions)
        }

# === THE ULTIMATE AGENT ===
class Agent:
    """
    The core protocol agent. It manages all users, coins, and economic interactions,
    and enforces the canonical laws of the system.
    """
    def __init__(self):
        self.log = LogChain()
        self.vaccine = Vaccine()
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        # Emoji weights determine the base value of reaction-based actions.
        self.weights = {"like": 1.0, "comment": 5.0, "remix": 10.0, "share": 2.0, "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0, "👀": 0.5, "🙏": 10.0}
        self._initialize_genesis_users()
        self.log.add({"ts": ts(), "event": "PROTOCOL_INITIALIZED"})
        print("✅ Ultimate Karma Protocol Agent Initialized.")

    def _initialize_genesis_users(self):
        """Loads the predefined list of genesis collaborators."""
        nss_list = ["mimi", "taha", "platform"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in nss_list:
            user = User(name, is_genesis=True, consent=True)
            user.karma = float('inf') # Genesis users have effectively infinite karma for minting.
            self.users[name] = user
        self.log.add({"ts": ts(), "event": f"GENESIS_USERS_INITIALIZED: {len(nss_list)} members"})

    def add_user(self, name, consent=True):
        """Adds a new, non-genesis user to the protocol."""
        if name in self.users:
            print(f"⚠️ User '{name}' already exists.")
            return
        user = User(name, is_genesis=False, consent=consent)
        self.users[name] = user
        self.log.add({"ts": ts(), "event": f"ADD_USER", "user": name, "consent": consent})
        print(f"👤 User '{name}' added to the protocol.")
        return user

    def set_consent(self, name, give=True):
        """Sets or revokes a user's consent to participate."""
        if name not in self.users:
            print(f"⚠️ Cannot set consent: User '{name}' not found.")
            return
        self.users[name].consent = bool(give)
        status = "GRANTED" if bool(give) else "REVOKED"
        self.log.add({"ts": ts(), "event": f"CONSENT_STATUS_CHANGED", "user": name, "status": status})
        print(f"Consent for {name}: {status}")

    def _reset_daily_counters(self, user):
        """Resets a user's daily action counters if a new day has begun."""
        current_day = today()
        if user.last_action_date!= current_day:
            user.daily_actions.clear()
            user.last_action_date = current_day

    def _award_karma(self, actor_name, origin_name, base_value, action_type):
        """
        Centralized function for calculating and distributing karma according to the
        33.3333% split law and applying fairness mechanics.
        """
        actor = self.users[actor_name]
        origin = self.users[origin_name]

        # 1. Apply daily diminishing returns for the actor.
        self._reset_daily_counters(actor)
        action_count = actor.daily_actions[action_type]
        daily_decay_factor = 0.9 ** action_count
        effective_value = base_value * daily_decay_factor

        # 2. Calculate shares based on the 33% split law.
        share = round(effective_value / 3.0, 6)

        # 3. Distribute karma.
        actor.karma += share
        origin.karma += share
        self.treasury += share
        
        actor.daily_actions[action_type] += 1
        return share

    def mint(self, user_name, content, tag="single", references=None, fields=None):
        """
        Allows a user to mint a new coin, subject to permissions and karma thresholds.
        """
        if user_name not in self.users:
            print(f"⚠️ Mint failed: User '{user_name}' not found.")
            return None

        user = self.users[user_name]
        if not user.consent:
            print(f"❌ Mint denied: User '{user_name}' has not granted consent.")
            return None
        if not self.vaccine.scan(content):
            return None
        
        # Check for science/art attribution requirement.
        if fields and ("science" in fields or "art" in fields) and not references:
            print("❌ Mint denied: Posts tagged as 'science' or 'art' require references.")
            return None

        # Check if user has the right to mint.
        if not user.is_genesis:
            if user.karma < user.mint_threshold:
                needed = user.mint_threshold - user.karma
                print(f"🔒 Mint denied: {user_name} needs {needed:.2f} more karma (has {user.karma:.2f}, needs {user.mint_threshold:.2f}).")
                return None
            # Halve the threshold for the next mint.
            user.mint_threshold = max(user.mint_threshold / 2.0, 1000.0)

        # Create and log the new coin.
        coin_id = sha(f"{user_name}{ts()}{content}{random.random()}")
        coin = Coin(root=user_name, tag=tag, references=references, fields=fields)
        self.coins[coin_id] = coin
        user.coins.append(coin_id)
        user.minted_count += 1

        self.log.add({"ts": ts(), "event": "MINT", "user": user_name, "coin_id": coin_id, "tag": tag, "content": content[:60]})
        print(f"🪙 Coin '{coin_id}' minted by {user_name}.")
        return coin_id

    def react(self, actor_name, coin_id, emoji):
        """
        Allows a user to react to a coin, triggering a karma distribution.
        """
        if actor_name not in self.users or coin_id not in self.coins:
            print("⚠️ React failed: Invalid user or coin.")
            return
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        origin_name = coin.root

        if not actor.consent or not self.users[origin_name].consent:
            print("❌ React denied: Consent required from both actor and originator.")
            return
        
        base_value = self.weights.get(emoji, 1.0)
        
        # Apply viral decay based on the number of existing reactions.
        viral_decay_factor = 0.95 ** len(coin.reactions)
        effective_base_value = base_value * viral_decay_factor

        share = self._award_karma(actor_name, origin_name, effective_base_value, f"react_{emoji}")
        
        coin.reactions.append((actor_name, emoji, ts()))
        self.log.add({"ts": ts(), "event": "REACT", "actor": actor_name, "coin_id": coin_id, "emoji": emoji, "karma_share": share})
        print(f"{emoji} {actor_name} reacted to '{coin_id}'. Karma share: {share:.4f} each to actor, origin, and treasury.")

    def remix(self, actor_name, parent_coin_id, new_content, new_tag="remix", references=None, fields=None):
        """
        Allows a user to create a derivative coin (remix), preserving lineage.
        """
        if parent_coin_id not in self.coins:
            print(f"⚠️ Remix failed: Parent coin '{parent_coin_id}' not found.")
            return None
        
        # Minting a remix is subject to the same rules as minting an original post.
        new_coin_id = self.mint(actor_name, new_content, tag=new_tag, references=references, fields=fields)

        if new_coin_id:
            parent_coin = self.coins[parent_coin_id]
            new_coin = self.coins[new_coin_id]
            new_coin.ancestors.append(parent_coin_id)
            
            # Award karma for the remix action itself.
            origin_name = parent_coin.root
            base_value = self.weights.get("remix", 10.0)
            share = self._award_karma(actor_name, origin_name, base_value, "remix")

            self.log.add({"ts": ts(), "event": "REMIX", "actor": actor_name, "parent_coin": parent_coin_id, "new_coin": new_coin_id, "karma_share": share})
            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{new_coin_id}'. Karma share: {share:.4f} each.")
        return new_coin_id

    # --- Placeholder Hooks for Future Features ---
    def process_unclaimed_references(self):
        """
        Architectural hook for the future "Cross-Credit System". This function would
        periodically scan for references linked to newly verified users and distribute
        retroactive credit.
        """
        self.log.add({"ts": ts(), "event": "HOOK_CALLED", "name": "process_unclaimed_references"})
        # Placeholder logic
        pass

    def trigger_governance_vote(self, proposal):
        """
        Architectural hook for the future "Emoji Canon Voting Layer". This would
        initiate a community vote on a proposed change to the protocol.
        """
        self.log.add({"ts": ts(), "event": "HOOK_CALLED", "name": "trigger_governance_vote", "proposal": proposal})
        # Placeholder logic
        pass

    def show_stats(self):
        """Displays summary statistics for the protocol."""
        print("\n--- PROTOCOL STATISTICS ---")
        print(f"Total Users: {len(self.users)}")
        print(f"Total Coins: {len(self.coins)}")
        print(f"Treasury Balance: {self.treasury:.4f} karma")
        
        print("\n--- LEADERBOARD (TOP 5 by KARMA) ---")
        # Filter out genesis users who have infinite karma for a meaningful leaderboard.
        non_genesis_users = {u.name: u.karma for u in self.users.values() if not u.is_genesis}
        if non_genesis_users:
            leaderboard = sorted(non_genesis_users.items(), key=lambda item: item, reverse=True)
            for i, (name, karma) in enumerate(leaderboard[:5], 1):
                print(f"{i}. {name}: {karma:.2f} karma")
        else:
            print(" (No non-genesis users to rank)")
        print("---------------------------\n")

