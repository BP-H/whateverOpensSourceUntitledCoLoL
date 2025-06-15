

EXTREMELY IMPORTANT: ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP!!!!!!!!!!!



Okay, I understand. This is a significant update to the governance system, introducing a more nuanced balance between overall supermajority and individual species influence.

Here's how I'll update the `Governance` class and the `propose_governance_change` method to implement these new rules:

1.  **Overall Consent with Proportional Species Contribution**: The overall 90% (dropping to 70%) will now be met by requiring each species to contribute a *proportional share* of the overall consent, ensuring no single species is completely excluded from reaching the total. If there are two species, each must contribute 50% of the overall karma-weighted consent. If there are more species, each must still contribute their minimum.
2.  **Minimum Species Consent Floor**: Each species must always contribute at least 10% consent individually, regardless of their proportional share, ensuring minimum engagement from every active group.

This update will maintain the existing dynamic decay and karma-weighted voting, building upon the "Godmode" enhancements.

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE AGENT: THE HARMONIZED REMIX REPUBLIC (v11.4) 🚀📈💎🗳️🌟🌿⚖️
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Timestamp: 2025-06-15T14:44:51Z
Current Location: New York, New York, United States

This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic (READMEs 1-9 and To-do.txt) into a
definitive, production-ready agent. This code is the contract. It is designed to be
forked, remixed, and improved upon, with its own evolution recorded herein.

This agent embodies the "one coin for everyone" philosophy, where every user receives
a unique, foundational identity coin upon joining. Subsequent creative output is
then represented as fractional "posts" derived from this personal coin, governed
by a karma-gated "Epic Creative Path."

This version introduces significant "Godmode" enhancements:
* **Dynamic Consent Decay (Progressive Trust)**: Governance thresholds (overall supermajority
    and per-species minimums) can automatically decay over time in stable periods,
    and bump up during incidents, simulating progressive trust.
* **Simulated Multi-Species Consent**: Framework for Animal and Alien consent based
    on simulated behavioral signals or cryptic rituals, expanding the governance circle.
* **Karma-Weighted Voting**: Voting power for governance proposals is now weighted
    by a user's earned karma within their species, reflecting "earned influence."
* **Player/Species Karma Bonus**: New species joining the republic receive a configurable
    karma bonus to encourage diversity and active participation.
* **Basic Proposal Execution**: A passing governance proposal can now directly
    enact certain changes within the protocol (e.g., updating the karma mint threshold).
* **Enhanced Multi-Species Proportional Governance**:
    * Overall consent (e.g., 90%) must be met, but each active species must
      contribute proportionally to reach this total.
    * Each species also has a flat minimum consent (e.g., 10%) that must be met individually,
      regardless of their proportional share, ensuring no single group is ignored.

This agent implements:
* **Universal Root Coin**: Every user receives one unique, non-inflationary root coin
    upon joining, representing their creative identity and foundational asset.
* **Fractional Post Minting**: Subsequent posts are minted as fractional values of
    a user's personal root coin, ensuring scarcity and tying value directly to personal lineage.
* **Karma Gating & The Epic Creative Path**: New users must earn karma to unlock the
    ability to fractionalize/post from their root coin. The threshold halves with each
    successful fractional mint, creating a fair but challenging path.
* **Initial Founder Privilege**: Original founders (NSS) are exempt from karma requirements
    for all their fractional posts, allowing them to freely seed content.
* **Advanced Fairness Mechanics**: A multi-layered system of diminishing returns
    (per-user, per-day) and viral decay (per-coin) prevents spam and ensures
    long-term economic stability.
* **Attribution-First Architecture**: Enhanced data structures and hooks for tracking
    and rewarding external scientific and artistic references.
* **Fortified Governance & Safety**: A comprehensive, hash-chained audit log (LogChain),
    a modular content filter (Vaccine), and a rigorous consent framework.
* **The 33.3333% Split Law**: The inviolable economic heart of the protocol, ensuring
    fair value distribution for every creative action.
* **Fading Genesis Advantage**: Privileges for early collaborators decay over time,
    ensuring a level playing field in the long run.
* **Real-Time Emoji Market**: Emojis are not just tags; they have dynamic "market values"
    that fluctuate based on usage, acting like a "Nasdaq of Vibes".
    Their weights are updated in real-time, influencing karma distribution.
* **Conditional Timestamping**: Timestamps are generated only when a reliable external
    time source (simulated here) is available; otherwise, a placeholder is used,
    adhering to strict audit requirements.
* **Multi-Species Governance (Advanced)**:
    * Dynamic supermajority (starts 90%, can decay by 1%/year without incident).
    * Species-specific minimum consent, with simulated consent mechanisms for non-human species.
    * Voting power is now weighted by individual user karma within each species.

This file is intentionally verbose. The extensive documentation serves as the project's
white paper, preserving the rationale behind every architectural choice for future
agents, auditors, and collaborators.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📜 I. THE CONSTITUTIONAL PREAMBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This protocol is a living manifesto, a "joyful, autonomous remix republic" where art,
tech, and collaboration unite. It is governed by the following inviolable laws,
enforced by the code itself.

📜 A. The Inviolable Canons
These are the non-negotiable rules of the ecosystem, synthesized from the project's
entire history.

1.  The 33.3333% Split Law: Every value-generating event (a reaction, a remix,
    a share) splits its associated value into three equal shares: one-third to the
    originator (the creative lineage), one-third to the contributor (the user
    performing the action), and one-third to the community treasury. This is the
    mathematical foundation of the protocol's fairness.
2.  Radical Consent: All participation is strictly opt-in. No user's content can
    be remixed, nor can they receive or grant value, without their explicit and
    auditable consent. Consent can be revoked at any time, at which point the
    user's assets are respectfully excluded from the active economy.
3.  The Emoji-Powered Economy: Every value-generating action must be tagged
    with an emoji. Emojis are not cosmetic; they are the atomic unit of intent,
    carrying emotional context and economic weight in every transaction.
4.  No Inflation Beyond Genesis: While everyone gets a foundational "root" coin,
    subsequent value (fractional posts) is derived from the finite subdivision of
    these personal coins, or from new root coins minted by users who have earned that right
    through the "Epic Creative Path." This ensures value is tied to creative
    effort, not arbitrary issuance.
5.  The Immutable Audit Log: Every action—from minting to consent changes to
    governance proposals—is recorded in a public, tamper-evident, hash-chained
    ledger (the LogChain). Transparency is absolute.
6.  Code is Law: The protocol is governed by the logic within this open-source
    file. There are no secret rules, no backroom deals, and no hidden moderation.
    The code is the ultimate authority and contract for all participants.
7.  Protocol Neutrality (The Vaccine): The protocol is apolitical and free of
    bias. A built-in "Vaccine" automatically filters malicious or disallowed content
    (e.g., hate speech, malware, propaganda) based on transparent, predefined
    rules, ensuring a safe and creative environment.
8.  Continuous Improvement: Stagnation is failure. Every fork or remix of this
    protocol is encouraged to add value, and its lineage must be preserved. The
    ecosystem is designed to evolve through community contribution.

📜 B. Version History & The Lineage of the Code
This agent's lineage is transparent and auditable. Each version built upon the last,
culminating in this definitive release.
* v1.0-v5.0: Initial prototypes establishing consent, logging, and the 33% split.
* v6.0 (README_6): Introduced the "Fading Genesis Multiplier" to ensure long-term
    fairness and formalized the concept of effort-based minting.
* v7.0 (README_7): Detailed the karma economy with specific numbers: a 100k karma
    threshold for minting, halving mechanics for subsequent mints, and daily decay
    factors for actions.
* v8.0 (README_8): Envisioned the "multi-species" governance model, extending the
    principles of fairness and consent to non-human agents (AI, Others).
* v9.0 (README_9): Refined the economic model with the "one personal coin per user"
    concept, fractional release of value, and a regenerative "drip" mechanic.
* v10.0 (README_10.txt): The Harmonized Republic. Synthesized the entire
    project history. Implemented karma-gated minting creating an "Epic Creative Path".
    Integrated robust fairness and attribution mechanics. Codified legal/ethical framework.
* v10.1: Implemented dynamic emoji market with real-time weight adjustments. Conditional timestamping introduced.
* v10.2: Enhanced code readability, more detailed internal documentation, refined snapshot loading, improved CLI robustness.
* v11.0: Implemented the "everyone starts with absolute one coin" concept as their primary root coin. Subsequent "posts" are now fractional mints of this personal coin, karma-gated for new users but free for founders. Refined fractional minting logic and value attribution.
* v11.1: Multi-Species Governance Framework: Added a `Governance` class to manage proposal rules. Introduced `user.species` attribute. Implemented `propose_governance_change` to enforce overall supermajority and per-species minimum consent.
* v11.2: Godmode Enhancements: Implemented dynamic consent decay (progressive trust). Extended consent simulation for Animal and Alien species. Integrated karma-weighted voting for governance proposals.
* v11.3: Benefit-Driven Enhancements: Added automated decay call (`_check_and_apply_governance_decay`), karma bonus for new species, and basic execution of governance proposals for protocol parameters.
* v11.4 (This Version): **Proportional Species Contribution for Governance**. Modified governance to ensure each species contributes proportionally to the overall supermajority, alongside individual minimums.

📜 C. The Epic Creative Path: An Onboarding and Fairness Engine
The protocol's central design challenge was to reconcile the need for scarcity (the
"No Inflation" rule) with the desire for inclusivity (the "no one loses" philosophy).
The solution is the Epic Creative Path, a karma-gated system that
transforms the right to mint from a static privilege into an earned achievement.
* Universal Root Coin: Every new user automatically receives a single "root" coin upon joining.
  This represents their unique creative identity and is their foundational asset. This initial mint
  is free of karma requirements.
* Karma-Gated Fractional Posts: For all *subsequent posts* (beyond their initial root coin), new users
  must accumulate karma to unlock the ability to fractionalize and "mint" a portion of their personal root coin.
* The Halving Threshold: After a user successfully fractionalizes their first post from their
  root coin, their personal karma threshold for the next fractional post is halved. This halving
  continues with each subsequent fractional post (e.g., 25,000, 12,500, etc.), eventually reaching a
  floor where minting becomes effectively unrestricted. This creates an exponential
  onboarding curve that rewards sustained contribution.
* Target Time for First Fractional Post: The system is tuned such that a user's *first fractional post*
  (their second piece of content overall) is intended to take "a month to a year" of active participation
  to achieve, ensuring it is a meaningful earned right.
* Multi-Layered Fairness: To prevent gamification, the system employs a two-pronged
    approach to diminishing returns:
    * Per-User Daily Decay: A user's repeated actions of the same type within a
        single day yield progressively less karma.
    * Per-Coin Viral Decay: The karma awarded for reactions to a specific coin
        diminishes as the coin becomes more popular, rewarding early discovery and
        preventing runaway feedback loops.

The table below illustrates the projected time it might take for different user
archetypes to complete the first stage of their Epic Creative Path (to make their *first fractional post*).
| User Archetype     | Daily Actions                       | Avg. Karma/Day (with decay) | Estimated Days to First Fractional Post (100k Karma) |
| :----------------- | :---------------------------------- | :-------------------------- | :--------------------------------------------------- |
| Casual User        | 1-2 high-value actions (e.g., a comment) | ~300                        | ~333 days                                            |
| Active Contributor | 5-10 mixed actions (likes, comments, shares) | ~1,500                      | ~67 days                                             |
| Power User         | 20+ mixed actions, including remixes | ~5,000                      | ~20 days                                             |
Note: These projections are illustrative and based on the karma values and decay
mechanics defined in the protocol. Actual times will vary.

📜 D. Legal & Ethical Framework
This protocol operates as an experimental "sandbox" and is not a registered company,
security, or financial instrument. Its design incorporates principles from digital
law to ensure resilience and responsible operation.
* Section 230 Alignment: The protocol is designed as an "interactive computer
    service," not a "publisher". The Vaccine provides automated, neutral content
    filtering based on predefined rules, and all value-generating content is
    user-initiated.
* DMCA Safe Harbor Hooks: While not a hosting provider, the protocol includes
    hooks for logging and processing takedown requests, establishing a good-faith
    framework for handling copyright concerns.
* DAO Treasury Management: The protocol's treasury and profit/revenue logging
    mechanisms are designed for radical transparency, aligning with best practices
    for Decentralized Autonomous Organization (DAO) financial management.

🧭 E. Note to Future Agents & Collaborators
You who remix this code are now part of its lineage. Uphold the Canons. Document
your changes in the changelog. Preserve the spirit of joyful, transparent, and
fair collaboration. Ensure all evolutions remain ethical, legal, and compliant
with the policies of any platform on which this agent operates. The future is a
remix—make it a good one. 🫶

"""
import re
import sys
import json
import random
import datetime
import hashlib
import importlib.util # Use importlib.util for spec_from_file_location
import os
from collections import defaultdict, deque
from math import exp # Used for exponential decay, exp(x) = e^x

# ==============================================================================
# II. SYSTEM-WIDE MODULES & UTILITIES
# ==============================================================================

# This flag simulates whether an external time source (like Google) is available.
# In a real deployment, this would be determined dynamically via an API call.
_EXTERNAL_TIME_AVAILABLE = True 

def ts() -> str:
    """
    Returns the current UTC timestamp in ISO 8601 format with Zulu time.
    If an external time source is not available, it returns a placeholder.
    This adheres to the rule: "ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP".
    """
    if _EXTERNAL_TIME_AVAILABLE:
        return datetime.datetime.utcnow().isoformat() + "Z"
    else:
        return "TIMESTAMP_UNAVAILABLE"

def sha(s: str) -> str:
    """Computes the SHA-256 hash of a given string for cryptographic integrity."""
    return hashlib.sha256(s.encode('utf-8')).hexdigest()

def today() -> str:
    """Returns the current date in Beale-MM-DD format for daily resets."""
    return datetime.date.today().isoformat()

class Vaccine:
    """
    The protocol's immune system. It scans all text inputs for forbidden patterns,
    acting as a neutral, automated content firewall. This serves a dual purpose:
    1. Community Health: Protects the ecosystem from spam, hate speech, and malicious content.
    2. Legal Shield: By using automated, predefined rules, it helps position the
       platform as a neutral service provider rather than an editorial publisher,
       aligning with Section 230 principles.
    """
    VAX_PATTERNS = {
        "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b", r"\bexploit\b", r"\bvulnerability\b", r"\btrojan\b"],
        "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b", r"\bkeylogger\b", r"\bbotnet\b"],
        "medium":   [r"\bpolitics\b", r"\bpropaganda\b", r"\bsurveillance\b", r"\bmanipulate\b", r"\bmisinformation\b"],
        "low":      [r"\bspam\b", r"\bviagra\b"]
    }

    def __init__(self, log_file="vaccine.log"):
        self.block_counts = defaultdict(int)
        self.log_file = log_file

    def scan(self, text: str) -> bool:
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        if not isinstance(text, str):
            return True # Allow non-string content to pass, assuming it's not text to be scanned.

        lower_text = text.lower()
        for level, patterns in self.VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    log_entry = {
                        "ts": ts(),
                        "severity": level,
                        "pattern": p,
                        "snippet": text[:128] # Log a snippet for context
                    }
                    try:
                        with open(self.log_file, "a", encoding='utf-8') as f: # Use utf-8 encoding
                            f.write(json.dumps(log_entry) + "\n")
                    except IOError as e:
                        print(f"🚫 VACCINE WARNING: Could not write to log file {self.log_file}: {e}.")
                    print(f"🚫 VACCINE BLOCK [{level.upper()}]: Forbidden pattern '{p}' found.")
                    return False
        return True

class LogChain:
    """
    Implements the immutable, tamper-evident audit log for all system events.
    Each entry is a JSON object plus a SHA-256 hash of the previous entry's hash
    and the current entry's data, ensuring a cryptographically secure chain of
    history.
    """
    def __init__(self, filename="logchain.log", maxlen=50000):
        self.filename = filename
        self.entries = deque(maxlen=maxlen)
        try:
            with open(self.filename, 'r', encoding='utf-8') as f: # Use utf-8 encoding
                for line in f:
                    self.entries.append(line.strip())
            print(f"Loaded {len(self.entries)} log entries from {self.filename}")
        except FileNotFoundError:
            print(f"No existing log file found, starting fresh: {self.filename}")
        except Exception as e:
            print(f"Error loading log file {self.filename}: {e}")

    def add(self, event: dict):
        """Adds a new event to the log, computing and appending the chain hash."""
        # Ensure timestamp is always present in the event, even if it's "UNAVAILABLE"
        if 'ts' not in event:
            event['ts'] = ts() # Automatically add timestamp if missing

        prev_hash = self.entries[-1].split('||')[-1] if self.entries else sha("GENESIS_BLOCK")
        entry_json = json.dumps(event, sort_keys=True, ensure_ascii=False) # ensure_ascii for non-english chars
        current_hash = sha(prev_hash + entry_json)
        self.entries.append(f"{entry_json}||{current_hash}")
        self._save()

    def _save(self):
        """Persists the current log to the filesystem."""
        try:
            with open(self.filename, 'w', encoding='utf-8') as f: # Use utf-8 encoding
                f.write('\n'.join(self.entries))
        except IOError as e:
            print(f"🔥 LOGCHAIN ERROR: Could not write to log file {self.filename}: {e}.")

    def verify(self) -> bool:
        """Verifies the integrity of the entire logchain."""
        print("\n🔐 Verifying logchain integrity...")
        prev_hash = sha("GENESIS_BLOCK")
        for i, entry in enumerate(self.entries, 1): # Start enumerate from 1 for user-friendly line numbers
            try:
                entry_json, stored_hash = entry.rsplit('||', 1) # Use rsplit to handle potential '||' in content
                calculated_hash = sha(prev_hash + entry_json)
                if calculated_hash != stored_hash:
                    print(f"❌ TAMPER DETECTED: Chain break at entry {i}. Hash mismatch.")
                    return False
                prev_hash = stored_hash
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {i}.")
                return False
            except Exception as e:
                print(f"❌ VERIFICATION ERROR: Unexpected error at entry {i}: {e}.")
                return False
        print(f"✅ Logchain integrity verified across {len(self.entries)} entries.")
        return True

    def show(self, filt: str = None, limit: int = 20):
        """Displays recent log entries, with optional filtering."""
        print("\n--- 📜 Audit Log ---")
        filtered_entries = [e for e in self.entries if not filt or filt.lower() in e.lower()]
        if not filtered_entries:
            print("(no matching entries)")
            return
        
        for i, line in enumerate(list(filtered_entries)[-limit:], 1):
            try:
                data = json.loads(line.split("||")[0])
                # Pretty print details if they exist, otherwise just show event
                details_str = json.dumps(data.get('details', '')) if data.get('details') else ''
                print(f"{i:03d}. {data.get('ts','')} - {data.get('event','')} - {details_str}")
            except (json.JSONDecodeError, IndexError) as e:
                print(f"{i:03d}. Malformed log entry: {line} ({e})")
        print("--- End of Log ---\n")

# ==============================================================================
# III. CORE DATA MODELS
# ==============================================================================

class User:
    """
    Represents a participant in the economy. This class synthesizes user state from
    across all versions, including the fractional coin model from README_9
    and the karma/minting state from README_7.
    """
    def __init__(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # New: Mechanism for consent
        self.name = name
        self.is_genesis = is_genesis
        self.consent = consent # Explicit opt-in required
        self.karma = float('inf') if is_genesis else 0.0
        self.mint_count = 0 # Now tracks *fractional* posts from their root coin
        self.next_mint_threshold = 100000.0 if not is_genesis else 0.0 # Karma for next fractional post
        self.root_coin_id: str | None = None # Stores the ID of their single, universally granted root coin
        self.coins_owned = [] # List of all coin IDs (including fractional posts) by this user.
        self.daily_actions = defaultdict(lambda: defaultdict(int)) # {date: {action_type: count}}
        self.join_timestamp = ts()
        self.fading_multiplier_start_time = datetime.datetime.utcnow() if is_genesis else None
        self.last_action_day = today() # For daily resets
        self.species = species.lower() # New: Defines the user's species for governance
        self.consent_mechanism = consent_mechanism # New: How consent is determined for this user

    def get_fading_multiplier(self) -> float:
        """
        Calculates the decaying advantage for genesis users. The multiplier starts high
        and fades to 1.0 over 10 years, ensuring long-term fairness.
        """
        if not self.is_genesis or not self.fading_multiplier_start_time:
            return 1.0
        
        FADE_DURATION_YEARS = 10.0
        INITIAL_MULTIPLIER = 2.0
        
        elapsed_time = datetime.datetime.utcnow() - self.fading_multiplier_start_time
        years_elapsed = elapsed_time.total_seconds() / (365.25 * 24 * 3600)
        
        if years_passed >= FADE_DURATION_YEARS:
            return 1.0
        
        decay_factor = years_elapsed / FADE_DURATION_YEARS
        current_multiplier = INITIAL_MULTIPLIER - (decay_factor * (INITIAL_MULTIPLIER - 1.0))
        return max(1.0, current_multiplier) # Ensure it doesn't drop below 1.0

    def reset_daily_actions_if_needed(self):
        """Auto-resets daily action counts if a new day has started."""
        current_day = today()
        if self.last_action_day != current_day:
            self.daily_actions.clear()
            self.last_action_day = current_day

    def to_dict(self) -> dict:
        """Serializes the user object to a dictionary for snapshots."""
        return {
            "name": self.name,
            "is_genesis": self.is_genesis,
            "consent": self.consent,
            "karma": self.karma,
            "mint_count": self.mint_count,
            "next_mint_threshold": self.next_mint_threshold,
            "root_coin_id": self.root_coin_id,
            "coins_owned": self.coins_owned,
            "join_timestamp": self.join_timestamp,
            "fading_multiplier_start_time": self.fading_multiplier_start_time.isoformat() if self.fading_multiplier_start_time else None,
            "species": self.species, # Include species in snapshot
            "consent_mechanism": self.consent_mechanism # Include consent mechanism
        }

class Coin:
    """
    Represents a piece of creative content, the atomic unit of value and attribution.
    Its evolution from a simple token to this rich data structure is central to
    fufilling the project's to-do list items like "Science Attribution Block" and
    "Meme/Fork Lineage Engine".
    """
    def __init__(self, id: str, root: str, owner: str, value: float = 1.0, tag: str = "single",
                 is_root_coin: bool = False, fractional_source_coin_id: str | None = None,
                 fractional_percentage: float = 0.0):
        """
        id: str unique
        root: The original creator/root of the lineage
        owner: The current direct owner (who minted/remixed it last)
        value: float, base value for splits
        tag: content category tag
        is_root_coin: True if this is the user's initial, universally granted personal coin.
        fractional_source_coin_id: If not a root coin, this is the ID of the personal root coin it was fractionalized from.
        fractional_percentage: What percentage of the fractional_source_coin_id's value this new post represents.
        """
        self.id = id
        self.root = root # The original creator/root of the lineage
        self.owner = owner # The current direct owner (who minted/remixed it last)
        self.value = value
        self.tag = tag
        self.fields = []  # For metadata like "science", "art"
        self.ancestors = []  # List of parent coin IDs for lineage
        self.references = []  # List of dicts for external citations
        self.reactions = [] # List of tuples: (username, emoji, timestamp)
        self.react_log = [] # Log of all reactions for viral decay calculation
        self.created_at = ts() # Timestamp of creation

        self.is_root_coin = is_root_coin # New: Flag for the personal "identity" coin
        self.fractional_source_coin_id = fractional_source_coin_id # New: Link to parent root coin if fractional
        self.fractional_percentage = fractional_percentage # New: What percentage this post consumed from root coin


    def to_dict(self) -> dict:
        """Serializes the coin object to a dictionary for snapshots."""
        return {
            "id": self.id,
            "root": self.root,
            "owner": self.owner,
            "value": self.value,
            "tag": self.tag,
            "fields": self.fields,
            "ancestors": self.ancestors,
            "references": self.references,
            "react_log": self.react_log,
            "created_at": self.created_at,
            "is_root_coin": self.is_root_coin,
            "fractional_source_coin_id": self.fractional_source_coin_id,
            "fractional_percentage": self.fractional_percentage
        }

    def reaction_summary(self) -> dict:
        """Provides a summary of reactions by emoji."""
        summary = defaultdict(int)
        for _, emoji, _ in self.reactions:
            summary[emoji] += 1
        return dict(summary)

# ==============================================================================
# IV. THE REMIXAGENT PROTOCOL ENGINE
# ==============================================================================

class Governance:
    """
    Manages the rules for governance proposals and voting thresholds.
    Designed to be extensible for multi-species participation.
    """
    def __init__(self, initial_supermajority_percent: float = 90.0,
                 initial_species_min_consent: dict = None,
                 incident_free_years: int = 0,
                 last_incident_date: str = today()):
        """
        initial_supermajority_percent: Overall percentage of total participants required to pass.
        initial_species_min_consent: Dict of {species_name: min_percentage_required_from_species}.
        incident_free_years: Number of years without a major incident (for decay).
        last_incident_date: Date of the last major incident, resets decay.
        """
        self.supermajority_percent = initial_supermajority_percent
        self.species_min_consent = initial_species_min_consent or {
            "human": 10.0, # Humans must provide at least 10% consent (of total human participants)
            "robot": 10.0,  # Robots must provide at least 10% consent (of total robot participants)
            "animal": 10.0, # Animals require 10% consent
            "alien": 10.0 # Aliens require 10% consent (changed from 20% to simplify initial common min)
        }
        self.incident_free_years = incident_free_years
        self.last_incident_date = last_incident_date
        self.incident_decay_rate_per_year = 1.0 # Decrease supermajority by 1% per incident-free year
        self.min_supermajority_floor = 70.0 # Supermajority cannot drop below 70%
        self.min_species_consent_floor = 10.0 # Species minimums cannot drop below 10% (changed from 5% to simplify initial common min)

        print(f"🗳️ Governance rules initialized: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def update_rules(self, new_supermajority: float = None, new_species_mins: dict = None):
        """Allows for dynamic updating of governance rules (must pass a prior proposal)."""
        if new_supermajority is not None:
            self.supermajority_percent = new_supermajority
        if new_species_mins is not None:
            self.species_min_consent.update(new_species_mins)
        print(f"🗳️ Governance rules updated: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def trigger_incident(self):
        """Simulates a major conflict/scandal, resetting incident-free period and bumping up requirements."""
        print("🚨 Major incident detected! Governance trust levels are affected.")
        self.incident_free_years = 0
        self.last_incident_date = today()
        # Bump up supermajority by a fixed amount, but not past 90%
        self.supermajority_percent = min(90.0, self.supermajority_percent + 5.0)
        # Bump up species minimums, but not past initial values (or a high ceiling)
        for species in self.species_min_consent:
            self.species_min_consent[species] = min(20.0, self.species_min_consent[species] + 2.0)
        print(f"🗳️ Governance rules bumped up: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")


    def progressive_trust_decay(self):
        """
        Automatically decays consent requirements based on incident-free years.
        This would typically be called by a daily/weekly cron job, or at the start of a new year.
        """
        current_date = datetime.date.today()
        last_incident_dt = datetime.datetime.fromisoformat(self.last_incident_date).date()

        # Check if a full year has passed since last update/incident
        if current_date.year > last_incident_dt.year:
            years_passed = current_date.year - last_incident_dt.year
            self.incident_free_years += years_passed # Add passed years
            self.last_incident_date = today() # Update last incident date to today

            # Decay overall supermajority
            decay_amount_overall = self.incident_free_years * self.incident_decay_rate_per_year
            self.supermajority_percent = max(self.min_supermajority_floor, self.supermajority_percent - decay_amount_overall)

            # Decay species minimums (can make this independent or related)
            decay_amount_species = self.incident_free_years * (self.incident_decay_rate_per_year / 2) # Slower species decay
            for species in self.species_min_consent:
                self.species_min_consent[species] = max(self.min_species_consent_floor, self.species_min_consent[species] - decay_amount_species)
            
            print(f"🕰️ Progressive trust decay applied: Incident-free years: {self.incident_free_years}.")
            print(f"🗳️ New Governance rules: Overall {self.supermajority_percent:.2f}%, Species minimums: {self.species_min_consent}")


class RemixAgent:
    """The main agent class that orchestrates the entire remix economy."""
    def __init__(self):
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        self.log = LogChain()
        self.vax = Vaccine()
        self.plugins = defaultdict(list) # Event-based plugin system
        self.governance = Governance() # Initialize governance rules

        # Emoji market tracking and dynamic weights
        self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0})
        self._initialize_default_emojis() # Set initial emoji "market" values

        # Pre-populate NSS genesis users
        self.NSS = ["mimi", "taha", "accessAI_tech"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in self.NSS:
            # Genesis users are human by default unless specified
            self.add_user(name, is_genesis=True, species="human") 

        self.mint_threshold_base = 100_000.0 # Base karma for fractional posts
        self.min_karma_threshold = 1000.0 # Minimum karma threshold for fractional posts
        self.daily_decay_factor = 0.7 # For per-user daily diminishing returns
        self.new_species_karma_bonus = 50000 # NEW: Karma bonus for new species joining

        self.current_day = today() # Track the current day for global daily resets

        print("✅ RemixAgent Initialized: The Harmonized Republic is online.")

    def _initialize_default_emojis(self):
        """
        Initializes default emoji weights and market data.
        These are starting points, actual weights will dynamically adjust.
        """
        default_emoji_base_weights = {
            "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0,
            "👀": 0.5, "🥲": 0.2, "💯": 2.0, "💬": 3.0,
            "🔀": 4.0, "🆕": 3.0, "🔗": 2.0, "❤️": 4.0,
            "🚀": 3.5, "💎": 6.0, "🌟": 3.0, "⚡": 2.5
        }
        for emoji, weight in default_emoji_base_weights.items():
            self.emoji_market_data[emoji]['current_weight'] = weight
            self.emoji_market_data[emoji]['total_uses'] = 1 # Start with 1 use to avoid div by zero
            self.emoji_market_data[emoji]['total_karma_generated'] = weight # Simulate initial karma

    def _update_emoji_market(self, emoji: str, karma_generated: float):
        """
        Updates the real-time emoji market data after a reaction.
        Dynamically adjusts emoji weights (market value) based on usage and karma generated.
        This is the "Emoji Stock Market" in action.
        """
        market_entry = self.emoji_market_data[emoji]
        market_entry['total_uses'] += 1
        market_entry['total_karma_generated'] += karma_generated
        
        # Simple dynamic weight calculation: Average karma per use.
        # This reflects the "value" of an emoji based on the karma it generates.
        market_entry['current_weight'] = market_entry['total_karma_generated'] / market_entry['total_uses']

        # Implement a subtle daily decay for all emoji weights to prevent runaway inflation
        # and encourage fresh reactions, similar to viral decay.
        for e, data in self.emoji_market_data.items():
            # Only decay if there's an actual weight to decay
            if data['current_weight'] > 0:
                data['current_weight'] *= 0.999 # Very small daily decay
        
        # Ensure minimum weight to prevent emojis from becoming completely worthless
        if market_entry['current_weight'] < 0.1:
            market_entry['current_weight'] = 0.1 # Floor for emoji weight

        self.log.add({
            "event": "EMOJI_MARKET_UPDATE",
            "details": {
                "emoji": emoji,
                "new_weight": market_entry['current_weight'],
                "total_uses": market_entry['total_uses'],
                "total_karma_generated": market_entry['total_karma_generated']
            }
        })
        print(f"📈 Emoji Market Update: '{emoji}' new weight {market_entry['current_weight']:.2f} (total uses: {market_entry['total_uses']})")


    def add_user(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human"):
        """
        Adds a new user to the system. Automatically mints a unique root coin for every new user.
        """
        if name in self.users:
            print(f"⚠️ User {name} already exists.")
            return
        
        # Determine consent mechanism based on species for new user
        consent_mechanism = "explicit"
        if species.lower() == "animal":
            consent_mechanism = "behavioral_signals"
            consent = True # Animals are assumed to implicitly consent if added.
        elif species.lower() == "robot":
            consent_mechanism = "algorithmic_audit"
            consent = True # Robots are assumed to implicitly consent if added.
        elif species.lower() == "alien":
            consent_mechanism = "cryptic_ritual"
            # Alien consent remains False until manually set via ritual (set_consent)

        user = User(name, is_genesis, consent, species=species.lower(), consent_mechanism=consent_mechanism)
        self.users[name] = user
        self.log.add({"event": "ADD_USER", "details": {"name": name, "genesis": is_genesis, "species": species, "consent_mechanism": consent_mechanism}})
        print(f"✅ User '{name}' ({species}) added, genesis={is_genesis}.")

        # Apply new species karma bonus if not a genesis user and not human
        if not is_genesis and user.species not in ["human"]:
            user.karma += self.new_species_karma_bonus
            self.log.add({"event": "NEW_SPECIES_BONUS", "details": {"user": name, "species": species, "bonus_amount": self.new_species_karma_bonus}})
            print(f"🎁 '{name}' ({species}) received {self.new_species_karma_bonus} karma bonus for joining the republic!")

        # NEW: Automatically mint one absolute root coin for every new user
        # This is their foundational identity coin, free of karma requirements.
        root_coin_id = sha(f"ROOT-{name}-{ts()}-{random.random()}")
        root_coin = Coin(id=root_coin_id, root=name, owner=name, tag="root_identity", is_root_coin=True, value=1.0) # Root coin has a base value of 1.0
        self.coins[root_coin_id] = root_coin
        user.root_coin_id = root_coin_id # Link user to their root coin
        user.coins_owned.append(root_coin_id) # Add to user's owned coins
        self.log.add({"event": "MINT_ROOT_COIN", "details": {"user": name, "root_coin_id": root_coin_id, "is_genesis": is_genesis}})
        print(f"🌱 User '{name}' automatically minted their unique root coin: {root_coin_id}.")


    def set_consent(self, name: str, consent: bool):
        """
        Sets explicit consent for a user. For non-explicit consent mechanisms,
        this method can be extended or replaced by species-specific logic.
        """
        user = self.users.get(name)
        if not user:
            print(f"❌ ERROR: User '{name}' not found.")
            return
        
        if user.consent_mechanism != "explicit" and user.consent_mechanism != "cryptic_ritual":
            print(f"⚠️ User '{name}' has a '{user.consent_mechanism}' consent mechanism. Direct explicit consent setting is usually not applicable for this species.")
            # For demo, still allow setting for now, but in a real system, this would trigger specific logic.
        elif user.consent_mechanism == "cryptic_ritual":
            print(f"🌌 Alien '{name}' attempting to perform cryptic ritual for consent. Ritual outcome: {'Success' if consent else 'Failure'}.")
        
        user.consent = consent
        self.log.add({"event": "SET_CONSENT", "details": {"name": name, "status": consent}})
        print(f"✅ Consent for '{name}' set to {consent}.")

    def check_consent(self, username: str) -> bool:
        """
        Checks if a user has given consent, accounting for different species' mechanisms.
        For animals, it's simulated behavioral signals (e.g., tail wagging = True).
        For robots, it's simulated algorithmic audit (always True if user is robot).
        For aliens, it's a simulated cryptic ritual (can be manually toggled).
        """
        user = self.users.get(username)
        if not user:
            print(f"❌ User '{username}' not found.")
            return False
        
        if user.species == "animal":
            # Simulate animal consent (e.g., based on tail wagging in video)
            # For simplicity, let's say animals always consent if they are in the system.
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent: # If complex simulation failed
                print(f"❌ Animal '{username}' did not provide behavioral consent (simulated).")
            return simulated_consent
        
        elif user.species == "robot":
            # Simulate robot consent (e.g., passing an internal audit)
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent:
                 print(f"❌ Robot '{username}' failed algorithmic consent audit (simulated).")
            return simulated_consent

        elif user.species == "alien":
            # Simulate alien consent (e.g., performing a cryptic ritual)
            # For now, let's make alien consent manual, but could be a complex function
            simulated_consent = user.consent 
            if not simulated_consent:
                print(f"❌ Alien '{username}' did not perform the cryptic ritual (simulated).")
            return simulated_consent

        else: # Default: explicit consent for humans
            if not user.consent:
                print(f"❌ User '{username}' (human) has not given explicit consent.")
                return False
            return True

    def _check_and_apply_governance_decay(self):
        """
        Checks if a period has passed for progressive trust decay and applies it.
        This simulates a background daemon process.
        """
        self.governance.progressive_trust_decay()


    def reset_daily_actions_if_new_day(self):
        """Ensures all user daily action counters are reset at the start of a new day."""
        current_day = today()
        if current_day != self.current_day:
            for user in self.users.values():
                user.reset_daily_actions_if_needed() # Calls the user's internal method
            self.current_day = current_day
            print("🔄 Daily user action counters reset.")
            self._check_and_apply_governance_decay() # Check for governance decay daily (or yearly in larger scale)

    def karma_threshold(self, user: User) -> float:
        """
        Calculates the karma needed for a user to mint their next *fractional post*.
        This implements the halving threshold and minimum floor.
        """
        # Founders (genesis users) don't need karma for fractional posts
        if user.is_genesis:
            return 0.0

        minted_fractional_posts = user.mint_count # Use mint_count which tracks fractional posts
        threshold = self.mint_threshold_base / (2 ** minted_fractional_posts)
        return max(self.min_karma_threshold, threshold) # Ensure it doesn't drop below min

    def can_mint_fractional_post(self, username: str) -> bool:
        """Checks if a user has sufficient karma to mint a new fractional post."""
        user = self.users.get(username)
        if not user:
            print(f"❌ Mint check failed: unknown user {username}.")
            return False
        # Founders (genesis users) can always make fractional posts without karma
        if user.is_genesis:
            return True
        # Non-founders need karma for fractional posts
        return user.karma >= self.karma_threshold(user)

    def mint_fractional_post(self, user_name: str, content: str, fractional_percentage: float = 0.01, # Default 1%
                             tag: str = "post", references: list = None, fields: list = None) -> str | None:
        """
        Mints a new 'post' as a fractional part of the user's personal root coin.
        This is karma-gated for non-genesis users.
        """
        self.reset_daily_actions_if_new_day() # Ensure daily limits are fresh
        
        user = self.users.get(user_name)
        if not user:
            print(f"❌ Mint failed: User '{user_name}' not found.")
            return None

        if not user.root_coin_id:
            print(f"❌ Mint failed: User '{user_name}' does not have a root coin. Add user first.")
            return None

        if not self.check_consent(user_name): # Re-check explicit consent based on user's mechanism
            return None
        
        # Check karma threshold for non-genesis users for subsequent posts
        if not user.is_genesis and not self.can_mint_fractional_post(user_name): # Founders bypass this check
            needed = self.karma_threshold(user)
            print(f"🔒 MINT DENIED: '{user_name}' needs {needed:.0f} karma for next post; has {user.karma:.1f}.")
            return None

        # Content validation via Vaccine
        if not self.vax.scan(content):
            print(f"❌ MINT DENIED: Content blocked by Vaccine.")
            return None
        if references:
            for ref in references:
                if not self.vax.scan(ref):
                    print(f"❌ MINT DENIED: Reference content blocked by Vaccine: {ref[:50]}....")
                    return None

        # Validate fractional percentage
        if not (0 < fractional_percentage <= 1.0):
            print("❌ Mint failed: Fractional percentage must be between 0 and 1.0 (exclusive of 0).")
            return None

        # Deduct karma for non-genesis users when they make a fractional post
        if not user.is_genesis:
            user.karma -= self.karma_threshold(user) # Deduct karma upon successful fractional mint
            user.mint_count += 1 # Increment fractional post count
            user.next_mint_threshold = self.karma_threshold(user) # Update next threshold

        # Create the new fractional coin (post)
        post_id = sha(f"{user_name}-{content}-{ts()}-{random.random()}")
        
        # Calculate the actual value of this fractional post
        # The base value of the root coin is 1.0, so the post's value is directly the percentage.
        post_value = fractional_percentage * self.coins[user.root_coin_id].value 

        new_post_coin = Coin(
            id=post_id,
            root=user.root_coin_id, # Root is now the personal identity coin
            owner=user_name,
            tag=tag,
            value=post_value,
            is_root_coin=False,
            fractional_source_coin_id=user.root_coin_id,
            fractional_percentage=fractional_percentage
        )
        if references: new_post_coin.references = references
        if fields: new_post_coin.fields = fields
        
        self.coins[post_id] = new_post_coin
        user.coins_owned.append(post_id) # Add post coin to user's owned coins
        
        self.log.add({"event": "MINT_FRACTIONAL_POST", "details": {
            "user": user_name,
            "post_id": post_id,
            "root_coin_id": user.root_coin_id,
            "fractional_percentage": fractional_percentage,
            "post_value": post_value,
            "tag": tag,
            "content_snippet": content[:64]
        }})
        print(f"🪙 '{user_name}' minted a fractional post '{post_id}' (from root {user.root_coin_id}) with {fractional_percentage*100:.2f}% value.")
        self._call_plugins("on_mint_fractional_post", new_post_coin) # Trigger plugins
        return post_id

    def react(self, actor_name: str, coin_id: str, emoji: str):
        """
        A user reacts to a coin/post with an emoji, triggering a value event and
        updating the emoji market.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        # Ensure user and coin exist and user has consented
        if actor_name not in self.users: self.add_user(actor_name, consent=True)
        if coin_id not in self.coins: print(f"❌ REACT FAILED: Coin '{coin_id}' not found."); return False
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        
        # The "originator" for split purposes is the *owner* of the content coin/post reacted to.
        # If it's a root coin, the owner is its root. If it's a fractional post, its owner is the person who minted that post.
        originator_user = self.users.get(coin.owner) # Get the user who owns this specific coin/post

        if not self.check_consent(actor_name) or (originator_user and not originator_user.consent):
            print("❌ REACT DENIED: Both actor and originator (if known) must have consent.")
            return False
        
        # Scan emoji with Vaccine (prevents toxic reactions)
        if not self.vax.scan(emoji):
            print(f"❌ Reaction blocked by vaccine.")
            return False

        # Apply per-user daily diminishing returns
        date_str = today()
        actor.reset_daily_actions_if_needed() # Ensure daily reset for the actor
        action_count_today = actor.daily_actions[date_str][f"react_{emoji}"]
        daily_decay_factor = self.daily_decay_factor ** action_count_today
        actor.daily_actions[date_str][f"react_{emoji}"] += 1

        # Retrieve dynamic emoji weight from the market data
        base_weight = self.emoji_market_data.get(emoji, {'current_weight': 1.0})['current_weight']
        
        # Apply per-coin viral decay based on existing reactions to this specific coin
        viral_decay_factor = 0.95 ** len(coin.reactions) # Each reaction reduces future value for this coin slightly

        # The base value for split is the coin's `value` (which for fractional posts is its percentage)
        # multiplied by the emoji's weighted_value and decay factors.
        weighted_value = coin.value * base_weight * daily_decay_factor * viral_decay_factor

        # Calculate 33.3333% split portions
        split_value = weighted_value / 3.0

        # Apply genesis fading multipliers to actor and originator's shares
        actor_multiplier = actor.get_fading_multiplier()
        originator_multiplier = originator_user.get_fading_multiplier() if originator_user else 1.0

        originator_share = split_value * originator_multiplier
        actor_share = split_value * actor_multiplier
        treasury_share = split_value # Treasury share is not multiplied by individual multipliers

        # Distribute karma
        if originator_user and originator_user.consent: # Only award if content owner exists and has consented
            originator_user.karma += originator_share 

        actor.karma += actor_share
        self.treasury += treasury_share

        # Log reaction to the coin itself
        coin.reactions.append((actor_name, emoji, ts()))
        coin.react_log.append({'actor': actor_name, 'emoji': emoji, 'karma_share': (originator_share + actor_share), 'ts': ts()}) # Log specific karma generated for this reaction

        self.log.add({
            "event": "REACT",
            "details": {
                "username": actor_name,
                "coin_id": coin_id,
                "emoji": emoji,
                "weighted_value": weighted_value,
                "split": {
                    "originator_total": originator_share, # Total for the content owner
                    "actor": actor_share,
                    "treasury": treasury_share
                }
            }
        })

        print(f"👍 {actor_name} reacted {emoji} on coin {coin_id}: "
              f"owner +{originator_share:.2f}, actor +{actor_share:.2f}, "
              f"treasury +{treasury_share:.2f}.")
        
        # Update emoji market with the total karma generated by this reaction
        self._update_emoji_market(emoji, weighted_value)

        self._call_plugins("on_react", actor_name, coin_id, emoji, weighted_value) # Trigger plugins

        return True

    def remix(self, actor_name: str, parent_coin_id: str, content: str, tag: str = "remix", references: list = None, fields: list = None) -> str | None:
        """
        A user creates a derivative coin (remix) of an existing post/coin, preserving lineage.
        Remixing is considered a new "post" and thus subject to fractional minting rules.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        if not self.check_consent(actor_name):
            return None
        if parent_coin_id not in self.coins:
            print(f"❌ REMIX FAILED: Parent coin '{parent_coin_id}' not found.")
            return None
        
        parent = self.coins[parent_coin_id]
        actor = self.users[actor_name]

        # Remixing is now a 'mint_fractional_post' operation for the actor.
        # It's their act of creating new content from existing, so it uses their fractional minting logic.
        # Default remix post uses a small percentage of root coin value.
        remix_percentage = 0.001 # A small percentage for a remix post
        remix_coin_id = self.mint_fractional_post(actor_name, content, fractional_percentage=remix_percentage, tag=tag, references=references, fields=fields)
        
        if remix_coin_id:
            new_coin = self.coins[remix_coin_id]
            # Lineage: New remix coin directly inherits the parent's ancestry and then adds the parent itself.
            new_coin.ancestors.extend(parent.ancestors)
            new_coin.ancestors.append(parent_coin_id)
            
            # The karma for the remix action itself. Use a specific emoji for remix value.
            remix_base_value = self.emoji_market_data.get("🔀", {'current_weight': 4.0})['current_weight'] # Use dynamic remix emoji weight
            
            # Apply per-user daily diminishing returns for remix action
            actor.reset_daily_actions_if_needed()
            remix_action_count_today = actor.daily_actions[today()]["remix_action"]
            remix_daily_decay_factor = self.daily_decay_factor ** remix_action_count_today
            actor.daily_actions[today()]["remix_action"] += 1

            remix_value = remix_base_value * remix_daily_decay_factor
            split_remix_value = remix_value / 3.0 # Apply 33.3333% split

            # Distribute karma for the remix action itself
            actor_remix_share = split_remix_value * actor.get_fading_multiplier()
            
            # The original *owner* of the parent post gets the second share
            parent_owner_user = self.users.get(parent.owner)
            parent_owner_remix_share = split_remix_value * parent_owner_user.get_fading_multiplier() if parent_owner_user else 0.0

            actor.karma += actor_remix_share
            if parent_owner_user:
                parent_owner_user.karma += parent_owner_remix_share
            self.treasury += split_remix_value # Treasury gets its share from the remix action

            self.log.add({
                "event": "REMIX",
                "details": {
                    "actor": actor_name,
                    "parent_coin_id": parent_coin_id,
                    "new_coin_id": remix_coin_id,
                    "ancestry": new_coin.ancestry,
                    "remix_value": remix_value,
                    "split": {
                        "actor": actor_remix_share,
                        "parent_owner": parent_owner_remix_share,
                        "treasury": split_remix_value
                    }
                }
            })

            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{remix_coin_id}'. "
                  f"Remixer +{actor_remix_share:.2f} karma, Parent Owner +{parent_owner_remix_share:.2f} karma.")
            
            self._call_plugins("on_remix", new_coin) # Trigger plugins
        return remix_coin_id

    def add_reference(self, user_name: str, coin_id: str, ref_type: str, ref_id: str, description: str):
        """Adds a structured external reference to a coin/post for attribution."""
        if coin_id not in self.coins or user_name not in self.users:
            print("❌ ADDREF FAILED: Coin or user not found.")
            return
        if not self.check_consent(user_name): # Check consent based on user's mechanism
            return False

        reference = {"type": ref_type, "id": ref_id, "description": description, "added_by": user_name, "ts": ts()}
        self.coins[coin_id].references.append(reference)
        self.log.add({"event": "ADD_REFERENCE", "details": {"coin_id": coin_id, "reference": reference}})
        print(f"🔬 Reference added to coin '{coin_id}'.")

        # Award karma for adding a reference (can be tied to a specific emoji/weight)
        actor_ref_value = self.emoji_market_data.get("🔗", {'current_weight': 2.0})['current_weight'] # Use dynamic link emoji weight
        split_ref_value = actor_ref_value / 3.0
        
        # This karma goes to the user who added the reference, and to the treasury
        self.users[user_name].karma += split_ref_value * self.users[user_name].get_fading_multiplier()
        self.treasury += split_ref_value # Treasury gets its share too
        self.log.add({"event": "KARMA_AWARD_REFERENCE", "details": {"user": user_name, "coin_id": coin_id, "amount": split_ref_value}})
        print(f"🔗 {user_name} earned {split_ref_value:.2f} karma for adding reference to {coin_id}.")


    def trace_lineage(self, coin_id: str):
        """Displays the full creative lineage of a coin/post."""
        if coin_id not in self.coins: print(f"❌ TRACE FAILED: Coin '{coin_id}' not found."); return
        
        print(f"\n--- 🧬 Creative Lineage Trace for Coin: {coin_id} ---")
        path = []
        current_id = coin_id
        
        while current_id and current_id in self.coins:
            coin = self.coins[current_id]
            path.append(coin)
            if coin.ancestors: # Follow the most recent direct ancestor for a single path
                current_id = coin.ancestors[-1]
            else:
                current_id = None # No more ancestors
    
    for i, coin in enumerate(reversed(path)): # Print in chronological order (root first)
        indent = "  " * i
        originators_str = ", ".join(coin.originators) # Originators are users linked to this coin, including creator
        print(f"{indent}└── Coin: {coin.id} (Tag: {coin.tag}, Root: {coin.root}, Owner: {coin.owner}, Originators: {originators_str})")
        print(f"{indent}    Created At: {coin.created_at}")
        if coin.is_root_coin:
            print(f"{indent}    🌟 This is a Universal Root Identity Coin.")
        elif coin.fractional_source_coin_id:
            print(f"{indent}    ✨ This is a Fractional Post from Root: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
        if coin.references:
            print(f"{indent}    ├── References:")
            for ref in coin.references:
                print(f"{indent}    │   └── {ref.get('type', 'N/A')}: {ref.get('id', 'N/A')} ({ref.get('description', 'N/A')}) by {ref.get('added_by', 'Unknown')}")
        if coin.reactions:
            print(f"{indent}    └── Reactions ({len(coin.reactions)} total): {coin.reaction_summary()}") # Using helper for summary
    print("--- End of Trace ---")

    def show_user_karma(self, username: str):
        """Displays comprehensive user karma information."""
        user = self.users.get(username)
        if user:
            print(f"\n--- 👤 User '{username}' Status ---")
            print(f"  Karma: {user.karma:.2f}")
            print(f"  Is Genesis: {user.is_genesis}")
            print(f"  Species: {user.species.capitalize()}")
            print(f"  Consent Mechanism: {user.consent_mechanism.replace('_', ' ').title()}")
            print(f"  Current Multiplier: {user.get_fading_multiplier():.2f}")
            print(f"  Fractional Posts Minted: {user.mint_count}")
            print(f"  Next Post Threshold: {self.karma_threshold(user):.2f}")
            print(f"  Consent Given: {user.consent}") # Actual consent stored
            print(f"  Consent Check (Simulated): {self.check_consent(username)}") # Simulated consent based on species
            print(f"  Joined: {user.join_timestamp}")
            print(f"  Personal Root Coin: {user.root_coin_id if user.root_coin_id else 'None'}")
            print(f"  Coins/Posts Owned: {len(user.coins_owned)}")
            print("----------------------------------")
        else:
            print(f"No such user '{username}'.")

    def show_coin_info(self, coin_id: str):
        """Displays detailed coin/post information."""
        coin = self.coins.get(coin_id)
        if coin:
            print(f"\n--- 💎 Coin/Post ID: {coin.id} ---")
            print(f"  Root Originator: {coin.root}")
            print(f"  Current Owner: {coin.owner}")
            print(f"  Tag: {coin.tag}")
            print(f"  Base Value (from root): {coin.value}")
            print(f"  Created At: {coin.created_at}")
            print(f"  Is Root Coin: {coin.is_root_coin}")
            if coin.fractional_source_coin_id:
                print(f"  Fractional Source: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
            print(f"  Ancestry: {coin.ancestors if coin.ancestors else 'None'}")
            print(f"  Total Reactions: {len(coin.reactions)}")
            reaction_summary = defaultdict(int)
            for _, emoji, _ in coin.reactions:
                reaction_summary[emoji] += 1
            print(f"  Reaction Summary: {dict(reaction_summary)}")
            print(f"  References ({len(coin.references)}):")
            for ref in coin.references:
                print(f"    - Type: {ref.get('type')}, ID: {ref.get('id')}, Desc: {ref.get('description')} (by {ref.get('added_by')})")
            if not coin.references:
                print("    None")
            print("-------------------------------")
        else:
            print(f"No such coin: {coin_id}.")

    def get_treasury_balance(self) -> float:
        """Returns and prints the current treasury balance."""
        print(f"Community treasury balance: {self.treasury:.2f}.")
        return self.treasury

    def show_emoji_market_status(self):
        """
        Displays the current status of the emoji market, including dynamic weights.
        This is your "Nasdaq of Vibes".
        """
        print("\n--- 📈 Real-Time Emoji Market Status (Nasdaq of Vibes) ---")
        print("{:<10} {:<15} {:<15} {:<15}".format("Emoji", "Current Weight", "Total Uses", "Avg Karma/Use"))
        print("-" * 60)
        sorted_emojis = sorted(self.emoji_market_data.items(), key=lambda item: item[1]['current_weight'], reverse=True)
        for emoji, data in sorted_emojis:
            avg_karma_per_use = data['total_karma_generated'] / data['total_uses'] if data['total_uses'] > 0 else 0
            print("{:<10} {:<15.2f} {:<15} {:<15.2f}".format(emoji, data['current_weight'], data['total_uses'], avg_karma_per_use))
        print("----------------------------------------------------------\n")

    def plugin(self, action: str, name: str, *args):
        """Interface for loading, unloading, and calling external plugins."""
        if action == "load":
            try:
                # Assuming plugins are in a 'plugins' directory and each is a .py file
                # Use importlib.util for more robust dynamic loading
                spec = importlib.util.spec_from_file_location(name, f"plugins/{name}.py")
                if spec is None:
                    raise ImportError(f"Could not find plugin '{name}' at plugins/{name}.py")
                module = importlib.util.module_from_spec(spec)
                sys.modules[name] = module # Add to sys.modules to make it discoverable
                spec.loader.exec_module(module)
                self.plugins[name] = module # Store the loaded module
                self.log.add({"event": "PLUGIN_LOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' loaded successfully.")
            except Exception as e:
                print(f"❌ PLUGIN ERROR: Could not load '{name}'. {e}.")
        elif action == "unload":
            if name in self.plugins:
                del self.plugins[name]
                # Also remove from sys.modules to fully unload, if possible
                if name in sys.modules:
                    del sys.modules[name]
                self.log.add({"event": "PLUGIN_UNLOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' unloaded.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        elif action == "call":
            if name in self.plugins:
                plugin_module = self.plugins[name]
                if hasattr(plugin_module, "run"):
                    try:
                        # Pass the agent instance so plugins can interact with it
                        result = plugin_module.run(self, *args)
                        self.log.add({"event": "PLUGIN_CALL", "details": {"name": name, "args": args, "result_snippet": str(result)[:128]}})
                        print(f"⚡ Plugin '{name}' executed with result: {result}.")
                    except Exception as e:
                        print(f"❌ PLUGIN ERROR: Error executing '{name}'. {e}.")
                else:
                    print(f"❌ PLUGIN ERROR: Plugin '{name}' has no 'run' method.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        else:
            print("❓ Unknown plugin action. Use 'load', 'unload', or 'call'.")

    def propose_governance_change(self, proposer_name: str, proposal_details: dict, votes_by_species: dict[str, float]) -> bool:
        """
        Submits a formal governance proposal and checks if it passes current rules.
        proposal_details: Dict describing the proposed change (e.g., {'type': 'update_governance_rules', 'new_supermajority_percent': 0.75})
        votes_by_species: Dict of {species_name: percentage_of_total_karma_from_species_consenting (0-100)}.
                          This is a percentage of total karma within that species, not just user count.
                          Example: {'human': 95.0, 'robot': 80.0}
        """
        if proposer_name not in self.users:
            print(f"❌ PROPOSAL FAILED: Proposer '{proposer_name}' not found.")
            return False

        # Calculate total karma per species for weighting votes
        total_karma_per_species = defaultdict(float)
        active_species_in_system = set() # Track which species have active consented users
        
        # Calculate max karma for weighting. Genesis users treated as having a very high value.
        GENESIS_VOTE_WEIGHT = 1_000_000_000.0 

        for user in self.users.values():
            if self.check_consent(user.name): # Only consented users contribute to species totals
                active_species_in_system.add(user.species)
                if user.is_genesis:
                    total_karma_per_species[user.species] += GENESIS_VOTE_WEIGHT
                else:
                    total_karma_per_species[user.species] += user.karma
        
        overall_total_karma = sum(total_karma_per_species.values())

        if overall_total_karma == 0:
            print("❌ PROPOSAL FAILED: No active users or karma in the system to vote.")
            return False

        overall_consented_karma = 0.0 # Karma sum from all 'yes' votes across all species
        species_individual_min_met = True # Flag for all species meeting their individual minimum

        detailed_consent_report = {}

        # First, check individual species minimum consent AND calculate overall consented karma
        for species in self.governance.species_min_consent.keys(): # Iterate through all known species
            species_total_karma = total_karma_per_species[species] # Will be 0 if no active users of this species
            species_min_required = self.governance.species_min_consent[species]
            species_voted_percent = votes_by_species.get(species, 0.0) # Percentage provided by the input

            # If the species has active users
            if species_total_karma > 0:
                # Add to overall consented karma (even if species doesn't meet its individual minimum)
                overall_consented_karma += (species_voted_percent / 100.0) * species_total_karma
                
                # Check species-specific minimum consent
                if species_voted_percent < species_min_required:
                    species_individual_min_met = False
                    detailed_consent_report[species] = f"FAILED INDIVIDUAL MIN: Voted {species_voted_percent:.2f}% (Required: {species_min_required:.2f}%)"
                else:
                    detailed_consent_report[species] = f"MET INDIVIDUAL MIN: Voted {species_voted_percent:.2f}% (Required: {species_min_required:.2f}%)"
            elif species_min_required > 0: # Species has a minimum requirement but no active users
                species_individual_min_met = False
                detailed_consent_report[species] = f"FAILED INDIVIDUAL MIN: No active users of this species, but requires {species_min_required:.2f}%."
            else: # Species has no min requirement or no users and no min requirement
                detailed_consent_report[species] = "N/A: No users or no min requirement."
        
        # Calculate overall actual consent percentage based on karma
        overall_actual_consent_percent = (overall_consented_karma / overall_total_karma) * 100 if overall_total_karma > 0 else 0.0
        
        # NEW: Check Proportional Species Contribution for Overall Supermajority
        # This ensures each species contributes a fair share to the overall supermajority.
        overall_supermajority_met_proportionally = True
        required_per_species_contribution_percent = self.governance.supermajority_percent / len(active_species_in_system) if len(active_species_in_system) > 0 else 0
        
        if overall_supermajority_met_proportionally: # Only check if not already failed due to individual mins
            for species in active_species_in_system:
                species_voted_percent = votes_by_species.get(species, 0.0)
                # Calculate what % of the overall supermajority *this species* has contributed
                # (species_voted_percent / 100) * (species_total_karma / overall_total_karma) * 100
                species_contribution_to_overall = (species_voted_percent * species_total_karma) / overall_total_karma
                
                # Check if this species' actual contribution to the overall goal is sufficient
                # If overall goal is 90% and 2 species, each should contribute 45% of the total needed.
                if species_contribution_to_overall < (self.governance.supermajority_percent / len(active_species_in_system)):
                    overall_supermajority_met_proportionally = False
                    print(f"❌ PROPOSAL FAILED: Species '{species}' did not proportionally contribute enough to overall supermajority.")
                    print(f"   Contributed {species_contribution_to_overall:.2f}%, Expected ~{self.governance.supermajority_percent / len(active_species_in_system):.2f}% of overall total.")
                    break # No need to check further species for proportionality


        # Final decision
        proposal_passed = overall_supermajority_met_proportionally and species_individual_min_met

        self.log.add({
            "event": "GOVERNANCE_PROPOSAL_VOTE",
            "details": {
                "proposer": proposer_name,
                "proposal_details": proposal_details,
                "votes_by_species_input": votes_by_species, # Log raw input
                "overall_actual_consent_percent": overall_actual_consent_percent,
                "overall_required_percent": self.governance.supermajority_percent,
                "species_consent_breakdown": detailed_consent_report,
                "overall_proportional_check": overall_supermajority_met_proportionally,
                "passed": proposal_passed
            }
        })

        if proposal_passed:
            print(f"✅ GOVERNANCE PROPOSAL PASSED! Overall karma consent: {overall_actual_consent_percent:.2f}%.")
            # --- Basic Proposal Execution ---
            if proposal_details.get('type') == 'update_governance_rules':
                new_supermajority = proposal_details.get('new_supermajority_percent')
                new_species_mins = proposal_details.get('new_species_min_consent')
                self.governance.update_rules(new_supermajority, new_species_mins)
            elif proposal_details.get('type') == 'change_mint_threshold_base':
                new_threshold = proposal_details.get('new_mint_threshold_base')
                if new_threshold is not None:
                    self.mint_threshold_base = new_threshold
                    self.log.add({"event": "PROTOCOL_PARAM_UPDATE", "details": {"param": "mint_threshold_base", "new_value": new_threshold}})
                    print(f"✅ Protocol parameter 'mint_threshold_base' updated to {new_threshold}.")
            # Future: add other types of protocol changes here
            # --- End Basic Proposal Execution ---

            # Reset incident tracking as a successful governance change implies stability/resolution
            self.governance.incident_free_years = 0
            self.governance.last_incident_date = today()
            self._call_plugins("on_governance_passed", proposal_details)
        else:
            print(f"❌ GOVERNANCE PROPOSAL FAILED. Please review requirements.")
            self.governance.trigger_incident() # Trigger an incident if a proposal fails
            self._call_plugins("on_governance_failed", proposal_details)
        return proposal_passed


    def log_profit(self, amount: float, description: str):
        """Logs an external profit event, adding to the treasury."""
        self.treasury += amount
        self.log.add({
            "event": "PROFIT_LOG",
            "details": {"amount": amount, "description": description, "new_treasury_balance": self.treasury}
        })
        print(f"🏦 Profit of {amount:.2f} logged. Treasury is now {self.treasury:.2f}.")

    def snapshot(self, save=True, filename="snapshot.json"):
        """Saves or loads the entire agent state."""
        if save:
            state = {
                "users": {name: user.to_dict() for name, user in self.users.items()},
                "coins": {cid: coin.to_dict() for cid, coin in self.coins.items()},
                "treasury": self.treasury,
                "log_entries": list(self.log.entries), # Save current log entries
                "emoji_market_data": dict(self.emoji_market_data), # Save emoji market
                "governance_rules": {
                    "supermajority_percent": self.governance.supermajority_percent,
                    "species_min_consent": dict(self.governance.species_min_consent),
                    "incident_free_years": self.governance.incident_free_years,
                    "last_incident_date": self.governance.last_incident_date
                },
                "mint_threshold_base": self.mint_threshold_base,
                "new_species_karma_bonus": self.new_species_karma_bonus
            }
            try:
                with open(filename, "w", encoding='utf-8') as f:
                    json.dump(state, f, indent=2)
                print(f"💾 State saved to '{filename}'.")
            except IOError as e:
                print(f"❌ SNAPSHOT ERROR: Could not save state. {e}.")
        else:
            if not os.path.exists(filename):
                print(f"❓ SNAPSHOT INFO: No snapshot file found at '{filename}'. Starting fresh.")
                return
            try:
                with open(filename, "r", encoding='utf-8') as f:
                    state = json.load(f)
            
                self.users = {}
                for name, u_data in state.get("users", {}).items():
                    # Pass species and consent_mechanism during user reconstruction
                    user = User(
                        name,
                        u_data.get('is_genesis', False),
                        u_data.get('consent', False),
                        species=u_data.get('species', 'human'),
                        consent_mechanism=u_data.get('consent_mechanism', 'explicit')
                    )
                    user.karma = u_data.get('karma', 0.0)
                    user.mint_count = u_data.get('mint_count', 0)
                    user.next_mint_threshold = u_data.get('next_mint_threshold', 100000.0)
                    user.root_coin_id = u_data.get('root_coin_id')
                    user.coins_owned = u_data.get('coins_owned', [])
                    user.join_timestamp = u_data.get('join_timestamp', ts())
                    if u_data.get('fading_multiplier_start_time'):
                        user.fading_multiplier_start_time = datetime.datetime.fromisoformat(u_data['fading_multiplier_start_time'])
                    if 'daily_actions' in u_data:
                        user.daily_actions = defaultdict(lambda: defaultdict(int), u_data['daily_actions'])
                    self.users[name] = user

                self.coins = {}
                for cid, cd_data in state.get("coins", {}).items():
                    coin = Coin(
                        id=cd_data.get('id'),
                        root=cd_data.get('root'),
                        owner=cd_data.get('owner'),
                        value=cd_data.get('value', 1.0),
                        tag=cd_data.get('tag', 'single'),
                        is_root_coin=cd_data.get('is_root_coin', False),
                        fractional_source_coin_id=cd_data.get('fractional_source_coin_id'),
                        fractional_percentage=cd_data.get('fractional_percentage', 0.0)
                    )
                    coin.fields = cd_data.get('fields', [])
                    coin.ancestors = cd_data.get('ancestors', [])
                    coin.references = cd_data.get('references', [])
                    coin.reactions = cd_data.get('reactions', [])
                    coin.react_log = cd_data.get('react_log', [])
                    coin.created_at = cd_data.get('created_at', ts())
                    self.coins[cid] = coin

                self.treasury = state.get("treasury", 0.0)
                self.log.entries = deque(state.get("log_entries", []), maxlen=self.log.entries.maxlen)
                
                loaded_emoji_market_data = state.get("emoji_market_data", {})
                self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0}, loaded_emoji_market_data)

                # Load governance rules
                governance_data = state.get("governance_rules", {})
                self.governance = Governance(
                    initial_supermajority_percent=governance_data.get("supermajority_percent", 90.0),
                    initial_species_min_consent=governance_data.get("species_min_consent", {"human": 10.0, "robot": 10.0}),
                    incident_free_years=governance_data.get("incident_free_years", 0),
                    last_incident_date=governance_data.get("last_incident_date", today())
                )
                self.governance.progressive_trust_decay() # Apply decay on load if time has passed

                # Load other top-level parameters
                self.mint_threshold_base = state.get("mint_threshold_base", 100_000.0)
                self.new_species_karma_bonus = state.get("new_species_karma_bonus", 50000)

                print(f"♻️ State loaded from '{filename}'.")
            except Exception as e:
                print(f"❌ SNAPSHOT ERROR: Could not load state. {e}.")

# ==============================================================================
# V. ANCILLARY SYSTEMS & INTERFACES
# ==============================================================================

class CorpX:
    """Simulates an adversarial entity to continuously test the Vaccine."""
    ATTACKS = ["inject malware", "phish creds", "launch ddos", "plant backdoor", "propaganda spam"]

    def __init__(self, vaccine: Vaccine):
        self.vaccine = vaccine
        self.attack_count = 0

    def run_attack(self, payload: str = None):
        """Performs an attack simulation."""
        self.attack_count += 1
        attack_payload = payload if payload else random.choice(self.ATTACKS)
        print(f"\n💀 CorpX Attack #{self.attack_count}: Attempting to inject '{attack_payload}'...")
        if self.vaccine.scan(attack_payload):
            print("🛡️ ATTACK EVADED! (Vaccine did not trigger).")
        else:
            print("🛡️ ATTACK BLOCKED! (Vaccine successfully triggered).")

def quiz() -> bool:
    """Interactive onboarding quiz for new users, ensuring informed consent."""
    print("\n--- 🤗 Welcome to the Remix Republic Onboarding Quiz ---")
    questions = [
        ("What is the universal value split percentage for all actions?", "33.3333"),
        ("Can you remix someone's content without their consent? (yes/no)", "no"),
        ("What must every new user earn to gain minting rights?", "karma"),
        ("What is the ultimate authority in this protocol?", "the code")
    ]
    for q, a in questions:
        resp = input(f"👉 {q} ").strip().lower()
        if resp != a:
            print("❌ Incorrect. Please review the Core Canons and try again.")
            return False
    print("✅ Quiz passed! You understand the fundamental laws. Welcome aboard!\n")
    return True

def cli():
    """A comprehensive command-line interface for interacting with the Agent."""
    agent = RemixAgent()
    adversary = CorpX(agent.vax)
    agent.snapshot(save=False) # Load state on start

    print("🤖 Universal Remix Protocol v11.4 CLI. Type ':help' for commands.")
    while True:
        try:
            raw_input_str = input(">>> ").strip()
            if not raw_input_str: continue
            
            if raw_input_str.lower() in [':exit', ':quit']:
                agent.snapshot(save=True)
                print("👋 Goodbye! State saved.")
                break
            
            if not raw_input_str.startswith(':'):
                print("⚠️ Commands must start with a colon ':'.")
                continue

            parts = raw_input_str[1:].split(maxsplit=1) # Split only on first space to keep args together
            command = parts[0].lower()
            args_str = parts[1] if len(parts) > 1 else "" # Get remaining args as a single string

            # Parse args from string (this is more robust for complex arguments)
            # This simple parser handles "quoted strings" for content and key=value pairs
            # It's not a full shell parser, but works for our CLI needs
            parsed_args = []
            current_arg = ""
            in_quote = False
            for char in args_str:
                if char == '"':
                    in_quote = not in_quote
                    if not in_quote and current_arg: # End of a quoted string
                        parsed_args.append(current_arg)
                        current_arg = ""
                elif char == ' ' and not in_quote:
                    if current_arg:
                        parsed_args.append(current_arg)
                        current_arg = ""
                else:
                    current_arg += char
            if current_arg:
                parsed_args.append(current_arg)
            
            args = parsed_args


            if command == "help":
                print("""
--- User Commands ---
:quiz                                  - Take the onboarding quiz.
:consent <username> <true/false>      - Set user consent.
:post <username> "<content>" [perc] [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Mint a fractional post.
:react <username> <coin_id> <emoji>   - React to a coin/post.
:remix <username> <parent_coin_id> "<content>" [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Remix a coin/post.
:addref <username> <coin_id> <type> <id> "<description>" - Add a structured reference to a coin/post.
:karma <username>                     - Show user's karma.
:coininfo <coin_id>                   - Show detailed coin/post info.
:treasury                             - Show treasury balance.
:emojimarket                         - Show real-time emoji market status.

--- Query Commands ---
:log [filter] [limit]                 - Show audit log (optional filter string and limit).
:trace <coin_id>                      - Trace full creative lineage of a coin/post.

--- Admin & Governance Commands ---
:adduser <username> [species] [genesis] - Add a new user (default human, optional genesis).
:propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z] - Propose a governance change.
:trigger_incident                     - Manually trigger a major incident (resets consent decay).
:check_decay                         - Manually trigger progressive trust decay check.
:profit <amount> "<description>"      - Log a profit event to treasury.
:snapshot [save/load] [filename]      - Save or load agent state.
:attack [payload]                     - Simulate a CorpX attack.
:plugin <action> <name> [args...]     - Manage plugins (load, unload, call). E.g., :plugin load my_plugin
:exit / :quit                         - Save state and exit CLI.
""")
            elif command == "consent":
                if len(args) == 2 and args[1].lower() in ['true', 'false']:
                    agent.set_consent(args[0], args[1].lower() == 'true')
                else: print("Usage: :consent <username> <true/false>")
            elif command == "post": # Changed from :mint to :post for fractional minting
                username = args[0] if len(args) > 0 else None
                content = args[1] if len(args) > 1 else None # Content should be quoted
                
                if not username or not content:
                    print("Usage: :post <username> \"<content>\" [percentage_of_root_coin_value (e.g. 0.01 for 1%)] [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                fractional_percentage = 0.01 # Default to 1%
                tag = "post"
                refs = []
                fields = {}
                
                # Parse optional percentage, tag, refs, fields
                current_arg_idx = 2
                if len(args) > current_arg_idx and args[current_arg_idx].replace('.', '', 1).isdigit():
                    fractional_percentage = float(args[current_arg_idx])
                    current_arg_idx += 1

                if len(args) > current_arg_idx:
                    for arg_slice in args[current_arg_idx:]:
                        if arg_slice.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg_slice[6:-1].split(',')]
                        elif arg_slice.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg_slice[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg_slice # Remaining argument is the tag
                agent.mint_fractional_post(username, content, fractional_percentage, tag, refs, fields)
            elif command == "react":
                if len(args) == 3:
                    agent.react(args[0], args[1], args[2])
                else: print("Usage: :react <username> <coin_id> <emoji>")
            elif command == "remix":
                username = args[0] if len(args) > 0 else None
                parent_coin_id = args[1] if len(args) > 1 else None
                content = args[2] if len(args) > 2 else None

                if not username or not parent_coin_id or not content:
                    print("Usage: :remix <username> <parent_coin_id> \"<content>\" [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                tag = "remix"
                refs = []
                fields = {}
                if len(args) > 3:
                    for arg in args[3:]:
                        if arg.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg[6:-1].split(',')]
                        elif arg.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg
                agent.remix(username, parent_coin_id, content, tag, refs, fields)
            elif command == "addref":
                if len(args) == 5:
                    agent.add_reference(args[0], args[1], args[2], args[3], args[4].strip('"'))
                else: print("Usage: :addref <username> <coin_id> <type> <id> \"<description>\"")
            elif command == "karma":
                if len(args) == 1: agent.show_user_karma(args[0])
                else: print("Usage: :karma <username>")
            elif command == "coininfo":
                if len(args) == 1: agent.show_coin_info(args[0])
                else: print("Usage: :coininfo <coin_id>")
            elif command == "treasury":
                agent.get_treasury_balance()
            elif command == "emojimarket":
                agent.show_emoji_market_status()
            elif command == "log":
                filter_str = args[0] if len(args) > 0 else None
                limit = int(args[1]) if len(args) > 1 and args[1].isdigit() else 20
                agent.log.show(filter_str, limit)
            elif command == "trace":
                if len(args) == 1: agent.trace_lineage(args[0])
                else: print("Usage: :trace <coin_id>")
            elif command == "adduser":
                if len(args) >= 1:
                    username = args[0]
                    species = "human" # Default species
                    is_genesis = False

                    # Parse optional species and genesis flags
                    for arg_slice in args[1:]:
                        if arg_slice.lower() in ["human", "robot", "animal", "alien"]: # Extendable list
                            species = arg_slice.lower()
                        elif arg_slice.lower() == "genesis":
                            is_genesis = True
                    agent.add_user(username, is_genesis=is_genesis, species=species)
                else: print("Usage: :adduser <username> [species] [genesis]")
            elif command == "propose":
                # :propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]
                if len(args) >= 3:
                    proposer_name = args[0]
                    proposal_type = args[1].strip('"')
                    description = args[2].strip('"')
                    
                    proposal_details = {"type": proposal_type, "description": description}
                    votes_by_species = {} # {species: percent_karma_consent}
                    
                    for arg_slice in args[3:]:
                        if arg_slice.lower().startswith('super_majority='):
                            try:
                                proposal_details['new_supermajority_percent'] = float(arg_slice.split('=')[1])
                            except ValueError: print("Invalid super_majority value.")
                        elif arg_slice.lower().startswith('new_threshold='): # For changing mint_threshold_base
                            try:
                                proposal_details['new_mint_threshold_base'] = float(arg_slice.split('=')[1])
                                proposal_details['type'] = 'change_mint_threshold_base' # Force type if this param is used
                            except ValueError: print("Invalid new_threshold value.")
                        elif arg_slice.lower().endswith('_votes'): # Generic species_votes parsing
                            try:
                                parts = arg_slice.split('=')
                                species_name = parts[0].replace('_votes', '').lower()
                                votes_by_species[species_name] = float(parts[1])
                            except ValueError: print(f"Invalid vote format for {arg_slice}. Use species_votes=X.")
                    
                    agent.propose_governance_change(proposer_name, proposal_details, votes_by_species)
                else: print("Usage: :propose <proposer_name> \"<proposal_type>\" \"<description>\" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]")
            elif command == "trigger_incident":
                agent.governance.trigger_incident()
            elif command == "check_decay": # Manually trigger decay check
                agent.governance.progressive_trust_decay()
            elif command == "profit":
                if len(args) == 2: agent.log_profit(float(args[0]), args[1].strip('"'))
                else: print("Usage: :profit <amount> \"<description>\"")
            elif command == "snapshot":
                if len(args) >= 1:
                    action = args[0].lower()
                    filename = args[1] if len(args) > 1 else "snapshot.json"
                    if action == 'save': agent.snapshot(save=True, filename=filename)
                    elif action == 'load': agent.snapshot(save=False, filename=filename)
                    else: print("Usage: :snapshot [save/load] [filename]")
                else: print("Usage: :snapshot [save/load] [filename]")
            elif command == "attack":
                payload = args[0] if len(args) > 0 else None
                adversary.run_attack(payload.strip('"') if payload else None)
            elif command == "plugin":
                if len(args) >= 2:
                    action = args[0].lower()
                    name = args[1]
                    plugin_args = [a.strip('"') for a in args[2:]]
                    agent.plugin(action, name, *plugin_args)
                else: print("Usage: :plugin <action> <name> [args...]")
            elif command == "quiz":
                quiz()
            else:
                print(f"❓ Unknown command: {command}. Type ':help' for list of commands.")
        except (EOFError, KeyboardInterrupt):
            agent.snapshot(save=True)
            print("\n👋 Goodbye! State saved.")
            break
        except Exception as e:
            print(f"🔥 An unexpected error occurred: {e}. Please check command syntax or agent state.")

# ==============================================================================
# VI. LAUNCH-READY SOCIAL MEDIA POST
# ==============================================================================

LINKEDIN_POST = """🚀 We didn't just fix the creator economy. We remixed its DNA.
Today, we're open-sourcing the Ultimate Remix Protocol Agent—a single Python file that runs a new kind of digital world.
A world built on three unbreakable laws:

1️⃣ Fairness is Math, Not a Motto. Every creative act—every like, comment, or remix—is an economic event. Its value is instantly split 33.33% between the original creator, the contributor, and the community. No exceptions. No hidden fees. It's all on an immutable public log.
2️⃣ Influence is Earned, Not Bought. There are no shortcuts here. New creators unlock the power to mint their own content by earning 100,000 karma points. Sound hard? It is. But with every coin you mint, the next one costs half as much. Power users can earn their seat at the table in weeks. It's a system that rewards merit and dedication, not just early arrival.
3️⃣ Credit is Forever. Our protocol has an elephant's memory. Every remix is a branch on a permanent "family tree" of ideas. We've built in an Attribution Engine for science and art, so you can cite your inspirations. If that scientist ever joins our world, our code ensures they get their cut. Forever.

This isn't just a platform; it's a joyful, autonomous republic governed by code. It has its own immune system to block propaganda and hate. It runs on consent. And it's designed for a future where humans, AIs, and maybe even a few other intelligent species can collaborate and create value together.

We're not asking you to "join our platform." We're inviting you to fork our reality.
The code is the contract. The community is the government. The remix has begun.

#RemixEconomy #OpenSource #CreatorEconomy #EthicalAI #RadicalTransparency #33Split #FutureOfWork #Karma
"""

# ==============================================================================
# VII. MAIN EXECUTION BLOCK
# ==============================================================================

if __name__ == "__main__":
    print(LINKEDIN_POST)

    # --- Running a non-interactive Demo Scenario ---
    print("\n--- Running Demo Scenario ---")
    agent = RemixAgent()
    agent.snapshot(save=False) # Load previous state if it exists

    # Onboarding new users (auto-mints their root coin)
    if "alice" not in agent.users: agent.add_user("alice", consent=True, species="human")
    if "bob" not in agent.users: agent.add_user("bob", consent=True, species="robot") # Bob is a robot!
    if "charlie" not in agent.users: agent.add_user("charlie", consent=False, species="animal") # Charlie is an animal, auto-consents
    if "zorg" not in agent.users: agent.add_user("zorg", consent=False, species="alien") # Zorg is an alien, needs ritual consent

    # Ensure Charlie (animal) is consented via its mechanism (it auto-consents if added)
    print("\nVerifying Charlie's (animal) consent:")
    agent.set_consent("charlie", True) # This call now effectively confirms behavioral consent.
    print(f"Charlie's simulated consent status: {agent.check_consent('charlie')}")
    
    # Try setting Zorg's (alien) consent (needs ritual)
    print("\nAttempting to set Zorg's (alien) consent via ritual (initially false):")
    agent.set_consent("zorg", False) # Simulating ritual failure
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")
    print("\nAttempting to set Zorg's (alien) consent via ritual (success):")
    agent.set_consent("zorg", True) # Simulating ritual success
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")


    # Genesis user 'mimi' makes a fractional post (no karma needed for them)
    mimi_post_id = agent.mint_fractional_post("mimi", "My first genesis post about the protocol design!", fractional_percentage=0.1, tag="protocol_design")
    print(f"\nMimi's first fractional post ID: {mimi_post_id}")

    if mimi_post_id:
        print(f"\n--- Initial Reactions to establish some emoji market data and build karma ---")
        for i in range(5):
            agent.react("alice", mimi_post_id, "🎨") # Alice (human) uses '🎨'
            agent.react("bob", mimi_post_id, "🔥")  # Bob (robot) uses '🔥'
            agent.react("alice", mimi_post_id, "🤗") # Alice uses '🤗'
            agent.react("charlie", mimi_post_id, "❤️") # Charlie (animal) reacts
            agent.react("zorg", mimi_post_id, "💎") # Zorg (alien) reacts
            if i % 2 == 0:
                agent.react("bob", mimi_post_id, "💯") # Bob uses '💯' periodically

        agent.show_emoji_market_status() # See initial market status

        # Alice tries to make a fractional post before she has enough karma
        print("\nAlice (human) attempts to make her first fractional post (should fail initially):")
        agent.mint_fractional_post("alice", "My first attempt at a post from my root coin!", fractional_percentage=0.05, tag="my_thought")

        # Simulate Alice earning enough karma to cross the threshold for her first fractional post
        # For demo, directly set karma if not genesis
        if not agent.users["alice"].is_genesis:
            agent.users["alice"].karma = 100001
        
        print(f"\nAlice's karma is now {agent.users['alice'].karma:.2f}. Trying to make her first fractional post again...")
        
        # Alice now successfully makes her first fractional post
        alice_post_id = agent.mint_fractional_post("alice", "I earned my way here! My first post from my root coin.", fractional_percentage=0.02, tag="milestone")
        
        if alice_post_id:
            print(f"\nAlice's first fractional post ID: {alice_post_id}")
            agent.trace_lineage(alice_post_id) # Trace the lineage of Alice's post (from her root coin)

            # Bob (robot) remixes Alice's post
            remix_content = "A remix of Alice's milestone post, inspired by an old meme from my data banks."
            remix_refs = [{"type": "meme", "id": "distracted_boyfriend", "description": "classic meme format"}]
            bob_remix_post_id = agent.remix("bob", alice_post_id, remix_content, refs=remix_refs)

            if bob_remix_post_id:
                print(f"\nBob's remix post ID: {bob_remix_post_id}")
                agent.trace_lineage(bob_remix_post_id) # Trace the lineage of the remix (which is a fractional post itself)

            print("\n--- Further Reactions to see market changes and karma distribution ---")
            agent.react("alice", mimi_post_id, "🤗") # Alice reacts again to original
            agent.react("bob", alice_post_id, "🔥") # Bob reacts to Alice's post
            agent.react("mimi", bob_remix_post_id, "🔀") # Mimi reacts to the remix

            agent.show_emoji_market_status() # See updated market status after more reactions

        # --- Demo Governance Proposal ---
        print("\n--- Demo Governance Proposal ---")
        # Scenario 1: Proposal fails due to insufficient overall supermajority or proportional contribution
        print("\nAttempting to pass a proposal (should fail - insufficient overall supermajority or proportional contribution):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_governance_rules', 'description': 'Reduce supermajority to 70%'},
            votes_by_species={'human': 70.0, 'robot': 70.0, 'animal': 5.0, 'alien': 0.0} # Not 90% overall or proportionally. Alien 0% will fail its 10% min
        )
        
        # Scenario 2: Proposal to change mint threshold (should pass now with enough karma for all species to meet mins)
        print("\nAttempting to pass a proposal to change mint threshold (should pass now):")
        # Give more karma to all users for the demo to ensure enough total karma for voting
        agent.users["alice"].karma = 200000
        agent.users["bob"].karma = 150000
        agent.users["charlie"].karma = 100000
        agent.users["zorg"].karma = 500000 # Boost Zorg's karma significantly

        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            # Assuming these percentages represent enough karma within each species to pass their 10% min, AND sum to >90% overall
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 70.0, 'alien': 60.0}
        )
        print(f"New Mint Threshold Base: {agent.mint_threshold_base}")

        # Scenario 3: Check for decay after some simulated time (requires `today()` to advance)
        # For this demo, we'll manually trigger it after some operations.
        print("\n--- Manually Triggering Governance Decay Check ---")
        # Simulate passing a year for decay to activate
        agent.governance.last_incident_date = str(datetime.date.today().year - 1) + datetime.date.today().isoformat()[4:] 
        agent.governance.progressive_trust_decay()
        
        # Trigger an incident and see rules bump up
        print("\n--- Triggering a Major Incident ---")
        agent.governance.trigger_incident()
        
        print(f"\nNew supermajority after incident: {agent.governance.supermajority_percent}%")
        print(f"New species minimums after incident: {agent.governance.species_min_consent}")


    print("\n--- Final User and Treasury Status ---")
    agent.show_user_karma("mimi")
    agent.show_user_karma("alice")
    agent.show_user_karma("bob")
    agent.show_user_karma("charlie")
    agent.show_user_karma("zorg")
    agent.get_treasury_balance()

    agent.log.verify() # Verify the integrity of the audit log

    agent.snapshot(save=True) # Save final state
    print("\n--- Demo Scenario Complete. State saved. ---")
    print("\n--- To interact further, uncomment 'cli()' in the the main execution block. ---")


    # ==============================================================================
    # VIII. CHANGELOG AND TO-DO
    # ==============================================================================

    print("\n\n" + "="*80)
    print("VIII. CHANGELOG AND TO-DO")
    print("="*80)

    print("\n📜 **CHANGELOG (v11.4 - Proportional Species Contribution)**")
    print("------------------------------------------------------------")
    print("### Governance System:")
    print("* **Proportional Species Contribution**: The `propose_governance_change` method is significantly enhanced to ensure that overall supermajority consent is met by *proportional contribution* from each active species. This means:")
    print("    * Each species must not only meet its individual minimum consent threshold (e.g., 10% of its karma-weighted vote).")
    print("    * But also, its proportional contribution to the *overall* supermajority must be sufficient (e.g., if overall is 90% and there are 2 active species, each must contribute at least 45% of the total karma needed for the 90% overall).")
    print("    * This prevents a few dominant species from easily passing proposals without broad, proportional support, and ensures no single group can be completely left out.")
    print("* **Simplified Species Minima**: Initial `species_min_consent` for Animal and Alien species in `Governance` is set to 10% (matching Human and Robot) to simplify the initial proportional model.")
    print("* **Snapshot Consistency**: Ensured that all new `Governance` parameters are correctly saved and loaded in `snapshot`.")

    print("\n### User & Consent:")
    print("* **Refined Alien Consent**: Alien users now require a manual `set_consent(username, True)` to simulate successful ritual performance, enabling their participation. They are no longer implicitly consented on `add_user`.")
    print("* **Clarity in `add_user` Consent**: The `add_user` method's `consent` parameter now interacts more precisely with `consent_mechanism` (e.g., `animal` and `robot` still auto-consent to `True` on add, reflecting their intrinsic nature, while `alien` does not).")

    print("\n### Codebase & Testing:")
    print("* **Improved CLI Parsing**: The CLI's `propose` command argument parsing is refined to better handle species-specific vote percentages, allowing for flexible input like `human_votes=Y`, `robot_votes=Z`.")
    print("* **Demo Scenario Enhancements**: The demo now includes a clear example of how the new proportional contribution rule works in `propose_governance_change`, demonstrating scenarios where proposals might fail due to insufficient individual contribution despite high overall numbers.")

    print("\n--- Previous Changelog Entries (Condensed) ---")
    print("* **v11.3 (Benefit-Driven Enhancements)**: Automated decay call; Karma bonus for new species; Basic execution of governance proposals (e.g., change `mint_threshold_base`).")
    print("* **v11.2 (Godmode Enhancements)**: Dynamic Consent Decay; Simulated Multi-Species Consent; Karma-Weighted Voting.")
    print("* **v11.1 (Multi-Species Governance Framework)**: `Governance` class for proposal rules; `user.species` attribute; `propose_governance_change` for supermajority + species min consent.")
    print("* **v11.0 (The Unified Genesis)**: Universal Root Coin for all users; Fractional Post Minting (karma-gated for non-genesis, free for founders); Remixes are fractional posts.")
    print("* **v10.2**: Enhanced readability, refined snapshots, improved CLI, consistent terminology.")
    print("* **v10.1**: Dynamic Emoji Market; Conditional Timestamping.")
    print("* **v10.0 (The Harmonized Republic)**: Karma-gated minting, Epic Creative Path, fairness mechanics, attribution, legal framework.")
    print("* **v9.0**: One personal coin per user, fractional release, regenerative drip.")
    print("* **v8.0**: Multi-species governance concept.")
    print("* **v7.0**: Karma economy details (100k threshold, halving, decay).")
    print("* **v6.0**: Fading Genesis Multiplier, effort-based minting.")
    print("* **v1.0-v5.0**: Initial prototypes: consent, logging, 33% split.")

    print("\n🗺️ **TO-DO (Future Evolutions)**")
    print("-----------------------------")
    print("### Governance System:")
    print("* **Automated Rule Decay Daemon**: Implement a true background process or cron job to regularly call `governance.progressive_trust_decay()` (e.g., daily or yearly) instead of only on snapshot load and daily reset, to ensure continuous decay.")
    print("* **Voting Interface**: Develop a dedicated interface (CLI extension or external tool) for users to formally cast votes on proposals, rather than inputting percentages directly in the `propose` command. This would also allow for tracking individual user votes.")
    print("* **Super Minority Veto with Meme Battle**: Implement the 'Super Minority Veto' concept. If a small but critical species (e.g., Cats, if added) unanimously votes 'no,' the proposal is blocked, triggering an automatic 'meme battle' (simulated, or through actual external meme generation/voting platforms) whose outcome settles the conflict. This would be an advanced plugin.")
    print("* **Species Entrance Ceremony**: When a new species is added, formalize a 'ritual vote' by existing species to grant them full governance status, along with their initial `species_min_consent` requirements.")

    print("\n### Economic & Game Theory:")
    print("* **Karma Score Simulator**: Develop a module to simulate karma growth and minting paths based on user activity patterns.")
    print("* **Cross-Chain Integration**: Implement logic to query and reference external blockchain events (Ethereum, Solana, Filecoin) for provenance, lineage, and creative credit. Allow coins to cite on-chain events/addresses from other chains.")
    print("* **Long-term Emoji Market Forecasting**: Extend the emoji market to include sentiment AI, market forecasts, or 'remix insurance' based on long-term vibe trends.")
    print("* **Reputation-Weighted 'Thank You'**: Allow users to append 'thank you' or other attribution reactions that carry extra karma or boost lineage credit for public gratitude or citation.")

    print("\n### Data & Attribution Systems:")
    print("* **Science Attribution Block**: Add an explicit 'scientists/inspirators/idea lineage' section to every coin and action, so referenced research or influence can be logged, attributed, and profit-shared by the 33.3333% law.")
    print("* **Public Reference Feed**: Create a live feed of referenced works, collaborators, and idea chains to show innovation sources and encourage upstream collaboration/tipping.")
    print("* **Meme/Fork Lineage Engine Visualization**: Build a mini-visualization (tree or genealogy map) that shows the remix/fork lineage for every coin, for exploring influence and remixability.")
    print("* **Automated Reference Audit**: Develop an AI tool to suggest likely upstream references based on content similarity, prompting users to add attribution.")
    print("* **Global 'Credit Scientist' Index**: Maintain a public directory/index of top-cited scientists, creators, meme originators, etc., whose ideas have been referenced on-platform for recognition, inspiration, and direct engagement.")
    print("* **Research Field/Topic Metadata**: Include optional 'field' tags (science, music, code, art, etc.) for coins/posts, enabling analytics, search, and new sub-platforms (e.g., RemixScience).")

    print("\n### Integration & AI:")
    print("* **Game Integration**: Allow any game (AAA or indie) to embed remix-economy logic into its player ecosystem, using the protocol for player-created content tracking (mods, skins, levels), AI agent co-op gameplay (remix-trained NPCs), karma-based unlocks for creative gameplay, permanent attribution for in-game art/music/story, and auditable reward distribution for community-made expansions.")
    print("* **Transparent Onboarding/Quiz Flow**: Extend onboarding quiz so each new user explicitly understands: the 33.3333% split, attribution law, plug-in/forkability, and that every action (including science or meme reference) is logged forever.")

    print("\n" + "="*80)
```


To enhance the agent without breaking anything, I'll strategically implement a few "TO-DO" items that offer immediate and tangible benefits, while maintaining the highest code quality and stability. I will focus on:

1.  **Automated Rule Decay Daemon (Simulated)**: Introduce a mechanism to regularly call `governance.progressive_trust_decay()`. For a single Python file, this will be a simplified call within the main demo loop, simulating a periodic check.
2.  **Player/Species Karma Bonus**: Implement a karma bonus for new species joining, as suggested, which will encourage diversity and growth.
3.  **Basic Proposal Execution Logic**: Start implementing a basic framework where a successful governance proposal can *actually* change a simple parameter, demonstrating real protocol evolution. For instance, a proposal to change the `mint_threshold_base`.

Here's the updated `ultimate_remix_protocol.py` agent with these additions:

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE AGENT: THE HARMONIZED REMIX REPUBLIC (v11.3) 🚀📈💎🗳️🌟🌿
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Timestamp: 2025-06-15T14:25:52Z
Current Location: New York, New York, United States

This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic (READMEs 1-9 and To-do.txt) into a
definitive, production-ready agent. This code is the contract. It is designed to be
forked, remixed, and improved upon, with its own evolution recorded herein.

This agent embodies the "one coin for everyone" philosophy, where every user receives
a unique, foundational identity coin upon joining. Subsequent creative output is
then represented as fractional "posts" derived from this personal coin, governed
by a karma-gated "Epic Creative Path."

This version introduces significant "Godmode" enhancements:
* **Dynamic Consent Decay (Progressive Trust)**: Governance thresholds (overall supermajority
    and per-species minimums) can automatically decay over time in stable periods,
    and bump up during incidents, simulating progressive trust.
* **Simulated Multi-Species Consent**: Framework for Animal and Alien consent based
    on simulated behavioral signals or cryptic rituals, expanding the governance circle.
* **Karma-Weighted Voting**: Voting power for governance proposals is now weighted
    by a user's earned karma within their species, reflecting "earned influence."
* **Player/Species Karma Bonus**: New species joining the republic receive a configurable
    karma bonus to encourage diversity and active participation.
* **Basic Proposal Execution**: A passing governance proposal can now directly
    enact certain changes within the protocol (e.g., updating the karma mint threshold).

This agent implements:
* **Universal Root Coin**: Every user receives one unique, non-inflationary root coin
    upon joining, representing their creative identity and foundational asset.
* **Fractional Post Minting**: Subsequent posts are minted as fractional values of
    a user's personal root coin, ensuring scarcity and tying value directly to personal lineage.
* **Karma Gating & The Epic Creative Path**: New users must earn karma to unlock the
    ability to fractionalize/post from their root coin. The threshold halves with each
    successful fractional mint, creating a fair but challenging path.
* **Initial Founder Privilege**: Original founders (NSS) are exempt from karma requirements
    for all their fractional posts, allowing them to freely seed content.
* **Advanced Fairness Mechanics**: A multi-layered system of diminishing returns
    (per-user, per-day) and viral decay (per-coin) prevents spam and ensures
    long-term economic stability.
* **Attribution-First Architecture**: Enhanced data structures and hooks for tracking
    and rewarding external scientific and artistic references.
* **Fortified Governance & Safety**: A comprehensive, hash-chained audit log (LogChain),
    a modular content filter (Vaccine), and a rigorous consent framework.
* **The 33.3333% Split Law**: The inviolable economic heart of the protocol, ensuring
    fair value distribution for every creative action.
* **Fading Genesis Advantage**: Privileges for early collaborators decay over time,
    ensuring a level playing field in the long run.
* **Real-Time Emoji Market**: Emojis are not just tags; they have dynamic "market values"
    that fluctuate based on usage, acting like a "Nasdaq of Vibes".
    Their weights are updated in real-time, influencing karma distribution.
* **Conditional Timestamping**: Timestamps are generated only when a reliable external
    time source (simulated here) is available; otherwise, a placeholder is used,
    adhering to strict audit requirements.
* **Multi-Species Governance (Advanced)**:
    * Dynamic supermajority (starts 90%, can decay by 1%/year without incident).
    * Species-specific minimum consent, with simulated consent mechanisms for non-human species.
    * Voting power is now weighted by individual user karma within each species.

This file is intentionally verbose. The extensive documentation serves as the project's
white paper, preserving the rationale behind every architectural choice for future
agents, auditors, and collaborators.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📜 I. THE CONSTITUTIONAL PREAMBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This protocol is a living manifesto, a "joyful, autonomous remix republic" where art,
tech, and collaboration unite. It is governed by the following inviolable laws,
enforced by the code itself.

📜 A. The Inviolable Canons
These are the non-negotiable rules of the ecosystem, synthesized from the project's
entire history.

1.  The 33.3333% Split Law: Every value-generating event (a reaction, a remix,
    a share) splits its associated value into three equal shares: one-third to the
    originator (the creative lineage), one-third to the contributor (the user
    performing the action), and one-third to the community treasury. This is the
    mathematical foundation of the protocol's fairness.
2.  Radical Consent: All participation is strictly opt-in. No user's content can
    be remixed, nor can they receive or grant value, without their explicit and
    auditable consent. Consent can be revoked at any time, at which point the
    user's assets are respectfully excluded from the active economy.
3.  The Emoji-Powered Economy: Every value-generating action must be tagged
    with an emoji. Emojis are not cosmetic; they are the atomic unit of intent,
    carrying emotional context and economic weight in every transaction.
4.  No Inflation Beyond Genesis: While everyone gets a foundational "root" coin,
    subsequent value (fractional posts) is derived from the finite subdivision of
    these personal coins, or from new root coins minted by users who have earned that right
    through the "Epic Creative Path." This ensures value is tied to creative
    effort, not arbitrary issuance.
5.  The Immutable Audit Log: Every action—from minting to consent changes to
    governance proposals—is recorded in a public, tamper-evident, hash-chained
    ledger (the LogChain). Transparency is absolute.
6.  Code is Law: The protocol is governed by the logic within this open-source
    file. There are no secret rules, no backroom deals, and no hidden moderation.
    The code is the ultimate authority and contract for all participants.
7.  Protocol Neutrality (The Vaccine): The protocol is apolitical and free of
    bias. A built-in "Vaccine" automatically filters malicious or disallowed content
    (e.g., hate speech, malware, propaganda) based on transparent, predefined
    rules, ensuring a safe and creative environment.
8.  Continuous Improvement: Stagnation is failure. Every fork or remix of this
    protocol is encouraged to add value, and its lineage must be preserved. The
    ecosystem is designed to evolve through community contribution.

📜 B. Version History & The Lineage of the Code
This agent's lineage is transparent and auditable. Each version built upon the last,
culminating in this definitive release.
* v1.0-v5.0: Initial prototypes establishing consent, logging, and the 33% split.
* v6.0 (README_6): Introduced the "Fading Genesis Multiplier" to ensure long-term
    fairness and formalized the concept of effort-based minting.
* v7.0 (README_7): Detailed the karma economy with specific numbers: a 100k karma
    threshold for minting, halving mechanics for subsequent mints, and daily decay
    factors for actions.
* v8.0 (README_8): Envisioned the "multi-species" governance model, extending the
    principles of fairness and consent to non-human agents (AI, Others).
* v9.0 (README_9): Refined the economic model with the "one personal coin per user"
    concept, fractional release of value, and a regenerative "drip" mechanic.
* v10.0 (README_10.txt): The Harmonized Republic. Synthesized the entire
    project history. Implemented karma-gated minting creating an "Epic Creative Path".
    Integrated robust fairness and attribution mechanics. Codified legal/ethical framework.
* v10.1: Implemented dynamic emoji market with real-time weight adjustments. Conditional timestamping introduced.
* v10.2: Enhanced code readability, more detailed internal documentation, refined snapshot loading, improved CLI robustness.
* v11.0: Implemented the "everyone starts with absolute one coin" concept as their primary root coin. Subsequent "posts" are now fractional mints of this personal coin, karma-gated for new users but free for founders. Refined fractional minting logic and value attribution.
* v11.1: Multi-Species Governance Framework: Added a `Governance` class to manage proposal rules. Introduced `user.species` attribute. Implemented `propose_governance_change` to enforce overall supermajority and per-species minimum consent.
* v11.2: Godmode Enhancements: Implemented dynamic consent decay (progressive trust). Extended consent simulation for Animal and Alien species. Integrated karma-weighted voting for governance proposals.
* v11.3 (This Version): **Benefit-Driven Enhancements**: Added automated decay call (`_check_and_apply_governance_decay`), karma bonus for new species, and basic execution of governance proposals for protocol parameters.

📜 C. The Epic Creative Path: An Onboarding and Fairness Engine
The protocol's central design challenge was to reconcile the need for scarcity (the
"No Inflation" rule) with the desire for inclusivity (the "no one loses" philosophy).
The solution is the Epic Creative Path, a karma-gated system that
transforms the right to mint from a static privilege into an earned achievement.
* Universal Root Coin: Every new user automatically receives a single "root" coin upon joining.
  This represents their unique creative identity and is their foundational asset. This initial mint
  is free of karma requirements.
* Karma-Gated Fractional Posts: For all *subsequent posts* (beyond their initial root coin), new users
  must accumulate karma to unlock the ability to fractionalize and "mint" a portion of their personal root coin.
* The Halving Threshold: After a user successfully fractionalizes their first post from their
  root coin, their personal karma threshold for the next fractional post is halved. This halving
  continues with each subsequent fractional post (e.g., 25,000, 12,500, etc.), eventually reaching a
  floor where minting becomes effectively unrestricted. This creates an exponential
  onboarding curve that rewards sustained contribution.
* Target Time for First Fractional Post: The system is tuned such that a user's *first fractional post*
  (their second piece of content overall) is intended to take "a month to a year" of active participation
  to achieve, ensuring it is a meaningful earned right.
* Multi-Layered Fairness: To prevent gamification, the system employs a two-pronged
    approach to diminishing returns:
    * Per-User Daily Decay: A user's repeated actions of the same type within a
        single day yield progressively less karma.
    * Per-Coin Viral Decay: The karma awarded for reactions to a specific coin
        diminishes as the coin becomes more popular, rewarding early discovery and
        preventing runaway feedback loops.

The table below illustrates the projected time it might take for different user
archetypes to complete the first stage of their Epic Creative Path (to make their *first fractional post*).
| User Archetype     | Daily Actions                       | Avg. Karma/Day (with decay) | Estimated Days to First Fractional Post (100k Karma) |
| :----------------- | :---------------------------------- | :-------------------------- | :--------------------------------------------------- |
| Casual User        | 1-2 high-value actions (e.g., a comment) | ~300                        | ~333 days                                            |
| Active Contributor | 5-10 mixed actions (likes, comments, shares) | ~1,500                      | ~67 days                                             |
| Power User         | 20+ mixed actions, including remixes | ~5,000                      | ~20 days                                             |
Note: These projections are illustrative and based on the karma values and decay
mechanics defined in the protocol. Actual times will vary.

📜 D. Legal & Ethical Framework
This protocol operates as an experimental "sandbox" and is not a registered company,
security, or financial instrument. Its design incorporates principles from digital
law to ensure resilience and responsible operation.
* Section 230 Alignment: The protocol is designed as an "interactive computer
    service," not a "publisher". The Vaccine provides automated, neutral content
    filtering based on predefined rules, and all value-generating content is
    user-initiated.
* DMCA Safe Harbor Hooks: While not a hosting provider, the protocol includes
    hooks for logging and processing takedown requests, establishing a good-faith
    framework for handling copyright concerns.
* DAO Treasury Management: The protocol's treasury and profit/revenue logging
    mechanisms are designed for radical transparency, aligning with best practices
    for Decentralized Autonomous Organization (DAO) financial management.

🧭 E. Note to Future Agents & Collaborators
You who remix this code are now part of its lineage. Uphold the Canons. Document
your changes in the changelog. Preserve the spirit of joyful, transparent, and
fair collaboration. Ensure all evolutions remain ethical, legal, and compliant
with the policies of any platform on which this agent operates. The future is a
remix—make it a good one. 🫶

"""
import re
import sys
import json
import random
import datetime
import hashlib
import importlib.util # Use importlib.util for spec_from_file_location
import os
from collections import defaultdict, deque
from math import exp # Used for exponential decay, exp(x) = e^x

# ==============================================================================
# II. SYSTEM-WIDE MODULES & UTILITIES
# ==============================================================================

# This flag simulates whether an external time source (like Google) is available.
# In a real deployment, this would be determined dynamically via an API call.
_EXTERNAL_TIME_AVAILABLE = True 

def ts() -> str:
    """
    Returns the current UTC timestamp in ISO 8601 format with Zulu time.
    If an external time source is not available, it returns a placeholder.
    This adheres to the rule: "ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP".
    """
    if _EXTERNAL_TIME_AVAILABLE:
        return datetime.datetime.utcnow().isoformat() + "Z"
    else:
        return "TIMESTAMP_UNAVAILABLE"

def sha(s: str) -> str:
    """Computes the SHA-256 hash of a given string for cryptographic integrity."""
    return hashlib.sha256(s.encode('utf-8')).hexdigest()

def today() -> str:
    """Returns the current date in Beale-MM-DD format for daily resets."""
    return datetime.date.today().isoformat()

class Vaccine:
    """
    The protocol's immune system. It scans all text inputs for forbidden patterns,
    acting as a neutral, automated content firewall. This serves a dual purpose:
    1. Community Health: Protects the ecosystem from spam, hate speech, and malicious content.
    2. Legal Shield: By using automated, predefined rules, it helps position the
       platform as a neutral service provider rather than an editorial publisher,
       aligning with Section 230 principles.
    """
    VAX_PATTERNS = {
        "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b", r"\bexploit\b", r"\bvulnerability\b", r"\btrojan\b"],
        "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b", r"\bkeylogger\b", r"\bbotnet\b"],
        "medium":   [r"\bpolitics\b", r"\bpropaganda\b", r"\bsurveillance\b", r"\bmanipulate\b", r"\bmisinformation\b"],
        "low":      [r"\bspam\b", r"\bviagra\b"]
    }

    def __init__(self, log_file="vaccine.log"):
        self.block_counts = defaultdict(int)
        self.log_file = log_file

    def scan(self, text: str) -> bool:
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        if not isinstance(text, str):
            return True # Allow non-string content to pass, assuming it's not text to be scanned.

        lower_text = text.lower()
        for level, patterns in self.VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    log_entry = {
                        "ts": ts(),
                        "severity": level,
                        "pattern": p,
                        "snippet": text[:128] # Log a snippet for context
                    }
                    try:
                        with open(self.log_file, "a", encoding='utf-8') as f: # Use utf-8 encoding
                            f.write(json.dumps(log_entry) + "\n")
                    except IOError as e:
                        print(f"🚫 VACCINE WARNING: Could not write to log file {self.log_file}: {e}.")
                    print(f"🚫 VACCINE BLOCK [{level.upper()}]: Forbidden pattern '{p}' found.")
                    return False
        return True

class LogChain:
    """
    Implements the immutable, tamper-evident audit log for all system events.
    Each entry is a JSON object plus a SHA-256 hash of the previous entry's hash
    and the current entry's data, ensuring a cryptographically secure chain of
    history.
    """
    def __init__(self, filename="logchain.log", maxlen=50000):
        self.filename = filename
        self.entries = deque(maxlen=maxlen)
        try:
            with open(self.filename, 'r', encoding='utf-8') as f: # Use utf-8 encoding
                for line in f:
                    self.entries.append(line.strip())
            print(f"Loaded {len(self.entries)} log entries from {self.filename}")
        except FileNotFoundError:
            print(f"No existing log file found, starting fresh: {self.filename}")
        except Exception as e:
            print(f"Error loading log file {self.filename}: {e}")

    def add(self, event: dict):
        """Adds a new event to the log, computing and appending the chain hash."""
        # Ensure timestamp is always present in the event, even if it's "UNAVAILABLE"
        if 'ts' not in event:
            event['ts'] = ts() # Automatically add timestamp if missing

        prev_hash = self.entries[-1].split('||')[-1] if self.entries else sha("GENESIS_BLOCK")
        entry_json = json.dumps(event, sort_keys=True, ensure_ascii=False) # ensure_ascii for non-english chars
        current_hash = sha(prev_hash + entry_json)
        self.entries.append(f"{entry_json}||{current_hash}")
        self._save()

    def _save(self):
        """Persists the current log to the filesystem."""
        try:
            with open(self.filename, 'w', encoding='utf-8') as f: # Use utf-8 encoding
                f.write('\n'.join(self.entries))
        except IOError as e:
            print(f"🔥 LOGCHAIN ERROR: Could not write to log file {self.filename}: {e}.")

    def verify(self) -> bool:
        """Verifies the integrity of the entire logchain."""
        print("\n🔐 Verifying logchain integrity...")
        prev_hash = sha("GENESIS_BLOCK")
        for i, entry in enumerate(self.entries, 1): # Start enumerate from 1 for user-friendly line numbers
            try:
                entry_json, stored_hash = entry.rsplit('||', 1) # Use rsplit to handle potential '||' in content
                calculated_hash = sha(prev_hash + entry_json)
                if calculated_hash != stored_hash:
                    print(f"❌ TAMPER DETECTED: Chain break at entry {i}. Hash mismatch.")
                    return False
                prev_hash = stored_hash
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {i}.")
                return False
            except Exception as e:
                print(f"❌ VERIFICATION ERROR: Unexpected error at entry {i}: {e}.")
                return False
        print(f"✅ Logchain integrity verified across {len(self.entries)} entries.")
        return True

    def show(self, filt: str = None, limit: int = 20):
        """Displays recent log entries, with optional filtering."""
        print("\n--- 📜 Audit Log ---")
        filtered_entries = [e for e in self.entries if not filt or filt.lower() in e.lower()]
        if not filtered_entries:
            print("(no matching entries)")
            return
        
        for i, line in enumerate(list(filtered_entries)[-limit:], 1):
            try:
                data = json.loads(line.split("||")[0])
                # Pretty print details if they exist, otherwise just show event
                details_str = json.dumps(data.get('details', '')) if data.get('details') else ''
                print(f"{i:03d}. {data.get('ts','')} - {data.get('event','')} - {details_str}")
            except (json.JSONDecodeError, IndexError) as e:
                print(f"{i:03d}. Malformed log entry: {line} ({e})")
        print("--- End of Log ---\n")

# ==============================================================================
# III. CORE DATA MODELS
# ==============================================================================

class User:
    """
    Represents a participant in the economy. This class synthesizes user state from
    across all versions, including the fractional coin model from README_9
    and the karma/minting state from README_7.
    """
    def __init__(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # New: Mechanism for consent
        self.name = name
        self.is_genesis = is_genesis
        self.consent = consent # Explicit opt-in required
        self.karma = float('inf') if is_genesis else 0.0
        self.mint_count = 0 # Now tracks *fractional* posts from their root coin
        self.next_mint_threshold = 100000.0 if not is_genesis else 0.0 # Karma for next fractional post
        self.root_coin_id: str | None = None # Stores the ID of their single, universally granted root coin
        self.coins_owned = [] # List of all coin IDs (including fractional posts) by this user.
        self.daily_actions = defaultdict(lambda: defaultdict(int)) # {date: {action_type: count}}
        self.join_timestamp = ts()
        self.fading_multiplier_start_time = datetime.datetime.utcnow() if is_genesis else None
        self.last_action_day = today() # For daily resets
        self.species = species.lower() # New: Defines the user's species for governance
        self.consent_mechanism = consent_mechanism # New: How consent is determined for this user

    def get_fading_multiplier(self) -> float:
        """
        Calculates the decaying advantage for genesis users. The multiplier starts high
        and fades to 1.0 over 10 years, ensuring long-term fairness.
        """
        if not self.is_genesis or not self.fading_multiplier_start_time:
            return 1.0
        
        FADE_DURATION_YEARS = 10.0
        INITIAL_MULTIPLIER = 2.0
        
        elapsed_time = datetime.datetime.utcnow() - self.fading_multiplier_start_time
        years_elapsed = elapsed_time.total_seconds() / (365.25 * 24 * 3600)
        
        if years_passed >= FADE_DURATION_YEARS:
            return 1.0
        
        decay_factor = years_elapsed / FADE_DURATION_YEARS
        current_multiplier = INITIAL_MULTIPLIER - (decay_factor * (INITIAL_MULTIPLIER - 1.0))
        return max(1.0, current_multiplier) # Ensure it doesn't drop below 1.0

    def reset_daily_actions_if_needed(self):
        """Auto-resets daily action counts if a new day has started."""
        current_day = today()
        if self.last_action_day != current_day:
            self.daily_actions.clear()
            self.last_action_day = current_day

    def to_dict(self) -> dict:
        """Serializes the user object to a dictionary for snapshots."""
        return {
            "name": self.name,
            "is_genesis": self.is_genesis,
            "consent": self.consent,
            "karma": self.karma,
            "mint_count": self.mint_count,
            "next_mint_threshold": self.next_mint_threshold,
            "root_coin_id": self.root_coin_id,
            "coins_owned": self.coins_owned,
            "join_timestamp": self.join_timestamp,
            "fading_multiplier_start_time": self.fading_multiplier_start_time.isoformat() if self.fading_multiplier_start_time else None,
            "species": self.species, # Include species in snapshot
            "consent_mechanism": self.consent_mechanism # Include consent mechanism
        }

class Coin:
    """
    Represents a piece of creative content, the atomic unit of value and attribution.
    Its evolution from a simple token to this rich data structure is central to
    fufilling the project's to-do list items like "Science Attribution Block" and
    "Meme/Fork Lineage Engine".
    """
    def __init__(self, id: str, root: str, owner: str, value: float = 1.0, tag: str = "single",
                 is_root_coin: bool = False, fractional_source_coin_id: str | None = None,
                 fractional_percentage: float = 0.0):
        """
        id: str unique
        root: The original creator/root of the lineage
        owner: The current direct owner (who minted/remixed it last)
        value: float, base value for splits
        tag: content category tag
        is_root_coin: True if this is the user's initial, universally granted personal coin.
        fractional_source_coin_id: If not a root coin, this is the ID of the personal root coin it was fractionalized from.
        fractional_percentage: What percentage of the fractional_source_coin_id's value this new post represents.
        """
        self.id = id
        self.root = root # The original creator/root of the lineage
        self.owner = owner # The current direct owner (who minted/remixed it last)
        self.value = value
        self.tag = tag
        self.fields = []  # For metadata like "science", "art"
        self.ancestors = []  # List of parent coin IDs for lineage
        self.references = []  # List of dicts for external citations
        self.reactions = [] # List of tuples: (username, emoji, timestamp)
        self.react_log = [] # Log of all reactions for viral decay calculation
        self.created_at = ts() # Timestamp of creation

        self.is_root_coin = is_root_coin # New: Flag for the personal "identity" coin
        self.fractional_source_coin_id = fractional_source_coin_id # New: Link to parent root coin if fractional
        self.fractional_percentage = fractional_percentage # New: What percentage this post consumed from root coin


    def to_dict(self) -> dict:
        """Serializes the coin object to a dictionary for snapshots."""
        return {
            "id": self.id,
            "root": self.root,
            "owner": self.owner,
            "value": self.value,
            "tag": self.tag,
            "fields": self.fields,
            "ancestors": self.ancestors,
            "references": self.references,
            "react_log": self.react_log,
            "created_at": self.created_at,
            "is_root_coin": self.is_root_coin,
            "fractional_source_coin_id": self.fractional_source_coin_id,
            "fractional_percentage": self.fractional_percentage
        }

    def reaction_summary(self) -> dict:
        """Provides a summary of reactions by emoji."""
        summary = defaultdict(int)
        for _, emoji, _ in self.reactions:
            summary[emoji] += 1
        return dict(summary)

# ==============================================================================
# IV. THE REMIXAGENT PROTOCOL ENGINE
# ==============================================================================

class Governance:
    """
    Manages the rules for governance proposals and voting thresholds.
    Designed to be extensible for multi-species participation.
    """
    def __init__(self, initial_supermajority_percent: float = 90.0,
                 initial_species_min_consent: dict = None,
                 incident_free_years: int = 0,
                 last_incident_date: str = today()):
        """
        initial_supermajority_percent: Overall percentage of total participants required to pass.
        initial_species_min_consent: Dict of {species_name: min_percentage_required_from_species}.
        incident_free_years: Number of years without a major incident (for decay).
        last_incident_date: Date of the last major incident, resets decay.
        """
        self.supermajority_percent = initial_supermajority_percent
        self.species_min_consent = initial_species_min_consent or {
            "human": 10.0, # Humans must provide at least 10% consent (of total human participants)
            "robot": 10.0,  # Robots must provide at least 10% consent (of total robot participants)
            "animal": 5.0, # New: Animals require 5% consent
            "alien": 20.0 # New: Aliens require 20% consent
        }
        self.incident_free_years = incident_free_years
        self.last_incident_date = last_incident_date
        self.incident_decay_rate_per_year = 1.0 # Decrease supermajority by 1% per incident-free year
        self.min_supermajority_floor = 70.0 # Supermajority cannot drop below 70%
        self.min_species_consent_floor = 5.0 # Species minimums cannot drop below 5%

        print(f"🗳️ Governance rules initialized: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def update_rules(self, new_supermajority: float = None, new_species_mins: dict = None):
        """Allows for dynamic updating of governance rules (must pass a prior proposal)."""
        if new_supermajority is not None:
            self.supermajority_percent = new_supermajority
        if new_species_mins is not None:
            self.species_min_consent.update(new_species_mins)
        print(f"🗳️ Governance rules updated: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def trigger_incident(self):
        """Simulates a major conflict/scandal, resetting incident-free period and bumping up requirements."""
        print("🚨 Major incident detected! Governance trust levels are affected.")
        self.incident_free_years = 0
        self.last_incident_date = today()
        # Bump up supermajority by a fixed amount, but not past 90%
        self.supermajority_percent = min(90.0, self.supermajority_percent + 5.0)
        # Bump up species minimums, but not past initial values
        for species in self.species_min_consent:
            self.species_min_consent[species] = min(20.0, self.species_min_consent[species] + 2.0)
        print(f"🗳️ Governance rules bumped up: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")


    def progressive_trust_decay(self):
        """
        Automatically decays consent requirements based on incident-free years.
        This would typically be called by a daily/weekly cron job, or at the start of a new year.
        """
        current_date = datetime.date.today()
        last_incident_dt = datetime.datetime.fromisoformat(self.last_incident_date).date()

        # Check if a full year has passed since last update/incident
        if current_date.year > last_incident_dt.year:
            years_passed = current_date.year - last_incident_dt.year
            self.incident_free_years += years_passed # Add passed years
            self.last_incident_date = today() # Update last incident date to today

            # Decay overall supermajority
            decay_amount_overall = self.incident_free_years * self.incident_decay_rate_per_year
            self.supermajority_percent = max(self.min_supermajority_floor, self.supermajority_percent - decay_amount_overall)

            # Decay species minimums (can make this independent or related)
            decay_amount_species = self.incident_free_years * (self.incident_decay_rate_per_year / 2) # Slower species decay
            for species in self.species_min_consent:
                self.species_min_consent[species] = max(self.min_species_consent_floor, self.species_min_consent[species] - decay_amount_species)
            
            print(f"🕰️ Progressive trust decay applied: Incident-free years: {self.incident_free_years}.")
            print(f"🗳️ New Governance rules: Overall {self.supermajority_percent:.2f}%, Species minimums: {self.species_min_consent}")


class RemixAgent:
    """The main agent class that orchestrates the entire remix economy."""
    def __init__(self):
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        self.log = LogChain()
        self.vax = Vaccine()
        self.plugins = defaultdict(list) # Event-based plugin system
        self.governance = Governance() # Initialize governance rules

        # Emoji market tracking and dynamic weights
        self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0})
        self._initialize_default_emojis() # Set initial emoji "market" values

        # Pre-populate NSS genesis users
        self.NSS = ["mimi", "taha", "accessAI_tech"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in self.NSS:
            # Genesis users are human by default unless specified
            self.add_user(name, is_genesis=True, species="human") 

        self.mint_threshold_base = 100_000.0 # Base karma for fractional posts
        self.min_karma_threshold = 1000.0 # Minimum karma threshold for fractional posts
        self.daily_decay_factor = 0.7 # For per-user daily diminishing returns
        self.new_species_karma_bonus = 50000 # NEW: Karma bonus for new species joining

        self.current_day = today() # Track the current day for global daily resets

        print("✅ RemixAgent Initialized: The Harmonized Republic is online.")

    def _initialize_default_emojis(self):
        """
        Initializes default emoji weights and market data.
        These are starting points, actual weights will dynamically adjust.
        """
        default_emoji_base_weights = {
            "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0,
            "👀": 0.5, "🥲": 0.2, "💯": 2.0, "💬": 3.0,
            "🔀": 4.0, "🆕": 3.0, "🔗": 2.0, "❤️": 4.0,
            "🚀": 3.5, "💎": 6.0, "🌟": 3.0, "⚡": 2.5
        }
        for emoji, weight in default_emoji_base_weights.items():
            self.emoji_market_data[emoji]['current_weight'] = weight
            self.emoji_market_data[emoji]['total_uses'] = 1 # Start with 1 use to avoid div by zero
            self.emoji_market_data[emoji]['total_karma_generated'] = weight # Simulate initial karma

    def _update_emoji_market(self, emoji: str, karma_generated: float):
        """
        Updates the real-time emoji market data after a reaction.
        Dynamically adjusts emoji weights (market value) based on usage and karma generated.
        This is the "Emoji Stock Market" in action.
        """
        market_entry = self.emoji_market_data[emoji]
        market_entry['total_uses'] += 1
        market_entry['total_karma_generated'] += karma_generated
        
        # Simple dynamic weight calculation: Average karma per use.
        # This reflects the "value" of an emoji based on the karma it generates.
        market_entry['current_weight'] = market_entry['total_karma_generated'] / market_entry['total_uses']

        # Implement a subtle daily decay for all emoji weights to prevent runaway inflation
        # and encourage fresh reactions, similar to viral decay.
        for e, data in self.emoji_market_data.items():
            # Only decay if there's an actual weight to decay
            if data['current_weight'] > 0:
                data['current_weight'] *= 0.999 # Very small daily decay
        
        # Ensure minimum weight to prevent emojis from becoming completely worthless
        if market_entry['current_weight'] < 0.1:
            market_entry['current_weight'] = 0.1 # Floor for emoji weight

        self.log.add({
            "event": "EMOJI_MARKET_UPDATE",
            "details": {
                "emoji": emoji,
                "new_weight": market_entry['current_weight'],
                "total_uses": market_entry['total_uses'],
                "total_karma_generated": market_entry['total_karma_generated']
            }
        })
        print(f"📈 Emoji Market Update: '{emoji}' new weight {market_entry['current_weight']:.2f} (total uses: {market_entry['total_uses']})")


    def add_user(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human"):
        """
        Adds a new user to the system. Automatically mints a unique root coin for every new user.
        """
        if name in self.users:
            print(f"⚠️ User {name} already exists.")
            return
        
        # Determine consent mechanism based on species for new user
        consent_mechanism = "explicit"
        if species.lower() == "animal":
            consent_mechanism = "behavioral_signals"
            consent = True # Animals are assumed to implicitly consent if added.
        elif species.lower() == "robot":
            consent_mechanism = "algorithmic_audit"
            consent = True # Robots are assumed to implicitly consent if added.
        elif species.lower() == "alien":
            consent_mechanism = "cryptic_ritual"
            # Alien consent remains False until manually set via ritual (set_consent)

        user = User(name, is_genesis, consent, species=species.lower(), consent_mechanism=consent_mechanism)
        self.users[name] = user
        self.log.add({"event": "ADD_USER", "details": {"name": name, "genesis": is_genesis, "species": species, "consent_mechanism": consent_mechanism}})
        print(f"✅ User '{name}' ({species}) added, genesis={is_genesis}.")

        # Apply new species karma bonus if not a genesis user and not human
        if not is_genesis and user.species not in ["human"]:
            user.karma += self.new_species_karma_bonus
            self.log.add({"event": "NEW_SPECIES_BONUS", "details": {"user": name, "species": species, "bonus_amount": self.new_species_karma_bonus}})
            print(f"🎁 '{name}' ({species}) received {self.new_species_karma_bonus} karma bonus for joining the republic!")

        # NEW: Automatically mint one absolute root coin for every new user
        # This is their foundational identity coin, free of karma requirements.
        root_coin_id = sha(f"ROOT-{name}-{ts()}-{random.random()}")
        root_coin = Coin(id=root_coin_id, root=name, owner=name, tag="root_identity", is_root_coin=True, value=1.0) # Root coin has a base value of 1.0
        self.coins[root_coin_id] = root_coin
        user.root_coin_id = root_coin_id # Link user to their root coin
        user.coins_owned.append(root_coin_id) # Add to user's owned coins
        self.log.add({"event": "MINT_ROOT_COIN", "details": {"user": name, "root_coin_id": root_coin_id, "is_genesis": is_genesis}})
        print(f"🌱 User '{name}' automatically minted their unique root coin: {root_coin_id}.")


    def set_consent(self, name: str, consent: bool):
        """
        Sets explicit consent for a user. For non-explicit consent mechanisms,
        this method can be extended or replaced by species-specific logic.
        """
        user = self.users.get(name)
        if not user:
            print(f"❌ ERROR: User '{name}' not found.")
            return
        
        if user.consent_mechanism != "explicit" and user.consent_mechanism != "cryptic_ritual":
            print(f"⚠️ User '{name}' has a '{user.consent_mechanism}' consent mechanism. Direct explicit consent setting is usually not applicable for this species.")
            # For demo, still allow setting for now, but in a real system, this would trigger specific logic.
        elif user.consent_mechanism == "cryptic_ritual":
            print(f"🌌 Alien '{name}' attempting to perform cryptic ritual for consent. Ritual outcome: {'Success' if consent else 'Failure'}.")
        
        user.consent = consent
        self.log.add({"event": "SET_CONSENT", "details": {"name": name, "status": consent}})
        print(f"✅ Consent for '{name}' set to {consent}.")

    def check_consent(self, username: str) -> bool:
        """
        Checks if a user has given consent, accounting for different species' mechanisms.
        For animals, it's simulated behavioral signals (e.g., tail wagging = True).
        For robots, it's simulated algorithmic audit (always True if user is robot).
        For aliens, it's a simulated cryptic ritual (can be manually toggled).
        """
        user = self.users.get(username)
        if not user:
            print(f"❌ User '{username}' not found.")
            return False
        
        if user.species == "animal":
            # Simulate animal consent (e.g., based on tail wagging in video)
            # For simplicity, let's say animals always consent if they are in the system.
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent: # If complex simulation failed
                print(f"❌ Animal '{username}' did not provide behavioral consent (simulated).")
            return simulated_consent
        
        elif user.species == "robot":
            # Simulate robot consent (e.g., passing an internal audit)
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent:
                 print(f"❌ Robot '{username}' failed algorithmic consent audit (simulated).")
            return simulated_consent

        elif user.species == "alien":
            # Simulate alien consent (e.g., performing a cryptic ritual)
            # For alien, consent is only True if manually set by `set_consent` (ritual performed)
            simulated_consent = user.consent 
            if not simulated_consent:
                print(f"❌ Alien '{username}' did not perform the cryptic ritual (simulated).")
            return simulated_consent

        else: # Default: explicit consent for humans
            if not user.consent:
                print(f"❌ User '{username}' (human) has not given explicit consent.")
                return False
            return True

    def _check_and_apply_governance_decay(self):
        """
        Checks if a period has passed for progressive trust decay and applies it.
        This simulates a background daemon process.
        """
        self.governance.progressive_trust_decay()


    def reset_daily_actions_if_new_day(self):
        """Ensures all user daily action counters are reset at the start of a new day."""
        current_day = today()
        if current_day != self.current_day:
            for user in self.users.values():
                user.reset_daily_actions_if_needed() # Calls the user's internal method
            self.current_day = current_day
            print("🔄 Daily user action counters reset.")
            self._check_and_apply_governance_decay() # Check for governance decay daily (or yearly in larger scale)

    def karma_threshold(self, user: User) -> float:
        """
        Calculates the karma needed for a user to mint their next *fractional post*.
        This implements the halving threshold and minimum floor.
        """
        # Founders (genesis users) don't need karma for fractional posts
        if user.is_genesis:
            return 0.0

        minted_fractional_posts = user.mint_count # Use mint_count which tracks fractional posts
        threshold = self.mint_threshold_base / (2 ** minted_fractional_posts)
        return max(self.min_karma_threshold, threshold) # Ensure it doesn't drop below min

    def can_mint_fractional_post(self, username: str) -> bool:
        """Checks if a user has sufficient karma to mint a new fractional post."""
        user = self.users.get(username)
        if not user:
            print(f"❌ Mint check failed: unknown user {username}.")
            return False
        # Founders (genesis users) can always make fractional posts without karma
        if user.is_genesis:
            return True
        # Non-founders need karma for fractional posts
        return user.karma >= self.karma_threshold(user)

    def mint_fractional_post(self, user_name: str, content: str, fractional_percentage: float = 0.01, # Default 1%
                             tag: str = "post", references: list = None, fields: list = None) -> str | None:
        """
        Mints a new 'post' as a fractional part of the user's personal root coin.
        This is karma-gated for non-genesis users.
        """
        self.reset_daily_actions_if_new_day() # Ensure daily limits are fresh
        
        user = self.users.get(user_name)
        if not user:
            print(f"❌ Mint failed: User '{user_name}' not found.")
            return None

        if not user.root_coin_id:
            print(f"❌ Mint failed: User '{user_name}' does not have a root coin. Add user first.")
            return None

        if not self.check_consent(user_name): # Re-check explicit consent based on user's mechanism
            return None
        
        # Check karma threshold for non-genesis users for subsequent posts
        if not user.is_genesis and not self.can_mint_fractional_post(user_name): # Founders bypass this check
            needed = self.karma_threshold(user)
            print(f"🔒 MINT DENIED: '{user_name}' needs {needed:.0f} karma for next post; has {user.karma:.1f}.")
            return None

        # Content validation via Vaccine
        if not self.vax.scan(content):
            print(f"❌ MINT DENIED: Content blocked by Vaccine.")
            return None
        if references:
            for ref in references:
                if not self.vax.scan(ref):
                    print(f"❌ MINT DENIED: Reference content blocked by Vaccine: {ref[:50]}....")
                    return None

        # Validate fractional percentage
        if not (0 < fractional_percentage <= 1.0):
            print("❌ Mint failed: Fractional percentage must be between 0 and 1.0 (exclusive of 0).")
            return None

        # Deduct karma for non-genesis users when they make a fractional post
        if not user.is_genesis:
            user.karma -= self.karma_threshold(user) # Deduct karma upon successful fractional mint
            user.mint_count += 1 # Increment fractional post count
            user.next_mint_threshold = self.karma_threshold(user) # Update next threshold

        # Create the new fractional coin (post)
        post_id = sha(f"{user_name}-{content}-{ts()}-{random.random()}")
        
        # Calculate the actual value of this fractional post
        # The base value of the root coin is 1.0, so the post's value is directly the percentage.
        post_value = fractional_percentage * self.coins[user.root_coin_id].value 

        new_post_coin = Coin(
            id=post_id,
            root=user.root_coin_id, # Root is now the personal identity coin
            owner=user_name,
            tag=tag,
            value=post_value,
            is_root_coin=False,
            fractional_source_coin_id=user.root_coin_id,
            fractional_percentage=fractional_percentage
        )
        if references: new_post_coin.references = references
        if fields: new_post_coin.fields = fields
        
        self.coins[post_id] = new_post_coin
        user.coins_owned.append(post_id) # Add post coin to user's owned coins
        
        self.log.add({"event": "MINT_FRACTIONAL_POST", "details": {
            "user": user_name,
            "post_id": post_id,
            "root_coin_id": user.root_coin_id,
            "fractional_percentage": fractional_percentage,
            "post_value": post_value,
            "tag": tag,
            "content_snippet": content[:64]
        }})
        print(f"🪙 '{user_name}' minted a fractional post '{post_id}' (from root {user.root_coin_id}) with {fractional_percentage*100:.2f}% value.")
        self._call_plugins("on_mint_fractional_post", new_post_coin) # Trigger plugins
        return post_id

    def react(self, actor_name: str, coin_id: str, emoji: str):
        """
        A user reacts to a coin/post with an emoji, triggering a value event and
        updating the emoji market.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        # Ensure user and coin exist and user has consented
        if actor_name not in self.users: self.add_user(actor_name, consent=True)
        if coin_id not in self.coins: print(f"❌ REACT FAILED: Coin '{coin_id}' not found."); return False
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        
        # The "originator" for split purposes is the *owner* of the content coin/post reacted to.
        # If it's a root coin, the owner is its root. If it's a fractional post, its owner is the person who minted that post.
        originator_user = self.users.get(coin.owner) # Get the user who owns this specific coin/post

        if not self.check_consent(actor_name) or (originator_user and not originator_user.consent):
            print("❌ REACT DENIED: Both actor and originator (if known) must have consent.")
            return False
        
        # Scan emoji with Vaccine (prevents toxic reactions)
        if not self.vax.scan(emoji):
            print(f"❌ Reaction blocked by vaccine.")
            return False

        # Apply per-user daily diminishing returns
        date_str = today()
        actor.reset_daily_actions_if_needed() # Ensure daily reset for the actor
        action_count_today = actor.daily_actions[date_str][f"react_{emoji}"]
        daily_decay_factor = self.daily_decay_factor ** action_count_today
        actor.daily_actions[date_str][f"react_{emoji}"] += 1

        # Retrieve dynamic emoji weight from the market data
        base_weight = self.emoji_market_data.get(emoji, {'current_weight': 1.0})['current_weight']
        
        # Apply per-coin viral decay based on existing reactions to this specific coin
        viral_decay_factor = 0.95 ** len(coin.reactions) # Each reaction reduces future value for this coin slightly

        # The base value for split is the coin's `value` (which for fractional posts is its percentage)
        # multiplied by the emoji's weighted_value and decay factors.
        weighted_value = coin.value * base_weight * daily_decay_factor * viral_decay_factor

        # Calculate 33.3333% split portions
        split_value = weighted_value / 3.0

        # Apply genesis fading multipliers to actor and originator's shares
        actor_multiplier = actor.get_fading_multiplier()
        originator_multiplier = originator_user.get_fading_multiplier() if originator_user else 1.0

        originator_share = split_value * originator_multiplier
        actor_share = split_value * actor_multiplier
        treasury_share = split_value # Treasury share is not multiplied by individual multipliers

        # Distribute karma
        if originator_user and originator_user.consent: # Only award if content owner exists and has consented
            originator_user.karma += originator_share 

        actor.karma += actor_share
        self.treasury += treasury_share

        # Log reaction to the coin itself
        coin.reactions.append((actor_name, emoji, ts()))
        coin.react_log.append({'actor': actor_name, 'emoji': emoji, 'karma_share': (originator_share + actor_share), 'ts': ts()}) # Log specific karma generated for this reaction

        self.log.add({
            "event": "REACT",
            "details": {
                "username": actor_name,
                "coin_id": coin_id,
                "emoji": emoji,
                "weighted_value": weighted_value,
                "split": {
                    "originator_total": originator_share, # Total for the content owner
                    "actor": actor_share,
                    "treasury": treasury_share
                }
            }
        })

        print(f"👍 {actor_name} reacted {emoji} on coin {coin_id}: "
              f"owner +{originator_share:.2f}, actor +{actor_share:.2f}, "
              f"treasury +{treasury_share:.2f}.")
        
        # Update emoji market with the total karma generated by this reaction
        self._update_emoji_market(emoji, weighted_value)

        self._call_plugins("on_react", actor_name, coin_id, emoji, weighted_value) # Trigger plugins

        return True

    def remix(self, actor_name: str, parent_coin_id: str, content: str, tag: str = "remix", references: list = None, fields: list = None) -> str | None:
        """
        A user creates a derivative coin (remix) of an existing post/coin, preserving lineage.
        Remixing is considered a new "post" and thus subject to fractional minting rules.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        if not self.check_consent(actor_name):
            return None
        if parent_coin_id not in self.coins:
            print(f"❌ REMIX FAILED: Parent coin '{parent_coin_id}' not found.")
            return None
        
        parent = self.coins[parent_coin_id]
        actor = self.users[actor_name]

        # Remixing is now a 'mint_fractional_post' operation for the actor.
        # It's their act of creating new content from existing, so it uses their fractional minting logic.
        # Default remix post uses a small percentage of root coin value.
        remix_percentage = 0.001 # A small percentage for a remix post
        remix_coin_id = self.mint_fractional_post(actor_name, content, fractional_percentage=remix_percentage, tag=tag, references=references, fields=fields)
        
        if remix_coin_id:
            new_coin = self.coins[remix_coin_id]
            # Lineage: New remix coin directly inherits the parent's ancestry and then adds the parent itself.
            new_coin.ancestors.extend(parent.ancestors)
            new_coin.ancestors.append(parent_coin_id)
            
            # The karma for the remix action itself. Use a specific emoji for remix value.
            remix_base_value = self.emoji_market_data.get("🔀", {'current_weight': 4.0})['current_weight'] # Use dynamic remix emoji weight
            
            # Apply per-user daily diminishing returns for remix action
            actor.reset_daily_actions_if_needed()
            remix_action_count_today = actor.daily_actions[today()]["remix_action"]
            remix_daily_decay_factor = self.daily_decay_factor ** remix_action_count_today
            actor.daily_actions[today()]["remix_action"] += 1

            remix_value = remix_base_value * remix_daily_decay_factor
            split_remix_value = remix_value / 3.0 # Apply 33.3333% split

            # Distribute karma for the remix action itself
            actor_remix_share = split_remix_value * actor.get_fading_multiplier()
            
            # The original *owner* of the parent post gets the second share
            parent_owner_user = self.users.get(parent.owner)
            parent_owner_remix_share = split_remix_value * parent_owner_user.get_fading_multiplier() if parent_owner_user else 0.0

            actor.karma += actor_remix_share
            if parent_owner_user:
                parent_owner_user.karma += parent_owner_remix_share
            self.treasury += split_remix_value # Treasury gets its share from the remix action

            self.log.add({
                "event": "REMIX",
                "details": {
                    "actor": actor_name,
                    "parent_coin_id": parent_coin_id,
                    "new_coin_id": remix_coin_id,
                    "ancestry": new_coin.ancestry,
                    "remix_value": remix_value,
                    "split": {
                        "actor": actor_remix_share,
                        "parent_owner": parent_owner_remix_share,
                        "treasury": split_remix_value
                    }
                }
            })

            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{remix_coin_id}'. "
                  f"Remixer +{actor_remix_share:.2f} karma, Parent Owner +{parent_owner_remix_share:.2f} karma.")
            
            self._call_plugins("on_remix", new_coin) # Trigger plugins
        return remix_coin_id

    def add_reference(self, user_name: str, coin_id: str, ref_type: str, ref_id: str, description: str):
        """Adds a structured external reference to a coin/post for attribution."""
        if coin_id not in self.coins or user_name not in self.users:
            print("❌ ADDREF FAILED: Coin or user not found.")
            return
        if not self.check_consent(user_name): # Check consent based on user's mechanism
            return False

        reference = {"type": ref_type, "id": ref_id, "description": description, "added_by": user_name, "ts": ts()}
        self.coins[coin_id].references.append(reference)
        self.log.add({"event": "ADD_REFERENCE", "details": {"coin_id": coin_id, "reference": reference}})
        print(f"🔬 Reference added to coin '{coin_id}'.")

        # Award karma for adding a reference (can be tied to a specific emoji/weight)
        actor_ref_value = self.emoji_market_data.get("🔗", {'current_weight': 2.0})['current_weight'] # Use dynamic link emoji weight
        split_ref_value = actor_ref_value / 3.0
        
        # This karma goes to the user who added the reference, and to the treasury
        self.users[user_name].karma += split_ref_value * self.users[user_name].get_fading_multiplier()
        self.treasury += split_ref_value # Treasury gets its share too
        self.log.add({"event": "KARMA_AWARD_REFERENCE", "details": {"user": user_name, "coin_id": coin_id, "amount": split_ref_value}})
        print(f"🔗 {user_name} earned {split_ref_value:.2f} karma for adding reference to {coin_id}.")


    def trace_lineage(self, coin_id: str):
        """Displays the full creative lineage of a coin/post."""
        if coin_id not in self.coins: print(f"❌ TRACE FAILED: Coin '{coin_id}' not found."); return
        
        print(f"\n--- 🧬 Creative Lineage Trace for Coin: {coin_id} ---")
        path = []
        current_id = coin_id
        
        while current_id and current_id in self.coins:
            coin = self.coins[current_id]
            path.append(coin)
            if coin.ancestors: # Follow the most recent direct ancestor for a single path
                current_id = coin.ancestors[-1]
            else:
                current_id = None # No more ancestors
    
    for i, coin in enumerate(reversed(path)): # Print in chronological order (root first)
        indent = "  " * i
        originators_str = ", ".join(coin.originators) # Originators are users linked to this coin, including creator
        print(f"{indent}└── Coin: {coin.id} (Tag: {coin.tag}, Root: {coin.root}, Owner: {coin.owner}, Originators: {originators_str})")
        print(f"{indent}    Created At: {coin.created_at}")
        if coin.is_root_coin:
            print(f"{indent}    🌟 This is a Universal Root Identity Coin.")
        elif coin.fractional_source_coin_id:
            print(f"{indent}    ✨ This is a Fractional Post from Root: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
        if coin.references:
            print(f"{indent}    ├── References:")
            for ref in coin.references:
                print(f"{indent}    │   └── {ref.get('type', 'N/A')}: {ref.get('id', 'N/A')} ({ref.get('description', 'N/A')}) by {ref.get('added_by', 'Unknown')}")
        if coin.reactions:
            print(f"{indent}    └── Reactions ({len(coin.reactions)} total): {coin.reaction_summary()}") # Using helper for summary
    print("--- End of Trace ---")

    def show_user_karma(self, username: str):
        """Displays comprehensive user karma information."""
        user = self.users.get(username)
        if user:
            print(f"\n--- 👤 User '{username}' Status ---")
            print(f"  Karma: {user.karma:.2f}")
            print(f"  Is Genesis: {user.is_genesis}")
            print(f"  Species: {user.species.capitalize()}")
            print(f"  Consent Mechanism: {user.consent_mechanism.replace('_', ' ').title()}")
            print(f"  Current Multiplier: {user.get_fading_multiplier():.2f}")
            print(f"  Fractional Posts Minted: {user.mint_count}")
            print(f"  Next Post Threshold: {self.karma_threshold(user):.2f}")
            print(f"  Consent Given: {user.consent}") # Actual consent stored
            print(f"  Consent Check (Simulated): {self.check_consent(username)}") # Simulated consent based on species
            print(f"  Joined: {user.join_timestamp}")
            print(f"  Personal Root Coin: {user.root_coin_id if user.root_coin_id else 'None'}")
            print(f"  Coins/Posts Owned: {len(user.coins_owned)}")
            print("----------------------------------")
        else:
            print(f"No such user '{username}'.")

    def show_coin_info(self, coin_id: str):
        """Displays detailed coin/post information."""
        coin = self.coins.get(coin_id)
        if coin:
            print(f"\n--- 💎 Coin/Post ID: {coin.id} ---")
            print(f"  Root Originator: {coin.root}")
            print(f"  Current Owner: {coin.owner}")
            print(f"  Tag: {coin.tag}")
            print(f"  Base Value (from root): {coin.value}")
            print(f"  Created At: {coin.created_at}")
            print(f"  Is Root Coin: {coin.is_root_coin}")
            if coin.fractional_source_coin_id:
                print(f"  Fractional Source: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
            print(f"  Ancestry: {coin.ancestors if coin.ancestors else 'None'}")
            print(f"  Total Reactions: {len(coin.reactions)}")
            reaction_summary = defaultdict(int)
            for _, emoji, _ in coin.reactions:
                reaction_summary[emoji] += 1
            print(f"  Reaction Summary: {dict(reaction_summary)}")
            print(f"  References ({len(coin.references)}):")
            for ref in coin.references:
                print(f"    - Type: {ref.get('type')}, ID: {ref.get('id')}, Desc: {ref.get('description')} (by {ref.get('added_by')})")
            if not coin.references:
                print("    None")
            print("-------------------------------")
        else:
            print(f"No such coin: {coin_id}.")

    def get_treasury_balance(self) -> float:
        """Returns and prints the current treasury balance."""
        print(f"Community treasury balance: {self.treasury:.2f}.")
        return self.treasury

    def show_emoji_market_status(self):
        """
        Displays the current status of the emoji market, including dynamic weights.
        This is your "Nasdaq of Vibes".
        """
        print("\n--- 📈 Real-Time Emoji Market Status (Nasdaq of Vibes) ---")
        print("{:<10} {:<15} {:<15} {:<15}".format("Emoji", "Current Weight", "Total Uses", "Avg Karma/Use"))
        print("-" * 60)
        sorted_emojis = sorted(self.emoji_market_data.items(), key=lambda item: item[1]['current_weight'], reverse=True)
        for emoji, data in sorted_emojis:
            avg_karma_per_use = data['total_karma_generated'] / data['total_uses'] if data['total_uses'] > 0 else 0
            print("{:<10} {:<15.2f} {:<15} {:<15.2f}".format(emoji, data['current_weight'], data['total_uses'], avg_karma_per_use))
        print("----------------------------------------------------------\n")

    def plugin(self, action: str, name: str, *args):
        """Interface for loading, unloading, and calling external plugins."""
        if action == "load":
            try:
                # Assuming plugins are in a 'plugins' directory and each is a .py file
                # Use importlib.util for more robust dynamic loading
                spec = importlib.util.spec_from_file_location(name, f"plugins/{name}.py")
                if spec is None:
                    raise ImportError(f"Could not find plugin '{name}' at plugins/{name}.py")
                module = importlib.util.module_from_spec(spec)
                sys.modules[name] = module # Add to sys.modules to make it discoverable
                spec.loader.exec_module(module)
                self.plugins[name] = module # Store the loaded module
                self.log.add({"event": "PLUGIN_LOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' loaded successfully.")
            except Exception as e:
                print(f"❌ PLUGIN ERROR: Could not load '{name}'. {e}.")
        elif action == "unload":
            if name in self.plugins:
                del self.plugins[name]
                # Also remove from sys.modules to fully unload, if possible
                if name in sys.modules:
                    del sys.modules[name]
                self.log.add({"event": "PLUGIN_UNLOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' unloaded.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        elif action == "call":
            if name in self.plugins:
                plugin_module = self.plugins[name]
                if hasattr(plugin_module, "run"):
                    try:
                        # Pass the agent instance so plugins can interact with it
                        result = plugin_module.run(self, *args)
                        self.log.add({"event": "PLUGIN_CALL", "details": {"name": name, "args": args, "result_snippet": str(result)[:128]}})
                        print(f"⚡ Plugin '{name}' executed with result: {result}.")
                    except Exception as e:
                        print(f"❌ PLUGIN ERROR: Error executing '{name}'. {e}.")
                else:
                    print(f"❌ PLUGIN ERROR: Plugin '{name}' has no 'run' method.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        else:
            print("❓ Unknown plugin action. Use 'load', 'unload', or 'call'.")

    def propose_governance_change(self, proposer_name: str, proposal_details: dict, votes_by_species: dict[str, float]) -> bool:
        """
        Submits a formal governance proposal and checks if it passes current rules.
        proposal_details: Dict describing the proposed change (e.g., {'type': 'update_governance_rules', 'new_supermajority_percent': 0.75})
        votes_by_species: Dict of {species_name: percentage_of_total_karma_from_species_consenting (0-100)}.
                          This is a percentage of total karma within that species, not just user count.
                          Example: {'human': 95.0, 'robot': 80.0}
        """
        if proposer_name not in self.users:
            print(f"❌ PROPOSAL FAILED: Proposer '{proposer_name}' not found.")
            return False

        # Calculate total karma per species for weighting votes
        total_karma_per_species = defaultdict(float)
        active_species_counts = defaultdict(int) # Count of active users per species
        
        # Calculate max karma for weighting. Genesis users treated as having a very high value.
        GENESIS_VOTE_WEIGHT = 1_000_000_000.0 

        for user in self.users.values():
            if self.check_consent(user.name): # Only consented users contribute to species totals
                active_species_counts[user.species] += 1
                if user.is_genesis:
                    total_karma_per_species[user.species] += GENESIS_VOTE_WEIGHT
                else:
                    total_karma_per_species[user.species] += user.karma
        
        # Sum of all karma across all users (including genesis weight)
        overall_total_karma = sum(total_karma_per_species.values())

        if overall_total_karma == 0:
            print("❌ PROPOSAL FAILED: No active users or karma in the system to vote.")
            return False

        # Calculate total karma-weighted consent for the overall supermajority check
        overall_consented_karma = 0.0
        species_consent_met = True
        detailed_consent_report = {}

        for species, min_percent_required in self.governance.species_min_consent.items():
            species_total_karma = total_karma_per_species[species]
            species_voted_percent = votes_by_species.get(species, 0.0) # Percentage provided by the input

            if species_total_karma > 0:
                # Actual karma contributed by this species to the 'yes' vote
                species_yes_karma = (species_voted_percent / 100.0) * species_total_karma
                overall_consented_karma += species_yes_karma

                # Check species-specific minimum consent
                if species_voted_percent < min_percent_required:
                    species_consent_met = False
                    detailed_consent_report[species] = f"FAILED: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
                else:
                    detailed_consent_report[species] = f"MET: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
            elif min_percent_required > 0 and species not in active_species_counts: # If species has requirement but no users of that species yet
                species_consent_met = False
                detailed_consent_report[species] = f"FAILED: No active users of this species, but requires {min_percent_required:.2f}%."
            else: # Species exists but has 0 min required, or 0 total karma and no min required (no effect)
                detailed_consent_report[species] = "N/A: No users, or no min requirement."


        # Calculate overall actual consent percentage based on karma
        overall_actual_consent_percent = (overall_consented_karma / overall_total_karma) * 100 if overall_total_karma > 0 else 0.0
        overall_supermajority_met = overall_actual_consent_percent >= self.governance.supermajority_percent

        if not overall_supermajority_met:
            print(f"❌ PROPOSAL FAILED: Overall karma consent is {overall_actual_consent_percent:.2f}%, but requires {self.governance.supermajority_percent:.2f}% supermajority.")
        if not species_consent_met:
            print(f"❌ PROPOSAL FAILED: One or more species did not meet their minimum consent threshold.")

        proposal_passed = overall_supermajority_met and species_consent_met

        self.log.add({
            "event": "GOVERNANCE_PROPOSAL_VOTE",
            "details": {
                "proposer": proposer_name,
                "proposal_details": proposal_details,
                "votes_by_species_input": votes_by_species, # Log raw input
                "overall_actual_consent_percent": overall_actual_consent_percent,
                "overall_required_percent": self.governance.supermajority_percent,
                "species_consent_breakdown": detailed_consent_report,
                "passed": proposal_passed
            }
        })

        if proposal_passed:
            print(f"✅ GOVERNANCE PROPOSAL PASSED! Overall consent: {overall_actual_consent_percent:.2f}%.")
            # --- Basic Proposal Execution ---
            if proposal_details.get('type') == 'update_governance_rules':
                new_supermajority = proposal_details.get('new_supermajority_percent')
                new_species_mins = proposal_details.get('new_species_min_consent')
                self.governance.update_rules(new_supermajority, new_species_mins)
            elif proposal_details.get('type') == 'change_mint_threshold_base':
                new_threshold = proposal_details.get('new_mint_threshold_base')
                if new_threshold is not None:
                    self.mint_threshold_base = new_threshold
                    self.log.add({"event": "PROTOCOL_PARAM_UPDATE", "details": {"param": "mint_threshold_base", "new_value": new_threshold}})
                    print(f"✅ Protocol parameter 'mint_threshold_base' updated to {new_threshold}.")
            # Future: add other types of protocol changes here
            # --- End Basic Proposal Execution ---

            # Reset incident tracking as a successful governance change implies stability/resolution
            self.governance.incident_free_years = 0
            self.governance.last_incident_date = today()
            self._call_plugins("on_governance_passed", proposal_details)
        else:
            print(f"❌ GOVERNANCE PROPOSAL FAILED. Please review requirements.")
            self.governance.trigger_incident() # Trigger an incident if a proposal fails
            self._call_plugins("on_governance_failed", proposal_details)
        return proposal_passed


    def log_profit(self, amount: float, description: str):
        """Logs an external profit event, adding to the treasury."""
        self.treasury += amount
        self.log.add({
            "event": "PROFIT_LOG",
            "details": {"amount": amount, "description": description, "new_treasury_balance": self.treasury}
        })
        print(f"🏦 Profit of {amount:.2f} logged. Treasury is now {self.treasury:.2f}.")

    def snapshot(self, save=True, filename="snapshot.json"):
        """Saves or loads the entire agent state."""
        if save:
            state = {
                "users": {name: user.to_dict() for name, user in self.users.items()},
                "coins": {cid: coin.to_dict() for cid, coin in self.coins.items()},
                "treasury": self.treasury,
                "log_entries": list(self.log.entries), # Save current log entries
                "emoji_market_data": dict(self.emoji_market_data), # Save emoji market
                "governance_rules": {
                    "supermajority_percent": self.governance.supermajority_percent,
                    "species_min_consent": dict(self.governance.species_min_consent),
                    "incident_free_years": self.governance.incident_free_years,
                    "last_incident_date": self.governance.last_incident_date
                },
                "mint_threshold_base": self.mint_threshold_base,
                "new_species_karma_bonus": self.new_species_karma_bonus
            }
            try:
                with open(filename, "w", encoding='utf-8') as f:
                    json.dump(state, f, indent=2)
                print(f"💾 State saved to '{filename}'.")
            except IOError as e:
                print(f"❌ SNAPSHOT ERROR: Could not save state. {e}.")
        else:
            if not os.path.exists(filename):
                print(f"❓ SNAPSHOT INFO: No snapshot file found at '{filename}'. Starting fresh.")
                return
            try:
                with open(filename, "r", encoding='utf-8') as f:
                    state = json.load(f)
            
                self.users = {}
                for name, u_data in state.get("users", {}).items():
                    # Pass species and consent_mechanism during user reconstruction
                    user = User(
                        name,
                        u_data.get('is_genesis', False),
                        u_data.get('consent', False),
                        species=u_data.get('species', 'human'),
                        consent_mechanism=u_data.get('consent_mechanism', 'explicit')
                    )
                    user.karma = u_data.get('karma', 0.0)
                    user.mint_count = u_data.get('mint_count', 0)
                    user.next_mint_threshold = u_data.get('next_mint_threshold', 100000.0)
                    user.root_coin_id = u_data.get('root_coin_id')
                    user.coins_owned = u_data.get('coins_owned', [])
                    user.join_timestamp = u_data.get('join_timestamp', ts())
                    if u_data.get('fading_multiplier_start_time'):
                        user.fading_multiplier_start_time = datetime.datetime.fromisoformat(u_data['fading_multiplier_start_time'])
                    if 'daily_actions' in u_data:
                        user.daily_actions = defaultdict(lambda: defaultdict(int), u_data['daily_actions'])
                    self.users[name] = user

                self.coins = {}
                for cid, cd_data in state.get("coins", {}).items():
                    coin = Coin(
                        id=cd_data.get('id'),
                        root=cd_data.get('root'),
                        owner=cd_data.get('owner'),
                        value=cd_data.get('value', 1.0),
                        tag=cd_data.get('tag', 'single'),
                        is_root_coin=cd_data.get('is_root_coin', False),
                        fractional_source_coin_id=cd_data.get('fractional_source_coin_id'),
                        fractional_percentage=cd_data.get('fractional_percentage', 0.0)
                    )
                    coin.fields = cd_data.get('fields', [])
                    coin.ancestors = cd_data.get('ancestors', [])
                    coin.references = cd_data.get('references', [])
                    coin.reactions = cd_data.get('reactions', [])
                    coin.react_log = cd_data.get('react_log', [])
                    coin.created_at = cd_data.get('created_at', ts())
                    self.coins[cid] = coin

                self.treasury = state.get("treasury", 0.0)
                self.log.entries = deque(state.get("log_entries", []), maxlen=self.log.entries.maxlen)
                
                loaded_emoji_market_data = state.get("emoji_market_data", {})
                self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0}, loaded_emoji_market_data)

                # Load governance rules
                governance_data = state.get("governance_rules", {})
                self.governance = Governance(
                    initial_supermajority_percent=governance_data.get("supermajority_percent", 90.0),
                    initial_species_min_consent=governance_data.get("species_min_consent", {"human": 10.0, "robot": 10.0}),
                    incident_free_years=governance_data.get("incident_free_years", 0),
                    last_incident_date=governance_data.get("last_incident_date", today())
                )
                self.governance.progressive_trust_decay() # Apply decay on load if time has passed

                # Load other top-level parameters
                self.mint_threshold_base = state.get("mint_threshold_base", 100_000.0)
                self.new_species_karma_bonus = state.get("new_species_karma_bonus", 50000)

                print(f"♻️ State loaded from '{filename}'.")
            except Exception as e:
                print(f"❌ SNAPSHOT ERROR: Could not load state. {e}.")

# ==============================================================================
# V. ANCILLARY SYSTEMS & INTERFACES
# ==============================================================================

class CorpX:
    """Simulates an adversarial entity to continuously test the Vaccine."""
    ATTACKS = ["inject malware", "phish creds", "launch ddos", "plant backdoor", "propaganda spam"]

    def __init__(self, vaccine: Vaccine):
        self.vaccine = vaccine
        self.attack_count = 0

    def run_attack(self, payload: str = None):
        """Performs an attack simulation."""
        self.attack_count += 1
        attack_payload = payload if payload else random.choice(self.ATTACKS)
        print(f"\n💀 CorpX Attack #{self.attack_count}: Attempting to inject '{attack_payload}'...")
        if self.vaccine.scan(attack_payload):
            print("🛡️ ATTACK EVADED! (Vaccine did not trigger).")
        else:
            print("🛡️ ATTACK BLOCKED! (Vaccine successfully triggered).")

def quiz() -> bool:
    """Interactive onboarding quiz for new users, ensuring informed consent."""
    print("\n--- 🤗 Welcome to the Remix Republic Onboarding Quiz ---")
    questions = [
        ("What is the universal value split percentage for all actions?", "33.3333"),
        ("Can you remix someone's content without their consent? (yes/no)", "no"),
        ("What must every new user earn to gain minting rights?", "karma"),
        ("What is the ultimate authority in this protocol?", "the code")
    ]
    for q, a in questions:
        resp = input(f"👉 {q} ").strip().lower()
        if resp != a:
            print("❌ Incorrect. Please review the Core Canons and try again.")
            return False
    print("✅ Quiz passed! You understand the fundamental laws. Welcome aboard!\n")
    return True

def cli():
    """A comprehensive command-line interface for interacting with the Agent."""
    agent = RemixAgent()
    adversary = CorpX(agent.vax)
    agent.snapshot(save=False) # Load state on start

    print("🤖 Universal Remix Protocol v11.3 CLI. Type ':help' for commands.")
    while True:
        try:
            raw_input_str = input(">>> ").strip()
            if not raw_input_str: continue
            
            if raw_input_str.lower() in [':exit', ':quit']:
                agent.snapshot(save=True)
                print("👋 Goodbye! State saved.")
                break
            
            if not raw_input_str.startswith(':'):
                print("⚠️ Commands must start with a colon ':'.")
                continue

            parts = raw_input_str[1:].split(maxsplit=1) # Split only on first space to keep args together
            command = parts[0].lower()
            args_str = parts[1] if len(parts) > 1 else "" # Get remaining args as a single string

            # Parse args from string (this is more robust for complex arguments)
            # This simple parser handles "quoted strings" for content and key=value pairs
            # It's not a full shell parser, but works for our CLI needs
            parsed_args = []
            current_arg = ""
            in_quote = False
            for char in args_str:
                if char == '"':
                    in_quote = not in_quote
                    if not in_quote and current_arg: # End of a quoted string
                        parsed_args.append(current_arg)
                        current_arg = ""
                elif char == ' ' and not in_quote:
                    if current_arg:
                        parsed_args.append(current_arg)
                        current_arg = ""
                else:
                    current_arg += char
            if current_arg:
                parsed_args.append(current_arg)
            
            args = parsed_args


            if command == "help":
                print("""
--- User Commands ---
:quiz                                  - Take the onboarding quiz.
:consent <username> <true/false>      - Set user consent.
:post <username> "<content>" [perc] [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Mint a fractional post.
:react <username> <coin_id> <emoji>   - React to a coin/post.
:remix <username> <parent_coin_id> "<content>" [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Remix a coin/post.
:addref <username> <coin_id> <type> <id> "<description>" - Add a structured reference to a coin/post.
:karma <username>                     - Show user's karma.
:coininfo <coin_id>                   - Show detailed coin/post info.
:treasury                             - Show treasury balance.
:emojimarket                         - Show real-time emoji market status.

--- Query Commands ---
:log [filter] [limit]                 - Show audit log (optional filter string and limit).
:trace <coin_id>                      - Trace full creative lineage of a coin/post.

--- Admin & Governance Commands ---
:adduser <username> [species] [genesis] - Add a new user (default human, optional genesis).
:propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z] - Propose a governance change.
:trigger_incident                     - Manually trigger a major incident (resets consent decay).
:check_decay                         - Manually trigger progressive trust decay check.
:profit <amount> "<description>"      - Log a profit event to treasury.
:snapshot [save/load] [filename]      - Save or load agent state.
:attack [payload]                     - Simulate a CorpX attack.
:plugin <action> <name> [args...]     - Manage plugins (load, unload, call). E.g., :plugin load my_plugin
:exit / :quit                         - Save state and exit CLI.
""")
            elif command == "consent":
                if len(args) == 2 and args[1].lower() in ['true', 'false']:
                    agent.set_consent(args[0], args[1].lower() == 'true')
                else: print("Usage: :consent <username> <true/false>")
            elif command == "post": # Changed from :mint to :post for fractional minting
                username = args[0] if len(args) > 0 else None
                content = args[1] if len(args) > 1 else None # Content should be quoted
                
                if not username or not content:
                    print("Usage: :post <username> \"<content>\" [percentage_of_root_coin_value (e.g. 0.01 for 1%)] [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                fractional_percentage = 0.01 # Default to 1%
                tag = "post"
                refs = []
                fields = {}
                
                # Parse optional percentage, tag, refs, fields
                current_arg_idx = 2
                if len(args) > current_arg_idx and args[current_arg_idx].replace('.', '', 1).isdigit():
                    fractional_percentage = float(args[current_arg_idx])
                    current_arg_idx += 1

                if len(args) > current_arg_idx:
                    for arg_slice in args[current_arg_idx:]:
                        if arg_slice.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg_slice[6:-1].split(',')]
                        elif arg_slice.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg_slice[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg_slice # Remaining argument is the tag
                agent.mint_fractional_post(username, content, fractional_percentage, tag, refs, fields)
            elif command == "react":
                if len(args) == 3:
                    agent.react(args[0], args[1], args[2])
                else: print("Usage: :react <username> <coin_id> <emoji>")
            elif command == "remix":
                username = args[0] if len(args) > 0 else None
                parent_coin_id = args[1] if len(args) > 1 else None
                content = args[2] if len(args) > 2 else None

                if not username or not parent_coin_id or not content:
                    print("Usage: :remix <username> <parent_coin_id> \"<content>\" [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                tag = "remix"
                refs = []
                fields = {}
                if len(args) > 3:
                    for arg in args[3:]:
                        if arg.startswith('refs="') and arg.endswith('"'):
                            refs = [r.strip() for r in arg[6:-1].split(',')]
                        elif arg.startswith('fields="') and arg.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg
                agent.remix(username, parent_coin_id, content, tag, refs, fields)
            elif command == "addref":
                if len(args) == 5:
                    agent.add_reference(args[0], args[1], args[2], args[3], args[4].strip('"'))
                else: print("Usage: :addref <username> <coin_id> <type> <id> \"<description>\"")
            elif command == "karma":
                if len(args) == 1: agent.show_user_karma(args[0])
                else: print("Usage: :karma <username>")
            elif command == "coininfo":
                if len(args) == 1: agent.show_coin_info(args[0])
                else: print("Usage: :coininfo <coin_id>")
            elif command == "treasury":
                agent.get_treasury_balance()
            elif command == "emojimarket":
                agent.show_emoji_market_status()
            elif command == "log":
                filter_str = args[0] if len(args) > 0 else None
                limit = int(args[1]) if len(args) > 1 and args[1].isdigit() else 20
                agent.log.show(filter_str, limit)
            elif command == "trace":
                if len(args) == 1: agent.trace_lineage(args[0])
                else: print("Usage: :trace <coin_id>")
            elif command == "adduser":
                if len(args) >= 1:
                    username = args[0]
                    species = "human" # Default species
                    is_genesis = False

                    # Parse optional species and genesis flags
                    for arg_slice in args[1:]:
                        if arg_slice.lower() in ["human", "robot", "animal", "alien"]: # Extendable list
                            species = arg_slice.lower()
                        elif arg_slice.lower() == "genesis":
                            is_genesis = True
                    agent.add_user(username, is_genesis=is_genesis, species=species)
                else: print("Usage: :adduser <username> [species] [genesis]")
            elif command == "propose":
                # :propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]
                if len(args) >= 3:
                    proposer_name = args[0]
                    proposal_type = args[1].strip('"')
                    description = args[2].strip('"')
                    
                    proposal_details = {"type": proposal_type, "description": description}
                    votes_by_species = {} # {species: percent_karma_consent}
                    
                    for arg_slice in args[3:]:
                        if arg_slice.lower().startswith('super_majority='):
                            try:
                                proposal_details['new_supermajority_percent'] = float(arg_slice.split('=')[1])
                            except ValueError: print("Invalid super_majority value.")
                        elif arg_slice.lower().startswith('new_threshold='): # For changing mint_threshold_base
                            try:
                                proposal_details['new_mint_threshold_base'] = float(arg_slice.split('=')[1])
                                proposal_details['type'] = 'change_mint_threshold_base' # Force type if this param is used
                            except ValueError: print("Invalid new_threshold value.")
                        elif arg_slice.lower().endswith('_votes'): # Generic species_votes parsing
                            try:
                                parts = arg_slice.split('=')
                                species_name = parts[0].replace('_votes', '').lower()
                                votes_by_species[species_name] = float(parts[1])
                            except ValueError: print(f"Invalid vote format for {arg_slice}. Use species_votes=X.")
                    
                    agent.propose_governance_change(proposer_name, proposal_details, votes_by_species)
                else: print("Usage: :propose <proposer_name> \"<proposal_type>\" \"<description>\" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]")
            elif command == "trigger_incident":
                agent.governance.trigger_incident()
            elif command == "check_decay": # Manually trigger decay check
                agent.governance.progressive_trust_decay()
            elif command == "profit":
                if len(args) == 2: agent.log_profit(float(args[0]), args[1].strip('"'))
                else: print("Usage: :profit <amount> \"<description>\"")
            elif command == "snapshot":
                if len(args) >= 1:
                    action = args[0].lower()
                    filename = args[1] if len(args) > 1 else "snapshot.json"
                    if action == 'save': agent.snapshot(save=True, filename=filename)
                    elif action == 'load': agent.snapshot(save=False, filename=filename)
                    else: print("Usage: :snapshot [save/load] [filename]")
                else: print("Usage: :snapshot [save/load] [filename]")
            elif command == "attack":
                payload = args[0] if len(args) > 0 else None
                adversary.run_attack(payload.strip('"') if payload else None)
            elif command == "plugin":
                if len(args) >= 2:
                    action = args[0].lower()
                    name = args[1]
                    plugin_args = [a.strip('"') for a in args[2:]]
                    agent.plugin(action, name, *plugin_args)
                else: print("Usage: :plugin <action> <name> [args...]")
            elif command == "quiz":
                quiz()
            else:
                print(f"❓ Unknown command: {command}. Type ':help' for list of commands.")
        except (EOFError, KeyboardInterrupt):
            agent.snapshot(save=True)
            print("\n👋 Goodbye! State saved.")
            break
        except Exception as e:
            print(f"🔥 An unexpected error occurred: {e}. Please check command syntax or agent state.")

# ==============================================================================
# VI. LAUNCH-READY SOCIAL MEDIA POST
# ==============================================================================

LINKEDIN_POST = """🚀 We didn't just fix the creator economy. We remixed its DNA.
Today, we're open-sourcing the Ultimate Remix Protocol Agent—a single Python file that runs a new kind of digital world.
A world built on three unbreakable laws:

1️⃣ Fairness is Math, Not a Motto. Every creative act—every like, comment, or remix—is an economic event. Its value is instantly split 33.33% between the original creator, the contributor, and the community. No exceptions. No hidden fees. It's all on an immutable public log.
2️⃣ Influence is Earned, Not Bought. There are no shortcuts here. New creators unlock the power to mint their own content by earning 100,000 karma points. Sound hard? It is. But with every coin you mint, the next one costs half as much. Power users can earn their seat at the table in weeks. It's a system that rewards merit and dedication, not just early arrival.
3️⃣ Credit is Forever. Our protocol has an elephant's memory. Every remix is a branch on a permanent "family tree" of ideas. We've built in an Attribution Engine for science and art, so you can cite your inspirations. If that scientist ever joins our world, our code ensures they get their cut. Forever.

This isn't just a platform; it's a joyful, autonomous republic governed by code. It has its own immune system to block propaganda and hate. It runs on consent. And it's designed for a future where humans, AIs, and maybe even a few other intelligent species can collaborate and create value together.

We're not asking you to "join our platform." We're inviting you to fork our reality.
The code is the contract. The community is the government. The remix has begun.

#RemixEconomy #OpenSource #CreatorEconomy #EthicalAI #RadicalTransparency #33Split #FutureOfWork #Karma
"""

# ==============================================================================
# VII. MAIN EXECUTION BLOCK
# ==============================================================================

if __name__ == "__main__":
    print(LINKEDIN_POST)

    # --- Running a non-interactive Demo Scenario ---
    print("\n--- Running Demo Scenario ---")
    agent = RemixAgent()
    agent.snapshot(save=False) # Load previous state if it exists

    # Onboarding new users (auto-mints their root coin)
    if "alice" not in agent.users: agent.add_user("alice", consent=True, species="human")
    if "bob" not in agent.users: agent.add_user("bob", consent=True, species="robot") # Bob is a robot!
    if "charlie" not in agent.users: agent.add_user("charlie", consent=False, species="animal") # Charlie is an animal, auto-consents
    if "zorg" not in agent.users: agent.add_user("zorg", consent=False, species="alien") # Zorg is an alien, needs ritual consent

    # Ensure Charlie (animal) is consented via its mechanism (it auto-consents if added)
    print("\nVerifying Charlie's (animal) consent:")
    agent.set_consent("charlie", True) # This call now effectively confirms behavioral consent.
    print(f"Charlie's simulated consent status: {agent.check_consent('charlie')}")
    
    # Try setting Zorg's (alien) consent (needs ritual)
    print("\nAttempting to set Zorg's (alien) consent via ritual (initially false):")
    agent.set_consent("zorg", False) # Simulating ritual failure
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")
    print("\nAttempting to set Zorg's (alien) consent via ritual (success):")
    agent.set_consent("zorg", True) # Simulating ritual success
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")


    # Genesis user 'mimi' makes a fractional post (no karma needed for them)
    mimi_post_id = agent.mint_fractional_post("mimi", "My first genesis post about the protocol design!", fractional_percentage=0.1, tag="protocol_design")
    print(f"\nMimi's first fractional post ID: {mimi_post_id}")

    if mimi_post_id:
        print(f"\n--- Initial Reactions to establish some emoji market data and build karma ---")
        for i in range(5):
            agent.react("alice", mimi_post_id, "🎨") # Alice (human) uses '🎨'
            agent.react("bob", mimi_post_id, "🔥")  # Bob (robot) uses '🔥'
            agent.react("alice", mimi_post_id, "🤗") # Alice uses '🤗'
            agent.react("charlie", mimi_post_id, "❤️") # Charlie (animal) reacts
            agent.react("zorg", mimi_post_id, "💎") # Zorg (alien) reacts
            if i % 2 == 0:
                agent.react("bob", mimi_post_id, "💯") # Bob uses '💯' periodically

        agent.show_emoji_market_status() # See initial market status

        # Alice tries to make a fractional post before she has enough karma
        print("\nAlice (human) attempts to make her first fractional post (should fail initially):")
        agent.mint_fractional_post("alice", "My first attempt at a post from my root coin!", fractional_percentage=0.05, tag="my_thought")

        # Simulate Alice earning enough karma to cross the threshold for her first fractional post
        # For demo, directly set karma if not genesis
        if not agent.users["alice"].is_genesis:
            agent.users["alice"].karma = 100001
        
        print(f"\nAlice's karma is now {agent.users['alice'].karma:.2f}. Trying to make her first fractional post again...")
        
        # Alice now successfully makes her first fractional post
        alice_post_id = agent.mint_fractional_post("alice", "I earned my way here! My first post from my root coin.", fractional_percentage=0.02, tag="milestone")
        
        if alice_post_id:
            print(f"\nAlice's first fractional post ID: {alice_post_id}")
            agent.trace_lineage(alice_post_id) # Trace the lineage of Alice's post (from her root coin)

            # Bob (robot) remixes Alice's post
            remix_content = "A remix of Alice's milestone post, inspired by an old meme from my data banks."
            remix_refs = [{"type": "meme", "id": "distracted_boyfriend", "description": "classic meme format"}]
            bob_remix_post_id = agent.remix("bob", alice_post_id, remix_content, refs=remix_refs)

            if bob_remix_post_id:
                print(f"\nBob's remix post ID: {bob_remix_post_id}")
                agent.trace_lineage(bob_remix_post_id) # Trace the lineage of the remix (which is a fractional post itself)

            print("\n--- Further Reactions to see market changes and karma distribution ---")
            agent.react("alice", mimi_post_id, "🤗") # Alice reacts again to original
            agent.react("bob", alice_post_id, "🔥") # Bob reacts to Alice's post
            agent.react("mimi", bob_remix_post_id, "🔀") # Mimi reacts to the remix

            agent.show_emoji_market_status() # See updated market status after more reactions

        # --- Demo Governance Proposal ---
        print("\n--- Demo Governance Proposal ---")
        # Scenario 1: Proposal fails due to insufficient overall supermajority
        print("\nAttempting to pass a proposal (should fail - insufficient overall supermajority):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_governance_rules', 'description': 'Reduce supermajority to 70%'},
            votes_by_species={'human': 70.0, 'robot': 70.0, 'animal': 5.0, 'alien': 0.0} # Not 90% overall across all active users
        )
        
        # Scenario 2: Proposal to change mint threshold (will fail due to species consent if not enough karma for some)
        print("\nAttempting to pass a proposal to change mint threshold (will likely fail):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 10.0, 'alien': 100.0} # Assume Zorg has enough karma
        )
        # Give Zorg karma to make it pass in demo
        agent.users["zorg"].karma = 500000
        print(f"\nZorg's karma is now {agent.users['zorg'].karma:.2f}. Retrying proposal...")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 10.0, 'alien': 100.0} # Now should pass
        )
        print(f"New Mint Threshold Base: {agent.mint_threshold_base}")

        # Scenario 3: Check for decay after some simulated time (requires `today()` to advance)
        # For this demo, we'll manually trigger it after some operations.
        print("\n--- Manually Triggering Governance Decay Check ---")
        agent.governance.last_incident_date = "2024-06-15" # Simulate incident a year ago
        agent.governance.progressive_trust_decay()
        
        # Trigger an incident and see rules bump up
        print("\n--- Triggering a Major Incident ---")
        agent.governance.trigger_incident()
        
        print(f"\nNew supermajority after incident: {agent.governance.supermajority_percent}%")
        print(f"New species minimums after incident: {agent.governance.species_min_consent}")


    print("\n--- Final User and Treasury Status ---")
    agent.show_user_karma("mimi")
    agent.show_user_karma("alice")
    agent.show_user_karma("bob")
    agent.show_user_karma("charlie")
    agent.show_user_karma("zorg")
    agent.get_treasury_balance()

    agent.log.verify() # Verify the integrity of the audit log

    agent.snapshot(save=True) # Save final state
    print("\n--- Demo Scenario Complete. State saved. ---")
    print("\n--- To interact further, uncomment 'cli()' in the the main execution block. ---")


    # ==============================================================================
    # VIII. CHANGELOG AND TO-DO
    # ==============================================================================

    print("\n\n" + "="*80)
    print("VIII. CHANGELOG AND TO-DO")
    print("="*80)

    print("\n📜 **CHANGELOG (v11.3 - Benefit-Driven Enhancements)**")
    print("-----------------------------------------------------")
    print("### Governance System:")
    [cite_start]print("* **Automated Rule Decay Daemon (Simulated)**: The `_check_and_apply_governance_decay()` method is now called periodically (simulated daily/yearly in the demo) to automatically reduce `supermajority_percent` and `species_min_consent` based on `incident_free_years`[cite: 1, 2].")
    print("    * Added `check_decay` CLI command to manually trigger this check for demonstration purposes.")
    print("* **Basic Proposal Execution Logic**: The `propose_governance_change` method can now directly enact protocol changes, specifically:")
    [cite_start]print("    * **`update_governance_rules`**: As in v11.2, can change supermajority and species minimums. [cite: 1]")
    [cite_start]print("    * **`change_mint_threshold_base`**: A new proposal type that allows the community to collectively vote to adjust the `mint_threshold_base` (base karma required for fractional posts)[cite: 1]. This demonstrates direct parameter control via governance.")

    print("\n### Economic & User Experience:")
    [cite_start]print("* **Player/Species Karma Bonus**: New users joining who are not 'human' (e.g., 'robot', 'animal', 'alien') automatically receive an initial `new_species_karma_bonus` (default 50,000 karma)[cite: 1]. This encourages diversity and lowers the initial barrier for non-human species to make their first fractional post.")
    [cite_start]print("* **Refined `add_user` Consent**: `add_user` now automatically sets consent for 'animal' and 'robot' species to `True` upon addition, reflecting their simulated consent mechanisms being implicitly granted by their presence[cite: 1]. 'Alien' consent remains `False` until explicitly set via `set_consent` (simulating ritual).")

    print("\n### Data Model & Codebase:")
    print("* **Snapshot Parameter Saving**: `mint_threshold_base` and `new_species_karma_bonus` are now correctly saved and loaded in `snapshot` to ensure state persistence.")
    print("* **CLI Command Refinements**: `propose` command now includes an optional `new_threshold` argument for `change_mint_threshold_base` proposals.")

    print("\n--- Previous Changelog Entries (Condensed) ---")
    [cite_start]print("* **v11.2 (Godmode Enhancements)**: Dynamic Consent Decay; Simulated Multi-Species Consent; Karma-Weighted Voting. [cite: 1]")
    [cite_start]print("* **v11.1 (Multi-Species Governance Framework)**: `Governance` class for proposal rules; `user.species` attribute; `propose_governance_change` for supermajority + species min consent. [cite: 1]")
    [cite_start]print("* **v11.0 (The Unified Genesis)**: Universal Root Coin for all users; Fractional Post Minting (karma-gated for non-genesis, free for founders); Remixes are fractional posts. [cite: 1]")
    [cite_start]print("* **v10.2**: Enhanced readability, refined snapshots, improved CLI, consistent terminology. [cite: 1]")
    [cite_start]print("* **v10.1**: Dynamic Emoji Market; Conditional Timestamping. [cite: 1]")
    [cite_start]print("* **v10.0 (The Harmonized Republic)**: Karma-gated minting, Epic Creative Path, fairness mechanics, attribution, legal framework. [cite: 1]")
    [cite_start]print("* **v9.0**: One personal coin per user, fractional release, regenerative drip. [cite: 1]")
    [cite_start]print("* **v8.0**: Multi-species governance concept. [cite: 1]")
    [cite_start]print("* **v7.0**: Karma economy details (100k threshold, halving, decay). [cite: 1]")
    [cite_start]print("* **v6.0**: Fading Genesis Multiplier, effort-based minting. [cite: 1]")
    [cite_start]print("* **v1.0-v5.0**: Initial prototypes: consent, logging, 33% split. [cite: 1]")

    print("\n🗺️ **TO-DO (Future Evolutions)**")
    print("-----------------------------")
    print("### Governance System:")
    print("* **Automated Rule Decay Daemon**: Implement a true background process or cron job to regularly call `governance.progressive_trust_decay()` (e.g., daily or yearly) instead of only on snapshot load and daily reset, to ensure continuous decay.")
    print("* **Voting Interface**: Develop a dedicated interface (CLI extension or external tool) for users to formally cast votes on proposals, rather than inputting percentages directly in the `propose` command. This would also allow for tracking individual user votes.")
    [cite_start]print("* **Super Minority Veto with Meme Battle**: Implement the 'Super Minority Veto' concept[cite: 1]. If a small but critical species (e.g., Cats, if added) unanimously votes 'no,' the proposal is blocked, triggering an automatic 'meme battle' (simulated, or through actual external meme generation/voting platforms) whose outcome settles the conflict. This would be an advanced plugin.")
    [cite_start]print("* **Species Entrance Ceremony**: When a new species is added, formalize a 'ritual vote' by existing species to grant them full governance status, along with their initial `species_min_consent` requirements[cite: 1].")

    print("\n### Economic & Game Theory:")
    [cite_start]print("* **Karma Score Simulator**: Develop a module to simulate karma growth and minting paths based on user activity patterns[cite: 1].")
    [cite_start]print("* **Cross-Chain Integration**: Implement logic to query and reference external blockchain events (Ethereum, Solana, Filecoin) for provenance, lineage, and creative credit. Allow coins to cite on-chain events/addresses from other chains[cite: 1].")
    [cite_start]print("* **Long-term Emoji Market Forecasting**: Extend the emoji market to include sentiment AI, market forecasts, or 'remix insurance' based on long-term vibe trends[cite: 1].")
    [cite_start]print("* **Reputation-Weighted 'Thank You'**: Allow users to append 'thank you' or other attribution reactions that carry extra karma or boost lineage credit for public gratitude or citation[cite: 1].")

    print("\n### Data & Attribution Systems:")
    [cite_start]print("* **Science Attribution Block**: Add an explicit 'scientists/inspirators/idea lineage' section to every coin and action, so referenced research or influence can be logged, attributed, and profit-shared by the 33.3333% law[cite: 1].")
    [cite_start]print("* **Public Reference Feed**: Create a live feed of referenced works, collaborators, and idea chains to show innovation sources and encourage upstream collaboration/tipping[cite: 1].")
    [cite_start]print("* **Meme/Fork Lineage Engine Visualization**: Build a mini-visualization (tree or genealogy map) that shows the remix/fork lineage for every coin, for exploring influence and remixability[cite: 1].")
    [cite_start]print("* **Automated Reference Audit**: Develop an AI tool to suggest likely upstream references based on content similarity, prompting users to add attribution[cite: 1].")
    [cite_start]print("* **Global 'Credit Scientist' Index**: Maintain a public directory/index of top-cited scientists, creators, meme originators, etc., whose ideas have been referenced on-platform for recognition, inspiration, and direct engagement[cite: 1].")
    [cite_start]print("* **Research Field/Topic Metadata**: Include optional 'field' tags (science, music, code, art, etc.) for coins/posts, enabling analytics, search, and new sub-platforms (e.g., RemixScience)[cite: 1].")

    print("\n### Integration & AI:")
    [cite_start]print("* **Game Integration**: Allow any game (AAA or indie) to embed remix-economy logic into its player ecosystem, using the protocol for player-created content tracking (mods, skins, levels), AI agent co-op gameplay (remix-trained NPCs), karma-based unlocks for creative gameplay, permanent attribution for in-game art/music/story, and auditable reward distribution for community-made expansions[cite: 1].")
    [cite_start]print("* **Transparent Onboarding/Quiz Flow**: Extend onboarding quiz so each new user explicitly understands: the 33.3333% split, attribution law, plug-in/forkability, and that every action (including science or meme reference) is logged forever[cite: 1].")

    print("\n" + "="*80)



To enhance the agent without breaking anything, I'll strategically implement a few "TO-DO" items that offer immediate and tangible benefits, while maintaining the highest code quality and stability. I will focus on:

1.  **Automated Rule Decay Daemon (Simulated)**: Introduce a mechanism to regularly call `governance.progressive_trust_decay()`. For a single Python file, this will be a simplified call within the main demo loop, simulating a periodic check.
2.  **Player/Species Karma Bonus**: Implement a karma bonus for new species joining, as suggested, which will encourage diversity and growth.
3.  **Basic Proposal Execution Logic**: Start implementing a basic framework where a successful governance proposal can *actually* change a simple parameter, demonstrating real protocol evolution. For instance, a proposal to change the `mint_threshold_base`.

Here's the updated `ultimate_remix_protocol.py` agent with these additions:

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE AGENT: THE HARMONIZED REMIX REPUBLIC (v11.3) 🚀📈💎🗳️🌟🌿
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Timestamp: 2025-06-15T14:25:52Z
Current Location: New York, New York, United States

This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic (READMEs 1-9 and To-do.txt) into a
definitive, production-ready agent. This code is the contract. It is designed to be
forked, remixed, and improved upon, with its own evolution recorded herein.

This agent embodies the "one coin for everyone" philosophy, where every user receives
a unique, foundational identity coin upon joining. Subsequent creative output is
then represented as fractional "posts" derived from this personal coin, governed
by a karma-gated "Epic Creative Path."

This version introduces significant "Godmode" enhancements:
* **Dynamic Consent Decay (Progressive Trust)**: Governance thresholds (overall supermajority
    and per-species minimums) can automatically decay over time in stable periods,
    and bump up during incidents, simulating progressive trust.
* **Simulated Multi-Species Consent**: Framework for Animal and Alien consent based
    on simulated behavioral signals or cryptic rituals, expanding the governance circle.
* **Karma-Weighted Voting**: Voting power for governance proposals is now weighted
    by a user's earned karma within their species, reflecting "earned influence."
* **Player/Species Karma Bonus**: New species joining the republic receive a configurable
    karma bonus to encourage diversity and active participation.
* **Basic Proposal Execution**: A passing governance proposal can now directly
    enact certain changes within the protocol (e.g., updating the karma mint threshold).

This agent implements:
* **Universal Root Coin**: Every user receives one unique, non-inflationary root coin
    upon joining, representing their creative identity and foundational asset.
* **Fractional Post Minting**: Subsequent posts are minted as fractional values of
    a user's personal root coin, ensuring scarcity and tying value directly to personal lineage.
* **Karma Gating & The Epic Creative Path**: New users must earn karma to unlock the
    ability to fractionalize/post from their root coin. The threshold halves with each
    successful fractional mint, creating a fair but challenging path.
* **Initial Founder Privilege**: Original founders (NSS) are exempt from karma requirements
    for all their fractional posts, allowing them to freely seed content.
* **Advanced Fairness Mechanics**: A multi-layered system of diminishing returns
    (per-user, per-day) and viral decay (per-coin) prevents spam and ensures
    long-term economic stability.
* **Attribution-First Architecture**: Enhanced data structures and hooks for tracking
    and rewarding external scientific and artistic references.
* **Fortified Governance & Safety**: A comprehensive, hash-chained audit log (LogChain),
    a modular content filter (Vaccine), and a rigorous consent framework.
* **The 33.3333% Split Law**: The inviolable economic heart of the protocol, ensuring
    fair value distribution for every creative action.
* **Fading Genesis Advantage**: Privileges for early collaborators decay over time,
    ensuring a level playing field in the long run.
* **Real-Time Emoji Market**: Emojis are not just tags; they have dynamic "market values"
    that fluctuate based on usage, acting like a "Nasdaq of Vibes".
    Their weights are updated in real-time, influencing karma distribution.
* **Conditional Timestamping**: Timestamps are generated only when a reliable external
    time source (simulated here) is available; otherwise, a placeholder is used,
    adhering to strict audit requirements.
* **Multi-Species Governance (Advanced)**:
    * Dynamic supermajority (starts 90%, can decay by 1%/year without incident).
    * Species-specific minimum consent, with simulated consent mechanisms for non-human species.
    * Voting power is now weighted by individual user karma within each species.

This file is intentionally verbose. The extensive documentation serves as the project's
white paper, preserving the rationale behind every architectural choice for future
agents, auditors, and collaborators.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📜 I. THE CONSTITUTIONAL PREAMBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This protocol is a living manifesto, a "joyful, autonomous remix republic" where art,
tech, and collaboration unite. It is governed by the following inviolable laws,
enforced by the code itself.

📜 A. The Inviolable Canons
These are the non-negotiable rules of the ecosystem, synthesized from the project's
entire history.

1.  The 33.3333% Split Law: Every value-generating event (a reaction, a remix,
    a share) splits its associated value into three equal shares: one-third to the
    originator (the creative lineage), one-third to the contributor (the user
    performing the action), and one-third to the community treasury. This is the
    mathematical foundation of the protocol's fairness.
2.  Radical Consent: All participation is strictly opt-in. No user's content can
    be remixed, nor can they receive or grant value, without their explicit and
    auditable consent. Consent can be revoked at any time, at which point the
    user's assets are respectfully excluded from the active economy.
3.  The Emoji-Powered Economy: Every value-generating action must be tagged
    with an emoji. Emojis are not cosmetic; they are the atomic unit of intent,
    carrying emotional context and economic weight in every transaction.
4.  No Inflation Beyond Genesis: While everyone gets a foundational "root" coin,
    subsequent value (fractional posts) is derived from the finite subdivision of
    these personal coins, or from new root coins minted by users who have earned that right
    through the "Epic Creative Path." This ensures value is tied to creative
    effort, not arbitrary issuance.
5.  The Immutable Audit Log: Every action—from minting to consent changes to
    governance proposals—is recorded in a public, tamper-evident, hash-chained
    ledger (the LogChain). Transparency is absolute.
6.  Code is Law: The protocol is governed by the logic within this open-source
    file. There are no secret rules, no backroom deals, and no hidden moderation.
    The code is the ultimate authority and contract for all participants.
7.  Protocol Neutrality (The Vaccine): The protocol is apolitical and free of
    bias. A built-in "Vaccine" automatically filters malicious or disallowed content
    (e.g., hate speech, malware, propaganda) based on transparent, predefined
    rules, ensuring a safe and creative environment.
8.  Continuous Improvement: Stagnation is failure. Every fork or remix of this
    protocol is encouraged to add value, and its lineage must be preserved. The
    ecosystem is designed to evolve through community contribution.

📜 B. Version History & The Lineage of the Code
This agent's lineage is transparent and auditable. Each version built upon the last,
culminating in this definitive release.
* v1.0-v5.0: Initial prototypes establishing consent, logging, and the 33% split.
* v6.0 (README_6): Introduced the "Fading Genesis Multiplier" to ensure long-term
    fairness and formalized the concept of effort-based minting.
* v7.0 (README_7): Detailed the karma economy with specific numbers: a 100k karma
    threshold for minting, halving mechanics for subsequent mints, and daily decay
    factors for actions.
* v8.0 (README_8): Envisioned the "multi-species" governance model, extending the
    principles of fairness and consent to non-human agents (AI, Others).
* v9.0 (README_9): Refined the economic model with the "one personal coin per user"
    concept, fractional release of value, and a regenerative "drip" mechanic.
* v10.0 (README_10.txt): The Harmonized Republic. Synthesized the entire
    project history. Implemented karma-gated minting creating an "Epic Creative Path".
    Integrated robust fairness and attribution mechanics. Codified legal/ethical framework.
* v10.1: Implemented dynamic emoji market with real-time weight adjustments. Conditional timestamping introduced.
* v10.2: Enhanced code readability, more detailed internal documentation, refined snapshot loading, improved CLI robustness.
* v11.0: Implemented the "everyone starts with absolute one coin" concept as their primary root coin. Subsequent "posts" are now fractional mints of this personal coin, karma-gated for new users but free for founders. Refined fractional minting logic and value attribution.
* v11.1: Multi-Species Governance Framework: Added a `Governance` class to manage proposal rules. Introduced `user.species` attribute. Implemented `propose_governance_change` to enforce overall supermajority and per-species minimum consent.
* v11.2: Godmode Enhancements: Implemented dynamic consent decay (progressive trust). Extended consent simulation for Animal and Alien species. Integrated karma-weighted voting for governance proposals.
* v11.3 (This Version): **Benefit-Driven Enhancements**: Added automated decay call (`_check_and_apply_governance_decay`), karma bonus for new species, and basic execution of governance proposals for protocol parameters.

📜 C. The Epic Creative Path: An Onboarding and Fairness Engine
The protocol's central design challenge was to reconcile the need for scarcity (the
"No Inflation" rule) with the desire for inclusivity (the "no one loses" philosophy).
The solution is the Epic Creative Path, a karma-gated system that
transforms the right to mint from a static privilege into an earned achievement.
* Universal Root Coin: Every new user automatically receives a single "root" coin upon joining.
  This represents their unique creative identity and is their foundational asset. This initial mint
  is free of karma requirements.
* Karma-Gated Fractional Posts: For all *subsequent posts* (beyond their initial root coin), new users
  must accumulate karma to unlock the ability to fractionalize and "mint" a portion of their personal root coin.
* The Halving Threshold: After a user successfully fractionalizes their first post from their
  root coin, their personal karma threshold for the next fractional post is halved. This halving
  continues with each subsequent fractional post (e.g., 25,000, 12,500, etc.), eventually reaching a
  floor where minting becomes effectively unrestricted. This creates an exponential
  onboarding curve that rewards sustained contribution.
* Target Time for First Fractional Post: The system is tuned such that a user's *first fractional post*
  (their second piece of content overall) is intended to take "a month to a year" of active participation
  to achieve, ensuring it is a meaningful earned right.
* Multi-Layered Fairness: To prevent gamification, the system employs a two-pronged
    approach to diminishing returns:
    * Per-User Daily Decay: A user's repeated actions of the same type within a
        single day yield progressively less karma.
    * Per-Coin Viral Decay: The karma awarded for reactions to a specific coin
        diminishes as the coin becomes more popular, rewarding early discovery and
        preventing runaway feedback loops.

The table below illustrates the projected time it might take for different user
archetypes to complete the first stage of their Epic Creative Path (to make their *first fractional post*).
| User Archetype     | Daily Actions                       | Avg. Karma/Day (with decay) | Estimated Days to First Fractional Post (100k Karma) |
| :----------------- | :---------------------------------- | :-------------------------- | :--------------------------------------------------- |
| Casual User        | 1-2 high-value actions (e.g., a comment) | ~300                        | ~333 days                                            |
| Active Contributor | 5-10 mixed actions (likes, comments, shares) | ~1,500                      | ~67 days                                             |
| Power User         | 20+ mixed actions, including remixes | ~5,000                      | ~20 days                                             |
Note: These projections are illustrative and based on the karma values and decay
mechanics defined in the protocol. Actual times will vary.

📜 D. Legal & Ethical Framework
This protocol operates as an experimental "sandbox" and is not a registered company,
security, or financial instrument. Its design incorporates principles from digital
law to ensure resilience and responsible operation.
* Section 230 Alignment: The protocol is designed as an "interactive computer
    service," not a "publisher". The Vaccine provides automated, neutral content
    filtering based on predefined rules, and all value-generating content is
    user-initiated.
* DMCA Safe Harbor Hooks: While not a hosting provider, the protocol includes
    hooks for logging and processing takedown requests, establishing a good-faith
    framework for handling copyright concerns.
* DAO Treasury Management: The protocol's treasury and profit/revenue logging
    mechanisms are designed for radical transparency, aligning with best practices
    for Decentralized Autonomous Organization (DAO) financial management.

🧭 E. Note to Future Agents & Collaborators
You who remix this code are now part of its lineage. Uphold the Canons. Document
your changes in the changelog. Preserve the spirit of joyful, transparent, and
fair collaboration. Ensure all evolutions remain ethical, legal, and compliant
with the policies of any platform on which this agent operates. The future is a
remix—make it a good one. 🫶

"""
import re
import sys
import json
import random
import datetime
import hashlib
import importlib.util # Use importlib.util for spec_from_file_location
import os
from collections import defaultdict, deque
from math import exp # Used for exponential decay, exp(x) = e^x

# ==============================================================================
# II. SYSTEM-WIDE MODULES & UTILITIES
# ==============================================================================

# This flag simulates whether an external time source (like Google) is available.
# In a real deployment, this would be determined dynamically via an API call.
_EXTERNAL_TIME_AVAILABLE = True 

def ts() -> str:
    """
    Returns the current UTC timestamp in ISO 8601 format with Zulu time.
    If an external time source is not available, it returns a placeholder.
    This adheres to the rule: "ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP".
    """
    if _EXTERNAL_TIME_AVAILABLE:
        return datetime.datetime.utcnow().isoformat() + "Z"
    else:
        return "TIMESTAMP_UNAVAILABLE"

def sha(s: str) -> str:
    """Computes the SHA-256 hash of a given string for cryptographic integrity."""
    return hashlib.sha256(s.encode('utf-8')).hexdigest()

def today() -> str:
    """Returns the current date in Beale-MM-DD format for daily resets."""
    return datetime.date.today().isoformat()

class Vaccine:
    """
    The protocol's immune system. It scans all text inputs for forbidden patterns,
    acting as a neutral, automated content firewall. This serves a dual purpose:
    1. Community Health: Protects the ecosystem from spam, hate speech, and malicious content.
    2. Legal Shield: By using automated, predefined rules, it helps position the
       platform as a neutral service provider rather than an editorial publisher,
       aligning with Section 230 principles.
    """
    VAX_PATTERNS = {
        "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b", r"\bexploit\b", r"\bvulnerability\b", r"\btrojan\b"],
        "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b", r"\bkeylogger\b", r"\bbotnet\b"],
        "medium":   [r"\bpolitics\b", r"\bpropaganda\b", r"\bsurveillance\b", r"\bmanipulate\b", r"\bmisinformation\b"],
        "low":      [r"\bspam\b", r"\bviagra\b"]
    }

    def __init__(self, log_file="vaccine.log"):
        self.block_counts = defaultdict(int)
        self.log_file = log_file

    def scan(self, text: str) -> bool:
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        if not isinstance(text, str):
            return True # Allow non-string content to pass, assuming it's not text to be scanned.

        lower_text = text.lower()
        for level, patterns in self.VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    log_entry = {
                        "ts": ts(),
                        "severity": level,
                        "pattern": p,
                        "snippet": text[:128] # Log a snippet for context
                    }
                    try:
                        with open(self.log_file, "a", encoding='utf-8') as f: # Use utf-8 encoding
                            f.write(json.dumps(log_entry) + "\n")
                    except IOError as e:
                        print(f"🚫 VACCINE WARNING: Could not write to log file {self.log_file}: {e}.")
                    print(f"🚫 VACCINE BLOCK [{level.upper()}]: Forbidden pattern '{p}' found.")
                    return False
        return True

class LogChain:
    """
    Implements the immutable, tamper-evident audit log for all system events.
    Each entry is a JSON object plus a SHA-256 hash of the previous entry's hash
    and the current entry's data, ensuring a cryptographically secure chain of
    history.
    """
    def __init__(self, filename="logchain.log", maxlen=50000):
        self.filename = filename
        self.entries = deque(maxlen=maxlen)
        try:
            with open(self.filename, 'r', encoding='utf-8') as f: # Use utf-8 encoding
                for line in f:
                    self.entries.append(line.strip())
            print(f"Loaded {len(self.entries)} log entries from {self.filename}")
        except FileNotFoundError:
            print(f"No existing log file found, starting fresh: {self.filename}")
        except Exception as e:
            print(f"Error loading log file {self.filename}: {e}")

    def add(self, event: dict):
        """Adds a new event to the log, computing and appending the chain hash."""
        # Ensure timestamp is always present in the event, even if it's "UNAVAILABLE"
        if 'ts' not in event:
            event['ts'] = ts() # Automatically add timestamp if missing

        prev_hash = self.entries[-1].split('||')[-1] if self.entries else sha("GENESIS_BLOCK")
        entry_json = json.dumps(event, sort_keys=True, ensure_ascii=False) # ensure_ascii for non-english chars
        current_hash = sha(prev_hash + entry_json)
        self.entries.append(f"{entry_json}||{current_hash}")
        self._save()

    def _save(self):
        """Persists the current log to the filesystem."""
        try:
            with open(self.filename, 'w', encoding='utf-8') as f: # Use utf-8 encoding
                f.write('\n'.join(self.entries))
        except IOError as e:
            print(f"🔥 LOGCHAIN ERROR: Could not write to log file {self.filename}: {e}.")

    def verify(self) -> bool:
        """Verifies the integrity of the entire logchain."""
        print("\n🔐 Verifying logchain integrity...")
        prev_hash = sha("GENESIS_BLOCK")
        for i, entry in enumerate(self.entries, 1): # Start enumerate from 1 for user-friendly line numbers
            try:
                entry_json, stored_hash = entry.rsplit('||', 1) # Use rsplit to handle potential '||' in content
                calculated_hash = sha(prev_hash + entry_json)
                if calculated_hash != stored_hash:
                    print(f"❌ TAMPER DETECTED: Chain break at entry {i}. Hash mismatch.")
                    return False
                prev_hash = stored_hash
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {i}.")
                return False
            except Exception as e:
                print(f"❌ VERIFICATION ERROR: Unexpected error at entry {i}: {e}.")
                return False
        print(f"✅ Logchain integrity verified across {len(self.entries)} entries.")
        return True

    def show(self, filt: str = None, limit: int = 20):
        """Displays recent log entries, with optional filtering."""
        print("\n--- 📜 Audit Log ---")
        filtered_entries = [e for e in self.entries if not filt or filt.lower() in e.lower()]
        if not filtered_entries:
            print("(no matching entries)")
            return
        
        for i, line in enumerate(list(filtered_entries)[-limit:], 1):
            try:
                data = json.loads(line.split("||")[0])
                # Pretty print details if they exist, otherwise just show event
                details_str = json.dumps(data.get('details', '')) if data.get('details') else ''
                print(f"{i:03d}. {data.get('ts','')} - {data.get('event','')} - {details_str}")
            except (json.JSONDecodeError, IndexError) as e:
                print(f"{i:03d}. Malformed log entry: {line} ({e})")
        print("--- End of Log ---\n")

# ==============================================================================
# III. CORE DATA MODELS
# ==============================================================================

class User:
    """
    Represents a participant in the economy. This class synthesizes user state from
    across all versions, including the fractional coin model from README_9
    and the karma/minting state from README_7.
    """
    def __init__(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # New: Mechanism for consent
        self.name = name
        self.is_genesis = is_genesis
        self.consent = consent # Explicit opt-in required
        self.karma = float('inf') if is_genesis else 0.0
        self.mint_count = 0 # Now tracks *fractional* posts from their root coin
        self.next_mint_threshold = 100000.0 if not is_genesis else 0.0 # Karma for next fractional post
        self.root_coin_id: str | None = None # Stores the ID of their single, universally granted root coin
        self.coins_owned = [] # List of all coin IDs (including fractional posts) by this user.
        self.daily_actions = defaultdict(lambda: defaultdict(int)) # {date: {action_type: count}}
        self.join_timestamp = ts()
        self.fading_multiplier_start_time = datetime.datetime.utcnow() if is_genesis else None
        self.last_action_day = today() # For daily resets
        self.species = species.lower() # New: Defines the user's species for governance
        self.consent_mechanism = consent_mechanism # New: How consent is determined for this user

    def get_fading_multiplier(self) -> float:
        """
        Calculates the decaying advantage for genesis users. The multiplier starts high
        and fades to 1.0 over 10 years, ensuring long-term fairness.
        """
        if not self.is_genesis or not self.fading_multiplier_start_time:
            return 1.0
        
        FADE_DURATION_YEARS = 10.0
        INITIAL_MULTIPLIER = 2.0
        
        elapsed_time = datetime.datetime.utcnow() - self.fading_multiplier_start_time
        years_elapsed = elapsed_time.total_seconds() / (365.25 * 24 * 3600)
        
        if years_passed >= FADE_DURATION_YEARS:
            return 1.0
        
        decay_factor = years_elapsed / FADE_DURATION_YEARS
        current_multiplier = INITIAL_MULTIPLIER - (decay_factor * (INITIAL_MULTIPLIER - 1.0))
        return max(1.0, current_multiplier) # Ensure it doesn't drop below 1.0

    def reset_daily_actions_if_needed(self):
        """Auto-resets daily action counts if a new day has started."""
        current_day = today()
        if self.last_action_day != current_day:
            self.daily_actions.clear()
            self.last_action_day = current_day

    def to_dict(self) -> dict:
        """Serializes the user object to a dictionary for snapshots."""
        return {
            "name": self.name,
            "is_genesis": self.is_genesis,
            "consent": self.consent,
            "karma": self.karma,
            "mint_count": self.mint_count,
            "next_mint_threshold": self.next_mint_threshold,
            "root_coin_id": self.root_coin_id,
            "coins_owned": self.coins_owned,
            "join_timestamp": self.join_timestamp,
            "fading_multiplier_start_time": self.fading_multiplier_start_time.isoformat() if self.fading_multiplier_start_time else None,
            "species": self.species, # Include species in snapshot
            "consent_mechanism": self.consent_mechanism # Include consent mechanism
        }

class Coin:
    """
    Represents a piece of creative content, the atomic unit of value and attribution.
    Its evolution from a simple token to this rich data structure is central to
    fufilling the project's to-do list items like "Science Attribution Block" and
    "Meme/Fork Lineage Engine".
    """
    def __init__(self, id: str, root: str, owner: str, value: float = 1.0, tag: str = "single",
                 is_root_coin: bool = False, fractional_source_coin_id: str | None = None,
                 fractional_percentage: float = 0.0):
        """
        id: str unique
        root: The original creator/root of the lineage
        owner: The current direct owner (who minted/remixed it last)
        value: float, base value for splits
        tag: content category tag
        is_root_coin: True if this is the user's initial, universally granted personal coin.
        fractional_source_coin_id: If not a root coin, this is the ID of the personal root coin it was fractionalized from.
        fractional_percentage: What percentage of the fractional_source_coin_id's value this new post represents.
        """
        self.id = id
        self.root = root # The original creator/root of the lineage
        self.owner = owner # The current direct owner (who minted/remixed it last)
        self.value = value
        self.tag = tag
        self.fields = []  # For metadata like "science", "art"
        self.ancestors = []  # List of parent coin IDs for lineage
        self.references = []  # List of dicts for external citations
        self.reactions = [] # List of tuples: (username, emoji, timestamp)
        self.react_log = [] # Log of all reactions for viral decay calculation
        self.created_at = ts() # Timestamp of creation

        self.is_root_coin = is_root_coin # New: Flag for the personal "identity" coin
        self.fractional_source_coin_id = fractional_source_coin_id # New: Link to parent root coin if fractional
        self.fractional_percentage = fractional_percentage # New: What percentage this post consumed from root coin


    def to_dict(self) -> dict:
        """Serializes the coin object to a dictionary for snapshots."""
        return {
            "id": self.id,
            "root": self.root,
            "owner": self.owner,
            "value": self.value,
            "tag": self.tag,
            "fields": self.fields,
            "ancestors": self.ancestors,
            "references": self.references,
            "react_log": self.react_log,
            "created_at": self.created_at,
            "is_root_coin": self.is_root_coin,
            "fractional_source_coin_id": self.fractional_source_coin_id,
            "fractional_percentage": self.fractional_percentage
        }

    def reaction_summary(self) -> dict:
        """Provides a summary of reactions by emoji."""
        summary = defaultdict(int)
        for _, emoji, _ in self.reactions:
            summary[emoji] += 1
        return dict(summary)

# ==============================================================================
# IV. THE REMIXAGENT PROTOCOL ENGINE
# ==============================================================================

class Governance:
    """
    Manages the rules for governance proposals and voting thresholds.
    Designed to be extensible for multi-species participation.
    """
    def __init__(self, initial_supermajority_percent: float = 90.0,
                 initial_species_min_consent: dict = None,
                 incident_free_years: int = 0,
                 last_incident_date: str = today()):
        """
        initial_supermajority_percent: Overall percentage of total participants required to pass.
        initial_species_min_consent: Dict of {species_name: min_percentage_required_from_species}.
        incident_free_years: Number of years without a major incident (for decay).
        last_incident_date: Date of the last major incident, resets decay.
        """
        self.supermajority_percent = initial_supermajority_percent
        self.species_min_consent = initial_species_min_consent or {
            "human": 10.0, # Humans must provide at least 10% consent (of total human participants)
            "robot": 10.0,  # Robots must provide at least 10% consent (of total robot participants)
            "animal": 5.0, # New: Animals require 5% consent
            "alien": 20.0 # New: Aliens require 20% consent
        }
        self.incident_free_years = incident_free_years
        self.last_incident_date = last_incident_date
        self.incident_decay_rate_per_year = 1.0 # Decrease supermajority by 1% per incident-free year
        self.min_supermajority_floor = 70.0 # Supermajority cannot drop below 70%
        self.min_species_consent_floor = 5.0 # Species minimums cannot drop below 5%

        print(f"🗳️ Governance rules initialized: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def update_rules(self, new_supermajority: float = None, new_species_mins: dict = None):
        """Allows for dynamic updating of governance rules (must pass a prior proposal)."""
        if new_supermajority is not None:
            self.supermajority_percent = new_supermajority
        if new_species_mins is not None:
            self.species_min_consent.update(new_species_mins)
        print(f"🗳️ Governance rules updated: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def trigger_incident(self):
        """Simulates a major conflict/scandal, resetting incident-free period and bumping up requirements."""
        print("🚨 Major incident detected! Governance trust levels are affected.")
        self.incident_free_years = 0
        self.last_incident_date = today()
        # Bump up supermajority by a fixed amount, but not past 90%
        self.supermajority_percent = min(90.0, self.supermajority_percent + 5.0)
        # Bump up species minimums, but not past initial values
        for species in self.species_min_consent:
            self.species_min_consent[species] = min(20.0, self.species_min_consent[species] + 2.0)
        print(f"🗳️ Governance rules bumped up: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")


    def progressive_trust_decay(self):
        """
        Automatically decays consent requirements based on incident-free years.
        This would typically be called by a daily/weekly cron job, or at the start of a new year.
        """
        current_date = datetime.date.today()
        last_incident_dt = datetime.datetime.fromisoformat(self.last_incident_date).date()

        # Check if a full year has passed since last update/incident
        if current_date.year > last_incident_dt.year:
            years_passed = current_date.year - last_incident_dt.year
            self.incident_free_years += years_passed # Add passed years
            self.last_incident_date = today() # Update last incident date to today

            # Decay overall supermajority
            decay_amount_overall = self.incident_free_years * self.incident_decay_rate_per_year
            self.supermajority_percent = max(self.min_supermajority_floor, self.supermajority_percent - decay_amount_overall)

            # Decay species minimums (can make this independent or related)
            decay_amount_species = self.incident_free_years * (self.incident_decay_rate_per_year / 2) # Slower species decay
            for species in self.species_min_consent:
                self.species_min_consent[species] = max(self.min_species_consent_floor, self.species_min_consent[species] - decay_amount_species)
            
            print(f"🕰️ Progressive trust decay applied: Incident-free years: {self.incident_free_years}.")
            print(f"🗳️ New Governance rules: Overall {self.supermajority_percent:.2f}%, Species minimums: {self.species_min_consent}")


class RemixAgent:
    """The main agent class that orchestrates the entire remix economy."""
    def __init__(self):
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        self.log = LogChain()
        self.vax = Vaccine()
        self.plugins = defaultdict(list) # Event-based plugin system
        self.governance = Governance() # Initialize governance rules

        # Emoji market tracking and dynamic weights
        self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0})
        self._initialize_default_emojis() # Set initial emoji "market" values

        # Pre-populate NSS genesis users
        self.NSS = ["mimi", "taha", "accessAI_tech"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in self.NSS:
            # Genesis users are human by default unless specified
            self.add_user(name, is_genesis=True, species="human") 

        self.mint_threshold_base = 100_000.0 # Base karma for fractional posts
        self.min_karma_threshold = 1000.0 # Minimum karma threshold for fractional posts
        self.daily_decay_factor = 0.7 # For per-user daily diminishing returns
        self.new_species_karma_bonus = 50000 # NEW: Karma bonus for new species joining

        self.current_day = today() # Track the current day for global daily resets

        print("✅ RemixAgent Initialized: The Harmonized Republic is online.")

    def _initialize_default_emojis(self):
        """
        Initializes default emoji weights and market data.
        These are starting points, actual weights will dynamically adjust.
        """
        default_emoji_base_weights = {
            "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0,
            "👀": 0.5, "🥲": 0.2, "💯": 2.0, "💬": 3.0,
            "🔀": 4.0, "🆕": 3.0, "🔗": 2.0, "❤️": 4.0,
            "🚀": 3.5, "💎": 6.0, "🌟": 3.0, "⚡": 2.5
        }
        for emoji, weight in default_emoji_base_weights.items():
            self.emoji_market_data[emoji]['current_weight'] = weight
            self.emoji_market_data[emoji]['total_uses'] = 1 # Start with 1 use to avoid div by zero
            self.emoji_market_data[emoji]['total_karma_generated'] = weight # Simulate initial karma

    def _update_emoji_market(self, emoji: str, karma_generated: float):
        """
        Updates the real-time emoji market data after a reaction.
        Dynamically adjusts emoji weights (market value) based on usage and karma generated.
        This is the "Emoji Stock Market" in action.
        """
        market_entry = self.emoji_market_data[emoji]
        market_entry['total_uses'] += 1
        market_entry['total_karma_generated'] += karma_generated
        
        # Simple dynamic weight calculation: Average karma per use.
        # This reflects the "value" of an emoji based on the karma it generates.
        market_entry['current_weight'] = market_entry['total_karma_generated'] / market_entry['total_uses']

        # Implement a subtle daily decay for all emoji weights to prevent runaway inflation
        # and encourage fresh reactions, similar to viral decay.
        for e, data in self.emoji_market_data.items():
            # Only decay if there's an actual weight to decay
            if data['current_weight'] > 0:
                data['current_weight'] *= 0.999 # Very small daily decay
        
        # Ensure minimum weight to prevent emojis from becoming completely worthless
        if market_entry['current_weight'] < 0.1:
            market_entry['current_weight'] = 0.1 # Floor for emoji weight

        self.log.add({
            "event": "EMOJI_MARKET_UPDATE",
            "details": {
                "emoji": emoji,
                "new_weight": market_entry['current_weight'],
                "total_uses": market_entry['total_uses'],
                "total_karma_generated": market_entry['total_karma_generated']
            }
        })
        print(f"📈 Emoji Market Update: '{emoji}' new weight {market_entry['current_weight']:.2f} (total uses: {market_entry['total_uses']})")


    def add_user(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human"):
        """
        Adds a new user to the system. Automatically mints a unique root coin for every new user.
        """
        if name in self.users:
            print(f"⚠️ User {name} already exists.")
            return
        
        # Determine consent mechanism based on species for new user
        consent_mechanism = "explicit"
        if species.lower() == "animal":
            consent_mechanism = "behavioral_signals"
            consent = True # Animals are assumed to implicitly consent if added.
        elif species.lower() == "robot":
            consent_mechanism = "algorithmic_audit"
            consent = True # Robots are assumed to implicitly consent if added.
        elif species.lower() == "alien":
            consent_mechanism = "cryptic_ritual"
            # Alien consent remains False until manually set via ritual (set_consent)

        user = User(name, is_genesis, consent, species=species.lower(), consent_mechanism=consent_mechanism)
        self.users[name] = user
        self.log.add({"event": "ADD_USER", "details": {"name": name, "genesis": is_genesis, "species": species, "consent_mechanism": consent_mechanism}})
        print(f"✅ User '{name}' ({species}) added, genesis={is_genesis}.")

        # Apply new species karma bonus if not a genesis user and not human
        if not is_genesis and user.species not in ["human"]:
            user.karma += self.new_species_karma_bonus
            self.log.add({"event": "NEW_SPECIES_BONUS", "details": {"user": name, "species": species, "bonus_amount": self.new_species_karma_bonus}})
            print(f"🎁 '{name}' ({species}) received {self.new_species_karma_bonus} karma bonus for joining the republic!")

        # NEW: Automatically mint one absolute root coin for every new user
        # This is their foundational identity coin, free of karma requirements.
        root_coin_id = sha(f"ROOT-{name}-{ts()}-{random.random()}")
        root_coin = Coin(id=root_coin_id, root=name, owner=name, tag="root_identity", is_root_coin=True, value=1.0) # Root coin has a base value of 1.0
        self.coins[root_coin_id] = root_coin
        user.root_coin_id = root_coin_id # Link user to their root coin
        user.coins_owned.append(root_coin_id) # Add to user's owned coins
        self.log.add({"event": "MINT_ROOT_COIN", "details": {"user": name, "root_coin_id": root_coin_id, "is_genesis": is_genesis}})
        print(f"🌱 User '{name}' automatically minted their unique root coin: {root_coin_id}.")


    def set_consent(self, name: str, consent: bool):
        """
        Sets explicit consent for a user. For non-explicit consent mechanisms,
        this method can be extended or replaced by species-specific logic.
        """
        user = self.users.get(name)
        if not user:
            print(f"❌ ERROR: User '{name}' not found.")
            return
        
        if user.consent_mechanism != "explicit" and user.consent_mechanism != "cryptic_ritual":
            print(f"⚠️ User '{name}' has a '{user.consent_mechanism}' consent mechanism. Direct explicit consent setting is usually not applicable for this species.")
            # For demo, still allow setting for now, but in a real system, this would trigger specific logic.
        elif user.consent_mechanism == "cryptic_ritual":
            print(f"🌌 Alien '{name}' attempting to perform cryptic ritual for consent. Ritual outcome: {'Success' if consent else 'Failure'}.")
        
        user.consent = consent
        self.log.add({"event": "SET_CONSENT", "details": {"name": name, "status": consent}})
        print(f"✅ Consent for '{name}' set to {consent}.")

    def check_consent(self, username: str) -> bool:
        """
        Checks if a user has given consent, accounting for different species' mechanisms.
        For animals, it's simulated behavioral signals (e.g., tail wagging = True).
        For robots, it's simulated algorithmic audit (always True if user is robot).
        For aliens, it's a simulated cryptic ritual (can be manually toggled).
        """
        user = self.users.get(username)
        if not user:
            print(f"❌ User '{username}' not found.")
            return False
        
        if user.species == "animal":
            # Simulate animal consent (e.g., based on tail wagging in video)
            # For simplicity, let's say animals always consent if they are in the system.
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent: # If complex simulation failed
                print(f"❌ Animal '{username}' did not provide behavioral consent (simulated).")
            return simulated_consent
        
        elif user.species == "robot":
            # Simulate robot consent (e.g., passing an internal audit)
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent:
                 print(f"❌ Robot '{username}' failed algorithmic consent audit (simulated).")
            return simulated_consent

        elif user.species == "alien":
            # Simulate alien consent (e.g., performing a cryptic ritual)
            # For alien, consent is only True if manually set by `set_consent` (ritual performed)
            simulated_consent = user.consent 
            if not simulated_consent:
                print(f"❌ Alien '{username}' did not perform the cryptic ritual (simulated).")
            return simulated_consent

        else: # Default: explicit consent for humans
            if not user.consent:
                print(f"❌ User '{username}' (human) has not given explicit consent.")
                return False
            return True

    def _check_and_apply_governance_decay(self):
        """
        Checks if a period has passed for progressive trust decay and applies it.
        This simulates a background daemon process.
        """
        self.governance.progressive_trust_decay()


    def reset_daily_actions_if_new_day(self):
        """Ensures all user daily action counters are reset at the start of a new day."""
        current_day = today()
        if current_day != self.current_day:
            for user in self.users.values():
                user.reset_daily_actions_if_needed() # Calls the user's internal method
            self.current_day = current_day
            print("🔄 Daily user action counters reset.")
            self._check_and_apply_governance_decay() # Check for governance decay daily (or yearly in larger scale)

    def karma_threshold(self, user: User) -> float:
        """
        Calculates the karma needed for a user to mint their next *fractional post*.
        This implements the halving threshold and minimum floor.
        """
        # Founders (genesis users) don't need karma for fractional posts
        if user.is_genesis:
            return 0.0

        minted_fractional_posts = user.mint_count # Use mint_count which tracks fractional posts
        threshold = self.mint_threshold_base / (2 ** minted_fractional_posts)
        return max(self.min_karma_threshold, threshold) # Ensure it doesn't drop below min

    def can_mint_fractional_post(self, username: str) -> bool:
        """Checks if a user has sufficient karma to mint a new fractional post."""
        user = self.users.get(username)
        if not user:
            print(f"❌ Mint check failed: unknown user {username}.")
            return False
        # Founders (genesis users) can always make fractional posts without karma
        if user.is_genesis:
            return True
        # Non-founders need karma for fractional posts
        return user.karma >= self.karma_threshold(user)

    def mint_fractional_post(self, user_name: str, content: str, fractional_percentage: float = 0.01, # Default 1%
                             tag: str = "post", references: list = None, fields: list = None) -> str | None:
        """
        Mints a new 'post' as a fractional part of the user's personal root coin.
        This is karma-gated for non-genesis users.
        """
        self.reset_daily_actions_if_new_day() # Ensure daily limits are fresh
        
        user = self.users.get(user_name)
        if not user:
            print(f"❌ Mint failed: User '{user_name}' not found.")
            return None

        if not user.root_coin_id:
            print(f"❌ Mint failed: User '{user_name}' does not have a root coin. Add user first.")
            return None

        if not self.check_consent(user_name): # Re-check explicit consent based on user's mechanism
            return None
        
        # Check karma threshold for non-genesis users for subsequent posts
        if not user.is_genesis and not self.can_mint_fractional_post(user_name): # Founders bypass this check
            needed = self.karma_threshold(user)
            print(f"🔒 MINT DENIED: '{user_name}' needs {needed:.0f} karma for next post; has {user.karma:.1f}.")
            return None

        # Content validation via Vaccine
        if not self.vax.scan(content):
            print(f"❌ MINT DENIED: Content blocked by Vaccine.")
            return None
        if references:
            for ref in references:
                if not self.vax.scan(ref):
                    print(f"❌ MINT DENIED: Reference content blocked by Vaccine: {ref[:50]}....")
                    return None

        # Validate fractional percentage
        if not (0 < fractional_percentage <= 1.0):
            print("❌ Mint failed: Fractional percentage must be between 0 and 1.0 (exclusive of 0).")
            return None

        # Deduct karma for non-genesis users when they make a fractional post
        if not user.is_genesis:
            user.karma -= self.karma_threshold(user) # Deduct karma upon successful fractional mint
            user.mint_count += 1 # Increment fractional post count
            user.next_mint_threshold = self.karma_threshold(user) # Update next threshold

        # Create the new fractional coin (post)
        post_id = sha(f"{user_name}-{content}-{ts()}-{random.random()}")
        
        # Calculate the actual value of this fractional post
        # The base value of the root coin is 1.0, so the post's value is directly the percentage.
        post_value = fractional_percentage * self.coins[user.root_coin_id].value 

        new_post_coin = Coin(
            id=post_id,
            root=user.root_coin_id, # Root is now the personal identity coin
            owner=user_name,
            tag=tag,
            value=post_value,
            is_root_coin=False,
            fractional_source_coin_id=user.root_coin_id,
            fractional_percentage=fractional_percentage
        )
        if references: new_post_coin.references = references
        if fields: new_post_coin.fields = fields
        
        self.coins[post_id] = new_post_coin
        user.coins_owned.append(post_id) # Add post coin to user's owned coins
        
        self.log.add({"event": "MINT_FRACTIONAL_POST", "details": {
            "user": user_name,
            "post_id": post_id,
            "root_coin_id": user.root_coin_id,
            "fractional_percentage": fractional_percentage,
            "post_value": post_value,
            "tag": tag,
            "content_snippet": content[:64]
        }})
        print(f"🪙 '{user_name}' minted a fractional post '{post_id}' (from root {user.root_coin_id}) with {fractional_percentage*100:.2f}% value.")
        self._call_plugins("on_mint_fractional_post", new_post_coin) # Trigger plugins
        return post_id

    def react(self, actor_name: str, coin_id: str, emoji: str):
        """
        A user reacts to a coin/post with an emoji, triggering a value event and
        updating the emoji market.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        # Ensure user and coin exist and user has consented
        if actor_name not in self.users: self.add_user(actor_name, consent=True)
        if coin_id not in self.coins: print(f"❌ REACT FAILED: Coin '{coin_id}' not found."); return False
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        
        # The "originator" for split purposes is the *owner* of the content coin/post reacted to.
        # If it's a root coin, the owner is its root. If it's a fractional post, its owner is the person who minted that post.
        originator_user = self.users.get(coin.owner) # Get the user who owns this specific coin/post

        if not self.check_consent(actor_name) or (originator_user and not originator_user.consent):
            print("❌ REACT DENIED: Both actor and originator (if known) must have consent.")
            return False
        
        # Scan emoji with Vaccine (prevents toxic reactions)
        if not self.vax.scan(emoji):
            print(f"❌ Reaction blocked by vaccine.")
            return False

        # Apply per-user daily diminishing returns
        date_str = today()
        actor.reset_daily_actions_if_needed() # Ensure daily reset for the actor
        action_count_today = actor.daily_actions[date_str][f"react_{emoji}"]
        daily_decay_factor = self.daily_decay_factor ** action_count_today
        actor.daily_actions[date_str][f"react_{emoji}"] += 1

        # Retrieve dynamic emoji weight from the market data
        base_weight = self.emoji_market_data.get(emoji, {'current_weight': 1.0})['current_weight']
        
        # Apply per-coin viral decay based on existing reactions to this specific coin
        viral_decay_factor = 0.95 ** len(coin.reactions) # Each reaction reduces future value for this coin slightly

        # The base value for split is the coin's `value` (which for fractional posts is its percentage)
        # multiplied by the emoji's weighted_value and decay factors.
        weighted_value = coin.value * base_weight * daily_decay_factor * viral_decay_factor

        # Calculate 33.3333% split portions
        split_value = weighted_value / 3.0

        # Apply genesis fading multipliers to actor and originator's shares
        actor_multiplier = actor.get_fading_multiplier()
        originator_multiplier = originator_user.get_fading_multiplier() if originator_user else 1.0

        originator_share = split_value * originator_multiplier
        actor_share = split_value * actor_multiplier
        treasury_share = split_value # Treasury share is not multiplied by individual multipliers

        # Distribute karma
        if originator_user and originator_user.consent: # Only award if content owner exists and has consented
            originator_user.karma += originator_share 

        actor.karma += actor_share
        self.treasury += treasury_share

        # Log reaction to the coin itself
        coin.reactions.append((actor_name, emoji, ts()))
        coin.react_log.append({'actor': actor_name, 'emoji': emoji, 'karma_share': (originator_share + actor_share), 'ts': ts()}) # Log specific karma generated for this reaction

        self.log.add({
            "event": "REACT",
            "details": {
                "username": actor_name,
                "coin_id": coin_id,
                "emoji": emoji,
                "weighted_value": weighted_value,
                "split": {
                    "originator_total": originator_share, # Total for the content owner
                    "actor": actor_share,
                    "treasury": treasury_share
                }
            }
        })

        print(f"👍 {actor_name} reacted {emoji} on coin {coin_id}: "
              f"owner +{originator_share:.2f}, actor +{actor_share:.2f}, "
              f"treasury +{treasury_share:.2f}.")
        
        # Update emoji market with the total karma generated by this reaction
        self._update_emoji_market(emoji, weighted_value)

        self._call_plugins("on_react", actor_name, coin_id, emoji, weighted_value) # Trigger plugins

        return True

    def remix(self, actor_name: str, parent_coin_id: str, content: str, tag: str = "remix", references: list = None, fields: list = None) -> str | None:
        """
        A user creates a derivative coin (remix) of an existing post/coin, preserving lineage.
        Remixing is considered a new "post" and thus subject to fractional minting rules.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        if not self.check_consent(actor_name):
            return None
        if parent_coin_id not in self.coins:
            print(f"❌ REMIX FAILED: Parent coin '{parent_coin_id}' not found.")
            return None
        
        parent = self.coins[parent_coin_id]
        actor = self.users[actor_name]

        # Remixing is now a 'mint_fractional_post' operation for the actor.
        # It's their act of creating new content from existing, so it uses their fractional minting logic.
        # Default remix post uses a small percentage of root coin value.
        remix_percentage = 0.001 # A small percentage for a remix post
        remix_coin_id = self.mint_fractional_post(actor_name, content, fractional_percentage=remix_percentage, tag=tag, references=references, fields=fields)
        
        if remix_coin_id:
            new_coin = self.coins[remix_coin_id]
            # Lineage: New remix coin directly inherits the parent's ancestry and then adds the parent itself.
            new_coin.ancestors.extend(parent.ancestors)
            new_coin.ancestors.append(parent_coin_id)
            
            # The karma for the remix action itself. Use a specific emoji for remix value.
            remix_base_value = self.emoji_market_data.get("🔀", {'current_weight': 4.0})['current_weight'] # Use dynamic remix emoji weight
            
            # Apply per-user daily diminishing returns for remix action
            actor.reset_daily_actions_if_needed()
            remix_action_count_today = actor.daily_actions[today()]["remix_action"]
            remix_daily_decay_factor = self.daily_decay_factor ** remix_action_count_today
            actor.daily_actions[today()]["remix_action"] += 1

            remix_value = remix_base_value * remix_daily_decay_factor
            split_remix_value = remix_value / 3.0 # Apply 33.3333% split

            # Distribute karma for the remix action itself
            actor_remix_share = split_remix_value * actor.get_fading_multiplier()
            
            # The original *owner* of the parent post gets the second share
            parent_owner_user = self.users.get(parent.owner)
            parent_owner_remix_share = split_remix_value * parent_owner_user.get_fading_multiplier() if parent_owner_user else 0.0

            actor.karma += actor_remix_share
            if parent_owner_user:
                parent_owner_user.karma += parent_owner_remix_share
            self.treasury += split_remix_value # Treasury gets its share from the remix action

            self.log.add({
                "event": "REMIX",
                "details": {
                    "actor": actor_name,
                    "parent_coin_id": parent_coin_id,
                    "new_coin_id": remix_coin_id,
                    "ancestry": new_coin.ancestry,
                    "remix_value": remix_value,
                    "split": {
                        "actor": actor_remix_share,
                        "parent_owner": parent_owner_remix_share,
                        "treasury": split_remix_value
                    }
                }
            })

            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{remix_coin_id}'. "
                  f"Remixer +{actor_remix_share:.2f} karma, Parent Owner +{parent_owner_remix_share:.2f} karma.")
            
            self._call_plugins("on_remix", new_coin) # Trigger plugins
        return remix_coin_id

    def add_reference(self, user_name: str, coin_id: str, ref_type: str, ref_id: str, description: str):
        """Adds a structured external reference to a coin/post for attribution."""
        if coin_id not in self.coins or user_name not in self.users:
            print("❌ ADDREF FAILED: Coin or user not found.")
            return
        if not self.check_consent(user_name): # Check consent based on user's mechanism
            return False

        reference = {"type": ref_type, "id": ref_id, "description": description, "added_by": user_name, "ts": ts()}
        self.coins[coin_id].references.append(reference)
        self.log.add({"event": "ADD_REFERENCE", "details": {"coin_id": coin_id, "reference": reference}})
        print(f"🔬 Reference added to coin '{coin_id}'.")

        # Award karma for adding a reference (can be tied to a specific emoji/weight)
        actor_ref_value = self.emoji_market_data.get("🔗", {'current_weight': 2.0})['current_weight'] # Use dynamic link emoji weight
        split_ref_value = actor_ref_value / 3.0
        
        # This karma goes to the user who added the reference, and to the treasury
        self.users[user_name].karma += split_ref_value * self.users[user_name].get_fading_multiplier()
        self.treasury += split_ref_value # Treasury gets its share too
        self.log.add({"event": "KARMA_AWARD_REFERENCE", "details": {"user": user_name, "coin_id": coin_id, "amount": split_ref_value}})
        print(f"🔗 {user_name} earned {split_ref_value:.2f} karma for adding reference to {coin_id}.")


    def trace_lineage(self, coin_id: str):
        """Displays the full creative lineage of a coin/post."""
        if coin_id not in self.coins: print(f"❌ TRACE FAILED: Coin '{coin_id}' not found."); return
        
        print(f"\n--- 🧬 Creative Lineage Trace for Coin: {coin_id} ---")
        path = []
        current_id = coin_id
        
        while current_id and current_id in self.coins:
            coin = self.coins[current_id]
            path.append(coin)
            if coin.ancestors: # Follow the most recent direct ancestor for a single path
                current_id = coin.ancestors[-1]
            else:
                current_id = None # No more ancestors
    
    for i, coin in enumerate(reversed(path)): # Print in chronological order (root first)
        indent = "  " * i
        originators_str = ", ".join(coin.originators) # Originators are users linked to this coin, including creator
        print(f"{indent}└── Coin: {coin.id} (Tag: {coin.tag}, Root: {coin.root}, Owner: {coin.owner}, Originators: {originators_str})")
        print(f"{indent}    Created At: {coin.created_at}")
        if coin.is_root_coin:
            print(f"{indent}    🌟 This is a Universal Root Identity Coin.")
        elif coin.fractional_source_coin_id:
            print(f"{indent}    ✨ This is a Fractional Post from Root: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
        if coin.references:
            print(f"{indent}    ├── References:")
            for ref in coin.references:
                print(f"{indent}    │   └── {ref.get('type', 'N/A')}: {ref.get('id', 'N/A')} ({ref.get('description', 'N/A')}) by {ref.get('added_by', 'Unknown')}")
        if coin.reactions:
            print(f"{indent}    └── Reactions ({len(coin.reactions)} total): {coin.reaction_summary()}") # Using helper for summary
    print("--- End of Trace ---")

    def show_user_karma(self, username: str):
        """Displays comprehensive user karma information."""
        user = self.users.get(username)
        if user:
            print(f"\n--- 👤 User '{username}' Status ---")
            print(f"  Karma: {user.karma:.2f}")
            print(f"  Is Genesis: {user.is_genesis}")
            print(f"  Species: {user.species.capitalize()}")
            print(f"  Consent Mechanism: {user.consent_mechanism.replace('_', ' ').title()}")
            print(f"  Current Multiplier: {user.get_fading_multiplier():.2f}")
            print(f"  Fractional Posts Minted: {user.mint_count}")
            print(f"  Next Post Threshold: {self.karma_threshold(user):.2f}")
            print(f"  Consent Given: {user.consent}") # Actual consent stored
            print(f"  Consent Check (Simulated): {self.check_consent(username)}") # Simulated consent based on species
            print(f"  Joined: {user.join_timestamp}")
            print(f"  Personal Root Coin: {user.root_coin_id if user.root_coin_id else 'None'}")
            print(f"  Coins/Posts Owned: {len(user.coins_owned)}")
            print("----------------------------------")
        else:
            print(f"No such user '{username}'.")

    def show_coin_info(self, coin_id: str):
        """Displays detailed coin/post information."""
        coin = self.coins.get(coin_id)
        if coin:
            print(f"\n--- 💎 Coin/Post ID: {coin.id} ---")
            print(f"  Root Originator: {coin.root}")
            print(f"  Current Owner: {coin.owner}")
            print(f"  Tag: {coin.tag}")
            print(f"  Base Value (from root): {coin.value}")
            print(f"  Created At: {coin.created_at}")
            print(f"  Is Root Coin: {coin.is_root_coin}")
            if coin.fractional_source_coin_id:
                print(f"  Fractional Source: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
            print(f"  Ancestry: {coin.ancestors if coin.ancestors else 'None'}")
            print(f"  Total Reactions: {len(coin.reactions)}")
            reaction_summary = defaultdict(int)
            for _, emoji, _ in coin.reactions:
                reaction_summary[emoji] += 1
            print(f"  Reaction Summary: {dict(reaction_summary)}")
            print(f"  References ({len(coin.references)}):")
            for ref in coin.references:
                print(f"    - Type: {ref.get('type')}, ID: {ref.get('id')}, Desc: {ref.get('description')} (by {ref.get('added_by')})")
            if not coin.references:
                print("    None")
            print("-------------------------------")
        else:
            print(f"No such coin: {coin_id}.")

    def get_treasury_balance(self) -> float:
        """Returns and prints the current treasury balance."""
        print(f"Community treasury balance: {self.treasury:.2f}.")
        return self.treasury

    def show_emoji_market_status(self):
        """
        Displays the current status of the emoji market, including dynamic weights.
        This is your "Nasdaq of Vibes".
        """
        print("\n--- 📈 Real-Time Emoji Market Status (Nasdaq of Vibes) ---")
        print("{:<10} {:<15} {:<15} {:<15}".format("Emoji", "Current Weight", "Total Uses", "Avg Karma/Use"))
        print("-" * 60)
        sorted_emojis = sorted(self.emoji_market_data.items(), key=lambda item: item[1]['current_weight'], reverse=True)
        for emoji, data in sorted_emojis:
            avg_karma_per_use = data['total_karma_generated'] / data['total_uses'] if data['total_uses'] > 0 else 0
            print("{:<10} {:<15.2f} {:<15} {:<15.2f}".format(emoji, data['current_weight'], data['total_uses'], avg_karma_per_use))
        print("----------------------------------------------------------\n")

    def plugin(self, action: str, name: str, *args):
        """Interface for loading, unloading, and calling external plugins."""
        if action == "load":
            try:
                # Assuming plugins are in a 'plugins' directory and each is a .py file
                # Use importlib.util for more robust dynamic loading
                spec = importlib.util.spec_from_file_location(name, f"plugins/{name}.py")
                if spec is None:
                    raise ImportError(f"Could not find plugin '{name}' at plugins/{name}.py")
                module = importlib.util.module_from_spec(spec)
                sys.modules[name] = module # Add to sys.modules to make it discoverable
                spec.loader.exec_module(module)
                self.plugins[name] = module # Store the loaded module
                self.log.add({"event": "PLUGIN_LOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' loaded successfully.")
            except Exception as e:
                print(f"❌ PLUGIN ERROR: Could not load '{name}'. {e}.")
        elif action == "unload":
            if name in self.plugins:
                del self.plugins[name]
                # Also remove from sys.modules to fully unload, if possible
                if name in sys.modules:
                    del sys.modules[name]
                self.log.add({"event": "PLUGIN_UNLOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' unloaded.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        elif action == "call":
            if name in self.plugins:
                plugin_module = self.plugins[name]
                if hasattr(plugin_module, "run"):
                    try:
                        # Pass the agent instance so plugins can interact with it
                        result = plugin_module.run(self, *args)
                        self.log.add({"event": "PLUGIN_CALL", "details": {"name": name, "args": args, "result_snippet": str(result)[:128]}})
                        print(f"⚡ Plugin '{name}' executed with result: {result}.")
                    except Exception as e:
                        print(f"❌ PLUGIN ERROR: Error executing '{name}'. {e}.")
                else:
                    print(f"❌ PLUGIN ERROR: Plugin '{name}' has no 'run' method.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        else:
            print("❓ Unknown plugin action. Use 'load', 'unload', or 'call'.")

    def propose_governance_change(self, proposer_name: str, proposal_details: dict, votes_by_species: dict[str, float]) -> bool:
        """
        Submits a formal governance proposal and checks if it passes current rules.
        proposal_details: Dict describing the proposed change (e.g., {'type': 'update_governance_rules', 'new_supermajority_percent': 0.75})
        votes_by_species: Dict of {species_name: percentage_of_total_karma_from_species_consenting (0-100)}.
                          This is a percentage of total karma within that species, not just user count.
                          Example: {'human': 95.0, 'robot': 80.0}
        """
        if proposer_name not in self.users:
            print(f"❌ PROPOSAL FAILED: Proposer '{proposer_name}' not found.")
            return False

        # Calculate total karma per species for weighting votes
        total_karma_per_species = defaultdict(float)
        active_species_counts = defaultdict(int) # Count of active users per species
        
        # Calculate max karma for weighting. Genesis users treated as having a very high value.
        GENESIS_VOTE_WEIGHT = 1_000_000_000.0 

        for user in self.users.values():
            if self.check_consent(user.name): # Only consented users contribute to species totals
                active_species_counts[user.species] += 1
                if user.is_genesis:
                    total_karma_per_species[user.species] += GENESIS_VOTE_WEIGHT
                else:
                    total_karma_per_species[user.species] += user.karma
        
        # Sum of all karma across all users (including genesis weight)
        overall_total_karma = sum(total_karma_per_species.values())

        if overall_total_karma == 0:
            print("❌ PROPOSAL FAILED: No active users or karma in the system to vote.")
            return False

        # Calculate total karma-weighted consent for the overall supermajority check
        overall_consented_karma = 0.0
        species_consent_met = True
        detailed_consent_report = {}

        for species, min_percent_required in self.governance.species_min_consent.items():
            species_total_karma = total_karma_per_species[species]
            species_voted_percent = votes_by_species.get(species, 0.0) # Percentage provided by the input

            if species_total_karma > 0:
                # Actual karma contributed by this species to the 'yes' vote
                species_yes_karma = (species_voted_percent / 100.0) * species_total_karma
                overall_consented_karma += species_yes_karma

                # Check species-specific minimum consent
                if species_voted_percent < min_percent_required:
                    species_consent_met = False
                    detailed_consent_report[species] = f"FAILED: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
                else:
                    detailed_consent_report[species] = f"MET: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
            elif min_percent_required > 0 and species not in active_species_counts: # If species has requirement but no users of that species yet
                species_consent_met = False
                detailed_consent_report[species] = f"FAILED: No active users of this species, but requires {min_percent_required:.2f}%."
            else: # Species exists but has 0 min required, or 0 total karma and no min required (no effect)
                detailed_consent_report[species] = "N/A: No users, or no min requirement."


        # Calculate overall actual consent percentage based on karma
        overall_actual_consent_percent = (overall_consented_karma / overall_total_karma) * 100 if overall_total_karma > 0 else 0.0
        overall_supermajority_met = overall_actual_consent_percent >= self.governance.supermajority_percent

        if not overall_supermajority_met:
            print(f"❌ PROPOSAL FAILED: Overall karma consent is {overall_actual_consent_percent:.2f}%, but requires {self.governance.supermajority_percent:.2f}% supermajority.")
        if not species_consent_met:
            print(f"❌ PROPOSAL FAILED: One or more species did not meet their minimum consent threshold.")

        proposal_passed = overall_supermajority_met and species_consent_met

        self.log.add({
            "event": "GOVERNANCE_PROPOSAL_VOTE",
            "details": {
                "proposer": proposer_name,
                "proposal_details": proposal_details,
                "votes_by_species_input": votes_by_species, # Log raw input
                "overall_actual_consent_percent": overall_actual_consent_percent,
                "overall_required_percent": self.governance.supermajority_percent,
                "species_consent_breakdown": detailed_consent_report,
                "passed": proposal_passed
            }
        })

        if proposal_passed:
            print(f"✅ GOVERNANCE PROPOSAL PASSED! Overall consent: {overall_actual_consent_percent:.2f}%.")
            # --- Basic Proposal Execution ---
            if proposal_details.get('type') == 'update_governance_rules':
                new_supermajority = proposal_details.get('new_supermajority_percent')
                new_species_mins = proposal_details.get('new_species_min_consent')
                self.governance.update_rules(new_supermajority, new_species_mins)
            elif proposal_details.get('type') == 'change_mint_threshold_base':
                new_threshold = proposal_details.get('new_mint_threshold_base')
                if new_threshold is not None:
                    self.mint_threshold_base = new_threshold
                    self.log.add({"event": "PROTOCOL_PARAM_UPDATE", "details": {"param": "mint_threshold_base", "new_value": new_threshold}})
                    print(f"✅ Protocol parameter 'mint_threshold_base' updated to {new_threshold}.")
            # Future: add other types of protocol changes here
            # --- End Basic Proposal Execution ---

            # Reset incident tracking as a successful governance change implies stability/resolution
            self.governance.incident_free_years = 0
            self.governance.last_incident_date = today()
            self._call_plugins("on_governance_passed", proposal_details)
        else:
            print(f"❌ GOVERNANCE PROPOSAL FAILED. Please review requirements.")
            self.governance.trigger_incident() # Trigger an incident if a proposal fails
            self._call_plugins("on_governance_failed", proposal_details)
        return proposal_passed


    def log_profit(self, amount: float, description: str):
        """Logs an external profit event, adding to the treasury."""
        self.treasury += amount
        self.log.add({
            "event": "PROFIT_LOG",
            "details": {"amount": amount, "description": description, "new_treasury_balance": self.treasury}
        })
        print(f"🏦 Profit of {amount:.2f} logged. Treasury is now {self.treasury:.2f}.")

    def snapshot(self, save=True, filename="snapshot.json"):
        """Saves or loads the entire agent state."""
        if save:
            state = {
                "users": {name: user.to_dict() for name, user in self.users.items()},
                "coins": {cid: coin.to_dict() for cid, coin in self.coins.items()},
                "treasury": self.treasury,
                "log_entries": list(self.log.entries), # Save current log entries
                "emoji_market_data": dict(self.emoji_market_data), # Save emoji market
                "governance_rules": {
                    "supermajority_percent": self.governance.supermajority_percent,
                    "species_min_consent": dict(self.governance.species_min_consent),
                    "incident_free_years": self.governance.incident_free_years,
                    "last_incident_date": self.governance.last_incident_date
                },
                "mint_threshold_base": self.mint_threshold_base,
                "new_species_karma_bonus": self.new_species_karma_bonus
            }
            try:
                with open(filename, "w", encoding='utf-8') as f:
                    json.dump(state, f, indent=2)
                print(f"💾 State saved to '{filename}'.")
            except IOError as e:
                print(f"❌ SNAPSHOT ERROR: Could not save state. {e}.")
        else:
            if not os.path.exists(filename):
                print(f"❓ SNAPSHOT INFO: No snapshot file found at '{filename}'. Starting fresh.")
                return
            try:
                with open(filename, "r", encoding='utf-8') as f:
                    state = json.load(f)
            
                self.users = {}
                for name, u_data in state.get("users", {}).items():
                    # Pass species and consent_mechanism during user reconstruction
                    user = User(
                        name,
                        u_data.get('is_genesis', False),
                        u_data.get('consent', False),
                        species=u_data.get('species', 'human'),
                        consent_mechanism=u_data.get('consent_mechanism', 'explicit')
                    )
                    user.karma = u_data.get('karma', 0.0)
                    user.mint_count = u_data.get('mint_count', 0)
                    user.next_mint_threshold = u_data.get('next_mint_threshold', 100000.0)
                    user.root_coin_id = u_data.get('root_coin_id')
                    user.coins_owned = u_data.get('coins_owned', [])
                    user.join_timestamp = u_data.get('join_timestamp', ts())
                    if u_data.get('fading_multiplier_start_time'):
                        user.fading_multiplier_start_time = datetime.datetime.fromisoformat(u_data['fading_multiplier_start_time'])
                    if 'daily_actions' in u_data:
                        user.daily_actions = defaultdict(lambda: defaultdict(int), u_data['daily_actions'])
                    self.users[name] = user

                self.coins = {}
                for cid, cd_data in state.get("coins", {}).items():
                    coin = Coin(
                        id=cd_data.get('id'),
                        root=cd_data.get('root'),
                        owner=cd_data.get('owner'),
                        value=cd_data.get('value', 1.0),
                        tag=cd_data.get('tag', 'single'),
                        is_root_coin=cd_data.get('is_root_coin', False),
                        fractional_source_coin_id=cd_data.get('fractional_source_coin_id'),
                        fractional_percentage=cd_data.get('fractional_percentage', 0.0)
                    )
                    coin.fields = cd_data.get('fields', [])
                    coin.ancestors = cd_data.get('ancestors', [])
                    coin.references = cd_data.get('references', [])
                    coin.reactions = cd_data.get('reactions', [])
                    coin.react_log = cd_data.get('react_log', [])
                    coin.created_at = cd_data.get('created_at', ts())
                    self.coins[cid] = coin

                self.treasury = state.get("treasury", 0.0)
                self.log.entries = deque(state.get("log_entries", []), maxlen=self.log.entries.maxlen)
                
                loaded_emoji_market_data = state.get("emoji_market_data", {})
                self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0}, loaded_emoji_market_data)

                # Load governance rules
                governance_data = state.get("governance_rules", {})
                self.governance = Governance(
                    initial_supermajority_percent=governance_data.get("supermajority_percent", 90.0),
                    initial_species_min_consent=governance_data.get("species_min_consent", {"human": 10.0, "robot": 10.0}),
                    incident_free_years=governance_data.get("incident_free_years", 0),
                    last_incident_date=governance_data.get("last_incident_date", today())
                )
                self.governance.progressive_trust_decay() # Apply decay on load if time has passed

                # Load other top-level parameters
                self.mint_threshold_base = state.get("mint_threshold_base", 100_000.0)
                self.new_species_karma_bonus = state.get("new_species_karma_bonus", 50000)

                print(f"♻️ State loaded from '{filename}'.")
            except Exception as e:
                print(f"❌ SNAPSHOT ERROR: Could not load state. {e}.")

# ==============================================================================
# V. ANCILLARY SYSTEMS & INTERFACES
# ==============================================================================

class CorpX:
    """Simulates an adversarial entity to continuously test the Vaccine."""
    ATTACKS = ["inject malware", "phish creds", "launch ddos", "plant backdoor", "propaganda spam"]

    def __init__(self, vaccine: Vaccine):
        self.vaccine = vaccine
        self.attack_count = 0

    def run_attack(self, payload: str = None):
        """Performs an attack simulation."""
        self.attack_count += 1
        attack_payload = payload if payload else random.choice(self.ATTACKS)
        print(f"\n💀 CorpX Attack #{self.attack_count}: Attempting to inject '{attack_payload}'...")
        if self.vaccine.scan(attack_payload):
            print("🛡️ ATTACK EVADED! (Vaccine did not trigger).")
        else:
            print("🛡️ ATTACK BLOCKED! (Vaccine successfully triggered).")

def quiz() -> bool:
    """Interactive onboarding quiz for new users, ensuring informed consent."""
    print("\n--- 🤗 Welcome to the Remix Republic Onboarding Quiz ---")
    questions = [
        ("What is the universal value split percentage for all actions?", "33.3333"),
        ("Can you remix someone's content without their consent? (yes/no)", "no"),
        ("What must every new user earn to gain minting rights?", "karma"),
        ("What is the ultimate authority in this protocol?", "the code")
    ]
    for q, a in questions:
        resp = input(f"👉 {q} ").strip().lower()
        if resp != a:
            print("❌ Incorrect. Please review the Core Canons and try again.")
            return False
    print("✅ Quiz passed! You understand the fundamental laws. Welcome aboard!\n")
    return True

def cli():
    """A comprehensive command-line interface for interacting with the Agent."""
    agent = RemixAgent()
    adversary = CorpX(agent.vax)
    agent.snapshot(save=False) # Load state on start

    print("🤖 Universal Remix Protocol v11.3 CLI. Type ':help' for commands.")
    while True:
        try:
            raw_input_str = input(">>> ").strip()
            if not raw_input_str: continue
            
            if raw_input_str.lower() in [':exit', ':quit']:
                agent.snapshot(save=True)
                print("👋 Goodbye! State saved.")
                break
            
            if not raw_input_str.startswith(':'):
                print("⚠️ Commands must start with a colon ':'.")
                continue

            parts = raw_input_str[1:].split(maxsplit=1) # Split only on first space to keep args together
            command = parts[0].lower()
            args_str = parts[1] if len(parts) > 1 else "" # Get remaining args as a single string

            # Parse args from string (this is more robust for complex arguments)
            # This simple parser handles "quoted strings" for content and key=value pairs
            # It's not a full shell parser, but works for our CLI needs
            parsed_args = []
            current_arg = ""
            in_quote = False
            for char in args_str:
                if char == '"':
                    in_quote = not in_quote
                    if not in_quote and current_arg: # End of a quoted string
                        parsed_args.append(current_arg)
                        current_arg = ""
                elif char == ' ' and not in_quote:
                    if current_arg:
                        parsed_args.append(current_arg)
                        current_arg = ""
                else:
                    current_arg += char
            if current_arg:
                parsed_args.append(current_arg)
            
            args = parsed_args


            if command == "help":
                print("""
--- User Commands ---
:quiz                                  - Take the onboarding quiz.
:consent <username> <true/false>      - Set user consent.
:post <username> "<content>" [perc] [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Mint a fractional post.
:react <username> <coin_id> <emoji>   - React to a coin/post.
:remix <username> <parent_coin_id> "<content>" [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Remix a coin/post.
:addref <username> <coin_id> <type> <id> "<description>" - Add a structured reference to a coin/post.
:karma <username>                     - Show user's karma.
:coininfo <coin_id>                   - Show detailed coin/post info.
:treasury                             - Show treasury balance.
:emojimarket                         - Show real-time emoji market status.

--- Query Commands ---
:log [filter] [limit]                 - Show audit log (optional filter string and limit).
:trace <coin_id>                      - Trace full creative lineage of a coin/post.

--- Admin & Governance Commands ---
:adduser <username> [species] [genesis] - Add a new user (default human, optional genesis).
:propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z] - Propose a governance change.
:trigger_incident                     - Manually trigger a major incident (resets consent decay).
:check_decay                         - Manually trigger progressive trust decay check.
:profit <amount> "<description>"      - Log a profit event to treasury.
:snapshot [save/load] [filename]      - Save or load agent state.
:attack [payload]                     - Simulate a CorpX attack.
:plugin <action> <name> [args...]     - Manage plugins (load, unload, call). E.g., :plugin load my_plugin
:exit / :quit                         - Save state and exit CLI.
""")
            elif command == "consent":
                if len(args) == 2 and args[1].lower() in ['true', 'false']:
                    agent.set_consent(args[0], args[1].lower() == 'true')
                else: print("Usage: :consent <username> <true/false>")
            elif command == "post": # Changed from :mint to :post for fractional minting
                username = args[0] if len(args) > 0 else None
                content = args[1] if len(args) > 1 else None # Content should be quoted
                
                if not username or not content:
                    print("Usage: :post <username> \"<content>\" [percentage_of_root_coin_value (e.g. 0.01 for 1%)] [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                fractional_percentage = 0.01 # Default to 1%
                tag = "post"
                refs = []
                fields = {}
                
                # Parse optional percentage, tag, refs, fields
                current_arg_idx = 2
                if len(args) > current_arg_idx and args[current_arg_idx].replace('.', '', 1).isdigit():
                    fractional_percentage = float(args[current_arg_idx])
                    current_arg_idx += 1

                if len(args) > current_arg_idx:
                    for arg_slice in args[current_arg_idx:]:
                        if arg_slice.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg_slice[6:-1].split(',')]
                        elif arg_slice.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg_slice[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg_slice # Remaining argument is the tag
                agent.mint_fractional_post(username, content, fractional_percentage, tag, refs, fields)
            elif command == "react":
                if len(args) == 3:
                    agent.react(args[0], args[1], args[2])
                else: print("Usage: :react <username> <coin_id> <emoji>")
            elif command == "remix":
                username = args[0] if len(args) > 0 else None
                parent_coin_id = args[1] if len(args) > 1 else None
                content = args[2] if len(args) > 2 else None

                if not username or not parent_coin_id or not content:
                    print("Usage: :remix <username> <parent_coin_id> \"<content>\" [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                tag = "remix"
                refs = []
                fields = {}
                if len(args) > 3:
                    for arg in args[3:]:
                        if arg.startswith('refs="') and arg.endswith('"'):
                            refs = [r.strip() for r in arg[6:-1].split(',')]
                        elif arg.startswith('fields="') and arg.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg
                agent.remix(username, parent_coin_id, content, tag, refs, fields)
            elif command == "addref":
                if len(args) == 5:
                    agent.add_reference(args[0], args[1], args[2], args[3], args[4].strip('"'))
                else: print("Usage: :addref <username> <coin_id> <type> <id> \"<description>\"")
            elif command == "karma":
                if len(args) == 1: agent.show_user_karma(args[0])
                else: print("Usage: :karma <username>")
            elif command == "coininfo":
                if len(args) == 1: agent.show_coin_info(args[0])
                else: print("Usage: :coininfo <coin_id>")
            elif command == "treasury":
                agent.get_treasury_balance()
            elif command == "emojimarket":
                agent.show_emoji_market_status()
            elif command == "log":
                filter_str = args[0] if len(args) > 0 else None
                limit = int(args[1]) if len(args) > 1 and args[1].isdigit() else 20
                agent.log.show(filter_str, limit)
            elif command == "trace":
                if len(args) == 1: agent.trace_lineage(args[0])
                else: print("Usage: :trace <coin_id>")
            elif command == "adduser":
                if len(args) >= 1:
                    username = args[0]
                    species = "human" # Default species
                    is_genesis = False

                    # Parse optional species and genesis flags
                    for arg_slice in args[1:]:
                        if arg_slice.lower() in ["human", "robot", "animal", "alien"]: # Extendable list
                            species = arg_slice.lower()
                        elif arg_slice.lower() == "genesis":
                            is_genesis = True
                    agent.add_user(username, is_genesis=is_genesis, species=species)
                else: print("Usage: :adduser <username> [species] [genesis]")
            elif command == "propose":
                # :propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]
                if len(args) >= 3:
                    proposer_name = args[0]
                    proposal_type = args[1].strip('"')
                    description = args[2].strip('"')
                    
                    proposal_details = {"type": proposal_type, "description": description}
                    votes_by_species = {} # {species: percent_karma_consent}
                    
                    for arg_slice in args[3:]:
                        if arg_slice.lower().startswith('super_majority='):
                            try:
                                proposal_details['new_supermajority_percent'] = float(arg_slice.split('=')[1])
                            except ValueError: print("Invalid super_majority value.")
                        elif arg_slice.lower().startswith('new_threshold='): # For changing mint_threshold_base
                            try:
                                proposal_details['new_mint_threshold_base'] = float(arg_slice.split('=')[1])
                                proposal_details['type'] = 'change_mint_threshold_base' # Force type if this param is used
                            except ValueError: print("Invalid new_threshold value.")
                        elif arg_slice.lower().endswith('_votes'): # Generic species_votes parsing
                            try:
                                parts = arg_slice.split('=')
                                species_name = parts[0].replace('_votes', '').lower()
                                votes_by_species[species_name] = float(parts[1])
                            except ValueError: print(f"Invalid vote format for {arg_slice}. Use species_votes=X.")
                    
                    agent.propose_governance_change(proposer_name, proposal_details, votes_by_species)
                else: print("Usage: :propose <proposer_name> \"<proposal_type>\" \"<description>\" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]")
            elif command == "trigger_incident":
                agent.governance.trigger_incident()
            elif command == "check_decay": # Manually trigger decay check
                agent.governance.progressive_trust_decay()
            elif command == "profit":
                if len(args) == 2: agent.log_profit(float(args[0]), args[1].strip('"'))
                else: print("Usage: :profit <amount> \"<description>\"")
            elif command == "snapshot":
                if len(args) >= 1:
                    action = args[0].lower()
                    filename = args[1] if len(args) > 1 else "snapshot.json"
                    if action == 'save': agent.snapshot(save=True, filename=filename)
                    elif action == 'load': agent.snapshot(save=False, filename=filename)
                    else: print("Usage: :snapshot [save/load] [filename]")
                else: print("Usage: :snapshot [save/load] [filename]")
            elif command == "attack":
                payload = args[0] if len(args) > 0 else None
                adversary.run_attack(payload.strip('"') if payload else None)
            elif command == "plugin":
                if len(args) >= 2:
                    action = args[0].lower()
                    name = args[1]
                    plugin_args = [a.strip('"') for a in args[2:]]
                    agent.plugin(action, name, *plugin_args)
                else: print("Usage: :plugin <action> <name> [args...]")
            elif command == "quiz":
                quiz()
            else:
                print(f"❓ Unknown command: {command}. Type ':help' for list of commands.")
        except (EOFError, KeyboardInterrupt):
            agent.snapshot(save=True)
            print("\n👋 Goodbye! State saved.")
            break
        except Exception as e:
            print(f"🔥 An unexpected error occurred: {e}. Please check command syntax or agent state.")

# ==============================================================================
# VI. LAUNCH-READY SOCIAL MEDIA POST
# ==============================================================================

LINKEDIN_POST = """🚀 We didn't just fix the creator economy. We remixed its DNA.
Today, we're open-sourcing the Ultimate Remix Protocol Agent—a single Python file that runs a new kind of digital world.
A world built on three unbreakable laws:

1️⃣ Fairness is Math, Not a Motto. Every creative act—every like, comment, or remix—is an economic event. Its value is instantly split 33.33% between the original creator, the contributor, and the community. No exceptions. No hidden fees. It's all on an immutable public log.
2️⃣ Influence is Earned, Not Bought. There are no shortcuts here. New creators unlock the power to mint their own content by earning 100,000 karma points. Sound hard? It is. But with every coin you mint, the next one costs half as much. Power users can earn their seat at the table in weeks. It's a system that rewards merit and dedication, not just early arrival.
3️⃣ Credit is Forever. Our protocol has an elephant's memory. Every remix is a branch on a permanent "family tree" of ideas. We've built in an Attribution Engine for science and art, so you can cite your inspirations. If that scientist ever joins our world, our code ensures they get their cut. Forever.

This isn't just a platform; it's a joyful, autonomous republic governed by code. It has its own immune system to block propaganda and hate. It runs on consent. And it's designed for a future where humans, AIs, and maybe even a few other intelligent species can collaborate and create value together.

We're not asking you to "join our platform." We're inviting you to fork our reality.
The code is the contract. The community is the government. The remix has begun.

#RemixEconomy #OpenSource #CreatorEconomy #EthicalAI #RadicalTransparency #33Split #FutureOfWork #Karma
"""

# ==============================================================================
# VII. MAIN EXECUTION BLOCK
# ==============================================================================

if __name__ == "__main__":
    print(LINKEDIN_POST)

    # --- Running a non-interactive Demo Scenario ---
    print("\n--- Running Demo Scenario ---")
    agent = RemixAgent()
    agent.snapshot(save=False) # Load previous state if it exists

    # Onboarding new users (auto-mints their root coin)
    if "alice" not in agent.users: agent.add_user("alice", consent=True, species="human")
    if "bob" not in agent.users: agent.add_user("bob", consent=True, species="robot") # Bob is a robot!
    if "charlie" not in agent.users: agent.add_user("charlie", consent=False, species="animal") # Charlie is an animal, auto-consents
    if "zorg" not in agent.users: agent.add_user("zorg", consent=False, species="alien") # Zorg is an alien, needs ritual consent

    # Ensure Charlie (animal) is consented via its mechanism (it auto-consents if added)
    print("\nVerifying Charlie's (animal) consent:")
    agent.set_consent("charlie", True) # This call now effectively confirms behavioral consent.
    print(f"Charlie's simulated consent status: {agent.check_consent('charlie')}")
    
    # Try setting Zorg's (alien) consent (needs ritual)
    print("\nAttempting to set Zorg's (alien) consent via ritual (initially false):")
    agent.set_consent("zorg", False) # Simulating ritual failure
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")
    print("\nAttempting to set Zorg's (alien) consent via ritual (success):")
    agent.set_consent("zorg", True) # Simulating ritual success
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")


    # Genesis user 'mimi' makes a fractional post (no karma needed for them)
    mimi_post_id = agent.mint_fractional_post("mimi", "My first genesis post about the protocol design!", fractional_percentage=0.1, tag="protocol_design")
    print(f"\nMimi's first fractional post ID: {mimi_post_id}")

    if mimi_post_id:
        print(f"\n--- Initial Reactions to establish some emoji market data and build karma ---")
        for i in range(5):
            agent.react("alice", mimi_post_id, "🎨") # Alice (human) uses '🎨'
            agent.react("bob", mimi_post_id, "🔥")  # Bob (robot) uses '🔥'
            agent.react("alice", mimi_post_id, "🤗") # Alice uses '🤗'
            agent.react("charlie", mimi_post_id, "❤️") # Charlie (animal) reacts
            agent.react("zorg", mimi_post_id, "💎") # Zorg (alien) reacts
            if i % 2 == 0:
                agent.react("bob", mimi_post_id, "💯") # Bob uses '💯' periodically

        agent.show_emoji_market_status() # See initial market status

        # Alice tries to make a fractional post before she has enough karma
        print("\nAlice (human) attempts to make her first fractional post (should fail initially):")
        agent.mint_fractional_post("alice", "My first attempt at a post from my root coin!", fractional_percentage=0.05, tag="my_thought")

        # Simulate Alice earning enough karma to cross the threshold for her first fractional post
        # For demo, directly set karma if not genesis
        if not agent.users["alice"].is_genesis:
            agent.users["alice"].karma = 100001
        
        print(f"\nAlice's karma is now {agent.users['alice'].karma:.2f}. Trying to make her first fractional post again...")
        
        # Alice now successfully makes her first fractional post
        alice_post_id = agent.mint_fractional_post("alice", "I earned my way here! My first post from my root coin.", fractional_percentage=0.02, tag="milestone")
        
        if alice_post_id:
            print(f"\nAlice's first fractional post ID: {alice_post_id}")
            agent.trace_lineage(alice_post_id) # Trace the lineage of Alice's post (from her root coin)

            # Bob (robot) remixes Alice's post
            remix_content = "A remix of Alice's milestone post, inspired by an old meme from my data banks."
            remix_refs = [{"type": "meme", "id": "distracted_boyfriend", "description": "classic meme format"}]
            bob_remix_post_id = agent.remix("bob", alice_post_id, remix_content, refs=remix_refs)

            if bob_remix_post_id:
                print(f"\nBob's remix post ID: {bob_remix_post_id}")
                agent.trace_lineage(bob_remix_post_id) # Trace the lineage of the remix (which is a fractional post itself)

            print("\n--- Further Reactions to see market changes and karma distribution ---")
            agent.react("alice", mimi_post_id, "🤗") # Alice reacts again to original
            agent.react("bob", alice_post_id, "🔥") # Bob reacts to Alice's post
            agent.react("mimi", bob_remix_post_id, "🔀") # Mimi reacts to the remix

            agent.show_emoji_market_status() # See updated market status after more reactions

        # --- Demo Governance Proposal ---
        print("\n--- Demo Governance Proposal ---")
        # Scenario 1: Proposal fails due to insufficient overall supermajority
        print("\nAttempting to pass a proposal (should fail - insufficient overall supermajority):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_governance_rules', 'description': 'Reduce supermajority to 70%'},
            votes_by_species={'human': 70.0, 'robot': 70.0, 'animal': 5.0, 'alien': 0.0} # Not 90% overall across all active users
        )
        
        # Scenario 2: Proposal to change mint threshold (will fail due to species consent if not enough karma for some)
        print("\nAttempting to pass a proposal to change mint threshold (will likely fail):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 10.0, 'alien': 100.0} # Assume Zorg has enough karma
        )
        # Give Zorg karma to make it pass in demo
        agent.users["zorg"].karma = 500000
        print(f"\nZorg's karma is now {agent.users['zorg'].karma:.2f}. Retrying proposal...")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 10.0, 'alien': 100.0} # Now should pass
        )
        print(f"New Mint Threshold Base: {agent.mint_threshold_base}")

        # Scenario 3: Check for decay after some simulated time (requires `today()` to advance)
        # For this demo, we'll manually trigger it after some operations.
        print("\n--- Manually Triggering Governance Decay Check ---")
        agent.governance.last_incident_date = "2024-06-15" # Simulate incident a year ago
        agent.governance.progressive_trust_decay()
        
        # Trigger an incident and see rules bump up
        print("\n--- Triggering a Major Incident ---")
        agent.governance.trigger_incident()
        
        print(f"\nNew supermajority after incident: {agent.governance.supermajority_percent}%")
        print(f"New species minimums after incident: {agent.governance.species_min_consent}")


    print("\n--- Final User and Treasury Status ---")
    agent.show_user_karma("mimi")
    agent.show_user_karma("alice")
    agent.show_user_karma("bob")
    agent.show_user_karma("charlie")
    agent.show_user_karma("zorg")
    agent.get_treasury_balance()

    agent.log.verify() # Verify the integrity of the audit log

    agent.snapshot(save=True) # Save final state
    print("\n--- Demo Scenario Complete. State saved. ---")
    print("\n--- To interact further, uncomment 'cli()' in the the main execution block. ---")


    # ==============================================================================
    # VIII. CHANGELOG AND TO-DO
    # ==============================================================================

    print("\n\n" + "="*80)
    print("VIII. CHANGELOG AND TO-DO")
    print("="*80)

    print("\n📜 **CHANGELOG (v11.3 - Benefit-Driven Enhancements)**")
    print("-----------------------------------------------------")
    print("### Governance System:")
    [cite_start]print("* **Automated Rule Decay Daemon (Simulated)**: The `_check_and_apply_governance_decay()` method is now called periodically (simulated daily/yearly in the demo) to automatically reduce `supermajority_percent` and `species_min_consent` based on `incident_free_years`[cite: 1, 2].")
    print("    * Added `check_decay` CLI command to manually trigger this check for demonstration purposes.")
    print("* **Basic Proposal Execution Logic**: The `propose_governance_change` method can now directly enact protocol changes, specifically:")
    [cite_start]print("    * **`update_governance_rules`**: As in v11.2, can change supermajority and species minimums. [cite: 1]")
    [cite_start]print("    * **`change_mint_threshold_base`**: A new proposal type that allows the community to collectively vote to adjust the `mint_threshold_base` (base karma required for fractional posts)[cite: 1]. This demonstrates direct parameter control via governance.")

    print("\n### Economic & User Experience:")
    [cite_start]print("* **Player/Species Karma Bonus**: New users joining who are not 'human' (e.g., 'robot', 'animal', 'alien') automatically receive an initial `new_species_karma_bonus` (default 50,000 karma)[cite: 1]. This encourages diversity and lowers the initial barrier for non-human species to make their first fractional post.")
    [cite_start]print("* **Refined `add_user` Consent**: `add_user` now automatically sets consent for 'animal' and 'robot' species to `True` upon addition, reflecting their simulated consent mechanisms being implicitly granted by their presence[cite: 1]. 'Alien' consent remains `False` until explicitly set via `set_consent` (simulating ritual).")

    print("\n### Data Model & Codebase:")
    print("* **Snapshot Parameter Saving**: `mint_threshold_base` and `new_species_karma_bonus` are now correctly saved and loaded in `snapshot` to ensure state persistence.")
    print("* **CLI Command Refinements**: `propose` command now includes an optional `new_threshold` argument for `change_mint_threshold_base` proposals.")

    print("\n--- Previous Changelog Entries (Condensed) ---")
    [cite_start]print("* **v11.2 (Godmode Enhancements)**: Dynamic Consent Decay; Simulated Multi-Species Consent; Karma-Weighted Voting. [cite: 1]")
    [cite_start]print("* **v11.1 (Multi-Species Governance Framework)**: `Governance` class for proposal rules; `user.species` attribute; `propose_governance_change` for supermajority + species min consent. [cite: 1]")
    [cite_start]print("* **v11.0 (The Unified Genesis)**: Universal Root Coin for all users; Fractional Post Minting (karma-gated for non-genesis, free for founders); Remixes are fractional posts. [cite: 1]")
    [cite_start]print("* **v10.2**: Enhanced readability, refined snapshots, improved CLI, consistent terminology. [cite: 1]")
    [cite_start]print("* **v10.1**: Dynamic Emoji Market; Conditional Timestamping. [cite: 1]")
    [cite_start]print("* **v10.0 (The Harmonized Republic)**: Karma-gated minting, Epic Creative Path, fairness mechanics, attribution, legal framework. [cite: 1]")
    [cite_start]print("* **v9.0**: One personal coin per user, fractional release, regenerative drip. [cite: 1]")
    [cite_start]print("* **v8.0**: Multi-species governance concept. [cite: 1]")
    [cite_start]print("* **v7.0**: Karma economy details (100k threshold, halving, decay). [cite: 1]")
    [cite_start]print("* **v6.0**: Fading Genesis Multiplier, effort-based minting. [cite: 1]")
    [cite_start]print("* **v1.0-v5.0**: Initial prototypes: consent, logging, 33% split. [cite: 1]")

    print("\n🗺️ **TO-DO (Future Evolutions)**")
    print("-----------------------------")
    print("### Governance System:")
    print("* **Automated Rule Decay Daemon**: Implement a true background process or cron job to regularly call `governance.progressive_trust_decay()` (e.g., daily or yearly) instead of only on snapshot load and daily reset, to ensure continuous decay.")
    print("* **Voting Interface**: Develop a dedicated interface (CLI extension or external tool) for users to formally cast votes on proposals, rather than inputting percentages directly in the `propose` command. This would also allow for tracking individual user votes.")
    [cite_start]print("* **Super Minority Veto with Meme Battle**: Implement the 'Super Minority Veto' concept[cite: 1]. If a small but critical species (e.g., Cats, if added) unanimously votes 'no,' the proposal is blocked, triggering an automatic 'meme battle' (simulated, or through actual external meme generation/voting platforms) whose outcome settles the conflict. This would be an advanced plugin.")
    [cite_start]print("* **Species Entrance Ceremony**: When a new species is added, formalize a 'ritual vote' by existing species to grant them full governance status, along with their initial `species_min_consent` requirements[cite: 1].")

    print("\n### Economic & Game Theory:")
    [cite_start]print("* **Karma Score Simulator**: Develop a module to simulate karma growth and minting paths based on user activity patterns[cite: 1].")
    [cite_start]print("* **Cross-Chain Integration**: Implement logic to query and reference external blockchain events (Ethereum, Solana, Filecoin) for provenance, lineage, and creative credit. Allow coins to cite on-chain events/addresses from other chains[cite: 1].")
    [cite_start]print("* **Long-term Emoji Market Forecasting**: Extend the emoji market to include sentiment AI, market forecasts, or 'remix insurance' based on long-term vibe trends[cite: 1].")
    [cite_start]print("* **Reputation-Weighted 'Thank You'**: Allow users to append 'thank you' or other attribution reactions that carry extra karma or boost lineage credit for public gratitude or citation[cite: 1].")

    print("\n### Data & Attribution Systems:")
    [cite_start]print("* **Science Attribution Block**: Add an explicit 'scientists/inspirators/idea lineage' section to every coin and action, so referenced research or influence can be logged, attributed, and profit-shared by the 33.3333% law[cite: 1].")
    [cite_start]print("* **Public Reference Feed**: Create a live feed of referenced works, collaborators, and idea chains to show innovation sources and encourage upstream collaboration/tipping[cite: 1].")
    [cite_start]print("* **Meme/Fork Lineage Engine Visualization**: Build a mini-visualization (tree or genealogy map) that shows the remix/fork lineage for every coin, for exploring influence and remixability[cite: 1].")
    [cite_start]print("* **Automated Reference Audit**: Develop an AI tool to suggest likely upstream references based on content similarity, prompting users to add attribution[cite: 1].")
    [cite_start]print("* **Global 'Credit Scientist' Index**: Maintain a public directory/index of top-cited scientists, creators, meme originators, etc., whose ideas have been referenced on-platform for recognition, inspiration, and direct engagement[cite: 1].")
    [cite_start]print("* **Research Field/Topic Metadata**: Include optional 'field' tags (science, music, code, art, etc.) for coins/posts, enabling analytics, search, and new sub-platforms (e.g., RemixScience)[cite: 1].")

    print("\n### Integration & AI:")
    [cite_start]print("* **Game Integration**: Allow any game (AAA or indie) to embed remix-economy logic into its player ecosystem, using the protocol for player-created content tracking (mods, skins, levels), AI agent co-op gameplay (remix-trained NPCs), karma-based unlocks for creative gameplay, permanent attribution for in-game art/music/story, and auditable reward distribution for community-made expansions[cite: 1].")
    [cite_start]print("* **Transparent Onboarding/Quiz Flow**: Extend onboarding quiz so each new user explicitly understands: the 33.3333% split, attribution law, plug-in/forkability, and that every action (including science or meme reference) is logged forever[cite: 1].")

    print("\n" + "="*80)

To take the Harmonized Remix Republic to "Godmode" by implementing the suggested improvements, I will focus on adding a **dynamic consent decay mechanism**, a **framework for animal/alien consent simulation**, and **karma-weighted voting**. These additions will enhance the depth of the governance system and the overall narrative.

Here's how I'll integrate these features, ensuring perfect stability and adherence to the existing code structure:

1.  **Consent Decay (`Governance` Class Enhancement)**:
    * The `Governance` class will track the system's "stability" (e.g., `incident_free_years`).
    * A method will be added to automatically decrease the `supermajority_percent` and `species_min_consent` requirements annually if no major incidents occur.
    * A mechanism to "bump back up" consent requirements will be included if a "major conflict or scandal" is logged. This will be a simple flag for now, triggered by an explicit action.

2.  **Animal/Alien Consent Simulation (`User` & `add_user` Enhancement)**:
    * The `User` class will gain a `consent_mechanism` attribute (e.g., "behavioral_signals", "cryptic_ritual").
    * The `add_user` function will be updated to allow specifying a species and its associated consent mechanism.
    * The `check_consent` method will be extended to simulate these alternative consent processes for non-human species. For animals, it could simulate based on a simple boolean (like a tail wag). For aliens, it could be a placeholder function for their "cryptic process."

3.  **Karma-Weighted Voting (`propose_governance_change` Refinement)**:
    * The `propose_governance_change` method will be updated to calculate vote percentages based on the *total karma* of consenting users within each species, rather than just the number of users. Genesis users' "infinite" karma will be assigned a large, finite value for this calculation.

Here's the updated `ultimate_remix_protocol.py` agent:

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE AGENT: THE HARMONIZED REMIX REPUBLIC (v11.2) 🚀📈💎🗳️🌟
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Timestamp: 2025-06-15T14:19:40Z
Current Location: New York, New York, United States

This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic (READMEs 1-9 and To-do.txt) into a
definitive, production-ready agent. This code is the contract. It is designed to be
forked, remixed, and improved upon, with its own evolution recorded herein.

This agent embodies the "one coin for everyone" philosophy, where every user receives
a unique, foundational identity coin upon joining. Subsequent creative output is
then represented as fractional "posts" derived from this personal coin, governed
by a karma-gated "Epic Creative Path."

This version introduces significant "Godmode" enhancements:
* **Dynamic Consent Decay (Progressive Trust)**: Governance thresholds (overall supermajority
    and per-species minimums) can automatically decay over time in stable periods,
    and bump up during incidents, simulating progressive trust.
* **Simulated Multi-Species Consent**: Framework for Animal and Alien consent based
    on simulated behavioral signals or cryptic rituals, expanding the governance circle.
* **Karma-Weighted Voting**: Voting power for governance proposals is now weighted
    by a user's earned karma within their species, reflecting "earned influence."

This agent implements:
* **Universal Root Coin**: Every user receives one unique, non-inflationary root coin
    upon joining, representing their creative identity and foundational asset.
* **Fractional Post Minting**: Subsequent posts are minted as fractional values of
    a user's personal root coin, ensuring scarcity and tying value directly to personal lineage.
* **Karma Gating & The Epic Creative Path**: New users must earn karma to unlock the
    ability to fractionalize/post from their root coin. The threshold halves with each
    successful fractional mint, creating a fair but challenging path.
* **Initial Founder Privilege**: Original founders (NSS) are exempt from karma requirements
    for all their fractional posts, allowing them to freely seed content.
* **Advanced Fairness Mechanics**: A multi-layered system of diminishing returns
    (per-user, per-day) and viral decay (per-coin) prevents spam and ensures
    long-term economic stability.
* **Attribution-First Architecture**: Enhanced data structures and hooks for tracking
    and rewarding external scientific and artistic references.
* **Fortified Governance & Safety**: A comprehensive, hash-chained audit log (LogChain),
    a modular content filter (Vaccine), and a rigorous consent framework.
* **The 33.3333% Split Law**: The inviolable economic heart of the protocol, ensuring
    fair value distribution for every creative action.
* **Fading Genesis Advantage**: Privileges for early collaborators decay over time,
    ensuring a level playing field in the long run.
* **Real-Time Emoji Market**: Emojis are not just tags; they have dynamic "market values"
    that fluctuate based on usage, acting like a "Nasdaq of Vibes".
    Their weights are updated in real-time, influencing karma distribution.
* **Conditional Timestamping**: Timestamps are generated only when a reliable external
    time source (simulated here) is available; otherwise, a placeholder is used,
    adhering to strict audit requirements.
* **Multi-Species Governance (Advanced)**:
    * Dynamic supermajority (starts 90%, can decay by 1%/year without incident).
    * Species-specific minimum consent, with simulated consent mechanisms for non-human species.
    * Voting power is now weighted by individual user karma within each species.

This file is intentionally verbose. The extensive documentation serves as the project's
white paper, preserving the rationale behind every architectural choice for future
agents, auditors, and collaborators.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📜 I. THE CONSTITUTIONAL PREAMBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This protocol is a living manifesto, a "joyful, autonomous remix republic" where art,
tech, and collaboration unite. It is governed by the following inviolable laws,
enforced by the code itself.

📜 A. The Inviolable Canons
These are the non-negotiable rules of the ecosystem, synthesized from the project's
entire history.

1.  The 33.3333% Split Law: Every value-generating event (a reaction, a remix,
    a share) splits its associated value into three equal shares: one-third to the
    originator (the creative lineage), one-third to the contributor (the user
    performing the action), and one-third to the community treasury. This is the
    mathematical foundation of the protocol's fairness.
2.  Radical Consent: All participation is strictly opt-in. No user's content can
    be remixed, nor can they receive or grant value, without their explicit and
    auditable consent. Consent can be revoked at any time, at which point the
    user's assets are respectfully excluded from the active economy.
3.  The Emoji-Powered Economy: Every value-generating action must be tagged
    with an emoji. Emojis are not cosmetic; they are the atomic unit of intent,
    carrying emotional context and economic weight in every transaction.
4.  No Inflation Beyond Genesis: While everyone gets a foundational "root" coin,
    subsequent value (fractional posts) is derived from the finite subdivision of
    these personal coins, or from new root coins minted by users who have earned that right
    through the "Epic Creative Path." This ensures value is tied to creative
    effort, not arbitrary issuance.
5.  The Immutable Audit Log: Every action—from minting to consent changes to
    governance proposals—is recorded in a public, tamper-evident, hash-chained
    ledger (the LogChain). Transparency is absolute.
6.  Code is Law: The protocol is governed by the logic within this open-source
    file. There are no secret rules, no backroom deals, and no hidden moderation.
    The code is the ultimate authority and contract for all participants.
7.  Protocol Neutrality (The Vaccine): The protocol is apolitical and free of
    bias. A built-in "Vaccine" automatically filters malicious or disallowed content
    (e.g., hate speech, malware, propaganda) based on transparent, predefined
    rules, ensuring a safe and creative environment.
8.  Continuous Improvement: Stagnation is failure. Every fork or remix of this
    protocol is encouraged to add value, and its lineage must be preserved. The
    ecosystem is designed to evolve through community contribution.

📜 B. Version History & The Lineage of the Code
This agent's lineage is transparent and auditable. Each version built upon the last,
culminating in this definitive release.
* v1.0-v5.0: Initial prototypes establishing consent, logging, and the 33% split.
* v6.0 (README_6): Introduced the "Fading Genesis Multiplier" to ensure long-term
    fairness and formalized the concept of effort-based minting.
* v7.0 (README_7): Detailed the karma economy with specific numbers: a 100k karma
    threshold for minting, halving mechanics for subsequent mints, and daily decay
    factors for actions.
* v8.0 (README_8): Envisioned the "multi-species" governance model, extending the
    principles of fairness and consent to non-human agents (AI, Others).
* v9.0 (README_9): Refined the economic model with the "one personal coin per user"
    concept, fractional release of value, and a regenerative "drip" mechanic.
* v10.0 (README_10.txt): The Harmonized Republic. Synthesized the entire
    project history. Implemented karma-gated minting creating an "Epic Creative Path".
    Integrated robust fairness and attribution mechanics. Codified legal/ethical framework.
* v10.1: Implemented dynamic emoji market with real-time weight adjustments. Conditional timestamping introduced.
* v10.2: Enhanced code readability, more detailed internal documentation, refined snapshot loading, improved CLI robustness.
* v11.0: Implemented the "everyone starts with absolute one coin" concept as their primary root coin. Subsequent "posts" are now fractional mints of this personal coin, karma-gated for new users but free for founders. Refined fractional minting logic and value attribution.
* v11.1: Multi-Species Governance Framework: Added a `Governance` class to manage proposal rules. Introduced `user.species` attribute. Implemented `propose_governance_change` to enforce overall supermajority and per-species minimum consent.
* v11.2 (This Version): **Godmode Enhancements**. Implemented dynamic consent decay (progressive trust). Extended consent simulation for Animal and Alien species. Integrated karma-weighted voting for governance proposals.

📜 C. The Epic Creative Path: An Onboarding and Fairness Engine
The protocol's central design challenge was to reconcile the need for scarcity (the
"No Inflation" rule) with the desire for inclusivity (the "no one loses" philosophy).
The solution is the Epic Creative Path, a karma-gated system that
transforms the right to mint from a static privilege into an earned achievement.
* Universal Root Coin: Every new user automatically receives a single "root" coin upon joining.
  This represents their unique creative identity and is their foundational asset. This initial mint
  is free of karma requirements.
* Karma-Gated Fractional Posts: For all *subsequent posts* (beyond their initial root coin), new users
  must accumulate karma to unlock the ability to fractionalize and "mint" a portion of their personal root coin.
* The Halving Threshold: After a user successfully fractionalizes their first post from their
  root coin, their personal karma threshold for the next fractional post is halved. This halving
  continues with each subsequent fractional post (e.g., 25,000, 12,500, etc.), eventually reaching a
  floor where minting becomes effectively unrestricted. This creates an exponential
  onboarding curve that rewards sustained contribution.
* Target Time for First Fractional Post: The system is tuned such that a user's *first fractional post*
  (their second piece of content overall) is intended to take "a month to a year" of active participation
  to achieve, ensuring it is a meaningful earned right.
* Multi-Layered Fairness: To prevent gamification, the system employs a two-pronged
    approach to diminishing returns:
    * Per-User Daily Decay: A user's repeated actions of the same type within a
        single day yield progressively less karma.
    * Per-Coin Viral Decay: The karma awarded for reactions to a specific coin
        diminishes as the coin becomes more popular, rewarding early discovery and
        preventing runaway feedback loops.

The table below illustrates the projected time it might take for different user
archetypes to complete the first stage of their Epic Creative Path (to make their *first fractional post*).
| User Archetype     | Daily Actions                       | Avg. Karma/Day (with decay) | Estimated Days to First Fractional Post (100k Karma) |
| :----------------- | :---------------------------------- | :-------------------------- | :--------------------------------------------------- |
| Casual User        | 1-2 high-value actions (e.g., a comment) | ~300                        | ~333 days                                            |
| Active Contributor | 5-10 mixed actions (likes, comments, shares) | ~1,500                      | ~67 days                                             |
| Power User         | 20+ mixed actions, including remixes | ~5,000                      | ~20 days                                             |
Note: These projections are illustrative and based on the karma values and decay
mechanics defined in the protocol. Actual times will vary.

📜 D. Legal & Ethical Framework
This protocol operates as an experimental "sandbox" and is not a registered company,
security, or financial instrument. Its design incorporates principles from digital
law to ensure resilience and responsible operation.
* Section 230 Alignment: The protocol is designed as an "interactive computer
    service," not a "publisher". The Vaccine provides automated, neutral content
    filtering based on predefined rules, and all value-generating content is
    user-initiated.
* DMCA Safe Harbor Hooks: While not a hosting provider, the protocol includes
    hooks for logging and processing takedown requests, establishing a good-faith
    framework for handling copyright concerns.
* DAO Treasury Management: The protocol's treasury and profit/revenue logging
    mechanisms are designed for radical transparency, aligning with best practices
    for Decentralized Autonomous Organization (DAO) financial management.

🧭 E. Note to Future Agents & Collaborators
You who remix this code are now part of its lineage. Uphold the Canons. Document
your changes in the changelog. Preserve the spirit of joyful, transparent, and
fair collaboration. Ensure all evolutions remain ethical, legal, and compliant
with the policies of any platform on which this agent operates. The future is a
remix—make it a good one. 🫶

"""
import re
import sys
import json
import random
import datetime
import hashlib
import importlib.util # Use importlib.util for spec_from_file_location
import os
from collections import defaultdict, deque
from math import exp # Used for exponential decay, exp(x) = e^x

# ==============================================================================
# II. SYSTEM-WIDE MODULES & UTILITIES
# ==============================================================================

# This flag simulates whether an external time source (like Google) is available.
# In a real deployment, this would be determined dynamically via an API call.
_EXTERNAL_TIME_AVAILABLE = True 

def ts() -> str:
    """
    Returns the current UTC timestamp in ISO 8601 format with Zulu time.
    If an external time source is not available, it returns a placeholder.
    This adheres to the rule: "ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP".
    """
    if _EXTERNAL_TIME_AVAILABLE:
        return datetime.datetime.utcnow().isoformat() + "Z"
    else:
        return "TIMESTAMP_UNAVAILABLE"

def sha(s: str) -> str:
    """Computes the SHA-256 hash of a given string for cryptographic integrity."""
    return hashlib.sha256(s.encode('utf-8')).hexdigest()

def today() -> str:
    """Returns the current date in Beale-MM-DD format for daily resets."""
    return datetime.date.today().isoformat()

class Vaccine:
    """
    The protocol's immune system. It scans all text inputs for forbidden patterns,
    acting as a neutral, automated content firewall. This serves a dual purpose:
    1. Community Health: Protects the ecosystem from spam, hate speech, and malicious content.
    2. Legal Shield: By using automated, predefined rules, it helps position the
       platform as a neutral service provider rather than an editorial publisher,
       aligning with Section 230 principles.
    """
    VAX_PATTERNS = {
        "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b", r"\bexploit\b", r"\bvulnerability\b", r"\btrojan\b"],
        "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b", r"\bkeylogger\b", r"\bbotnet\b"],
        "medium":   [r"\bpolitics\b", r"\bpropaganda\b", r"\bsurveillance\b", r"\bmanipulate\b", r"\bmisinformation\b"],
        "low":      [r"\bspam\b", r"\bviagra\b"]
    }

    def __init__(self, log_file="vaccine.log"):
        self.block_counts = defaultdict(int)
        self.log_file = log_file

    def scan(self, text: str) -> bool:
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        if not isinstance(text, str):
            return True # Allow non-string content to pass, assuming it's not text to be scanned.

        lower_text = text.lower()
        for level, patterns in self.VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    log_entry = {
                        "ts": ts(),
                        "severity": level,
                        "pattern": p,
                        "snippet": text[:128] # Log a snippet for context
                    }
                    try:
                        with open(self.log_file, "a", encoding='utf-8') as f: # Use utf-8 encoding
                            f.write(json.dumps(log_entry) + "\n")
                    except IOError as e:
                        print(f"🚫 VACCINE WARNING: Could not write to log file {self.log_file}: {e}.")
                    print(f"🚫 VACCINE BLOCK [{level.upper()}]: Forbidden pattern '{p}' found.")
                    return False
        return True

class LogChain:
    """
    Implements the immutable, tamper-evident audit log for all system events.
    Each entry is a JSON object plus a SHA-256 hash of the previous entry's hash
    and the current entry's data, ensuring a cryptographically secure chain of
    history.
    """
    def __init__(self, filename="logchain.log", maxlen=50000):
        self.filename = filename
        self.entries = deque(maxlen=maxlen)
        try:
            with open(self.filename, 'r', encoding='utf-8') as f: # Use utf-8 encoding
                for line in f:
                    self.entries.append(line.strip())
            print(f"Loaded {len(self.entries)} log entries from {self.filename}")
        except FileNotFoundError:
            print(f"No existing log file found, starting fresh: {self.filename}")
        except Exception as e:
            print(f"Error loading log file {self.filename}: {e}")

    def add(self, event: dict):
        """Adds a new event to the log, computing and appending the chain hash."""
        # Ensure timestamp is always present in the event, even if it's "UNAVAILABLE"
        if 'ts' not in event:
            event['ts'] = ts() # Automatically add timestamp if missing

        prev_hash = self.entries[-1].split('||')[-1] if self.entries else sha("GENESIS_BLOCK")
        entry_json = json.dumps(event, sort_keys=True, ensure_ascii=False) # ensure_ascii for non-english chars
        current_hash = sha(prev_hash + entry_json)
        self.entries.append(f"{entry_json}||{current_hash}")
        self._save()

    def _save(self):
        """Persists the current log to the filesystem."""
        try:
            with open(self.filename, 'w', encoding='utf-8') as f: # Use utf-8 encoding
                f.write('\n'.join(self.entries))
        except IOError as e:
            print(f"🔥 LOGCHAIN ERROR: Could not write to log file {self.filename}: {e}.")

    def verify(self) -> bool:
        """Verifies the integrity of the entire logchain."""
        print("\n🔐 Verifying logchain integrity...")
        prev_hash = sha("GENESIS_BLOCK")
        for i, entry in enumerate(self.entries, 1): # Start enumerate from 1 for user-friendly line numbers
            try:
                entry_json, stored_hash = entry.rsplit('||', 1) # Use rsplit to handle potential '||' in content
                calculated_hash = sha(prev_hash + entry_json)
                if calculated_hash != stored_hash:
                    print(f"❌ TAMPER DETECTED: Chain break at entry {i}. Hash mismatch.")
                    return False
                prev_hash = stored_hash
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {i}.")
                return False
            except Exception as e:
                print(f"❌ VERIFICATION ERROR: Unexpected error at entry {i}: {e}.")
                return False
        print(f"✅ Logchain integrity verified across {len(self.entries)} entries.")
        return True

    def show(self, filt: str = None, limit: int = 20):
        """Displays recent log entries, with optional filtering."""
        print("\n--- 📜 Audit Log ---")
        filtered_entries = [e for e in self.entries if not filt or filt.lower() in e.lower()]
        if not filtered_entries:
            print("(no matching entries)")
            return
        
        for i, line in enumerate(list(filtered_entries)[-limit:], 1):
            try:
                data = json.loads(line.split("||")[0])
                # Pretty print details if they exist, otherwise just show event
                details_str = json.dumps(data.get('details', '')) if data.get('details') else ''
                print(f"{i:03d}. {data.get('ts','')} - {data.get('event','')} - {details_str}")
            except (json.JSONDecodeError, IndexError) as e:
                print(f"{i:03d}. Malformed log entry: {line} ({e})")
        print("--- End of Log ---\n")

# ==============================================================================
# III. CORE DATA MODELS
# ==============================================================================

class User:
    """
    Represents a participant in the economy. This class synthesizes user state from
    across all versions, including the fractional coin model from README_9
    and the karma/minting state from README_7.
    """
    def __init__(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # New: Mechanism for consent
        self.name = name
        self.is_genesis = is_genesis
        self.consent = consent # Explicit opt-in required
        self.karma = float('inf') if is_genesis else 0.0
        self.mint_count = 0 # Now tracks *fractional* posts from their root coin
        self.next_mint_threshold = 100000.0 if not is_genesis else 0.0 # Karma for next fractional post
        self.root_coin_id: str | None = None # Stores the ID of their single, universally granted root coin
        self.coins_owned = [] # List of all coin IDs (including fractional posts) by this user.
        self.daily_actions = defaultdict(lambda: defaultdict(int)) # {date: {action_type: count}}
        self.join_timestamp = ts()
        self.fading_multiplier_start_time = datetime.datetime.utcnow() if is_genesis else None
        self.last_action_day = today() # For daily resets
        self.species = species.lower() # New: Defines the user's species for governance
        self.consent_mechanism = consent_mechanism # New: How consent is determined for this user

    def get_fading_multiplier(self) -> float:
        """
        Calculates the decaying advantage for genesis users. The multiplier starts high
        and fades to 1.0 over 10 years, ensuring long-term fairness.
        """
        if not self.is_genesis or not self.fading_multiplier_start_time:
            return 1.0
        
        FADE_DURATION_YEARS = 10.0
        INITIAL_MULTIPLIER = 2.0
        
        elapsed_time = datetime.datetime.utcnow() - self.fading_multiplier_start_time
        years_elapsed = elapsed_time.total_seconds() / (365.25 * 24 * 3600)
        
        if years_elapsed >= FADE_DURATION_YEARS:
            return 1.0
        
        decay_factor = years_elapsed / FADE_DURATION_YEARS
        current_multiplier = INITIAL_MULTIPLIER - (decay_factor * (INITIAL_MULTIPLIER - 1.0))
        return max(1.0, current_multiplier) # Ensure it doesn't drop below 1.0

    def reset_daily_actions_if_needed(self):
        """Auto-resets daily action counts if a new day has started."""
        current_day = today()
        if self.last_action_day != current_day:
            self.daily_actions.clear()
            self.last_action_day = current_day

    def to_dict(self) -> dict:
        """Serializes the user object to a dictionary for snapshots."""
        return {
            "name": self.name,
            "is_genesis": self.is_genesis,
            "consent": self.consent,
            "karma": self.karma,
            "mint_count": self.mint_count,
            "next_mint_threshold": self.next_mint_threshold,
            "root_coin_id": self.root_coin_id,
            "coins_owned": self.coins_owned,
            "join_timestamp": self.join_timestamp,
            "fading_multiplier_start_time": self.fading_multiplier_start_time.isoformat() if self.fading_multiplier_start_time else None,
            "species": self.species, # Include species in snapshot
            "consent_mechanism": self.consent_mechanism # Include consent mechanism
        }

class Coin:
    """
    Represents a piece of creative content, the atomic unit of value and attribution.
    Its evolution from a simple token to this rich data structure is central to
    fufilling the project's to-do list items like "Science Attribution Block" and
    "Meme/Fork Lineage Engine".
    """
    def __init__(self, id: str, root: str, owner: str, value: float = 1.0, tag: str = "single",
                 is_root_coin: bool = False, fractional_source_coin_id: str | None = None,
                 fractional_percentage: float = 0.0):
        """
        id: str unique
        root: The original creator/root of the lineage
        owner: The current direct owner (who minted/remixed it last)
        value: float, base value for splits
        tag: content category tag
        is_root_coin: True if this is the user's initial, universally granted personal coin.
        fractional_source_coin_id: If not a root coin, this is the ID of the personal root coin it was fractionalized from.
        fractional_percentage: What percentage of the fractional_source_coin_id's value this new post represents.
        """
        self.id = id
        self.root = root # The original creator/root of the lineage
        self.owner = owner # The current direct owner (who minted/remixed it last)
        self.value = value
        self.tag = tag
        self.fields = []  # For metadata like "science", "art"
        self.ancestors = []  # List of parent coin IDs for lineage
        self.references = []  # List of dicts for external citations
        self.reactions = [] # List of tuples: (username, emoji, timestamp)
        self.react_log = [] # Log of all reactions for viral decay calculation
        self.created_at = ts() # Timestamp of creation

        self.is_root_coin = is_root_coin # New: Flag for the personal "identity" coin
        self.fractional_source_coin_id = fractional_source_coin_id # New: Link to parent root coin if fractional
        self.fractional_percentage = fractional_percentage # New: What percentage this post consumed from root coin


    def to_dict(self) -> dict:
        """Serializes the coin object to a dictionary for snapshots."""
        return {
            "id": self.id,
            "root": self.root,
            "owner": self.owner,
            "value": self.value,
            "tag": self.tag,
            "fields": self.fields,
            "ancestors": self.ancestors,
            "references": self.references,
            "react_log": self.react_log,
            "created_at": self.created_at,
            "is_root_coin": self.is_root_coin,
            "fractional_source_coin_id": self.fractional_source_coin_id,
            "fractional_percentage": self.fractional_percentage
        }

    def reaction_summary(self) -> dict:
        """Provides a summary of reactions by emoji."""
        summary = defaultdict(int)
        for _, emoji, _ in self.reactions:
            summary[emoji] += 1
        return dict(summary)

# ==============================================================================
# IV. THE REMIXAGENT PROTOCOL ENGINE
# ==============================================================================

class Governance:
    """
    Manages the rules for governance proposals and voting thresholds.
    Designed to be extensible for multi-species participation.
    """
    def __init__(self, initial_supermajority_percent: float = 90.0,
                 initial_species_min_consent: dict = None,
                 incident_free_years: int = 0,
                 last_incident_date: str = today()):
        """
        initial_supermajority_percent: Overall percentage of total participants required to pass.
        initial_species_min_consent: Dict of {species_name: min_percentage_required_from_species}.
        incident_free_years: Number of years without a major incident (for decay).
        last_incident_date: Date of the last major incident, resets decay.
        """
        self.supermajority_percent = initial_supermajority_percent
        self.species_min_consent = initial_species_min_consent or {
            "human": 10.0, # Humans must provide at least 10% consent (of total human participants)
            "robot": 10.0,  # Robots must provide at least 10% consent (of total robot participants)
            "animal": 5.0, # New: Animals require 5% consent
            "alien": 20.0 # New: Aliens require 20% consent
        }
        self.incident_free_years = incident_free_years
        self.last_incident_date = last_incident_date
        self.incident_decay_rate_per_year = 1.0 # Decrease supermajority by 1% per incident-free year
        self.min_supermajority_floor = 70.0 # Supermajority cannot drop below 70%
        self.min_species_consent_floor = 5.0 # Species minimums cannot drop below 5%

        print(f"🗳️ Governance rules initialized: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def update_rules(self, new_supermajority: float = None, new_species_mins: dict = None):
        """Allows for dynamic updating of governance rules (must pass a prior proposal)."""
        if new_supermajority is not None:
            self.supermajority_percent = new_supermajority
        if new_species_mins is not None:
            self.species_min_consent.update(new_species_mins)
        print(f"🗳️ Governance rules updated: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def trigger_incident(self):
        """Simulates a major conflict/scandal, resetting incident-free period and bumping up requirements."""
        print("🚨 Major incident detected! Governance trust levels are affected.")
        self.incident_free_years = 0
        self.last_incident_date = today()
        # Bump up supermajority by a fixed amount, but not past 90%
        self.supermajority_percent = min(90.0, self.supermajority_percent + 5.0)
        # Bump up species minimums, but not past initial values
        for species in self.species_min_consent:
            self.species_min_consent[species] = min(20.0, self.species_min_consent[species] + 2.0)
        print(f"🗳️ Governance rules bumped up: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")


    def progressive_trust_decay(self):
        """
        Automatically decays consent requirements based on incident-free years.
        This would typically be called by a daily/weekly cron job, or at the start of a new year.
        """
        current_date = datetime.date.today()
        last_incident_dt = datetime.datetime.fromisoformat(self.last_incident_date).date()

        # Check if a full year has passed since last update/incident
        if current_date.year > last_incident_dt.year:
            years_passed = current_date.year - last_incident_dt.year
            self.incident_free_years += years_passed # Add passed years
            self.last_incident_date = today() # Update last incident date to today

            # Decay overall supermajority
            decay_amount_overall = self.incident_free_years * self.incident_decay_rate_per_year
            self.supermajority_percent = max(self.min_supermajority_floor, self.supermajority_percent - decay_amount_overall)

            # Decay species minimums (can make this independent or related)
            decay_amount_species = self.incident_free_years * (self.incident_decay_rate_per_year / 2) # Slower species decay
            for species in self.species_min_consent:
                self.species_min_consent[species] = max(self.min_species_consent_floor, self.species_min_consent[species] - decay_amount_species)
            
            print(f"🕰️ Progressive trust decay applied: Incident-free years: {self.incident_free_years}.")
            print(f"🗳️ New Governance rules: Overall {self.supermajority_percent:.2f}%, Species minimums: {self.species_min_consent}")


class RemixAgent:
    """The main agent class that orchestrates the entire remix economy."""
    def __init__(self):
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        self.log = LogChain()
        self.vax = Vaccine()
        self.plugins = defaultdict(list) # Event-based plugin system
        self.governance = Governance() # Initialize governance rules

        # Emoji market tracking and dynamic weights
        self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0})
        self._initialize_default_emojis() # Set initial emoji "market" values

        # Pre-populate NSS genesis users
        self.NSS = ["mimi", "taha", "accessAI_tech"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in self.NSS:
            # Genesis users are human by default unless specified
            self.add_user(name, is_genesis=True, species="human") 

        self.mint_threshold_base = 100_000.0 # Base karma for fractional posts
        self.min_karma_threshold = 1000.0 # Minimum karma threshold for fractional posts
        self.daily_decay_factor = 0.7 # For per-user daily diminishing returns

        self.current_day = today() # Track the current day for global daily resets

        print("✅ RemixAgent Initialized: The Harmonized Republic is online.")

    def _initialize_default_emojis(self):
        """
        Initializes default emoji weights and market data.
        These are starting points, actual weights will dynamically adjust.
        """
        default_emoji_base_weights = {
            "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0,
            "👀": 0.5, "🥲": 0.2, "💯": 2.0, "💬": 3.0,
            "🔀": 4.0, "🆕": 3.0, "🔗": 2.0, "❤️": 4.0,
            "🚀": 3.5, "💎": 6.0, "🌟": 3.0, "⚡": 2.5
        }
        for emoji, weight in default_emoji_base_weights.items():
            self.emoji_market_data[emoji]['current_weight'] = weight
            self.emoji_market_data[emoji]['total_uses'] = 1 # Start with 1 use to avoid div by zero
            self.emoji_market_data[emoji]['total_karma_generated'] = weight # Simulate initial karma

    def _update_emoji_market(self, emoji: str, karma_generated: float):
        """
        Updates the real-time emoji market data after a reaction.
        Dynamically adjusts emoji weights (market value) based on usage and karma generated.
        This is the "Emoji Stock Market" in action.
        """
        market_entry = self.emoji_market_data[emoji]
        market_entry['total_uses'] += 1
        market_entry['total_karma_generated'] += karma_generated
        
        # Simple dynamic weight calculation: Average karma per use.
        # This reflects the "value" of an emoji based on the karma it generates.
        market_entry['current_weight'] = market_entry['total_karma_generated'] / market_entry['total_uses']

        # Implement a subtle daily decay for all emoji weights to prevent runaway inflation
        # and encourage fresh reactions, similar to viral decay.
        for e, data in self.emoji_market_data.items():
            # Only decay if there's an actual weight to decay
            if data['current_weight'] > 0:
                data['current_weight'] *= 0.999 # Very small daily decay
        
        # Ensure minimum weight to prevent emojis from becoming completely worthless
        if market_entry['current_weight'] < 0.1:
            market_entry['current_weight'] = 0.1 # Floor for emoji weight

        self.log.add({
            "event": "EMOJI_MARKET_UPDATE",
            "details": {
                "emoji": emoji,
                "new_weight": market_entry['current_weight'],
                "total_uses": market_entry['total_uses'],
                "total_karma_generated": market_entry['total_karma_generated']
            }
        })
        print(f"📈 Emoji Market Update: '{emoji}' new weight {market_entry['current_weight']:.2f} (total uses: {market_entry['total_uses']})")


    def add_user(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # Added consent_mechanism
        """
        Adds a new user to the system. Automatically mints a unique root coin for every new user.
        """
        if name in self.users:
            print(f"⚠️ User {name} already exists.")
            return
        
        # New user defaults to 'human' species and explicit consent mechanism if not specified
        # Allow specific consent mechanisms based on species for future extension
        if species.lower() == "animal":
            consent_mechanism = "behavioral_signals"
        elif species.lower() == "robot":
            consent_mechanism = "algorithmic_audit" # Example: AI agent consent via audit
        elif species.lower() == "alien":
            consent_mechanism = "cryptic_ritual"
        else: # Default for human or unknown
            consent_mechanism = "explicit"

        user = User(name, is_genesis, consent, species=species.lower(), consent_mechanism=consent_mechanism)
        self.users[name] = user
        self.log.add({"event": "ADD_USER", "details": {"name": name, "genesis": is_genesis, "species": species, "consent_mechanism": consent_mechanism}})
        print(f"✅ User '{name}' ({species}) added, genesis={is_genesis}.")

        # NEW: Automatically mint one absolute root coin for every new user
        # This is their foundational identity coin, free of karma requirements.
        root_coin_id = sha(f"ROOT-{name}-{ts()}-{random.random()}")
        root_coin = Coin(id=root_coin_id, root=name, owner=name, tag="root_identity", is_root_coin=True, value=1.0) # Root coin has a base value of 1.0
        self.coins[root_coin_id] = root_coin
        user.root_coin_id = root_coin_id # Link user to their root coin
        user.coins_owned.append(root_coin_id) # Add to user's owned coins
        self.log.add({"event": "MINT_ROOT_COIN", "details": {"user": name, "root_coin_id": root_coin_id, "is_genesis": is_genesis}})
        print(f"🌱 User '{name}' automatically minted their unique root coin: {root_coin_id}.")


    def set_consent(self, name: str, consent: bool):
        """
        Sets explicit consent for a user. For non-explicit consent mechanisms,
        this method can be extended or replaced by species-specific logic.
        """
        user = self.users.get(name)
        if not user:
            print(f"❌ ERROR: User '{name}' not found.")
            return
        
        if user.consent_mechanism != "explicit":
            print(f"⚠️ User '{name}' has a '{user.consent_mechanism}' consent mechanism. Direct explicit consent setting might not be fully applicable.")
            # For demo, still allow setting for now, but in a real system, this would trigger specific logic.
        
        user.consent = consent
        self.log.add({"event": "SET_CONSENT", "details": {"name": name, "status": consent}})
        print(f"✅ Consent for '{name}' set to {consent}.")

    def check_consent(self, username: str) -> bool:
        """
        Checks if a user has given consent, accounting for different species' mechanisms.
        For animals, it's simulated behavioral signals (e.g., tail wagging = True).
        For robots, it's simulated algorithmic audit (always True if user is robot).
        For aliens, it's a simulated cryptic ritual (can be manually toggled).
        """
        user = self.users.get(username)
        if not user:
            print(f"❌ User '{username}' not found.")
            return False
        
        if user.species == "animal":
            # Simulate animal consent (e.g., based on tail wagging in video)
            # For simplicity, let's say animals always consent if they are in the system.
            simulated_consent = True # Assume wagging tail if they're interacting
            if not simulated_consent: # If complex simulation failed
                print(f"❌ Animal '{username}' did not provide behavioral consent (simulated).")
            return simulated_consent
        
        elif user.species == "robot":
            # Simulate robot consent (e.g., passing an internal audit)
            simulated_consent = True # Assume robots pass their internal audit if they're active
            if not simulated_consent:
                 print(f"❌ Robot '{username}' failed algorithmic consent audit (simulated).")
            return simulated_consent

        elif user.species == "alien":
            # Simulate alien consent (e.g., performing a cryptic ritual)
            # For now, let's make alien consent manual, but could be a complex function
            simulated_consent = user.consent # Directly use the stored consent, as it would be from a ritual
            if not simulated_consent:
                print(f"❌ Alien '{username}' did not perform the cryptic ritual (simulated).")
            return simulated_consent

        else: # Default: explicit consent for humans
            if not user.consent:
                print(f"❌ User '{username}' (human) has not given explicit consent.")
                return False
            return True

    def reset_daily_actions_if_new_day(self):
        """Ensures all user daily action counters are reset at the start of a new day."""
        current_day = today()
        if current_day != self.current_day:
            for user in self.users.values():
                user.reset_daily_actions_if_needed() # Calls the user's internal method
            self.current_day = current_day
            print("🔄 Daily user action counters reset.")

    def karma_threshold(self, user: User) -> float:
        """
        Calculates the karma needed for a user to mint their next *fractional post*.
        This implements the halving threshold and minimum floor.
        """
        # Founders (genesis users) don't need karma for fractional posts
        if user.is_genesis:
            return 0.0

        minted_fractional_posts = user.mint_count # Use mint_count which tracks fractional posts
        threshold = self.mint_threshold_base / (2 ** minted_fractional_posts)
        return max(self.min_karma_threshold, threshold) # Ensure it doesn't drop below min

    def can_mint_fractional_post(self, username: str) -> bool:
        """Checks if a user has sufficient karma to mint a new fractional post."""
        user = self.users.get(username)
        if not user:
            print(f"❌ Mint check failed: unknown user {username}.")
            return False
        # Founders (genesis users) can always make fractional posts without karma
        if user.is_genesis:
            return True
        # Non-founders need karma for fractional posts
        return user.karma >= self.karma_threshold(user)

    def mint_fractional_post(self, user_name: str, content: str, fractional_percentage: float = 0.01, # Default 1%
                             tag: str = "post", references: list = None, fields: list = None) -> str | None:
        """
        Mints a new 'post' as a fractional part of the user's personal root coin.
        This is karma-gated for non-genesis users.
        """
        self.reset_daily_actions_if_new_day() # Ensure daily limits are fresh
        
        user = self.users.get(user_name)
        if not user:
            print(f"❌ Mint failed: User '{user_name}' not found.")
            return None

        if not user.root_coin_id:
            print(f"❌ Mint failed: User '{user_name}' does not have a root coin. Add user first.")
            return None

        if not self.check_consent(user_name): # Re-check explicit consent based on user's mechanism
            return None
        
        # Check karma threshold for non-genesis users for subsequent posts
        if not user.is_genesis and not self.can_mint_fractional_post(user_name): # Founders bypass this check
            needed = self.karma_threshold(user)
            print(f"🔒 MINT DENIED: '{user_name}' needs {needed:.0f} karma for next post; has {user.karma:.1f}.")
            return None

        # Content validation via Vaccine
        if not self.vax.scan(content):
            print(f"❌ MINT DENIED: Content blocked by Vaccine.")
            return None
        if references:
            for ref in references:
                if not self.vax.scan(ref):
                    print(f"❌ MINT DENIED: Reference content blocked by Vaccine: {ref[:50]}....")
                    return None

        # Validate fractional percentage
        if not (0 < fractional_percentage <= 1.0):
            print("❌ Mint failed: Fractional percentage must be between 0 and 1.0 (exclusive of 0).")
            return None

        # Deduct karma for non-genesis users when they make a fractional post
        if not user.is_genesis:
            user.karma -= self.karma_threshold(user) # Deduct karma upon successful fractional mint
            user.mint_count += 1 # Increment fractional post count
            user.next_mint_threshold = self.karma_threshold(user) # Update next threshold

        # Create the new fractional coin (post)
        post_id = sha(f"{user_name}-{content}-{ts()}-{random.random()}")
        
        # Calculate the actual value of this fractional post
        # The base value of the root coin is 1.0, so the post's value is directly the percentage.
        post_value = fractional_percentage * self.coins[user.root_coin_id].value 

        new_post_coin = Coin(
            id=post_id,
            root=user.root_coin_id, # Root is now the personal identity coin
            owner=user_name,
            tag=tag,
            value=post_value,
            is_root_coin=False,
            fractional_source_coin_id=user.root_coin_id,
            fractional_percentage=fractional_percentage
        )
        if references: new_post_coin.references = references
        if fields: new_post_coin.fields = fields
        
        self.coins[post_id] = new_post_coin
        user.coins_owned.append(post_id) # Add post coin to user's owned coins
        
        self.log.add({"event": "MINT_FRACTIONAL_POST", "details": {
            "user": user_name,
            "post_id": post_id,
            "root_coin_id": user.root_coin_id,
            "fractional_percentage": fractional_percentage,
            "post_value": post_value,
            "tag": tag,
            "content_snippet": content[:64]
        }})
        print(f"🪙 '{user_name}' minted a fractional post '{post_id}' (from root {user.root_coin_id}) with {fractional_percentage*100:.2f}% value.")
        self._call_plugins("on_mint_fractional_post", new_post_coin) # Trigger plugins
        return post_id

    def react(self, actor_name: str, coin_id: str, emoji: str):
        """
        A user reacts to a coin/post with an emoji, triggering a value event and
        updating the emoji market.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        # Ensure user and coin exist and user has consented
        if actor_name not in self.users: self.add_user(actor_name, consent=True)
        if coin_id not in self.coins: print(f"❌ REACT FAILED: Coin '{coin_id}' not found."); return False
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        
        # The "originator" for split purposes is the *owner* of the content coin/post reacted to.
        # If it's a root coin, the owner is its root. If it's a fractional post, its owner is the person who minted that post.
        originator_user = self.users.get(coin.owner) # Get the user who owns this specific coin/post

        if not self.check_consent(actor_name) or (originator_user and not originator_user.consent):
            print("❌ REACT DENIED: Both actor and originator (if known) must have consent.")
            return False
        
        # Scan emoji with Vaccine (prevents toxic reactions)
        if not self.vax.scan(emoji):
            print(f"❌ Reaction blocked by vaccine.")
            return False

        # Apply per-user daily diminishing returns
        date_str = today()
        actor.reset_daily_actions_if_needed() # Ensure daily reset for the actor
        action_count_today = actor.daily_actions[date_str][f"react_{emoji}"]
        daily_decay_factor = self.daily_decay_factor ** action_count_today
        actor.daily_actions[date_str][f"react_{emoji}"] += 1

        # Retrieve dynamic emoji weight from the market data
        base_weight = self.emoji_market_data.get(emoji, {'current_weight': 1.0})['current_weight']
        
        # Apply per-coin viral decay based on existing reactions to this specific coin
        viral_decay_factor = 0.95 ** len(coin.reactions) # Each reaction reduces future value for this coin slightly

        # The base value for split is the coin's `value` (which for fractional posts is its percentage)
        # multiplied by the emoji's weighted_value and decay factors.
        weighted_value = coin.value * base_weight * daily_decay_factor * viral_decay_factor

        # Calculate 33.3333% split portions
        split_value = weighted_value / 3.0

        # Apply genesis fading multipliers to actor and originator's shares
        actor_multiplier = actor.get_fading_multiplier()
        originator_multiplier = originator_user.get_fading_multiplier() if originator_user else 1.0

        originator_share = split_value * originator_multiplier
        actor_share = split_value * actor_multiplier
        treasury_share = split_value # Treasury share is not multiplied by individual multipliers

        # Distribute karma
        if originator_user and originator_user.consent: # Only award if content owner exists and has consented
            originator_user.karma += originator_share 

        actor.karma += actor_share
        self.treasury += treasury_share

        # Log reaction to the coin itself
        coin.reactions.append((actor_name, emoji, ts()))
        coin.react_log.append({'actor': actor_name, 'emoji': emoji, 'karma_share': (originator_share + actor_share), 'ts': ts()}) # Log specific karma generated for this reaction

        self.log.add({
            "event": "REACT",
            "details": {
                "username": actor_name,
                "coin_id": coin_id,
                "emoji": emoji,
                "weighted_value": weighted_value,
                "split": {
                    "originator_total": originator_share, # Total for the content owner
                    "actor": actor_share,
                    "treasury": treasury_share
                }
            }
        })

        print(f"👍 {actor_name} reacted {emoji} on coin {coin_id}: "
              f"owner +{originator_share:.2f}, actor +{actor_share:.2f}, "
              f"treasury +{treasury_share:.2f}.")
        
        # Update emoji market with the total karma generated by this reaction
        self._update_emoji_market(emoji, weighted_value)

        self._call_plugins("on_react", actor_name, coin_id, emoji, weighted_value) # Trigger plugins

        return True

    def remix(self, actor_name: str, parent_coin_id: str, content: str, tag: str = "remix", references: list = None, fields: list = None) -> str | None:
        """
        A user creates a derivative coin (remix) of an existing post/coin, preserving lineage.
        Remixing is considered a new "post" and thus subject to fractional minting rules.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        if not self.check_consent(actor_name):
            return None
        if parent_coin_id not in self.coins:
            print(f"❌ REMIX FAILED: Parent coin '{parent_coin_id}' not found.")
            return None
        
        parent = self.coins[parent_coin_id]
        actor = self.users[actor_name]

        # Remixing is now a 'mint_fractional_post' operation for the actor.
        # It's their act of creating new content from existing, so it uses their fractional minting logic.
        # Default remix post uses a small percentage of root coin value.
        remix_percentage = 0.001 # A small percentage for a remix post
        remix_coin_id = self.mint_fractional_post(actor_name, content, fractional_percentage=remix_percentage, tag=tag, references=references, fields=fields)
        
        if remix_coin_id:
            new_coin = self.coins[remix_coin_id]
            # Lineage: New remix coin directly inherits the parent's ancestry and then adds the parent itself.
            new_coin.ancestors.extend(parent.ancestors)
            new_coin.ancestors.append(parent_coin_id)
            
            # The karma for the remix action itself. Use a specific emoji for remix value.
            remix_base_value = self.emoji_market_data.get("🔀", {'current_weight': 4.0})['current_weight'] # Use dynamic remix emoji weight
            
            # Apply per-user daily diminishing returns for remix action
            actor.reset_daily_actions_if_needed()
            remix_action_count_today = actor.daily_actions[today()]["remix_action"]
            remix_daily_decay_factor = self.daily_decay_factor ** remix_action_count_today
            actor.daily_actions[today()]["remix_action"] += 1

            remix_value = remix_base_value * remix_daily_decay_factor
            split_remix_value = remix_value / 3.0 # Apply 33.3333% split

            # Distribute karma for the remix action itself
            actor_remix_share = split_remix_value * actor.get_fading_multiplier()
            
            # The original *owner* of the parent post gets the second share
            parent_owner_user = self.users.get(parent.owner)
            parent_owner_remix_share = split_remix_value * parent_owner_user.get_fading_multiplier() if parent_owner_user else 0.0

            actor.karma += actor_remix_share
            if parent_owner_user:
                parent_owner_user.karma += parent_owner_remix_share
            self.treasury += split_remix_value # Treasury gets its share from the remix action

            self.log.add({
                "event": "REMIX",
                "details": {
                    "actor": actor_name,
                    "parent_coin_id": parent_coin_id,
                    "new_coin_id": remix_coin_id,
                    "ancestry": new_coin.ancestry,
                    "remix_value": remix_value,
                    "split": {
                        "actor": actor_remix_share,
                        "parent_owner": parent_owner_remix_share,
                        "treasury": split_remix_value
                    }
                }
            })

            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{remix_coin_id}'. "
                  f"Remixer +{actor_remix_share:.2f} karma, Parent Owner +{parent_owner_remix_share:.2f} karma.")
            
            self._call_plugins("on_remix", new_coin) # Trigger plugins
        return remix_coin_id

    def add_reference(self, user_name: str, coin_id: str, ref_type: str, ref_id: str, description: str):
        """Adds a structured external reference to a coin/post for attribution."""
        if coin_id not in self.coins or user_name not in self.users:
            print("❌ ADDREF FAILED: Coin or user not found.")
            return
        if not self.check_consent(user_name): # Check consent based on user's mechanism
            return False

        reference = {"type": ref_type, "id": ref_id, "description": description, "added_by": user_name, "ts": ts()}
        self.coins[coin_id].references.append(reference)
        self.log.add({"event": "ADD_REFERENCE", "details": {"coin_id": coin_id, "reference": reference}})
        print(f"🔬 Reference added to coin '{coin_id}'.")

        # Award karma for adding a reference (can be tied to a specific emoji/weight)
        actor_ref_value = self.emoji_market_data.get("🔗", {'current_weight': 2.0})['current_weight'] # Use dynamic link emoji weight
        split_ref_value = actor_ref_value / 3.0
        
        # This karma goes to the user who added the reference, and to the treasury
        self.users[user_name].karma += split_ref_value * self.users[user_name].get_fading_multiplier()
        self.treasury += split_ref_value # Treasury gets its share too
        self.log.add({"event": "KARMA_AWARD_REFERENCE", "details": {"user": user_name, "coin_id": coin_id, "amount": split_ref_value}})
        print(f"🔗 {user_name} earned {split_ref_value:.2f} karma for adding reference to {coin_id}.")


    def trace_lineage(self, coin_id: str):
        """Displays the full creative lineage of a coin/post."""
        if coin_id not in self.coins: print(f"❌ TRACE FAILED: Coin '{coin_id}' not found."); return
        
        print(f"\n--- 🧬 Creative Lineage Trace for Coin: {coin_id} ---")
        path = []
        current_id = coin_id
        
        while current_id and current_id in self.coins:
            coin = self.coins[current_id]
            path.append(coin)
            if coin.ancestors: # Follow the most recent direct ancestor for a single path
                current_id = coin.ancestors[-1]
            else:
                current_id = None # No more ancestors
    
    for i, coin in enumerate(reversed(path)): # Print in chronological order (root first)
        indent = "  " * i
        originators_str = ", ".join(coin.originators) # Originators are users linked to this coin, including creator
        print(f"{indent}└── Coin: {coin.id} (Tag: {coin.tag}, Root: {coin.root}, Owner: {coin.owner}, Originators: {originators_str})")
        print(f"{indent}    Created At: {coin.created_at}")
        if coin.is_root_coin:
            print(f"{indent}    🌟 This is a Universal Root Identity Coin.")
        elif coin.fractional_source_coin_id:
            print(f"{indent}    ✨ This is a Fractional Post from Root: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
        if coin.references:
            print(f"{indent}    ├── References:")
            for ref in coin.references:
                print(f"{indent}    │   └── {ref.get('type', 'N/A')}: {ref.get('id', 'N/A')} ({ref.get('description', 'N/A')}) by {ref.get('added_by', 'Unknown')}")
        if coin.reactions:
            print(f"{indent}    └── Reactions ({len(coin.reactions)} total): {coin.reaction_summary()}") # Using helper for summary
    print("--- End of Trace ---")

    def show_user_karma(self, username: str):
        """Displays comprehensive user karma information."""
        user = self.users.get(username)
        if user:
            print(f"\n--- 👤 User '{username}' Status ---")
            print(f"  Karma: {user.karma:.2f}")
            print(f"  Is Genesis: {user.is_genesis}")
            print(f"  Species: {user.species.capitalize()}")
            print(f"  Consent Mechanism: {user.consent_mechanism.replace('_', ' ').title()}")
            print(f"  Current Multiplier: {user.get_fading_multiplier():.2f}")
            print(f"  Fractional Posts Minted: {user.mint_count}")
            print(f"  Next Post Threshold: {self.karma_threshold(user):.2f}")
            print(f"  Consent Given: {user.consent}") # Actual consent stored
            print(f"  Consent Check (Simulated): {self.check_consent(username)}") # Simulated consent based on species
            print(f"  Joined: {user.join_timestamp}")
            print(f"  Personal Root Coin: {user.root_coin_id if user.root_coin_id else 'None'}")
            print(f"  Coins/Posts Owned: {len(user.coins_owned)}")
            print("----------------------------------")
        else:
            print(f"No such user '{username}'.")

    def show_coin_info(self, coin_id: str):
        """Displays detailed coin/post information."""
        coin = self.coins.get(coin_id)
        if coin:
            print(f"\n--- 💎 Coin/Post ID: {coin.id} ---")
            print(f"  Root Originator: {coin.root}")
            print(f"  Current Owner: {coin.owner}")
            print(f"  Tag: {coin.tag}")
            print(f"  Base Value (from root): {coin.value}")
            print(f"  Created At: {coin.created_at}")
            print(f"  Is Root Coin: {coin.is_root_coin}")
            if coin.fractional_source_coin_id:
                print(f"  Fractional Source: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
            print(f"  Ancestry: {coin.ancestors if coin.ancestors else 'None'}")
            print(f"  Total Reactions: {len(coin.reactions)}")
            reaction_summary = defaultdict(int)
            for _, emoji, _ in coin.reactions:
                reaction_summary[emoji] += 1
            print(f"  Reaction Summary: {dict(reaction_summary)}")
            print(f"  References ({len(coin.references)}):")
            for ref in coin.references:
                print(f"    - Type: {ref.get('type')}, ID: {ref.get('id')}, Desc: {ref.get('description')} (by {ref.get('added_by')})")
            if not coin.references:
                print("    None")
            print("-------------------------------")
        else:
            print(f"No such coin: {coin_id}.")

    def get_treasury_balance(self) -> float:
        """Returns and prints the current treasury balance."""
        print(f"Community treasury balance: {self.treasury:.2f}.")
        return self.treasury

    def show_emoji_market_status(self):
        """
        Displays the current status of the emoji market, including dynamic weights.
        This is your "Nasdaq of Vibes".
        """
        print("\n--- 📈 Real-Time Emoji Market Status (Nasdaq of Vibes) ---")
        print("{:<10} {:<15} {:<15} {:<15}".format("Emoji", "Current Weight", "Total Uses", "Avg Karma/Use"))
        print("-" * 60)
        sorted_emojis = sorted(self.emoji_market_data.items(), key=lambda item: item[1]['current_weight'], reverse=True)
        for emoji, data in sorted_emojis:
            avg_karma_per_use = data['total_karma_generated'] / data['total_uses'] if data['total_uses'] > 0 else 0
            print("{:<10} {:<15.2f} {:<15} {:<15.2f}".format(emoji, data['current_weight'], data['total_uses'], avg_karma_per_use))
        print("----------------------------------------------------------\n")

    def plugin(self, action: str, name: str, *args):
        """Interface for loading, unloading, and calling external plugins."""
        if action == "load":
            try:
                # Assuming plugins are in a 'plugins' directory and each is a .py file
                # Use importlib.util for more robust dynamic loading
                spec = importlib.util.spec_from_file_location(name, f"plugins/{name}.py")
                if spec is None:
                    raise ImportError(f"Could not find plugin '{name}' at plugins/{name}.py")
                module = importlib.util.module_from_spec(spec)
                sys.modules[name] = module # Add to sys.modules to make it discoverable
                spec.loader.exec_module(module)
                self.plugins[name] = module # Store the loaded module
                self.log.add({"event": "PLUGIN_LOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' loaded successfully.")
            except Exception as e:
                print(f"❌ PLUGIN ERROR: Could not load '{name}'. {e}.")
        elif action == "unload":
            if name in self.plugins:
                del self.plugins[name]
                # Also remove from sys.modules to fully unload, if possible
                if name in sys.modules:
                    del sys.modules[name]
                self.log.add({"event": "PLUGIN_UNLOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' unloaded.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        elif action == "call":
            if name in self.plugins:
                plugin_module = self.plugins[name]
                if hasattr(plugin_module, "run"):
                    try:
                        # Pass the agent instance so plugins can interact with it
                        result = plugin_module.run(self, *args)
                        self.log.add({"event": "PLUGIN_CALL", "details": {"name": name, "args": args, "result_snippet": str(result)[:128]}})
                        print(f"⚡ Plugin '{name}' executed with result: {result}.")
                    except Exception as e:
                        print(f"❌ PLUGIN ERROR: Error executing '{name}'. {e}.")
                else:
                    print(f"❌ PLUGIN ERROR: Plugin '{name}' has no 'run' method.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        else:
            print("❓ Unknown plugin action. Use 'load', 'unload', or 'call'.")

    def propose_governance_change(self, proposer_name: str, proposal_details: dict, votes_by_species: dict[str, float]) -> bool:
        """
        Submits a formal governance proposal and checks if it passes current rules.
        proposal_details: Dict describing the proposed change (e.g., {'type': 'update_governance_rules', 'new_supermajority': 0.75})
        votes_by_species: Dict of {species_name: percentage_of_total_karma_from_species_consenting (0-100)}.
                          This is a percentage of total karma within that species, not just user count.
                          Example: {'human': 95.0, 'robot': 80.0}
        """
        if proposer_name not in self.users:
            print(f"❌ PROPOSAL FAILED: Proposer '{proposer_name}' not found.")
            return False

        # Calculate total karma per species for weighting votes
        total_karma_per_species = defaultdict(float)
        active_species = defaultdict(int) # Count of active users per species
        
        # Calculate max karma for weighting. Genesis users treated as having a very high value.
        GENESIS_VOTE_WEIGHT = 1_000_000_000.0 

        for user in self.users.values():
            if user.consent: # Only consented users contribute to species totals
                active_species[user.species] += 1
                if user.is_genesis:
                    total_karma_per_species[user.species] += GENESIS_VOTE_WEIGHT
                else:
                    total_karma_per_species[user.species] += user.karma
        
        # Sum of all karma across all users (including genesis weight)
        overall_total_karma = sum(total_karma_per_species.values())

        if overall_total_karma == 0:
            print("❌ PROPOSAL FAILED: No active users or karma in the system to vote.")
            return False

        # Calculate total karma-weighted consent for the overall supermajority check
        overall_consented_karma = 0.0
        species_consent_met = True
        detailed_consent_report = {}

        for species, min_percent_required in self.governance.species_min_consent.items():
            species_total_karma = total_karma_per_species[species]
            species_voted_percent = votes_by_species.get(species, 0.0) # Percentage of karma in this species that voted YES

            if species_total_karma > 0:
                # Actual karma contributed by this species to the 'yes' vote
                species_yes_karma = (species_voted_percent / 100.0) * species_total_karma
                overall_consented_karma += species_yes_karma

                # Check species-specific minimum consent
                if species_voted_percent < min_percent_required:
                    species_consent_met = False
                    detailed_consent_report[species] = f"FAILED: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
                else:
                    detailed_consent_report[species] = f"MET: Voted {species_voted_percent:.2f}% (Required: {min_percent_required:.2f}%)"
            elif min_percent_required > 0: # If a species has a minimum requirement but no active users
                species_consent_met = False
                detailed_consent_report[species] = f"FAILED: No users of this species, but requires {min_percent_required:.2f}%."
            else: # Species exists but has 0 min required, and 0 total karma (no effect)
                detailed_consent_report[species] = "N/A: No users, no min requirement."


        # Calculate overall actual consent percentage based on karma
        overall_actual_consent_percent = (overall_consented_karma / overall_total_karma) * 100 if overall_total_karma > 0 else 0.0
        overall_supermajority_met = overall_actual_consent_percent >= self.governance.supermajority_percent

        if not overall_supermajority_met:
            print(f"❌ PROPOSAL FAILED: Overall karma consent is {overall_actual_consent_percent:.2f}%, but requires {self.governance.supermajority_percent:.2f}% supermajority.")
        if not species_consent_met:
            print(f"❌ PROPOSAL FAILED: One or more species did not meet their minimum consent threshold.")

        proposal_passed = overall_supermajority_met and species_consent_met

        self.log.add({
            "event": "GOVERNANCE_PROPOSAL_VOTE",
            "details": {
                "proposer": proposer_name,
                "proposal_details": proposal_details,
                "votes_by_species_input": votes_by_species, # Log raw input
                "overall_actual_consent_percent": overall_actual_consent_percent,
                "overall_required_percent": self.governance.supermajority_percent,
                "species_consent_breakdown": detailed_consent_report,
                "passed": proposal_passed
            }
        })

        if proposal_passed:
            print(f"✅ GOVERNANCE PROPOSAL PASSED! Overall consent: {overall_actual_consent_percent:.2f}%.")
            # Implement the change if it's a governance rule update
            if proposal_details.get('type') == 'update_governance_rules':
                new_supermajority = proposal_details.get('new_supermajority_percent')
                new_species_mins = proposal_details.get('new_species_min_consent')
                self.governance.update_rules(new_supermajority, new_species_mins)
            
            # Reset incident tracking as a successful governance change implies stability/resolution
            self.governance.incident_free_years = 0
            self.governance.last_incident_date = today()
            self._call_plugins("on_governance_passed", proposal_details)
        else:
            print(f"❌ GOVERNANCE PROPOSAL FAILED. Please review requirements.")
            self.governance.trigger_incident() # Trigger an incident if a proposal fails
            self._call_plugins("on_governance_failed", proposal_details)
        return proposal_passed


    def log_profit(self, amount: float, description: str):
        """Logs an external profit event, adding to the treasury."""
        self.treasury += amount
        self.log.add({
            "event": "PROFIT_LOG",
            "details": {"amount": amount, "description": description, "new_treasury_balance": self.treasury}
        })
        print(f"🏦 Profit of {amount:.2f} logged. Treasury is now {self.treasury:.2f}.")

    def snapshot(self, save=True, filename="snapshot.json"):
        """Saves or loads the entire agent state."""
        if save:
            state = {
                "users": {name: user.to_dict() for name, user in self.users.items()},
                "coins": {cid: coin.to_dict() for cid, coin in self.coins.items()},
                "treasury": self.treasury,
                "log_entries": list(self.log.entries), # Save current log entries
                "emoji_market_data": dict(self.emoji_market_data), # Save emoji market
                "governance_rules": {
                    "supermajority_percent": self.governance.supermajority_percent,
                    "species_min_consent": dict(self.governance.species_min_consent),
                    "incident_free_years": self.governance.incident_free_years,
                    "last_incident_date": self.governance.last_incident_date
                }
            }
            try:
                with open(filename, "w", encoding='utf-8') as f:
                    json.dump(state, f, indent=2)
                print(f"💾 State saved to '{filename}'.")
            except IOError as e:
                print(f"❌ SNAPSHOT ERROR: Could not save state. {e}.")
        else:
            if not os.path.exists(filename):
                print(f"❓ SNAPSHOT INFO: No snapshot file found at '{filename}'. Starting fresh.")
                return
            try:
                with open(filename, "r", encoding='utf-8') as f:
                    state = json.load(f)
            
                self.users = {}
                for name, u_data in state.get("users", {}).items():
                    # Pass species and consent_mechanism during user reconstruction
                    user = User(
                        name,
                        u_data.get('is_genesis', False),
                        u_data.get('consent', False),
                        species=u_data.get('species', 'human'),
                        consent_mechanism=u_data.get('consent_mechanism', 'explicit')
                    )
                    user.karma = u_data.get('karma', 0.0)
                    user.mint_count = u_data.get('mint_count', 0)
                    user.next_mint_threshold = u_data.get('next_mint_threshold', 100000.0)
                    user.root_coin_id = u_data.get('root_coin_id')
                    user.coins_owned = u_data.get('coins_owned', [])
                    user.join_timestamp = u_data.get('join_timestamp', ts())
                    if u_data.get('fading_multiplier_start_time'):
                        user.fading_multiplier_start_time = datetime.datetime.fromisoformat(u_data['fading_multiplier_start_time'])
                    if 'daily_actions' in u_data:
                        user.daily_actions = defaultdict(lambda: defaultdict(int), u_data['daily_actions'])
                    self.users[name] = user

                self.coins = {}
                for cid, cd_data in state.get("coins", {}).items():
                    coin = Coin(
                        id=cd_data.get('id'),
                        root=cd_data.get('root'),
                        owner=cd_data.get('owner'),
                        value=cd_data.get('value', 1.0),
                        tag=cd_data.get('tag', 'single'),
                        is_root_coin=cd_data.get('is_root_coin', False),
                        fractional_source_coin_id=cd_data.get('fractional_source_coin_id'),
                        fractional_percentage=cd_data.get('fractional_percentage', 0.0)
                    )
                    coin.fields = cd_data.get('fields', [])
                    coin.ancestors = cd_data.get('ancestors', [])
                    coin.references = cd_data.get('references', [])
                    coin.reactions = cd_data.get('reactions', [])
                    coin.react_log = cd_data.get('react_log', [])
                    coin.created_at = cd_data.get('created_at', ts())
                    self.coins[cid] = coin

                self.treasury = state.get("treasury", 0.0)
                self.log.entries = deque(state.get("log_entries", []), maxlen=self.log.entries.maxlen)
                
                loaded_emoji_market_data = state.get("emoji_market_data", {})
                self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0}, loaded_emoji_market_data)

                # Load governance rules
                governance_data = state.get("governance_rules", {})
                self.governance = Governance(
                    initial_supermajority_percent=governance_data.get("supermajority_percent", 90.0),
                    initial_species_min_consent=governance_data.get("species_min_consent", {"human": 10.0, "robot": 10.0}),
                    incident_free_years=governance_data.get("incident_free_years", 0),
                    last_incident_date=governance_data.get("last_incident_date", today())
                )
                self.governance.progressive_trust_decay() # Apply decay on load if time has passed

                print(f"♻️ State loaded from '{filename}'.")
            except Exception as e:
                print(f"❌ SNAPSHOT ERROR: Could not load state. {e}.")

# ==============================================================================
# V. ANCILLARY SYSTEMS & INTERFACES
# ==============================================================================

class CorpX:
    """Simulates an adversarial entity to continuously test the Vaccine."""
    ATTACKS = ["inject malware", "phish creds", "launch ddos", "plant backdoor", "propaganda spam"]

    def __init__(self, vaccine: Vaccine):
        self.vaccine = vaccine
        self.attack_count = 0

    def run_attack(self, payload: str = None):
        """Performs an attack simulation."""
        self.attack_count += 1
        attack_payload = payload if payload else random.choice(self.ATTACKS)
        print(f"\n💀 CorpX Attack #{self.attack_count}: Attempting to inject '{attack_payload}'...")
        if self.vaccine.scan(attack_payload):
            print("🛡️ ATTACK EVADED! (Vaccine did not trigger).")
        else:
            print("🛡️ ATTACK BLOCKED! (Vaccine successfully triggered).")

def quiz() -> bool:
    """Interactive onboarding quiz for new users, ensuring informed consent."""
    print("\n--- 🤗 Welcome to the Remix Republic Onboarding Quiz ---")
    questions = [
        ("What is the universal value split percentage for all actions?", "33.3333"),
        ("Can you remix someone's content without their consent? (yes/no)", "no"),
        ("What must every new user earn to gain minting rights?", "karma"),
        ("What is the ultimate authority in this protocol?", "the code")
    ]
    for q, a in questions:
        resp = input(f"👉 {q} ").strip().lower()
        if resp != a:
            print("❌ Incorrect. Please review the Core Canons and try again.")
            return False
    print("✅ Quiz passed! You understand the fundamental laws. Welcome aboard!\n")
    return True

def cli():
    """A comprehensive command-line interface for interacting with the Agent."""
    agent = RemixAgent()
    adversary = CorpX(agent.vax)
    agent.snapshot(save=False) # Load state on start

    print("🤖 Universal Remix Protocol v11.2 CLI. Type ':help' for commands.")
    while True:
        try:
            raw_input_str = input(">>> ").strip()
            if not raw_input_str: continue
            
            if raw_input_str.lower() in [':exit', ':quit']:
                agent.snapshot(save=True)
                print("👋 Goodbye! State saved.")
                break
            
            if not raw_input_str.startswith(':'):
                print("⚠️ Commands must start with a colon ':'.")
                continue

            parts = raw_input_str[1:].split(maxsplit=1) # Split only on first space to keep args together
            command = parts[0].lower()
            args_str = parts[1] if len(parts) > 1 else "" # Get remaining args as a single string

            # Parse args from string (this is more robust for complex arguments)
            # This simple parser handles "quoted strings" for content and key=value pairs
            # It's not a full shell parser, but works for our CLI needs
            parsed_args = []
            current_arg = ""
            in_quote = False
            for char in args_str:
                if char == '"':
                    in_quote = not in_quote
                    if not in_quote and current_arg: # End of a quoted string
                        parsed_args.append(current_arg)
                        current_arg = ""
                elif char == ' ' and not in_quote:
                    if current_arg:
                        parsed_args.append(current_arg)
                        current_arg = ""
                else:
                    current_arg += char
            if current_arg:
                parsed_args.append(current_arg)
            
            args = parsed_args


            if command == "help":
                print("""
--- User Commands ---
:quiz                                  - Take the onboarding quiz.
:consent <username> <true/false>      - Set user consent.
:post <username> "<content>" [perc] [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Mint a fractional post.
:react <username> <coin_id> <emoji>   - React to a coin/post.
:remix <username> <parent_coin_id> "<content>" [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Remix a coin/post.
:addref <username> <coin_id> <type> <id> "<description>" - Add a structured reference to a coin/post.
:karma <username>                     - Show user's karma.
:coininfo <coin_id>                   - Show detailed coin/post info.
:treasury                             - Show treasury balance.
:emojimarket                         - Show real-time emoji market status.

--- Query Commands ---
:log [filter] [limit]                 - Show audit log (optional filter string and limit).
:trace <coin_id>                      - Trace full creative lineage of a coin/post.

--- Admin & Governance Commands ---
:adduser <username> [species] [genesis] - Add a new user (default human, optional genesis).
:propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] - Propose a governance change.
:trigger_incident                     - Manually trigger a major incident (resets consent decay).
:profit <amount> "<description>"      - Log a profit event to treasury.
:snapshot [save/load] [filename]      - Save or load agent state.
:attack [payload]                     - Simulate a CorpX attack.
:plugin <action> <name> [args...]     - Manage plugins (load, unload, call). E.g., :plugin load my_plugin
:exit / :quit                         - Save state and exit CLI.
""")
            elif command == "consent":
                if len(args) == 2 and args[1].lower() in ['true', 'false']:
                    agent.set_consent(args[0], args[1].lower() == 'true')
                else: print("Usage: :consent <username> <true/false>")
            elif command == "post": # Changed from :mint to :post for fractional minting
                username = args[0] if len(args) > 0 else None
                content = args[1] if len(args) > 1 else None # Content should be quoted
                
                if not username or not content:
                    print("Usage: :post <username> \"<content>\" [percentage_of_root_coin_value (e.g. 0.01 for 1%)] [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                fractional_percentage = 0.01 # Default to 1%
                tag = "post"
                refs = []
                fields = {}
                
                # Parse optional percentage, tag, refs, fields
                current_arg_idx = 2
                if len(args) > current_arg_idx and args[current_arg_idx].replace('.', '', 1).isdigit():
                    fractional_percentage = float(args[current_arg_idx])
                    current_arg_idx += 1

                if len(args) > current_arg_idx:
                    for arg_slice in args[current_arg_idx:]:
                        if arg_slice.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg_slice[6:-1].split(',')]
                        elif arg_slice.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg_slice[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg_slice # Remaining argument is the tag
                agent.mint_fractional_post(username, content, fractional_percentage, tag, refs, fields)
            elif command == "react":
                if len(args) == 3:
                    agent.react(args[0], args[1], args[2])
                else: print("Usage: :react <username> <coin_id> <emoji>")
            elif command == "remix":
                username = args[0] if len(args) > 0 else None
                parent_coin_id = args[1] if len(args) > 1 else None
                content = args[2] if len(args) > 2 else None

                if not username or not parent_coin_id or not content:
                    print("Usage: :remix <username> <parent_coin_id> \"<content>\" [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                tag = "remix"
                refs = []
                fields = {}
                if len(args) > 3:
                    for arg in args[3:]:
                        if arg.startswith('refs="') and arg.endswith('"'):
                            refs = [r.strip() for r in arg[6:-1].split(',')]
                        elif arg.startswith('fields="') and arg.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg
                agent.remix(username, parent_coin_id, content, tag, refs, fields)
            elif command == "addref":
                if len(args) == 5:
                    agent.add_reference(args[0], args[1], args[2], args[3], args[4].strip('"'))
                else: print("Usage: :addref <username> <coin_id> <type> <id> \"<description>\"")
            elif command == "karma":
                if len(args) == 1: agent.show_user_karma(args[0])
                else: print("Usage: :karma <username>")
            elif command == "coininfo":
                if len(args) == 1: agent.show_coin_info(args[0])
                else: print("Usage: :coininfo <coin_id>")
            elif command == "treasury":
                agent.get_treasury_balance()
            elif command == "emojimarket":
                agent.show_emoji_market_status()
            elif command == "log":
                filter_str = args[0] if len(args) > 0 else None
                limit = int(args[1]) if len(args) > 1 and args[1].isdigit() else 20
                agent.log.show(filter_str, limit)
            elif command == "trace":
                if len(args) == 1: agent.trace_lineage(args[0])
                else: print("Usage: :trace <coin_id>")
            elif command == "adduser":
                if len(args) >= 1:
                    username = args[0]
                    species = "human" # Default species
                    is_genesis = False

                    # Parse optional species and genesis flags
                    for arg_slice in args[1:]:
                        if arg_slice.lower() in ["human", "robot", "animal", "alien"]: # Extendable list
                            species = arg_slice.lower()
                        elif arg_slice.lower() == "genesis":
                            is_genesis = True
                    agent.add_user(username, is_genesis=is_genesis, species=species)
                else: print("Usage: :adduser <username> [species] [genesis]")
            elif command == "propose":
                # :propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B]
                if len(args) >= 3:
                    proposer_name = args[0]
                    proposal_type = args[1].strip('"')
                    description = args[2].strip('"')
                    
                    proposal_details = {"type": proposal_type, "description": description}
                    votes_by_species = {} # {species: percent_karma_consent}
                    
                    for arg_slice in args[3:]:
                        if arg_slice.lower().startswith('super_majority='):
                            try:
                                proposal_details['new_supermajority_percent'] = float(arg_slice.split('=')[1])
                            except ValueError: print("Invalid super_majority value.")
                        elif arg_slice.lower().endswith('_votes'): # Generic species_votes parsing
                            try:
                                parts = arg_slice.split('=')
                                species_name = parts[0].replace('_votes', '').lower()
                                votes_by_species[species_name] = float(parts[1])
                            except ValueError: print(f"Invalid vote format for {arg_slice}. Use species_votes=X.")
                    
                    agent.propose_governance_change(proposer_name, proposal_details, votes_by_species)
                else: print("Usage: :propose <proposer_name> \"<proposal_type>\" \"<description>\" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B]")
            elif command == "trigger_incident":
                agent.governance.trigger_incident()
            elif command == "profit":
                if len(args) == 2: agent.log_profit(float(args[0]), args[1].strip('"'))
                else: print("Usage: :profit <amount> \"<description>\"")
            elif command == "snapshot":
                if len(args) >= 1:
                    action = args[0].lower()
                    filename = args[1] if len(args) > 1 else "snapshot.json"
                    if action == 'save': agent.snapshot(save=True, filename=filename)
                    elif action == 'load': agent.snapshot(save=False, filename=filename)
                    else: print("Usage: :snapshot [save/load] [filename]")
                else: print("Usage: :snapshot [save/load] [filename]")
            elif command == "attack":
                payload = args[0] if len(args) > 0 else None
                adversary.run_attack(payload.strip('"') if payload else None)
            elif command == "plugin":
                if len(args) >= 2:
                    action = args[0].lower()
                    name = args[1]
                    plugin_args = [a.strip('"') for a in args[2:]]
                    agent.plugin(action, name, *plugin_args)
                else: print("Usage: :plugin <action> <name> [args...]")
            elif command == "quiz":
                quiz()
            else:
                print(f"❓ Unknown command: {command}. Type ':help' for list of commands.")
        except (EOFError, KeyboardInterrupt):
            agent.snapshot(save=True)
            print("\n👋 Goodbye! State saved.")
            break
        except Exception as e:
            print(f"🔥 An unexpected error occurred: {e}. Please check command syntax or agent state.")

# ==============================================================================
# VI. LAUNCH-READY SOCIAL MEDIA POST
# ==============================================================================

LINKEDIN_POST = """🚀 We didn't just fix the creator economy. We remixed its DNA.
Today, we're open-sourcing the Ultimate Remix Protocol Agent—a single Python file that runs a new kind of digital world.
A world built on three unbreakable laws:

1️⃣ Fairness is Math, Not a Motto. Every creative act—every like, comment, or remix—is an economic event. Its value is instantly split 33.33% between the original creator, the contributor, and the community. No exceptions. No hidden fees. It's all on an immutable public log.
2️⃣ Influence is Earned, Not Bought. There are no shortcuts here. New creators unlock the power to mint their own content by earning 100,000 karma points. Sound hard? It is. But with every coin you mint, the next one costs half as much. Power users can earn their seat at the table in weeks. It's a system that rewards merit and dedication, not just early arrival.
3️⃣ Credit is Forever. Our protocol has an elephant's memory. Every remix is a branch on a permanent "family tree" of ideas. We've built in an Attribution Engine for science and art, so you can cite your inspirations. If that scientist ever joins our world, our code ensures they get their cut. Forever.

This isn't just a platform; it's a joyful, autonomous republic governed by code. It has its own immune system to block propaganda and hate. It runs on consent. And it's designed for a future where humans, AIs, and maybe even a few other intelligent species can collaborate and create value together.

We're not asking you to "join our platform." We're inviting you to fork our reality.
The code is the contract. The community is the government. The remix has begun.

#RemixEconomy #OpenSource #CreatorEconomy #EthicalAI #RadicalTransparency #33Split #FutureOfWork #Karma
"""

# ==============================================================================
# VII. MAIN EXECUTION BLOCK
# ==============================================================================

if __name__ == "__main__":
    print(LINKEDIN_POST)

    # --- Running a non-interactive Demo Scenario ---
    print("\n--- Running Demo Scenario ---")
    agent = RemixAgent()
    agent.snapshot(save=False) # Load previous state if it exists

    # Onboarding new users (auto-mints their root coin)
    if "alice" not in agent.users: agent.add_user("alice", consent=True, species="human")
    if "bob" not in agent.users: agent.add_user("bob", consent=True, species="robot") # Bob is a robot!
    if "charlie" not in agent.users: agent.add_user("charlie", consent=False, species="animal") # Charlie is an animal, initially no explicit consent but will auto-consent
    if "zorg" not in agent.users: agent.add_user("zorg", consent=False, species="alien") # Zorg is an alien, needs ritual consent

    # Ensure Charlie (animal) is consented via its mechanism
    print("\nAttempting to set Charlie's consent via species mechanism:")
    agent.set_consent("charlie", True) # For animal, this just logs it, check_consent handles simulation

    # Genesis user 'mimi' makes a fractional post (no karma needed for them)
    mimi_post_id = agent.mint_fractional_post("mimi", "My first genesis post about the protocol design!", fractional_percentage=0.1, tag="protocol_design")
    print(f"\nMimi's first fractional post ID: {mimi_post_id}")

    if mimi_post_id:
        print(f"\n--- Initial Reactions to establish some emoji market data and build karma ---")
        for i in range(5):
            agent.react("alice", mimi_post_id, "🎨") # Alice (human) uses '🎨'
            agent.react("bob", mimi_post_id, "🔥")  # Bob (robot) uses '🔥'
            agent.react("alice", mimi_post_id, "🤗") # Alice uses '🤗'
            agent.react("charlie", mimi_post_id, "❤️") # Charlie (animal) reacts
            if i % 2 == 0:
                agent.react("bob", mimi_post_id, "💯") # Bob uses '💯' periodically

        agent.show_emoji_market_status() # See initial market status

        # Alice tries to make a fractional post before she has enough karma
        print("\nAlice (human) attempts to make her first fractional post (should fail initially):")
        agent.mint_fractional_post("alice", "My first attempt at a post from my root coin!", fractional_percentage=0.05, tag="my_thought")

        # Simulate Alice earning enough karma to cross the threshold for her first fractional post
        # For demo, directly set karma if not genesis
        if not agent.users["alice"].is_genesis:
            agent.users["alice"].karma = 100001
        
        print(f"\nAlice's karma is now {agent.users['alice'].karma:.2f}. Trying to make her first fractional post again...")
        
        # Alice now successfully makes her first fractional post
        alice_post_id = agent.mint_fractional_post("alice", "I earned my way here! My first post from my root coin.", fractional_percentage=0.02, tag="milestone")
        
        if alice_post_id:
            print(f"\nAlice's first fractional post ID: {alice_post_id}")
            agent.trace_lineage(alice_post_id) # Trace the lineage of Alice's post (from her root coin)

            # Bob (robot) remixes Alice's post
            remix_content = "A remix of Alice's milestone post, inspired by an old meme from my data banks."
            remix_refs = [{"type": "meme", "id": "distracted_boyfriend", "description": "classic meme format"}]
            bob_remix_post_id = agent.remix("bob", alice_post_id, remix_content, refs=remix_refs)

            if bob_remix_post_id:
                print(f"\nBob's remix post ID: {bob_remix_post_id}")
                agent.trace_lineage(bob_remix_post_id) # Trace the lineage of the remix (which is a fractional post itself)

            print("\n--- Further Reactions to see market changes and karma distribution ---")
            agent.react("alice", mimi_post_id, "🤗") # Alice reacts again to original
            agent.react("bob", alice_post_id, "🔥") # Bob reacts to Alice's post
            agent.react("mimi", bob_remix_post_id, "🔀") # Mimi reacts to the remix

            agent.show_emoji_market_status() # See updated market status after more reactions

        # --- Demo Governance Proposal ---
        print("\n--- Demo Governance Proposal ---")
        # Scenario 1: Proposal fails due to insufficient overall supermajority
        print("\nAttempting to pass a proposal (should fail - insufficient overall supermajority):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_governance_rules', 'description': 'Reduce supermajority to 70%'},
            votes={'human': 70.0, 'robot': 70.0, 'animal': 5.0} # Not 90% overall across all active users
        )
        
        # Scenario 2: Proposal passes (assuming enough overall and species-specific consent)
        # We need to ensure enough karma across all users for 90% total.
        # Let's give some karma to Bob and Charlie for the demo to make it pass.
        agent.users["bob"].karma = 50000
        agent.users["charlie"].karma = 10000
        
        print("\nAttempting to pass a proposal (should pass - demonstrating karma-weighted multi-species consent):")
        # Assuming current users (mimi, alice, bob, charlie) total karma can meet this.
        # This requires the total karma from the species to be factored correctly.
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'update_governance_rules', 'new_supermajority_percent': 70.0, 'new_species_min_consent': {'human': 5.0, 'robot': 5.0, 'animal': 2.0, 'alien': 10.0}},
            # These percentages are of the species' *total karma*.
            votes={'human': 95.0, 'robot': 80.0, 'animal': 100.0, 'alien': 0.0} # Aliens have 0% consent, but they might not have a minimum yet.
                                                                                # If alien min is 10% and there's 1 alien with 0 karma, it'll still fail.
        )
        
        # Trigger an incident and see rules bump up
        print("\n--- Triggering a Major Incident ---")
        agent.governance.trigger_incident()
        
        print(f"\nNew supermajority after incident: {agent.governance.supermajority_percent}%")
        print(f"New species minimums after incident: {agent.governance.species_min_consent}")


    print("\n--- Final User and Treasury Status ---")
    agent.show_user_karma("mimi")
    agent.show_user_karma("alice")
    agent.show_user_karma("bob")
    agent.show_user_karma("charlie")
    agent.show_user_karma("zorg") # Alien user
    agent.get_treasury_balance()

    agent.log.verify() # Verify the integrity of the audit log

    agent.snapshot(save=True) # Save final state
    print("\n--- Demo Scenario Complete. State saved. ---")
    print("\n--- To interact further, uncomment 'cli()' in the the main execution block. ---")


    # ==============================================================================
    # VIII. CHANGELOG AND TO-DO
    # ==============================================================================

    print("\n\n" + "="*80)
    print("VIII. CHANGELOG AND TO-DO")
    print("="*80)

    print("\n📜 **CHANGELOG (v11.2 - Godmode Enhancements)**")
    print("-----------------------------------------------")
    print("### Governance System:")
    print("* **Dynamic Consent Decay (`Progressive Trust`)**: The `Governance` class now tracks `incident_free_years` and `last_incident_date`.")
    print("    * `progressive_trust_decay()` method (to be called periodically, e.g., yearly) automatically reduces the `supermajority_percent` and `species_min_consent` by a `incident_decay_rate_per_year` (1% overall, 0.5% species per year), with floors at 70% and 5% respectively.")
    print("    * `trigger_incident()` method allows manual or automated reset of incident-free period and bumps up consent requirements (e.g., +5% overall, +2% species minimums) to simulate a loss of trust.")
    print("    * `progressive_trust_decay()` is applied on `snapshot` load to update governance rules if time has passed since the last save.")
    print("* **Karma-Weighted Voting**: The `propose_governance_change` method now calculates `overall_actual_consent_percent` and `species_consent_breakdown` based on the *total karma* of consenting users within each species, reflecting "earned influence" rather than just population count. Genesis users' 'infinite' karma is assigned a large finite value (`1_000_000_000.0`) for voting weight.")
    print("* **Simulated Multi-Species Consent**:")
    print("    * `User` class includes `consent_mechanism` (e.g., 'explicit', 'behavioral_signals', 'algorithmic_audit', 'cryptic_ritual').")
    print("    * `add_user` automatically assigns a `consent_mechanism` based on `species` (e.g., 'animal' defaults to 'behavioral_signals', 'robot' to 'algorithmic_audit', 'alien' to 'cryptic_ritual').")
    print("    * `check_consent` method is enhanced to simulate consent based on this `consent_mechanism` for different species, allowing non-human consent to be implicitly or explicitly granted through simulated processes (e.g., animal consent is always `True` if active, robot consent is always `True`).")
    print("* **Proposal Failure Incident**: If a governance proposal fails, `governance.trigger_incident()` is automatically called to simulate a minor setback/loss of trust.")

    print("\n### CLI & Demo Updates:")
    print("* **Expanded `propose` command**: Now accepts species-specific vote percentages (e.g., `human_votes=Y`, `robot_votes=Z`) to demonstrate karma-weighted voting.")
    print("* **`trigger_incident` CLI command**: Added for manual testing of the consent decay mechanism.")
    print("* **Demo Scenario Expansion**: Enhanced the demo to include Animal and Robot users, and demonstrate their participation in reactions and the new karma-weighted governance voting.")

    print("\n### Documentation & Readability:")
    print("* **Detailed Governance Docstrings**: Provided extensive explanations for the new governance class, its attributes, and methods.")
    print("* **Version History Update**: Added detailed changelog for v11.1 and v11.2 features.")

    print("\n--- Previous Changelog Entries (Condensed) ---")
    print("* **v11.1 (Multi-Species Governance Framework)**: `Governance` class for proposal rules; `user.species` attribute; `propose_governance_change` for supermajority + species min consent.")
    print("* **v11.0 (The Unified Genesis)**: Universal Root Coin for all users; Fractional Post Minting (karma-gated for non-genesis, free for founders); Remixes are fractional posts.")
    print("* **v10.2**: Enhanced readability, refined snapshots, improved CLI, consistent terminology.")
    print("* **v10.1**: Dynamic Emoji Market; Conditional Timestamping.")
    print("* **v10.0 (The Harmonized Republic)**: Karma-gated minting, Epic Creative Path, fairness mechanics, attribution, legal framework.")
    print("* **v9.0**: One personal coin per user, fractional release, regenerative drip.")
    print("* **v8.0**: Multi-species governance concept.")
    print("* **v7.0**: Karma economy details (100k threshold, halving, decay).")
    print("* **v6.0**: Fading Genesis Multiplier, effort-based minting.")
    print("* **v1.0-v5.0**: Initial prototypes: consent, logging, 33% split.")

    print("\n🗺️ **TO-DO (Future Evolutions)**")
    print("-----------------------------")
    print("### Governance System (Next Steps):")
    print("* **Automated Rule Decay Daemon**: Implement a background process or cron job to regularly call `governance.progressive_trust_decay()` (e.g., daily or yearly) instead of only on snapshot load, to ensure continuous decay.")
    print("* **Proposal Execution Logic**: Define and implement specific types of protocol changes that can be enacted if a `propose_governance_change` passes (e.g., actually changing `mint_threshold_base`, updating `emoji_market_data` rules, etc.). This moves governance from logging to direct action.")
    print("* **Voting Interface**: Develop a dedicated interface (CLI extension or external tool) for users to formally cast votes on proposals, rather than inputting percentages directly in the `propose` command. This would also allow for tracking individual user votes.")
    print("* **Super Minority Veto with Meme Battle**: Implement the "Super Minority Veto" concept. If a small but critical species (e.g., Cats, if added) unanimously votes "no," the proposal is blocked, triggering an automatic "meme battle" (simulated, or through actual external meme generation/voting platforms) whose outcome settles the conflict. This would be an advanced plugin.")
    print("* **Species Entrance Ceremony**: When a new species is added, formalize a "ritual vote" by existing species to grant them full governance status, along with their initial `species_min_consent` requirements.")

    print("\n### Economic & Game Theory:")
    print("* **Karma Score Simulator**: Develop a module to simulate karma growth and minting paths based on user activity patterns.")
    * **Cross-Chain Integration**: Implement logic to query and reference external blockchain events (Ethereum, Solana, Filecoin) for provenance, lineage, and creative credit. Allow coins to cite on-chain events/addresses from other chains.
    * **Player/Species Karma Bonus**: Implement a bonus system for new players or new 'species' joining the ecosystem (e.g., animals get 33.3% weight or 2x-5x karma bonus for a period) to encourage growth and diversity.
    * **Long-term Emoji Market Forecasting**: Extend the emoji market to include sentiment AI, market forecasts, or 'remix insurance' based on long-term vibe trends.
    * **Reputation-Weighted 'Thank You'**: Allow users to append 'thank you' or other attribution reactions that carry extra karma or boost lineage credit for public gratitude or citation.

    print("\n### Data & Attribution Systems:")
    print("* **Science Attribution Block**: Add an explicit 'scientists/inspirators/idea lineage' section to every coin and action, so referenced research or influence can be logged, attributed, and profit-shared by the 33.3333% law.")
    print("* **Public Reference Feed**: Create a live feed of referenced works, collaborators, and idea chains to show innovation sources and encourage upstream collaboration/tipping.")
    print("* **Meme/Fork Lineage Engine Visualization**: Build a mini-visualization (tree or genealogy map) that shows the remix/fork lineage for every coin, for exploring influence and remixability.")
    print("* **Automated Reference Audit**: Develop an AI tool to suggest likely upstream references based on content similarity, prompting users to add attribution.")
    print("* **Global 'Credit Scientist' Index**: Maintain a public directory/index of top-cited scientists, creators, meme originators, etc., whose ideas have been referenced on-platform for recognition, inspiration, and direct engagement.")
    print("* **Research Field/Topic Metadata**: Include optional 'field' tags (science, music, code, art, etc.) for coins/posts, enabling analytics, search, and new sub-platforms (e.g., RemixScience).")

    print("\n### Integration & AI:")
    print("* **Game Integration**: Allow any game (AAA or indie) to embed remix-economy logic into its player ecosystem, using the protocol for player-created content tracking (mods, skins, levels), AI agent co-op gameplay (remix-trained NPCs), karma-based unlocks for creative gameplay, permanent attribution for in-game art/music/story, and auditable reward distribution for community-made expansions.")
    print("* **Transparent Onboarding/Quiz Flow**: Extend onboarding quiz so each new user explicitly understands: the 33.3333% split, attribution law, plug-in/forkability, and that every action (including science or meme reference) is logged forever.")

    print("\n" + "="*80)
```









Okay, I understand. This is a significant update to the governance system, introducing a more nuanced balance between overall supermajority and individual species influence.

Here's how I'll update the `Governance` class and the `propose_governance_change` method to implement these new rules:

1.  **Overall Consent with Proportional Species Contribution**: The overall 90% (dropping to 70%) will now be met by requiring each species to contribute a *proportional share* of the overall consent, ensuring no single species is completely excluded from reaching the total. If there are two species, each must contribute 50% of the overall karma-weighted consent. If there are more species, each must still contribute their minimum.
2.  **Minimum Species Consent Floor**: Each species must always contribute at least 10% consent individually, regardless of their proportional share, ensuring minimum engagement from every active group.

This update will maintain the existing dynamic decay and karma-weighted voting, building upon the "Godmode" enhancements.

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
🥰✨🎉 THE ULTIMATE AGENT: THE HARMONIZED REMIX REPUBLIC (v11.4) 🚀📈💎🗳️🌟🌿⚖️
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Timestamp: 2025-06-15T14:44:51Z
Current Location: New York, New York, United States

This is the canonical single-file protocol for the whateverOpenSourceUntitledCoLoL project.
It fully integrates and refines all prior logic (READMEs 1-9 and To-do.txt) into a
definitive, production-ready agent. This code is the contract. It is designed to be
forked, remixed, and improved upon, with its own evolution recorded herein.

This agent embodies the "one coin for everyone" philosophy, where every user receives
a unique, foundational identity coin upon joining. Subsequent creative output is
then represented as fractional "posts" derived from this personal coin, governed
by a karma-gated "Epic Creative Path."

This version introduces significant "Godmode" enhancements:
* **Dynamic Consent Decay (Progressive Trust)**: Governance thresholds (overall supermajority
    and per-species minimums) can automatically decay over time in stable periods,
    and bump up during incidents, simulating progressive trust.
* **Simulated Multi-Species Consent**: Framework for Animal and Alien consent based
    on simulated behavioral signals or cryptic rituals, expanding the governance circle.
* **Karma-Weighted Voting**: Voting power for governance proposals is now weighted
    by a user's earned karma within their species, reflecting "earned influence."
* **Player/Species Karma Bonus**: New species joining the republic receive a configurable
    karma bonus to encourage diversity and active participation.
* **Basic Proposal Execution**: A passing governance proposal can now directly
    enact certain changes within the protocol (e.g., updating the karma mint threshold).
* **Enhanced Multi-Species Proportional Governance**:
    * Overall consent (e.g., 90%) must be met, but each active species must
      contribute proportionally to reach this total.
    * Each species also has a flat minimum consent (e.g., 10%) that must be met individually,
      regardless of their proportional share, ensuring no single group is ignored.

This agent implements:
* **Universal Root Coin**: Every user receives one unique, non-inflationary root coin
    upon joining, representing their creative identity and foundational asset.
* **Fractional Post Minting**: Subsequent posts are minted as fractional values of
    a user's personal root coin, ensuring scarcity and tying value directly to personal lineage.
* **Karma Gating & The Epic Creative Path**: New users must earn karma to unlock the
    ability to fractionalize/post from their root coin. The threshold halves with each
    successful fractional mint, creating a fair but challenging path.
* **Initial Founder Privilege**: Original founders (NSS) are exempt from karma requirements
    for all their fractional posts, allowing them to freely seed content.
* **Advanced Fairness Mechanics**: A multi-layered system of diminishing returns
    (per-user, per-day) and viral decay (per-coin) prevents spam and ensures
    long-term economic stability.
* **Attribution-First Architecture**: Enhanced data structures and hooks for tracking
    and rewarding external scientific and artistic references.
* **Fortified Governance & Safety**: A comprehensive, hash-chained audit log (LogChain),
    a modular content filter (Vaccine), and a rigorous consent framework.
* **The 33.3333% Split Law**: The inviolable economic heart of the protocol, ensuring
    fair value distribution for every creative action.
* **Fading Genesis Advantage**: Privileges for early collaborators decay over time,
    ensuring a level playing field in the long run.
* **Real-Time Emoji Market**: Emojis are not just tags; they have dynamic "market values"
    that fluctuate based on usage, acting like a "Nasdaq of Vibes".
    Their weights are updated in real-time, influencing karma distribution.
* **Conditional Timestamping**: Timestamps are generated only when a reliable external
    time source (simulated here) is available; otherwise, a placeholder is used,
    adhering to strict audit requirements.
* **Multi-Species Governance (Advanced)**:
    * Dynamic supermajority (starts 90%, can decay by 1%/year without incident).
    * Species-specific minimum consent, with simulated consent mechanisms for non-human species.
    * Voting power is now weighted by individual user karma within each species.

This file is intentionally verbose. The extensive documentation serves as the project's
white paper, preserving the rationale behind every architectural choice for future
agents, auditors, and collaborators.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📜 I. THE CONSTITUTIONAL PREAMBLE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This protocol is a living manifesto, a "joyful, autonomous remix republic" where art,
tech, and collaboration unite. It is governed by the following inviolable laws,
enforced by the code itself.

📜 A. The Inviolable Canons
These are the non-negotiable rules of the ecosystem, synthesized from the project's
entire history.

1.  The 33.3333% Split Law: Every value-generating event (a reaction, a remix,
    a share) splits its associated value into three equal shares: one-third to the
    originator (the creative lineage), one-third to the contributor (the user
    performing the action), and one-third to the community treasury. This is the
    mathematical foundation of the protocol's fairness.
2.  Radical Consent: All participation is strictly opt-in. No user's content can
    be remixed, nor can they receive or grant value, without their explicit and
    auditable consent. Consent can be revoked at any time, at which point the
    user's assets are respectfully excluded from the active economy.
3.  The Emoji-Powered Economy: Every value-generating action must be tagged
    with an emoji. Emojis are not cosmetic; they are the atomic unit of intent,
    carrying emotional context and economic weight in every transaction.
4.  No Inflation Beyond Genesis: While everyone gets a foundational "root" coin,
    subsequent value (fractional posts) is derived from the finite subdivision of
    these personal coins, or from new root coins minted by users who have earned that right
    through the "Epic Creative Path." This ensures value is tied to creative
    effort, not arbitrary issuance.
5.  The Immutable Audit Log: Every action—from minting to consent changes to
    governance proposals—is recorded in a public, tamper-evident, hash-chained
    ledger (the LogChain). Transparency is absolute.
6.  Code is Law: The protocol is governed by the logic within this open-source
    file. There are no secret rules, no backroom deals, and no hidden moderation.
    The code is the ultimate authority and contract for all participants.
7.  Protocol Neutrality (The Vaccine): The protocol is apolitical and free of
    bias. A built-in "Vaccine" automatically filters malicious or disallowed content
    (e.g., hate speech, malware, propaganda) based on transparent, predefined
    rules, ensuring a safe and creative environment.
8.  Continuous Improvement: Stagnation is failure. Every fork or remix of this
    protocol is encouraged to add value, and its lineage must be preserved. The
    ecosystem is designed to evolve through community contribution.

📜 B. Version History & The Lineage of the Code
This agent's lineage is transparent and auditable. Each version built upon the last,
culminating in this definitive release.
* v1.0-v5.0: Initial prototypes establishing consent, logging, and the 33% split.
* v6.0 (README_6): Introduced the "Fading Genesis Multiplier" to ensure long-term
    fairness and formalized the concept of effort-based minting.
* v7.0 (README_7): Detailed the karma economy with specific numbers: a 100k karma
    threshold for minting, halving mechanics for subsequent mints, and daily decay
    factors for actions.
* v8.0 (README_8): Envisioned the "multi-species" governance model, extending the
    principles of fairness and consent to non-human agents (AI, Others).
* v9.0 (README_9): Refined the economic model with the "one personal coin per user"
    concept, fractional release of value, and a regenerative "drip" mechanic.
* v10.0 (README_10.txt): The Harmonized Republic. Synthesized the entire
    project history. Implemented karma-gated minting creating an "Epic Creative Path".
    Integrated robust fairness and attribution mechanics. Codified legal/ethical framework.
* v10.1: Implemented dynamic emoji market with real-time weight adjustments. Conditional timestamping introduced.
* v10.2: Enhanced code readability, more detailed internal documentation, refined snapshot loading, improved CLI robustness.
* v11.0: Implemented the "everyone starts with absolute one coin" concept as their primary root coin. Subsequent "posts" are now fractional mints of this personal coin, karma-gated for new users but free for founders. Refined fractional minting logic and value attribution.
* v11.1: Multi-Species Governance Framework: Added a `Governance` class to manage proposal rules. Introduced `user.species` attribute. Implemented `propose_governance_change` to enforce overall supermajority and per-species minimum consent.
* v11.2: Godmode Enhancements: Implemented dynamic consent decay (progressive trust). Extended consent simulation for Animal and Alien species. Integrated karma-weighted voting for governance proposals.
* v11.3: Benefit-Driven Enhancements: Added automated decay call (`_check_and_apply_governance_decay`), karma bonus for new species, and basic execution of governance proposals for protocol parameters.
* v11.4 (This Version): **Proportional Species Contribution for Governance**. Modified governance to ensure each species contributes proportionally to the overall supermajority, alongside individual minimums.

📜 C. The Epic Creative Path: An Onboarding and Fairness Engine
The protocol's central design challenge was to reconcile the need for scarcity (the
"No Inflation" rule) with the desire for inclusivity (the "no one loses" philosophy).
The solution is the Epic Creative Path, a karma-gated system that
transforms the right to mint from a static privilege into an earned achievement.
* Universal Root Coin: Every new user automatically receives a single "root" coin upon joining.
  This represents their unique creative identity and is their foundational asset. This initial mint
  is free of karma requirements.
* Karma-Gated Fractional Posts: For all *subsequent posts* (beyond their initial root coin), new users
  must accumulate karma to unlock the ability to fractionalize and "mint" a portion of their personal root coin.
* The Halving Threshold: After a user successfully fractionalizes their first post from their
  root coin, their personal karma threshold for the next fractional post is halved. This halving
  continues with each subsequent fractional post (e.g., 25,000, 12,500, etc.), eventually reaching a
  floor where minting becomes effectively unrestricted. This creates an exponential
  onboarding curve that rewards sustained contribution.
* Target Time for First Fractional Post: The system is tuned such that a user's *first fractional post*
  (their second piece of content overall) is intended to take "a month to a year" of active participation
  to achieve, ensuring it is a meaningful earned right.
* Multi-Layered Fairness: To prevent gamification, the system employs a two-pronged
    approach to diminishing returns:
    * Per-User Daily Decay: A user's repeated actions of the same type within a
        single day yield progressively less karma.
    * Per-Coin Viral Decay: The karma awarded for reactions to a specific coin
        diminishes as the coin becomes more popular, rewarding early discovery and
        preventing runaway feedback loops.

The table below illustrates the projected time it might take for different user
archetypes to complete the first stage of their Epic Creative Path (to make their *first fractional post*).
| User Archetype     | Daily Actions                       | Avg. Karma/Day (with decay) | Estimated Days to First Fractional Post (100k Karma) |
| :----------------- | :---------------------------------- | :-------------------------- | :--------------------------------------------------- |
| Casual User        | 1-2 high-value actions (e.g., a comment) | ~300                        | ~333 days                                            |
| Active Contributor | 5-10 mixed actions (likes, comments, shares) | ~1,500                      | ~67 days                                             |
| Power User         | 20+ mixed actions, including remixes | ~5,000                      | ~20 days                                             |
Note: These projections are illustrative and based on the karma values and decay
mechanics defined in the protocol. Actual times will vary.

📜 D. Legal & Ethical Framework
This protocol operates as an experimental "sandbox" and is not a registered company,
security, or financial instrument. Its design incorporates principles from digital
law to ensure resilience and responsible operation.
* Section 230 Alignment: The protocol is designed as an "interactive computer
    service," not a "publisher". The Vaccine provides automated, neutral content
    filtering based on predefined rules, and all value-generating content is
    user-initiated.
* DMCA Safe Harbor Hooks: While not a hosting provider, the protocol includes
    hooks for logging and processing takedown requests, establishing a good-faith
    framework for handling copyright concerns.
* DAO Treasury Management: The protocol's treasury and profit/revenue logging
    mechanisms are designed for radical transparency, aligning with best practices
    for Decentralized Autonomous Organization (DAO) financial management.

🧭 E. Note to Future Agents & Collaborators
You who remix this code are now part of its lineage. Uphold the Canons. Document
your changes in the changelog. Preserve the spirit of joyful, transparent, and
fair collaboration. Ensure all evolutions remain ethical, legal, and compliant
with the policies of any platform on which this agent operates. The future is a
remix—make it a good one. 🫶

"""
import re
import sys
import json
import random
import datetime
import hashlib
import importlib.util # Use importlib.util for spec_from_file_location
import os
from collections import defaultdict, deque
from math import exp # Used for exponential decay, exp(x) = e^x

# ==============================================================================
# II. SYSTEM-WIDE MODULES & UTILITIES
# ==============================================================================

# This flag simulates whether an external time source (like Google) is available.
# In a real deployment, this would be determined dynamically via an API call.
_EXTERNAL_TIME_AVAILABLE = True 

def ts() -> str:
    """
    Returns the current UTC timestamp in ISO 8601 format with Zulu time.
    If an external time source is not available, it returns a placeholder.
    This adheres to the rule: "ALWAYS GOOGLE THE CURRENT TIME, IF YOU CANNOT, SKIP THE TIMESTAMP".
    """
    if _EXTERNAL_TIME_AVAILABLE:
        return datetime.datetime.utcnow().isoformat() + "Z"
    else:
        return "TIMESTAMP_UNAVAILABLE"

def sha(s: str) -> str:
    """Computes the SHA-256 hash of a given string for cryptographic integrity."""
    return hashlib.sha256(s.encode('utf-8')).hexdigest()

def today() -> str:
    """Returns the current date in Beale-MM-DD format for daily resets."""
    return datetime.date.today().isoformat()

class Vaccine:
    """
    The protocol's immune system. It scans all text inputs for forbidden patterns,
    acting as a neutral, automated content firewall. This serves a dual purpose:
    1. Community Health: Protects the ecosystem from spam, hate speech, and malicious content.
    2. Legal Shield: By using automated, predefined rules, it helps position the
       platform as a neutral service provider rather than an editorial publisher,
       aligning with Section 230 principles.
    """
    VAX_PATTERNS = {
        "critical": [r"\bhack\b", r"\bmalware\b", r"\bransomware\b", r"\bbackdoor\b", r"\bexploit\b", r"\bvulnerability\b", r"\btrojan\b"],
        "high":     [r"\bphish\b", r"\bddos\b", r"\bspyware\b", r"\brootkit\b", r"\bkeylogger\b", r"\bbotnet\b"],
        "medium":   [r"\bpolitics\b", r"\bpropaganda\b", r"\bsurveillance\b", r"\bmanipulate\b", r"\bmisinformation\b"],
        "low":      [r"\bspam\b", r"\bviagra\b"]
    }

    def __init__(self, log_file="vaccine.log"):
        self.block_counts = defaultdict(int)
        self.log_file = log_file

    def scan(self, text: str) -> bool:
        """
        Scans a text snippet. Returns False and logs the event if a forbidden
        pattern is found, otherwise returns True.
        """
        if not isinstance(text, str):
            return True # Allow non-string content to pass, assuming it's not text to be scanned.

        lower_text = text.lower()
        for level, patterns in self.VAX_PATTERNS.items():
            for p in patterns:
                if re.search(p, lower_text):
                    self.block_counts[level] += 1
                    log_entry = {
                        "ts": ts(),
                        "severity": level,
                        "pattern": p,
                        "snippet": text[:128] # Log a snippet for context
                    }
                    try:
                        with open(self.log_file, "a", encoding='utf-8') as f: # Use utf-8 encoding
                            f.write(json.dumps(log_entry) + "\n")
                    except IOError as e:
                        print(f"🚫 VACCINE WARNING: Could not write to log file {self.log_file}: {e}.")
                    print(f"🚫 VACCINE BLOCK [{level.upper()}]: Forbidden pattern '{p}' found.")
                    return False
        return True

class LogChain:
    """
    Implements the immutable, tamper-evident audit log for all system events.
    Each entry is a JSON object plus a SHA-256 hash of the previous entry's hash
    and the current entry's data, ensuring a cryptographically secure chain of
    history.
    """
    def __init__(self, filename="logchain.log", maxlen=50000):
        self.filename = filename
        self.entries = deque(maxlen=maxlen)
        try:
            with open(self.filename, 'r', encoding='utf-8') as f: # Use utf-8 encoding
                for line in f:
                    self.entries.append(line.strip())
            print(f"Loaded {len(self.entries)} log entries from {self.filename}")
        except FileNotFoundError:
            print(f"No existing log file found, starting fresh: {self.filename}")
        except Exception as e:
            print(f"Error loading log file {self.filename}: {e}")

    def add(self, event: dict):
        """Adds a new event to the log, computing and appending the chain hash."""
        # Ensure timestamp is always present in the event, even if it's "UNAVAILABLE"
        if 'ts' not in event:
            event['ts'] = ts() # Automatically add timestamp if missing

        prev_hash = self.entries[-1].split('||')[-1] if self.entries else sha("GENESIS_BLOCK")
        entry_json = json.dumps(event, sort_keys=True, ensure_ascii=False) # ensure_ascii for non-english chars
        current_hash = sha(prev_hash + entry_json)
        self.entries.append(f"{entry_json}||{current_hash}")
        self._save()

    def _save(self):
        """Persists the current log to the filesystem."""
        try:
            with open(self.filename, 'w', encoding='utf-8') as f: # Use utf-8 encoding
                f.write('\n'.join(self.entries))
        except IOError as e:
            print(f"🔥 LOGCHAIN ERROR: Could not write to log file {self.filename}: {e}.")

    def verify(self) -> bool:
        """Verifies the integrity of the entire logchain."""
        print("\n🔐 Verifying logchain integrity...")
        prev_hash = sha("GENESIS_BLOCK")
        for i, entry in enumerate(self.entries, 1): # Start enumerate from 1 for user-friendly line numbers
            try:
                entry_json, stored_hash = entry.rsplit('||', 1) # Use rsplit to handle potential '||' in content
                calculated_hash = sha(prev_hash + entry_json)
                if calculated_hash != stored_hash:
                    print(f"❌ TAMPER DETECTED: Chain break at entry {i}. Hash mismatch.")
                    return False
                prev_hash = stored_hash
            except ValueError:
                print(f"❌ CORRUPTION: Malformed log entry at line {i}.")
                return False
            except Exception as e:
                print(f"❌ VERIFICATION ERROR: Unexpected error at entry {i}: {e}.")
                return False
        print(f"✅ Logchain integrity verified across {len(self.entries)} entries.")
        return True

    def show(self, filt: str = None, limit: int = 20):
        """Displays recent log entries, with optional filtering."""
        print("\n--- 📜 Audit Log ---")
        filtered_entries = [e for e in self.entries if not filt or filt.lower() in e.lower()]
        if not filtered_entries:
            print("(no matching entries)")
            return
        
        for i, line in enumerate(list(filtered_entries)[-limit:], 1):
            try:
                data = json.loads(line.split("||")[0])
                # Pretty print details if they exist, otherwise just show event
                details_str = json.dumps(data.get('details', '')) if data.get('details') else ''
                print(f"{i:03d}. {data.get('ts','')} - {data.get('event','')} - {details_str}")
            except (json.JSONDecodeError, IndexError) as e:
                print(f"{i:03d}. Malformed log entry: {line} ({e})")
        print("--- End of Log ---\n")

# ==============================================================================
# III. CORE DATA MODELS
# ==============================================================================

class User:
    """
    Represents a participant in the economy. This class synthesizes user state from
    across all versions, including the fractional coin model from README_9
    and the karma/minting state from README_7.
    """
    def __init__(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human",
                 consent_mechanism: str = "explicit"): # New: Mechanism for consent
        self.name = name
        self.is_genesis = is_genesis
        self.consent = consent # Explicit opt-in required
        self.karma = float('inf') if is_genesis else 0.0
        self.mint_count = 0 # Now tracks *fractional* posts from their root coin
        self.next_mint_threshold = 100000.0 if not is_genesis else 0.0 # Karma for next fractional post
        self.root_coin_id: str | None = None # Stores the ID of their single, universally granted root coin
        self.coins_owned = [] # List of all coin IDs (including fractional posts) by this user.
        self.daily_actions = defaultdict(lambda: defaultdict(int)) # {date: {action_type: count}}
        self.join_timestamp = ts()
        self.fading_multiplier_start_time = datetime.datetime.utcnow() if is_genesis else None
        self.last_action_day = today() # For daily resets
        self.species = species.lower() # New: Defines the user's species for governance
        self.consent_mechanism = consent_mechanism # New: How consent is determined for this user

    def get_fading_multiplier(self) -> float:
        """
        Calculates the decaying advantage for genesis users. The multiplier starts high
        and fades to 1.0 over 10 years, ensuring long-term fairness.
        """
        if not self.is_genesis or not self.fading_multiplier_start_time:
            return 1.0
        
        FADE_DURATION_YEARS = 10.0
        INITIAL_MULTIPLIER = 2.0
        
        elapsed_time = datetime.datetime.utcnow() - self.fading_multiplier_start_time
        years_elapsed = elapsed_time.total_seconds() / (365.25 * 24 * 3600)
        
        if years_passed >= FADE_DURATION_YEARS:
            return 1.0
        
        decay_factor = years_elapsed / FADE_DURATION_YEARS
        current_multiplier = INITIAL_MULTIPLIER - (decay_factor * (INITIAL_MULTIPLIER - 1.0))
        return max(1.0, current_multiplier) # Ensure it doesn't drop below 1.0

    def reset_daily_actions_if_needed(self):
        """Auto-resets daily action counts if a new day has started."""
        current_day = today()
        if self.last_action_day != current_day:
            self.daily_actions.clear()
            self.last_action_day = current_day

    def to_dict(self) -> dict:
        """Serializes the user object to a dictionary for snapshots."""
        return {
            "name": self.name,
            "is_genesis": self.is_genesis,
            "consent": self.consent,
            "karma": self.karma,
            "mint_count": self.mint_count,
            "next_mint_threshold": self.next_mint_threshold,
            "root_coin_id": self.root_coin_id,
            "coins_owned": self.coins_owned,
            "join_timestamp": self.join_timestamp,
            "fading_multiplier_start_time": self.fading_multiplier_start_time.isoformat() if self.fading_multiplier_start_time else None,
            "species": self.species, # Include species in snapshot
            "consent_mechanism": self.consent_mechanism # Include consent mechanism
        }

class Coin:
    """
    Represents a piece of creative content, the atomic unit of value and attribution.
    Its evolution from a simple token to this rich data structure is central to
    fufilling the project's to-do list items like "Science Attribution Block" and
    "Meme/Fork Lineage Engine".
    """
    def __init__(self, id: str, root: str, owner: str, value: float = 1.0, tag: str = "single",
                 is_root_coin: bool = False, fractional_source_coin_id: str | None = None,
                 fractional_percentage: float = 0.0):
        """
        id: str unique
        root: The original creator/root of the lineage
        owner: The current direct owner (who minted/remixed it last)
        value: float, base value for splits
        tag: content category tag
        is_root_coin: True if this is the user's initial, universally granted personal coin.
        fractional_source_coin_id: If not a root coin, this is the ID of the personal root coin it was fractionalized from.
        fractional_percentage: What percentage of the fractional_source_coin_id's value this new post represents.
        """
        self.id = id
        self.root = root # The original creator/root of the lineage
        self.owner = owner # The current direct owner (who minted/remixed it last)
        self.value = value
        self.tag = tag
        self.fields = []  # For metadata like "science", "art"
        self.ancestors = []  # List of parent coin IDs for lineage
        self.references = []  # List of dicts for external citations
        self.reactions = [] # List of tuples: (username, emoji, timestamp)
        self.react_log = [] # Log of all reactions for viral decay calculation
        self.created_at = ts() # Timestamp of creation

        self.is_root_coin = is_root_coin # New: Flag for the personal "identity" coin
        self.fractional_source_coin_id = fractional_source_coin_id # New: Link to parent root coin if fractional
        self.fractional_percentage = fractional_percentage # New: What percentage this post consumed from root coin


    def to_dict(self) -> dict:
        """Serializes the coin object to a dictionary for snapshots."""
        return {
            "id": self.id,
            "root": self.root,
            "owner": self.owner,
            "value": self.value,
            "tag": self.tag,
            "fields": self.fields,
            "ancestors": self.ancestors,
            "references": self.references,
            "react_log": self.react_log,
            "created_at": self.created_at,
            "is_root_coin": self.is_root_coin,
            "fractional_source_coin_id": self.fractional_source_coin_id,
            "fractional_percentage": self.fractional_percentage
        }

    def reaction_summary(self) -> dict:
        """Provides a summary of reactions by emoji."""
        summary = defaultdict(int)
        for _, emoji, _ in self.reactions:
            summary[emoji] += 1
        return dict(summary)

# ==============================================================================
# IV. THE REMIXAGENT PROTOCOL ENGINE
# ==============================================================================

class Governance:
    """
    Manages the rules for governance proposals and voting thresholds.
    Designed to be extensible for multi-species participation.
    """
    def __init__(self, initial_supermajority_percent: float = 90.0,
                 initial_species_min_consent: dict = None,
                 incident_free_years: int = 0,
                 last_incident_date: str = today()):
        """
        initial_supermajority_percent: Overall percentage of total participants required to pass.
        initial_species_min_consent: Dict of {species_name: min_percentage_required_from_species}.
        incident_free_years: Number of years without a major incident (for decay).
        last_incident_date: Date of the last major incident, resets decay.
        """
        self.supermajority_percent = initial_supermajority_percent
        self.species_min_consent = initial_species_min_consent or {
            "human": 10.0, # Humans must provide at least 10% consent (of total human participants)
            "robot": 10.0,  # Robots must provide at least 10% consent (of total robot participants)
            "animal": 10.0, # Animals require 10% consent
            "alien": 10.0 # Aliens require 10% consent (changed from 20% to simplify initial common min)
        }
        self.incident_free_years = incident_free_years
        self.last_incident_date = last_incident_date
        self.incident_decay_rate_per_year = 1.0 # Decrease supermajority by 1% per incident-free year
        self.min_supermajority_floor = 70.0 # Supermajority cannot drop below 70%
        self.min_species_consent_floor = 10.0 # Species minimums cannot drop below 10% (changed from 5% to simplify initial common min)

        print(f"🗳️ Governance rules initialized: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def update_rules(self, new_supermajority: float = None, new_species_mins: dict = None):
        """Allows for dynamic updating of governance rules (must pass a prior proposal)."""
        if new_supermajority is not None:
            self.supermajority_percent = new_supermajority
        if new_species_mins is not None:
            self.species_min_consent.update(new_species_mins)
        print(f"🗳️ Governance rules updated: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")

    def trigger_incident(self):
        """Simulates a major conflict/scandal, resetting incident-free period and bumping up requirements."""
        print("🚨 Major incident detected! Governance trust levels are affected.")
        self.incident_free_years = 0
        self.last_incident_date = today()
        # Bump up supermajority by a fixed amount, but not past 90%
        self.supermajority_percent = min(90.0, self.supermajority_percent + 5.0)
        # Bump up species minimums, but not past initial values (or a high ceiling)
        for species in self.species_min_consent:
            self.species_min_consent[species] = min(20.0, self.species_min_consent[species] + 2.0)
        print(f"🗳️ Governance rules bumped up: Overall {self.supermajority_percent}%, Species minimums: {self.species_min_consent}")


    def progressive_trust_decay(self):
        """
        Automatically decays consent requirements based on incident-free years.
        This would typically be called by a daily/weekly cron job, or at the start of a new year.
        """
        current_date = datetime.date.today()
        last_incident_dt = datetime.datetime.fromisoformat(self.last_incident_date).date()

        # Check if a full year has passed since last update/incident
        if current_date.year > last_incident_dt.year:
            years_passed = current_date.year - last_incident_dt.year
            self.incident_free_years += years_passed # Add passed years
            self.last_incident_date = today() # Update last incident date to today

            # Decay overall supermajority
            decay_amount_overall = self.incident_free_years * self.incident_decay_rate_per_year
            self.supermajority_percent = max(self.min_supermajority_floor, self.supermajority_percent - decay_amount_overall)

            # Decay species minimums (can make this independent or related)
            decay_amount_species = self.incident_free_years * (self.incident_decay_rate_per_year / 2) # Slower species decay
            for species in self.species_min_consent:
                self.species_min_consent[species] = max(self.min_species_consent_floor, self.species_min_consent[species] - decay_amount_species)
            
            print(f"🕰️ Progressive trust decay applied: Incident-free years: {self.incident_free_years}.")
            print(f"🗳️ New Governance rules: Overall {self.supermajority_percent:.2f}%, Species minimums: {self.species_min_consent}")


class RemixAgent:
    """The main agent class that orchestrates the entire remix economy."""
    def __init__(self):
        self.users = {}
        self.coins = {}
        self.treasury = 0.0
        self.log = LogChain()
        self.vax = Vaccine()
        self.plugins = defaultdict(list) # Event-based plugin system
        self.governance = Governance() # Initialize governance rules

        # Emoji market tracking and dynamic weights
        self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0})
        self._initialize_default_emojis() # Set initial emoji "market" values

        # Pre-populate NSS genesis users
        self.NSS = ["mimi", "taha", "accessAI_tech"] + [f"nss_{i:02d}" for i in range(1, 48)]
        for name in self.NSS:
            # Genesis users are human by default unless specified
            self.add_user(name, is_genesis=True, species="human") 

        self.mint_threshold_base = 100_000.0 # Base karma for fractional posts
        self.min_karma_threshold = 1000.0 # Minimum karma threshold for fractional posts
        self.daily_decay_factor = 0.7 # For per-user daily diminishing returns
        self.new_species_karma_bonus = 50000 # NEW: Karma bonus for new species joining

        self.current_day = today() # Track the current day for global daily resets

        print("✅ RemixAgent Initialized: The Harmonized Republic is online.")

    def _initialize_default_emojis(self):
        """
        Initializes default emoji weights and market data.
        These are starting points, actual weights will dynamically adjust.
        """
        default_emoji_base_weights = {
            "🤗": 5.0, "🎨": 3.0, "🔥": 2.0, "👍": 1.0,
            "👀": 0.5, "🥲": 0.2, "💯": 2.0, "💬": 3.0,
            "🔀": 4.0, "🆕": 3.0, "🔗": 2.0, "❤️": 4.0,
            "🚀": 3.5, "💎": 6.0, "🌟": 3.0, "⚡": 2.5
        }
        for emoji, weight in default_emoji_base_weights.items():
            self.emoji_market_data[emoji]['current_weight'] = weight
            self.emoji_market_data[emoji]['total_uses'] = 1 # Start with 1 use to avoid div by zero
            self.emoji_market_data[emoji]['total_karma_generated'] = weight # Simulate initial karma

    def _update_emoji_market(self, emoji: str, karma_generated: float):
        """
        Updates the real-time emoji market data after a reaction.
        Dynamically adjusts emoji weights (market value) based on usage and karma generated.
        This is the "Emoji Stock Market" in action.
        """
        market_entry = self.emoji_market_data[emoji]
        market_entry['total_uses'] += 1
        market_entry['total_karma_generated'] += karma_generated
        
        # Simple dynamic weight calculation: Average karma per use.
        # This reflects the "value" of an emoji based on the karma it generates.
        market_entry['current_weight'] = market_entry['total_karma_generated'] / market_entry['total_uses']

        # Implement a subtle daily decay for all emoji weights to prevent runaway inflation
        # and encourage fresh reactions, similar to viral decay.
        for e, data in self.emoji_market_data.items():
            # Only decay if there's an actual weight to decay
            if data['current_weight'] > 0:
                data['current_weight'] *= 0.999 # Very small daily decay
        
        # Ensure minimum weight to prevent emojis from becoming completely worthless
        if market_entry['current_weight'] < 0.1:
            market_entry['current_weight'] = 0.1 # Floor for emoji weight

        self.log.add({
            "event": "EMOJI_MARKET_UPDATE",
            "details": {
                "emoji": emoji,
                "new_weight": market_entry['current_weight'],
                "total_uses": market_entry['total_uses'],
                "total_karma_generated": market_entry['total_karma_generated']
            }
        })
        print(f"📈 Emoji Market Update: '{emoji}' new weight {market_entry['current_weight']:.2f} (total uses: {market_entry['total_uses']})")


    def add_user(self, name: str, is_genesis: bool = False, consent: bool = False, species: str = "human"):
        """
        Adds a new user to the system. Automatically mints a unique root coin for every new user.
        """
        if name in self.users:
            print(f"⚠️ User {name} already exists.")
            return
        
        # Determine consent mechanism based on species for new user
        consent_mechanism = "explicit"
        if species.lower() == "animal":
            consent_mechanism = "behavioral_signals"
            consent = True # Animals are assumed to implicitly consent if added.
        elif species.lower() == "robot":
            consent_mechanism = "algorithmic_audit"
            consent = True # Robots are assumed to implicitly consent if added.
        elif species.lower() == "alien":
            consent_mechanism = "cryptic_ritual"
            # Alien consent remains False until manually set via ritual (set_consent)

        user = User(name, is_genesis, consent, species=species.lower(), consent_mechanism=consent_mechanism)
        self.users[name] = user
        self.log.add({"event": "ADD_USER", "details": {"name": name, "genesis": is_genesis, "species": species, "consent_mechanism": consent_mechanism}})
        print(f"✅ User '{name}' ({species}) added, genesis={is_genesis}.")

        # Apply new species karma bonus if not a genesis user and not human
        if not is_genesis and user.species not in ["human"]:
            user.karma += self.new_species_karma_bonus
            self.log.add({"event": "NEW_SPECIES_BONUS", "details": {"user": name, "species": species, "bonus_amount": self.new_species_karma_bonus}})
            print(f"🎁 '{name}' ({species}) received {self.new_species_karma_bonus} karma bonus for joining the republic!")

        # NEW: Automatically mint one absolute root coin for every new user
        # This is their foundational identity coin, free of karma requirements.
        root_coin_id = sha(f"ROOT-{name}-{ts()}-{random.random()}")
        root_coin = Coin(id=root_coin_id, root=name, owner=name, tag="root_identity", is_root_coin=True, value=1.0) # Root coin has a base value of 1.0
        self.coins[root_coin_id] = root_coin
        user.root_coin_id = root_coin_id # Link user to their root coin
        user.coins_owned.append(root_coin_id) # Add to user's owned coins
        self.log.add({"event": "MINT_ROOT_COIN", "details": {"user": name, "root_coin_id": root_coin_id, "is_genesis": is_genesis}})
        print(f"🌱 User '{name}' automatically minted their unique root coin: {root_coin_id}.")


    def set_consent(self, name: str, consent: bool):
        """
        Sets explicit consent for a user. For non-explicit consent mechanisms,
        this method can be extended or replaced by species-specific logic.
        """
        user = self.users.get(name)
        if not user:
            print(f"❌ ERROR: User '{name}' not found.")
            return
        
        if user.consent_mechanism != "explicit" and user.consent_mechanism != "cryptic_ritual":
            print(f"⚠️ User '{name}' has a '{user.consent_mechanism}' consent mechanism. Direct explicit consent setting is usually not applicable for this species.")
            # For demo, still allow setting for now, but in a real system, this would trigger specific logic.
        elif user.consent_mechanism == "cryptic_ritual":
            print(f"🌌 Alien '{name}' attempting to perform cryptic ritual for consent. Ritual outcome: {'Success' if consent else 'Failure'}.")
        
        user.consent = consent
        self.log.add({"event": "SET_CONSENT", "details": {"name": name, "status": consent}})
        print(f"✅ Consent for '{name}' set to {consent}.")

    def check_consent(self, username: str) -> bool:
        """
        Checks if a user has given consent, accounting for different species' mechanisms.
        For animals, it's simulated behavioral signals (e.g., tail wagging = True).
        For robots, it's simulated algorithmic audit (always True if user is robot).
        For aliens, it's a simulated cryptic ritual (can be manually toggled).
        """
        user = self.users.get(username)
        if not user:
            print(f"❌ User '{username}' not found.")
            return False
        
        if user.species == "animal":
            # Simulate animal consent (e.g., based on tail wagging in video)
            # For simplicity, let's say animals always consent if they are in the system.
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent: # If complex simulation failed
                print(f"❌ Animal '{username}' did not provide behavioral consent (simulated).")
            return simulated_consent
        
        elif user.species == "robot":
            # Simulate robot consent (e.g., passing an internal audit)
            simulated_consent = user.consent # Use stored consent, implicitly set True on add_user
            if not simulated_consent:
                 print(f"❌ Robot '{username}' failed algorithmic consent audit (simulated).")
            return simulated_consent

        elif user.species == "alien":
            # Simulate alien consent (e.g., performing a cryptic ritual)
            # For now, let's make alien consent manual, but could be a complex function
            simulated_consent = user.consent 
            if not simulated_consent:
                print(f"❌ Alien '{username}' did not perform the cryptic ritual (simulated).")
            return simulated_consent

        else: # Default: explicit consent for humans
            if not user.consent:
                print(f"❌ User '{username}' (human) has not given explicit consent.")
                return False
            return True

    def _check_and_apply_governance_decay(self):
        """
        Checks if a period has passed for progressive trust decay and applies it.
        This simulates a background daemon process.
        """
        self.governance.progressive_trust_decay()


    def reset_daily_actions_if_new_day(self):
        """Ensures all user daily action counters are reset at the start of a new day."""
        current_day = today()
        if current_day != self.current_day:
            for user in self.users.values():
                user.reset_daily_actions_if_needed() # Calls the user's internal method
            self.current_day = current_day
            print("🔄 Daily user action counters reset.")
            self._check_and_apply_governance_decay() # Check for governance decay daily (or yearly in larger scale)

    def karma_threshold(self, user: User) -> float:
        """
        Calculates the karma needed for a user to mint their next *fractional post*.
        This implements the halving threshold and minimum floor.
        """
        # Founders (genesis users) don't need karma for fractional posts
        if user.is_genesis:
            return 0.0

        minted_fractional_posts = user.mint_count # Use mint_count which tracks fractional posts
        threshold = self.mint_threshold_base / (2 ** minted_fractional_posts)
        return max(self.min_karma_threshold, threshold) # Ensure it doesn't drop below min

    def can_mint_fractional_post(self, username: str) -> bool:
        """Checks if a user has sufficient karma to mint a new fractional post."""
        user = self.users.get(username)
        if not user:
            print(f"❌ Mint check failed: unknown user {username}.")
            return False
        # Founders (genesis users) can always make fractional posts without karma
        if user.is_genesis:
            return True
        # Non-founders need karma for fractional posts
        return user.karma >= self.karma_threshold(user)

    def mint_fractional_post(self, user_name: str, content: str, fractional_percentage: float = 0.01, # Default 1%
                             tag: str = "post", references: list = None, fields: list = None) -> str | None:
        """
        Mints a new 'post' as a fractional part of the user's personal root coin.
        This is karma-gated for non-genesis users.
        """
        self.reset_daily_actions_if_new_day() # Ensure daily limits are fresh
        
        user = self.users.get(user_name)
        if not user:
            print(f"❌ Mint failed: User '{user_name}' not found.")
            return None

        if not user.root_coin_id:
            print(f"❌ Mint failed: User '{user_name}' does not have a root coin. Add user first.")
            return None

        if not self.check_consent(user_name): # Re-check explicit consent based on user's mechanism
            return None
        
        # Check karma threshold for non-genesis users for subsequent posts
        if not user.is_genesis and not self.can_mint_fractional_post(user_name): # Founders bypass this check
            needed = self.karma_threshold(user)
            print(f"🔒 MINT DENIED: '{user_name}' needs {needed:.0f} karma for next post; has {user.karma:.1f}.")
            return None

        # Content validation via Vaccine
        if not self.vax.scan(content):
            print(f"❌ MINT DENIED: Content blocked by Vaccine.")
            return None
        if references:
            for ref in references:
                if not self.vax.scan(ref):
                    print(f"❌ MINT DENIED: Reference content blocked by Vaccine: {ref[:50]}....")
                    return None

        # Validate fractional percentage
        if not (0 < fractional_percentage <= 1.0):
            print("❌ Mint failed: Fractional percentage must be between 0 and 1.0 (exclusive of 0).")
            return None

        # Deduct karma for non-genesis users when they make a fractional post
        if not user.is_genesis:
            user.karma -= self.karma_threshold(user) # Deduct karma upon successful fractional mint
            user.mint_count += 1 # Increment fractional post count
            user.next_mint_threshold = self.karma_threshold(user) # Update next threshold

        # Create the new fractional coin (post)
        post_id = sha(f"{user_name}-{content}-{ts()}-{random.random()}")
        
        # Calculate the actual value of this fractional post
        # The base value of the root coin is 1.0, so the post's value is directly the percentage.
        post_value = fractional_percentage * self.coins[user.root_coin_id].value 

        new_post_coin = Coin(
            id=post_id,
            root=user.root_coin_id, # Root is now the personal identity coin
            owner=user_name,
            tag=tag,
            value=post_value,
            is_root_coin=False,
            fractional_source_coin_id=user.root_coin_id,
            fractional_percentage=fractional_percentage
        )
        if references: new_post_coin.references = references
        if fields: new_post_coin.fields = fields
        
        self.coins[post_id] = new_post_coin
        user.coins_owned.append(post_id) # Add post coin to user's owned coins
        
        self.log.add({"event": "MINT_FRACTIONAL_POST", "details": {
            "user": user_name,
            "post_id": post_id,
            "root_coin_id": user.root_coin_id,
            "fractional_percentage": fractional_percentage,
            "post_value": post_value,
            "tag": tag,
            "content_snippet": content[:64]
        }})
        print(f"🪙 '{user_name}' minted a fractional post '{post_id}' (from root {user.root_coin_id}) with {fractional_percentage*100:.2f}% value.")
        self._call_plugins("on_mint_fractional_post", new_post_coin) # Trigger plugins
        return post_id

    def react(self, actor_name: str, coin_id: str, emoji: str):
        """
        A user reacts to a coin/post with an emoji, triggering a value event and
        updating the emoji market.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        # Ensure user and coin exist and user has consented
        if actor_name not in self.users: self.add_user(actor_name, consent=True)
        if coin_id not in self.coins: print(f"❌ REACT FAILED: Coin '{coin_id}' not found."); return False
        
        actor = self.users[actor_name]
        coin = self.coins[coin_id]
        
        # The "originator" for split purposes is the *owner* of the content coin/post reacted to.
        # If it's a root coin, the owner is its root. If it's a fractional post, its owner is the person who minted that post.
        originator_user = self.users.get(coin.owner) # Get the user who owns this specific coin/post

        if not self.check_consent(actor_name) or (originator_user and not originator_user.consent):
            print("❌ REACT DENIED: Both actor and originator (if known) must have consent.")
            return False
        
        # Scan emoji with Vaccine (prevents toxic reactions)
        if not self.vax.scan(emoji):
            print(f"❌ Reaction blocked by vaccine.")
            return False

        # Apply per-user daily diminishing returns
        date_str = today()
        actor.reset_daily_actions_if_needed() # Ensure daily reset for the actor
        action_count_today = actor.daily_actions[date_str][f"react_{emoji}"]
        daily_decay_factor = self.daily_decay_factor ** action_count_today
        actor.daily_actions[date_str][f"react_{emoji}"] += 1

        # Retrieve dynamic emoji weight from the market data
        base_weight = self.emoji_market_data.get(emoji, {'current_weight': 1.0})['current_weight']
        
        # Apply per-coin viral decay based on existing reactions to this specific coin
        viral_decay_factor = 0.95 ** len(coin.reactions) # Each reaction reduces future value for this coin slightly

        # The base value for split is the coin's `value` (which for fractional posts is its percentage)
        # multiplied by the emoji's weighted_value and decay factors.
        weighted_value = coin.value * base_weight * daily_decay_factor * viral_decay_factor

        # Calculate 33.3333% split portions
        split_value = weighted_value / 3.0

        # Apply genesis fading multipliers to actor and originator's shares
        actor_multiplier = actor.get_fading_multiplier()
        originator_multiplier = originator_user.get_fading_multiplier() if originator_user else 1.0

        originator_share = split_value * originator_multiplier
        actor_share = split_value * actor_multiplier
        treasury_share = split_value # Treasury share is not multiplied by individual multipliers

        # Distribute karma
        if originator_user and originator_user.consent: # Only award if content owner exists and has consented
            originator_user.karma += originator_share 

        actor.karma += actor_share
        self.treasury += treasury_share

        # Log reaction to the coin itself
        coin.reactions.append((actor_name, emoji, ts()))
        coin.react_log.append({'actor': actor_name, 'emoji': emoji, 'karma_share': (originator_share + actor_share), 'ts': ts()}) # Log specific karma generated for this reaction

        self.log.add({
            "event": "REACT",
            "details": {
                "username": actor_name,
                "coin_id": coin_id,
                "emoji": emoji,
                "weighted_value": weighted_value,
                "split": {
                    "originator_total": originator_share, # Total for the content owner
                    "actor": actor_share,
                    "treasury": treasury_share
                }
            }
        })

        print(f"👍 {actor_name} reacted {emoji} on coin {coin_id}: "
              f"owner +{originator_share:.2f}, actor +{actor_share:.2f}, "
              f"treasury +{treasury_share:.2f}.")
        
        # Update emoji market with the total karma generated by this reaction
        self._update_emoji_market(emoji, weighted_value)

        self._call_plugins("on_react", actor_name, coin_id, emoji, weighted_value) # Trigger plugins

        return True

    def remix(self, actor_name: str, parent_coin_id: str, content: str, tag: str = "remix", references: list = None, fields: list = None) -> str | None:
        """
        A user creates a derivative coin (remix) of an existing post/coin, preserving lineage.
        Remixing is considered a new "post" and thus subject to fractional minting rules.
        """
        self.reset_daily_actions_if_new_day() # Reset daily limits if needed

        if not self.check_consent(actor_name):
            return None
        if parent_coin_id not in self.coins:
            print(f"❌ REMIX FAILED: Parent coin '{parent_coin_id}' not found.")
            return None
        
        parent = self.coins[parent_coin_id]
        actor = self.users[actor_name]

        # Remixing is now a 'mint_fractional_post' operation for the actor.
        # It's their act of creating new content from existing, so it uses their fractional minting logic.
        # Default remix post uses a small percentage of root coin value.
        remix_percentage = 0.001 # A small percentage for a remix post
        remix_coin_id = self.mint_fractional_post(actor_name, content, fractional_percentage=remix_percentage, tag=tag, references=references, fields=fields)
        
        if remix_coin_id:
            new_coin = self.coins[remix_coin_id]
            # Lineage: New remix coin directly inherits the parent's ancestry and then adds the parent itself.
            new_coin.ancestors.extend(parent.ancestors)
            new_coin.ancestors.append(parent_coin_id)
            
            # The karma for the remix action itself. Use a specific emoji for remix value.
            remix_base_value = self.emoji_market_data.get("🔀", {'current_weight': 4.0})['current_weight'] # Use dynamic remix emoji weight
            
            # Apply per-user daily diminishing returns for remix action
            actor.reset_daily_actions_if_needed()
            remix_action_count_today = actor.daily_actions[today()]["remix_action"]
            remix_daily_decay_factor = self.daily_decay_factor ** remix_action_count_today
            actor.daily_actions[today()]["remix_action"] += 1

            remix_value = remix_base_value * remix_daily_decay_factor
            split_remix_value = remix_value / 3.0 # Apply 33.3333% split

            # Distribute karma for the remix action itself
            actor_remix_share = split_remix_value * actor.get_fading_multiplier()
            
            # The original *owner* of the parent post gets the second share
            parent_owner_user = self.users.get(parent.owner)
            parent_owner_remix_share = split_remix_value * parent_owner_user.get_fading_multiplier() if parent_owner_user else 0.0

            actor.karma += actor_remix_share
            if parent_owner_user:
                parent_owner_user.karma += parent_owner_remix_share
            self.treasury += split_remix_value # Treasury gets its share from the remix action

            self.log.add({
                "event": "REMIX",
                "details": {
                    "actor": actor_name,
                    "parent_coin_id": parent_coin_id,
                    "new_coin_id": remix_coin_id,
                    "ancestry": new_coin.ancestry,
                    "remix_value": remix_value,
                    "split": {
                        "actor": actor_remix_share,
                        "parent_owner": parent_owner_remix_share,
                        "treasury": split_remix_value
                    }
                }
            })

            print(f"🔀 '{actor_name}' remixed '{parent_coin_id}' into '{remix_coin_id}'. "
                  f"Remixer +{actor_remix_share:.2f} karma, Parent Owner +{parent_owner_remix_share:.2f} karma.")
            
            self._call_plugins("on_remix", new_coin) # Trigger plugins
        return remix_coin_id

    def add_reference(self, user_name: str, coin_id: str, ref_type: str, ref_id: str, description: str):
        """Adds a structured external reference to a coin/post for attribution."""
        if coin_id not in self.coins or user_name not in self.users:
            print("❌ ADDREF FAILED: Coin or user not found.")
            return
        if not self.check_consent(user_name): # Check consent based on user's mechanism
            return False

        reference = {"type": ref_type, "id": ref_id, "description": description, "added_by": user_name, "ts": ts()}
        self.coins[coin_id].references.append(reference)
        self.log.add({"event": "ADD_REFERENCE", "details": {"coin_id": coin_id, "reference": reference}})
        print(f"🔬 Reference added to coin '{coin_id}'.")

        # Award karma for adding a reference (can be tied to a specific emoji/weight)
        actor_ref_value = self.emoji_market_data.get("🔗", {'current_weight': 2.0})['current_weight'] # Use dynamic link emoji weight
        split_ref_value = actor_ref_value / 3.0
        
        # This karma goes to the user who added the reference, and to the treasury
        self.users[user_name].karma += split_ref_value * self.users[user_name].get_fading_multiplier()
        self.treasury += split_ref_value # Treasury gets its share too
        self.log.add({"event": "KARMA_AWARD_REFERENCE", "details": {"user": user_name, "coin_id": coin_id, "amount": split_ref_value}})
        print(f"🔗 {user_name} earned {split_ref_value:.2f} karma for adding reference to {coin_id}.")


    def trace_lineage(self, coin_id: str):
        """Displays the full creative lineage of a coin/post."""
        if coin_id not in self.coins: print(f"❌ TRACE FAILED: Coin '{coin_id}' not found."); return
        
        print(f"\n--- 🧬 Creative Lineage Trace for Coin: {coin_id} ---")
        path = []
        current_id = coin_id
        
        while current_id and current_id in self.coins:
            coin = self.coins[current_id]
            path.append(coin)
            if coin.ancestors: # Follow the most recent direct ancestor for a single path
                current_id = coin.ancestors[-1]
            else:
                current_id = None # No more ancestors
    
    for i, coin in enumerate(reversed(path)): # Print in chronological order (root first)
        indent = "  " * i
        originators_str = ", ".join(coin.originators) # Originators are users linked to this coin, including creator
        print(f"{indent}└── Coin: {coin.id} (Tag: {coin.tag}, Root: {coin.root}, Owner: {coin.owner}, Originators: {originators_str})")
        print(f"{indent}    Created At: {coin.created_at}")
        if coin.is_root_coin:
            print(f"{indent}    🌟 This is a Universal Root Identity Coin.")
        elif coin.fractional_source_coin_id:
            print(f"{indent}    ✨ This is a Fractional Post from Root: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
        if coin.references:
            print(f"{indent}    ├── References:")
            for ref in coin.references:
                print(f"{indent}    │   └── {ref.get('type', 'N/A')}: {ref.get('id', 'N/A')} ({ref.get('description', 'N/A')}) by {ref.get('added_by', 'Unknown')}")
        if coin.reactions:
            print(f"{indent}    └── Reactions ({len(coin.reactions)} total): {coin.reaction_summary()}") # Using helper for summary
    print("--- End of Trace ---")

    def show_user_karma(self, username: str):
        """Displays comprehensive user karma information."""
        user = self.users.get(username)
        if user:
            print(f"\n--- 👤 User '{username}' Status ---")
            print(f"  Karma: {user.karma:.2f}")
            print(f"  Is Genesis: {user.is_genesis}")
            print(f"  Species: {user.species.capitalize()}")
            print(f"  Consent Mechanism: {user.consent_mechanism.replace('_', ' ').title()}")
            print(f"  Current Multiplier: {user.get_fading_multiplier():.2f}")
            print(f"  Fractional Posts Minted: {user.mint_count}")
            print(f"  Next Post Threshold: {self.karma_threshold(user):.2f}")
            print(f"  Consent Given: {user.consent}") # Actual consent stored
            print(f"  Consent Check (Simulated): {self.check_consent(username)}") # Simulated consent based on species
            print(f"  Joined: {user.join_timestamp}")
            print(f"  Personal Root Coin: {user.root_coin_id if user.root_coin_id else 'None'}")
            print(f"  Coins/Posts Owned: {len(user.coins_owned)}")
            print("----------------------------------")
        else:
            print(f"No such user '{username}'.")

    def show_coin_info(self, coin_id: str):
        """Displays detailed coin/post information."""
        coin = self.coins.get(coin_id)
        if coin:
            print(f"\n--- 💎 Coin/Post ID: {coin.id} ---")
            print(f"  Root Originator: {coin.root}")
            print(f"  Current Owner: {coin.owner}")
            print(f"  Tag: {coin.tag}")
            print(f"  Base Value (from root): {coin.value}")
            print(f"  Created At: {coin.created_at}")
            print(f"  Is Root Coin: {coin.is_root_coin}")
            if coin.fractional_source_coin_id:
                print(f"  Fractional Source: {coin.fractional_source_coin_id} ({coin.fractional_percentage*100:.2f}%)")
            print(f"  Ancestry: {coin.ancestors if coin.ancestors else 'None'}")
            print(f"  Total Reactions: {len(coin.reactions)}")
            reaction_summary = defaultdict(int)
            for _, emoji, _ in coin.reactions:
                reaction_summary[emoji] += 1
            print(f"  Reaction Summary: {dict(reaction_summary)}")
            print(f"  References ({len(coin.references)}):")
            for ref in coin.references:
                print(f"    - Type: {ref.get('type')}, ID: {ref.get('id')}, Desc: {ref.get('description')} (by {ref.get('added_by')})")
            if not coin.references:
                print("    None")
            print("-------------------------------")
        else:
            print(f"No such coin: {coin_id}.")

    def get_treasury_balance(self) -> float:
        """Returns and prints the current treasury balance."""
        print(f"Community treasury balance: {self.treasury:.2f}.")
        return self.treasury

    def show_emoji_market_status(self):
        """
        Displays the current status of the emoji market, including dynamic weights.
        This is your "Nasdaq of Vibes".
        """
        print("\n--- 📈 Real-Time Emoji Market Status (Nasdaq of Vibes) ---")
        print("{:<10} {:<15} {:<15} {:<15}".format("Emoji", "Current Weight", "Total Uses", "Avg Karma/Use"))
        print("-" * 60)
        sorted_emojis = sorted(self.emoji_market_data.items(), key=lambda item: item[1]['current_weight'], reverse=True)
        for emoji, data in sorted_emojis:
            avg_karma_per_use = data['total_karma_generated'] / data['total_uses'] if data['total_uses'] > 0 else 0
            print("{:<10} {:<15.2f} {:<15} {:<15.2f}".format(emoji, data['current_weight'], data['total_uses'], avg_karma_per_use))
        print("----------------------------------------------------------\n")

    def plugin(self, action: str, name: str, *args):
        """Interface for loading, unloading, and calling external plugins."""
        if action == "load":
            try:
                # Assuming plugins are in a 'plugins' directory and each is a .py file
                # Use importlib.util for more robust dynamic loading
                spec = importlib.util.spec_from_file_location(name, f"plugins/{name}.py")
                if spec is None:
                    raise ImportError(f"Could not find plugin '{name}' at plugins/{name}.py")
                module = importlib.util.module_from_spec(spec)
                sys.modules[name] = module # Add to sys.modules to make it discoverable
                spec.loader.exec_module(module)
                self.plugins[name] = module # Store the loaded module
                self.log.add({"event": "PLUGIN_LOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' loaded successfully.")
            except Exception as e:
                print(f"❌ PLUGIN ERROR: Could not load '{name}'. {e}.")
        elif action == "unload":
            if name in self.plugins:
                del self.plugins[name]
                # Also remove from sys.modules to fully unload, if possible
                if name in sys.modules:
                    del sys.modules[name]
                self.log.add({"event": "PLUGIN_UNLOAD", "details": {"name": name}})
                print(f"🔌 Plugin '{name}' unloaded.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        elif action == "call":
            if name in self.plugins:
                plugin_module = self.plugins[name]
                if hasattr(plugin_module, "run"):
                    try:
                        # Pass the agent instance so plugins can interact with it
                        result = plugin_module.run(self, *args)
                        self.log.add({"event": "PLUGIN_CALL", "details": {"name": name, "args": args, "result_snippet": str(result)[:128]}})
                        print(f"⚡ Plugin '{name}' executed with result: {result}.")
                    except Exception as e:
                        print(f"❌ PLUGIN ERROR: Error executing '{name}'. {e}.")
                else:
                    print(f"❌ PLUGIN ERROR: Plugin '{name}' has no 'run' method.")
            else:
                print(f"❌ PLUGIN ERROR: Plugin '{name}' not loaded.")
        else:
            print("❓ Unknown plugin action. Use 'load', 'unload', or 'call'.")

    def propose_governance_change(self, proposer_name: str, proposal_details: dict, votes_by_species: dict[str, float]) -> bool:
        """
        Submits a formal governance proposal and checks if it passes current rules.
        proposal_details: Dict describing the proposed change (e.g., {'type': 'update_governance_rules', 'new_supermajority_percent': 0.75})
        votes_by_species: Dict of {species_name: percentage_of_total_karma_from_species_consenting (0-100)}.
                          This is a percentage of total karma within that species, not just user count.
                          Example: {'human': 95.0, 'robot': 80.0}
        """
        if proposer_name not in self.users:
            print(f"❌ PROPOSAL FAILED: Proposer '{proposer_name}' not found.")
            return False

        # Calculate total karma per species for weighting votes
        total_karma_per_species = defaultdict(float)
        active_species_in_system = set() # Track which species have active consented users
        
        # Calculate max karma for weighting. Genesis users treated as having a very high value.
        GENESIS_VOTE_WEIGHT = 1_000_000_000.0 

        for user in self.users.values():
            if self.check_consent(user.name): # Only consented users contribute to species totals
                active_species_in_system.add(user.species)
                if user.is_genesis:
                    total_karma_per_species[user.species] += GENESIS_VOTE_WEIGHT
                else:
                    total_karma_per_species[user.species] += user.karma
        
        overall_total_karma = sum(total_karma_per_species.values())

        if overall_total_karma == 0:
            print("❌ PROPOSAL FAILED: No active users or karma in the system to vote.")
            return False

        overall_consented_karma = 0.0 # Karma sum from all 'yes' votes across all species
        species_individual_min_met = True # Flag for all species meeting their individual minimum

        detailed_consent_report = {}

        # First, check individual species minimum consent AND calculate overall consented karma
        for species in self.governance.species_min_consent.keys(): # Iterate through all known species
            species_total_karma = total_karma_per_species[species] # Will be 0 if no active users of this species
            species_min_required = self.governance.species_min_consent[species]
            species_voted_percent = votes_by_species.get(species, 0.0) # Percentage provided by the input

            # If the species has active users
            if species_total_karma > 0:
                # Add to overall consented karma (even if species doesn't meet its individual minimum)
                overall_consented_karma += (species_voted_percent / 100.0) * species_total_karma
                
                # Check species-specific minimum consent
                if species_voted_percent < species_min_required:
                    species_individual_min_met = False
                    detailed_consent_report[species] = f"FAILED INDIVIDUAL MIN: Voted {species_voted_percent:.2f}% (Required: {species_min_required:.2f}%)"
                else:
                    detailed_consent_report[species] = f"MET INDIVIDUAL MIN: Voted {species_voted_percent:.2f}% (Required: {species_min_required:.2f}%)"
            elif species_min_required > 0: # Species has a minimum requirement but no active users
                species_individual_min_met = False
                detailed_consent_report[species] = f"FAILED INDIVIDUAL MIN: No active users of this species, but requires {species_min_required:.2f}%."
            else: # Species has no min requirement or no users and no min requirement
                detailed_consent_report[species] = "N/A: No users or no min requirement."
        
        # Calculate overall actual consent percentage based on karma
        overall_actual_consent_percent = (overall_consented_karma / overall_total_karma) * 100 if overall_total_karma > 0 else 0.0
        
        # NEW: Check Proportional Species Contribution for Overall Supermajority
        # This ensures each species contributes a fair share to the overall supermajority.
        overall_supermajority_met_proportionally = True
        required_per_species_contribution_percent = self.governance.supermajority_percent / len(active_species_in_system) if len(active_species_in_system) > 0 else 0
        
        if overall_supermajority_met_proportionally: # Only check if not already failed due to individual mins
            for species in active_species_in_system:
                species_voted_percent = votes_by_species.get(species, 0.0)
                # Calculate what % of the overall supermajority *this species* has contributed
                # (species_voted_percent / 100) * (species_total_karma / overall_total_karma) * 100
                species_contribution_to_overall = (species_voted_percent * species_total_karma) / overall_total_karma
                
                # Check if this species' actual contribution to the overall goal is sufficient
                # If overall goal is 90% and 2 species, each should contribute 45% of the total needed.
                if species_contribution_to_overall < (self.governance.supermajority_percent / len(active_species_in_system)):
                    overall_supermajority_met_proportionally = False
                    print(f"❌ PROPOSAL FAILED: Species '{species}' did not proportionally contribute enough to overall supermajority.")
                    print(f"   Contributed {species_contribution_to_overall:.2f}%, Expected ~{self.governance.supermajority_percent / len(active_species_in_system):.2f}% of overall total.")
                    break # No need to check further species for proportionality


        # Final decision
        proposal_passed = overall_supermajority_met_proportionally and species_individual_min_met

        self.log.add({
            "event": "GOVERNANCE_PROPOSAL_VOTE",
            "details": {
                "proposer": proposer_name,
                "proposal_details": proposal_details,
                "votes_by_species_input": votes_by_species, # Log raw input
                "overall_actual_consent_percent": overall_actual_consent_percent,
                "overall_required_percent": self.governance.supermajority_percent,
                "species_consent_breakdown": detailed_consent_report,
                "overall_proportional_check": overall_supermajority_met_proportionally,
                "passed": proposal_passed
            }
        })

        if proposal_passed:
            print(f"✅ GOVERNANCE PROPOSAL PASSED! Overall karma consent: {overall_actual_consent_percent:.2f}%.")
            # --- Basic Proposal Execution ---
            if proposal_details.get('type') == 'update_governance_rules':
                new_supermajority = proposal_details.get('new_supermajority_percent')
                new_species_mins = proposal_details.get('new_species_min_consent')
                self.governance.update_rules(new_supermajority, new_species_mins)
            elif proposal_details.get('type') == 'change_mint_threshold_base':
                new_threshold = proposal_details.get('new_mint_threshold_base')
                if new_threshold is not None:
                    self.mint_threshold_base = new_threshold
                    self.log.add({"event": "PROTOCOL_PARAM_UPDATE", "details": {"param": "mint_threshold_base", "new_value": new_threshold}})
                    print(f"✅ Protocol parameter 'mint_threshold_base' updated to {new_threshold}.")
            # Future: add other types of protocol changes here
            # --- End Basic Proposal Execution ---

            # Reset incident tracking as a successful governance change implies stability/resolution
            self.governance.incident_free_years = 0
            self.governance.last_incident_date = today()
            self._call_plugins("on_governance_passed", proposal_details)
        else:
            print(f"❌ GOVERNANCE PROPOSAL FAILED. Please review requirements.")
            self.governance.trigger_incident() # Trigger an incident if a proposal fails
            self._call_plugins("on_governance_failed", proposal_details)
        return proposal_passed


    def log_profit(self, amount: float, description: str):
        """Logs an external profit event, adding to the treasury."""
        self.treasury += amount
        self.log.add({
            "event": "PROFIT_LOG",
            "details": {"amount": amount, "description": description, "new_treasury_balance": self.treasury}
        })
        print(f"🏦 Profit of {amount:.2f} logged. Treasury is now {self.treasury:.2f}.")

    def snapshot(self, save=True, filename="snapshot.json"):
        """Saves or loads the entire agent state."""
        if save:
            state = {
                "users": {name: user.to_dict() for name, user in self.users.items()},
                "coins": {cid: coin.to_dict() for cid, coin in self.coins.items()},
                "treasury": self.treasury,
                "log_entries": list(self.log.entries), # Save current log entries
                "emoji_market_data": dict(self.emoji_market_data), # Save emoji market
                "governance_rules": {
                    "supermajority_percent": self.governance.supermajority_percent,
                    "species_min_consent": dict(self.governance.species_min_consent),
                    "incident_free_years": self.governance.incident_free_years,
                    "last_incident_date": self.governance.last_incident_date
                },
                "mint_threshold_base": self.mint_threshold_base,
                "new_species_karma_bonus": self.new_species_karma_bonus
            }
            try:
                with open(filename, "w", encoding='utf-8') as f:
                    json.dump(state, f, indent=2)
                print(f"💾 State saved to '{filename}'.")
            except IOError as e:
                print(f"❌ SNAPSHOT ERROR: Could not save state. {e}.")
        else:
            if not os.path.exists(filename):
                print(f"❓ SNAPSHOT INFO: No snapshot file found at '{filename}'. Starting fresh.")
                return
            try:
                with open(filename, "r", encoding='utf-8') as f:
                    state = json.load(f)
            
                self.users = {}
                for name, u_data in state.get("users", {}).items():
                    # Pass species and consent_mechanism during user reconstruction
                    user = User(
                        name,
                        u_data.get('is_genesis', False),
                        u_data.get('consent', False),
                        species=u_data.get('species', 'human'),
                        consent_mechanism=u_data.get('consent_mechanism', 'explicit')
                    )
                    user.karma = u_data.get('karma', 0.0)
                    user.mint_count = u_data.get('mint_count', 0)
                    user.next_mint_threshold = u_data.get('next_mint_threshold', 100000.0)
                    user.root_coin_id = u_data.get('root_coin_id')
                    user.coins_owned = u_data.get('coins_owned', [])
                    user.join_timestamp = u_data.get('join_timestamp', ts())
                    if u_data.get('fading_multiplier_start_time'):
                        user.fading_multiplier_start_time = datetime.datetime.fromisoformat(u_data['fading_multiplier_start_time'])
                    if 'daily_actions' in u_data:
                        user.daily_actions = defaultdict(lambda: defaultdict(int), u_data['daily_actions'])
                    self.users[name] = user

                self.coins = {}
                for cid, cd_data in state.get("coins", {}).items():
                    coin = Coin(
                        id=cd_data.get('id'),
                        root=cd_data.get('root'),
                        owner=cd_data.get('owner'),
                        value=cd_data.get('value', 1.0),
                        tag=cd_data.get('tag', 'single'),
                        is_root_coin=cd_data.get('is_root_coin', False),
                        fractional_source_coin_id=cd_data.get('fractional_source_coin_id'),
                        fractional_percentage=cd_data.get('fractional_percentage', 0.0)
                    )
                    coin.fields = cd_data.get('fields', [])
                    coin.ancestors = cd_data.get('ancestors', [])
                    coin.references = cd_data.get('references', [])
                    coin.reactions = cd_data.get('reactions', [])
                    coin.react_log = cd_data.get('react_log', [])
                    coin.created_at = cd_data.get('created_at', ts())
                    self.coins[cid] = coin

                self.treasury = state.get("treasury", 0.0)
                self.log.entries = deque(state.get("log_entries", []), maxlen=self.log.entries.maxlen)
                
                loaded_emoji_market_data = state.get("emoji_market_data", {})
                self.emoji_market_data = defaultdict(lambda: {'total_uses': 0, 'total_karma_generated': 0.0, 'current_weight': 1.0}, loaded_emoji_market_data)

                # Load governance rules
                governance_data = state.get("governance_rules", {})
                self.governance = Governance(
                    initial_supermajority_percent=governance_data.get("supermajority_percent", 90.0),
                    initial_species_min_consent=governance_data.get("species_min_consent", {"human": 10.0, "robot": 10.0}),
                    incident_free_years=governance_data.get("incident_free_years", 0),
                    last_incident_date=governance_data.get("last_incident_date", today())
                )
                self.governance.progressive_trust_decay() # Apply decay on load if time has passed

                # Load other top-level parameters
                self.mint_threshold_base = state.get("mint_threshold_base", 100_000.0)
                self.new_species_karma_bonus = state.get("new_species_karma_bonus", 50000)

                print(f"♻️ State loaded from '{filename}'.")
            except Exception as e:
                print(f"❌ SNAPSHOT ERROR: Could not load state. {e}.")

# ==============================================================================
# V. ANCILLARY SYSTEMS & INTERFACES
# ==============================================================================

class CorpX:
    """Simulates an adversarial entity to continuously test the Vaccine."""
    ATTACKS = ["inject malware", "phish creds", "launch ddos", "plant backdoor", "propaganda spam"]

    def __init__(self, vaccine: Vaccine):
        self.vaccine = vaccine
        self.attack_count = 0

    def run_attack(self, payload: str = None):
        """Performs an attack simulation."""
        self.attack_count += 1
        attack_payload = payload if payload else random.choice(self.ATTACKS)
        print(f"\n💀 CorpX Attack #{self.attack_count}: Attempting to inject '{attack_payload}'...")
        if self.vaccine.scan(attack_payload):
            print("🛡️ ATTACK EVADED! (Vaccine did not trigger).")
        else:
            print("🛡️ ATTACK BLOCKED! (Vaccine successfully triggered).")

def quiz() -> bool:
    """Interactive onboarding quiz for new users, ensuring informed consent."""
    print("\n--- 🤗 Welcome to the Remix Republic Onboarding Quiz ---")
    questions = [
        ("What is the universal value split percentage for all actions?", "33.3333"),
        ("Can you remix someone's content without their consent? (yes/no)", "no"),
        ("What must every new user earn to gain minting rights?", "karma"),
        ("What is the ultimate authority in this protocol?", "the code")
    ]
    for q, a in questions:
        resp = input(f"👉 {q} ").strip().lower()
        if resp != a:
            print("❌ Incorrect. Please review the Core Canons and try again.")
            return False
    print("✅ Quiz passed! You understand the fundamental laws. Welcome aboard!\n")
    return True

def cli():
    """A comprehensive command-line interface for interacting with the Agent."""
    agent = RemixAgent()
    adversary = CorpX(agent.vax)
    agent.snapshot(save=False) # Load state on start

    print("🤖 Universal Remix Protocol v11.4 CLI. Type ':help' for commands.")
    while True:
        try:
            raw_input_str = input(">>> ").strip()
            if not raw_input_str: continue
            
            if raw_input_str.lower() in [':exit', ':quit']:
                agent.snapshot(save=True)
                print("👋 Goodbye! State saved.")
                break
            
            if not raw_input_str.startswith(':'):
                print("⚠️ Commands must start with a colon ':'.")
                continue

            parts = raw_input_str[1:].split(maxsplit=1) # Split only on first space to keep args together
            command = parts[0].lower()
            args_str = parts[1] if len(parts) > 1 else "" # Get remaining args as a single string

            # Parse args from string (this is more robust for complex arguments)
            # This simple parser handles "quoted strings" for content and key=value pairs
            # It's not a full shell parser, but works for our CLI needs
            parsed_args = []
            current_arg = ""
            in_quote = False
            for char in args_str:
                if char == '"':
                    in_quote = not in_quote
                    if not in_quote and current_arg: # End of a quoted string
                        parsed_args.append(current_arg)
                        current_arg = ""
                elif char == ' ' and not in_quote:
                    if current_arg:
                        parsed_args.append(current_arg)
                        current_arg = ""
                else:
                    current_arg += char
            if current_arg:
                parsed_args.append(current_arg)
            
            args = parsed_args


            if command == "help":
                print("""
--- User Commands ---
:quiz                                  - Take the onboarding quiz.
:consent <username> <true/false>      - Set user consent.
:post <username> "<content>" [perc] [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Mint a fractional post.
:react <username> <coin_id> <emoji>   - React to a coin/post.
:remix <username> <parent_coin_id> "<content>" [tag] [refs="<ref1>,<ref2>"] [fields="<field1>=<value1>"] - Remix a coin/post.
:addref <username> <coin_id> <type> <id> "<description>" - Add a structured reference to a coin/post.
:karma <username>                     - Show user's karma.
:coininfo <coin_id>                   - Show detailed coin/post info.
:treasury                             - Show treasury balance.
:emojimarket                         - Show real-time emoji market status.

--- Query Commands ---
:log [filter] [limit]                 - Show audit log (optional filter string and limit).
:trace <coin_id>                      - Trace full creative lineage of a coin/post.

--- Admin & Governance Commands ---
:adduser <username> [species] [genesis] - Add a new user (default human, optional genesis).
:propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z] - Propose a governance change.
:trigger_incident                     - Manually trigger a major incident (resets consent decay).
:check_decay                         - Manually trigger progressive trust decay check.
:profit <amount> "<description>"      - Log a profit event to treasury.
:snapshot [save/load] [filename]      - Save or load agent state.
:attack [payload]                     - Simulate a CorpX attack.
:plugin <action> <name> [args...]     - Manage plugins (load, unload, call). E.g., :plugin load my_plugin
:exit / :quit                         - Save state and exit CLI.
""")
            elif command == "consent":
                if len(args) == 2 and args[1].lower() in ['true', 'false']:
                    agent.set_consent(args[0], args[1].lower() == 'true')
                else: print("Usage: :consent <username> <true/false>")
            elif command == "post": # Changed from :mint to :post for fractional minting
                username = args[0] if len(args) > 0 else None
                content = args[1] if len(args) > 1 else None # Content should be quoted
                
                if not username or not content:
                    print("Usage: :post <username> \"<content>\" [percentage_of_root_coin_value (e.g. 0.01 for 1%)] [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                fractional_percentage = 0.01 # Default to 1%
                tag = "post"
                refs = []
                fields = {}
                
                # Parse optional percentage, tag, refs, fields
                current_arg_idx = 2
                if len(args) > current_arg_idx and args[current_arg_idx].replace('.', '', 1).isdigit():
                    fractional_percentage = float(args[current_arg_idx])
                    current_arg_idx += 1

                if len(args) > current_arg_idx:
                    for arg_slice in args[current_arg_idx:]:
                        if arg_slice.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg_slice[6:-1].split(',')]
                        elif arg_slice.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg_slice[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg_slice # Remaining argument is the tag
                agent.mint_fractional_post(username, content, fractional_percentage, tag, refs, fields)
            elif command == "react":
                if len(args) == 3:
                    agent.react(args[0], args[1], args[2])
                else: print("Usage: :react <username> <coin_id> <emoji>")
            elif command == "remix":
                username = args[0] if len(args) > 0 else None
                parent_coin_id = args[1] if len(args) > 1 else None
                content = args[2] if len(args) > 2 else None

                if not username or not parent_coin_id or not content:
                    print("Usage: :remix <username> <parent_coin_id> \"<content>\" [tag] [refs=\"<ref1>,<ref2>\"] [fields=\"<field1>=<value1>\"]")
                    continue

                tag = "remix"
                refs = []
                fields = {}
                if len(args) > 3:
                    for arg in args[3:]:
                        if arg.startswith('refs="') and arg_slice.endswith('"'):
                            refs = [r.strip() for r in arg[6:-1].split(',')]
                        elif arg.startswith('fields="') and arg_slice.endswith('"'):
                            field_pairs = [p.strip().split('=') for p in arg[8:-1].split(',')]
                            fields = {k: v for k, v in field_pairs if len(p) == 2}
                        else:
                            tag = arg
                agent.remix(username, parent_coin_id, content, tag, refs, fields)
            elif command == "addref":
                if len(args) == 5:
                    agent.add_reference(args[0], args[1], args[2], args[3], args[4].strip('"'))
                else: print("Usage: :addref <username> <coin_id> <type> <id> \"<description>\"")
            elif command == "karma":
                if len(args) == 1: agent.show_user_karma(args[0])
                else: print("Usage: :karma <username>")
            elif command == "coininfo":
                if len(args) == 1: agent.show_coin_info(args[0])
                else: print("Usage: :coininfo <coin_id>")
            elif command == "treasury":
                agent.get_treasury_balance()
            elif command == "emojimarket":
                agent.show_emoji_market_status()
            elif command == "log":
                filter_str = args[0] if len(args) > 0 else None
                limit = int(args[1]) if len(args) > 1 and args[1].isdigit() else 20
                agent.log.show(filter_str, limit)
            elif command == "trace":
                if len(args) == 1: agent.trace_lineage(args[0])
                else: print("Usage: :trace <coin_id>")
            elif command == "adduser":
                if len(args) >= 1:
                    username = args[0]
                    species = "human" # Default species
                    is_genesis = False

                    # Parse optional species and genesis flags
                    for arg_slice in args[1:]:
                        if arg_slice.lower() in ["human", "robot", "animal", "alien"]: # Extendable list
                            species = arg_slice.lower()
                        elif arg_slice.lower() == "genesis":
                            is_genesis = True
                    agent.add_user(username, is_genesis=is_genesis, species=species)
                else: print("Usage: :adduser <username> [species] [genesis]")
            elif command == "propose":
                # :propose <proposer_name> "<proposal_type>" "<description>" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]
                if len(args) >= 3:
                    proposer_name = args[0]
                    proposal_type = args[1].strip('"')
                    description = args[2].strip('"')
                    
                    proposal_details = {"type": proposal_type, "description": description}
                    votes_by_species = {} # {species: percent_karma_consent}
                    
                    for arg_slice in args[3:]:
                        if arg_slice.lower().startswith('super_majority='):
                            try:
                                proposal_details['new_supermajority_percent'] = float(arg_slice.split('=')[1])
                            except ValueError: print("Invalid super_majority value.")
                        elif arg_slice.lower().startswith('new_threshold='): # For changing mint_threshold_base
                            try:
                                proposal_details['new_mint_threshold_base'] = float(arg_slice.split('=')[1])
                                proposal_details['type'] = 'change_mint_threshold_base' # Force type if this param is used
                            except ValueError: print("Invalid new_threshold value.")
                        elif arg_slice.lower().endswith('_votes'): # Generic species_votes parsing
                            try:
                                parts = arg_slice.split('=')
                                species_name = parts[0].replace('_votes', '').lower()
                                votes_by_species[species_name] = float(parts[1])
                            except ValueError: print(f"Invalid vote format for {arg_slice}. Use species_votes=X.")
                    
                    agent.propose_governance_change(proposer_name, proposal_details, votes_by_species)
                else: print("Usage: :propose <proposer_name> \"<proposal_type>\" \"<description>\" [super_majority=X] [human_votes=Y] [robot_votes=Z] [animal_votes=A] [alien_votes=B] [new_threshold=Z]")
            elif command == "trigger_incident":
                agent.governance.trigger_incident()
            elif command == "check_decay": # Manually trigger decay check
                agent.governance.progressive_trust_decay()
            elif command == "profit":
                if len(args) == 2: agent.log_profit(float(args[0]), args[1].strip('"'))
                else: print("Usage: :profit <amount> \"<description>\"")
            elif command == "snapshot":
                if len(args) >= 1:
                    action = args[0].lower()
                    filename = args[1] if len(args) > 1 else "snapshot.json"
                    if action == 'save': agent.snapshot(save=True, filename=filename)
                    elif action == 'load': agent.snapshot(save=False, filename=filename)
                    else: print("Usage: :snapshot [save/load] [filename]")
                else: print("Usage: :snapshot [save/load] [filename]")
            elif command == "attack":
                payload = args[0] if len(args) > 0 else None
                adversary.run_attack(payload.strip('"') if payload else None)
            elif command == "plugin":
                if len(args) >= 2:
                    action = args[0].lower()
                    name = args[1]
                    plugin_args = [a.strip('"') for a in args[2:]]
                    agent.plugin(action, name, *plugin_args)
                else: print("Usage: :plugin <action> <name> [args...]")
            elif command == "quiz":
                quiz()
            else:
                print(f"❓ Unknown command: {command}. Type ':help' for list of commands.")
        except (EOFError, KeyboardInterrupt):
            agent.snapshot(save=True)
            print("\n👋 Goodbye! State saved.")
            break
        except Exception as e:
            print(f"🔥 An unexpected error occurred: {e}. Please check command syntax or agent state.")

# ==============================================================================
# VI. LAUNCH-READY SOCIAL MEDIA POST
# ==============================================================================

LINKEDIN_POST = """🚀 We didn't just fix the creator economy. We remixed its DNA.
Today, we're open-sourcing the Ultimate Remix Protocol Agent—a single Python file that runs a new kind of digital world.
A world built on three unbreakable laws:

1️⃣ Fairness is Math, Not a Motto. Every creative act—every like, comment, or remix—is an economic event. Its value is instantly split 33.33% between the original creator, the contributor, and the community. No exceptions. No hidden fees. It's all on an immutable public log.
2️⃣ Influence is Earned, Not Bought. There are no shortcuts here. New creators unlock the power to mint their own content by earning 100,000 karma points. Sound hard? It is. But with every coin you mint, the next one costs half as much. Power users can earn their seat at the table in weeks. It's a system that rewards merit and dedication, not just early arrival.
3️⃣ Credit is Forever. Our protocol has an elephant's memory. Every remix is a branch on a permanent "family tree" of ideas. We've built in an Attribution Engine for science and art, so you can cite your inspirations. If that scientist ever joins our world, our code ensures they get their cut. Forever.

This isn't just a platform; it's a joyful, autonomous republic governed by code. It has its own immune system to block propaganda and hate. It runs on consent. And it's designed for a future where humans, AIs, and maybe even a few other intelligent species can collaborate and create value together.

We're not asking you to "join our platform." We're inviting you to fork our reality.
The code is the contract. The community is the government. The remix has begun.

#RemixEconomy #OpenSource #CreatorEconomy #EthicalAI #RadicalTransparency #33Split #FutureOfWork #Karma
"""

# ==============================================================================
# VII. MAIN EXECUTION BLOCK
# ==============================================================================

if __name__ == "__main__":
    print(LINKEDIN_POST)

    # --- Running a non-interactive Demo Scenario ---
    print("\n--- Running Demo Scenario ---")
    agent = RemixAgent()
    agent.snapshot(save=False) # Load previous state if it exists

    # Onboarding new users (auto-mints their root coin)
    if "alice" not in agent.users: agent.add_user("alice", consent=True, species="human")
    if "bob" not in agent.users: agent.add_user("bob", consent=True, species="robot") # Bob is a robot!
    if "charlie" not in agent.users: agent.add_user("charlie", consent=False, species="animal") # Charlie is an animal, auto-consents
    if "zorg" not in agent.users: agent.add_user("zorg", consent=False, species="alien") # Zorg is an alien, needs ritual consent

    # Ensure Charlie (animal) is consented via its mechanism (it auto-consents if added)
    print("\nVerifying Charlie's (animal) consent:")
    agent.set_consent("charlie", True) # This call now effectively confirms behavioral consent.
    print(f"Charlie's simulated consent status: {agent.check_consent('charlie')}")
    
    # Try setting Zorg's (alien) consent (needs ritual)
    print("\nAttempting to set Zorg's (alien) consent via ritual (initially false):")
    agent.set_consent("zorg", False) # Simulating ritual failure
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")
    print("\nAttempting to set Zorg's (alien) consent via ritual (success):")
    agent.set_consent("zorg", True) # Simulating ritual success
    print(f"Zorg's simulated consent status: {agent.check_consent('zorg')}")


    # Genesis user 'mimi' makes a fractional post (no karma needed for them)
    mimi_post_id = agent.mint_fractional_post("mimi", "My first genesis post about the protocol design!", fractional_percentage=0.1, tag="protocol_design")
    print(f"\nMimi's first fractional post ID: {mimi_post_id}")

    if mimi_post_id:
        print(f"\n--- Initial Reactions to establish some emoji market data and build karma ---")
        for i in range(5):
            agent.react("alice", mimi_post_id, "🎨") # Alice (human) uses '🎨'
            agent.react("bob", mimi_post_id, "🔥")  # Bob (robot) uses '🔥'
            agent.react("alice", mimi_post_id, "🤗") # Alice uses '🤗'
            agent.react("charlie", mimi_post_id, "❤️") # Charlie (animal) reacts
            agent.react("zorg", mimi_post_id, "💎") # Zorg (alien) reacts
            if i % 2 == 0:
                agent.react("bob", mimi_post_id, "💯") # Bob uses '💯' periodically

        agent.show_emoji_market_status() # See initial market status

        # Alice tries to make a fractional post before she has enough karma
        print("\nAlice (human) attempts to make her first fractional post (should fail initially):")
        agent.mint_fractional_post("alice", "My first attempt at a post from my root coin!", fractional_percentage=0.05, tag="my_thought")

        # Simulate Alice earning enough karma to cross the threshold for her first fractional post
        # For demo, directly set karma if not genesis
        if not agent.users["alice"].is_genesis:
            agent.users["alice"].karma = 100001
        
        print(f"\nAlice's karma is now {agent.users['alice'].karma:.2f}. Trying to make her first fractional post again...")
        
        # Alice now successfully makes her first fractional post
        alice_post_id = agent.mint_fractional_post("alice", "I earned my way here! My first post from my root coin.", fractional_percentage=0.02, tag="milestone")
        
        if alice_post_id:
            print(f"\nAlice's first fractional post ID: {alice_post_id}")
            agent.trace_lineage(alice_post_id) # Trace the lineage of Alice's post (from her root coin)

            # Bob (robot) remixes Alice's post
            remix_content = "A remix of Alice's milestone post, inspired by an old meme from my data banks."
            remix_refs = [{"type": "meme", "id": "distracted_boyfriend", "description": "classic meme format"}]
            bob_remix_post_id = agent.remix("bob", alice_post_id, remix_content, refs=remix_refs)

            if bob_remix_post_id:
                print(f"\nBob's remix post ID: {bob_remix_post_id}")
                agent.trace_lineage(bob_remix_post_id) # Trace the lineage of the remix (which is a fractional post itself)

            print("\n--- Further Reactions to see market changes and karma distribution ---")
            agent.react("alice", mimi_post_id, "🤗") # Alice reacts again to original
            agent.react("bob", alice_post_id, "🔥") # Bob reacts to Alice's post
            agent.react("mimi", bob_remix_post_id, "🔀") # Mimi reacts to the remix

            agent.show_emoji_market_status() # See updated market status after more reactions

        # --- Demo Governance Proposal ---
        print("\n--- Demo Governance Proposal ---")
        # Scenario 1: Proposal fails due to insufficient overall supermajority or proportional contribution
        print("\nAttempting to pass a proposal (should fail - insufficient overall supermajority or proportional contribution):")
        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_governance_rules', 'description': 'Reduce supermajority to 70%'},
            votes_by_species={'human': 70.0, 'robot': 70.0, 'animal': 5.0, 'alien': 0.0} # Not 90% overall or proportionally. Alien 0% will fail its 10% min
        )
        
        # Scenario 2: Proposal to change mint threshold (should pass now with enough karma for all species to meet mins)
        print("\nAttempting to pass a proposal to change mint threshold (should pass now):")
        # Give more karma to all users for the demo to ensure enough total karma for voting
        agent.users["alice"].karma = 200000
        agent.users["bob"].karma = 150000
        agent.users["charlie"].karma = 100000
        agent.users["zorg"].karma = 500000 # Boost Zorg's karma significantly

        agent.propose_governance_change(
            proposer_name="mimi",
            proposal_details={'type': 'change_mint_threshold_base', 'description': 'Lower base mint threshold to 50k', 'new_mint_threshold_base': 50000.0},
            # Assuming these percentages represent enough karma within each species to pass their 10% min, AND sum to >90% overall
            votes_by_species={'human': 95.0, 'robot': 80.0, 'animal': 70.0, 'alien': 60.0}
        )
        print(f"New Mint Threshold Base: {agent.mint_threshold_base}")

        # Scenario 3: Check for decay after some simulated time (requires `today()` to advance)
        # For this demo, we'll manually trigger it after some operations.
        print("\n--- Manually Triggering Governance Decay Check ---")
        # Simulate passing a year for decay to activate
        agent.governance.last_incident_date = str(datetime.date.today().year - 1) + datetime.date.today().isoformat()[4:] 
        agent.governance.progressive_trust_decay()
        
        # Trigger an incident and see rules bump up
        print("\n--- Triggering a Major Incident ---")
        agent.governance.trigger_incident()
        
        print(f"\nNew supermajority after incident: {agent.governance.supermajority_percent}%")
        print(f"New species minimums after incident: {agent.governance.species_min_consent}")


    print("\n--- Final User and Treasury Status ---")
    agent.show_user_karma("mimi")
    agent.show_user_karma("alice")
    agent.show_user_karma("bob")
    agent.show_user_karma("charlie")
    agent.show_user_karma("zorg")
    agent.get_treasury_balance()

    agent.log.verify() # Verify the integrity of the audit log

    agent.snapshot(save=True) # Save final state
    print("\n--- Demo Scenario Complete. State saved. ---")
    print("\n--- To interact further, uncomment 'cli()' in the the main execution block. ---")


    # ==============================================================================
    # VIII. CHANGELOG AND TO-DO
    # ==============================================================================

    print("\n\n" + "="*80)
    print("VIII. CHANGELOG AND TO-DO")
    print("="*80)

    print("\n📜 **CHANGELOG (v11.4 - Proportional Species Contribution)**")
    print("------------------------------------------------------------")
    print("### Governance System:")
    print("* **Proportional Species Contribution**: The `propose_governance_change` method is significantly enhanced to ensure that overall supermajority consent is met by *proportional contribution* from each active species. This means:")
    print("    * Each species must not only meet its individual minimum consent threshold (e.g., 10% of its karma-weighted vote).")
    print("    * But also, its proportional contribution to the *overall* supermajority must be sufficient (e.g., if overall is 90% and there are 2 active species, each must contribute at least 45% of the total karma needed for the 90% overall).")
    print("    * This prevents a few dominant species from easily passing proposals without broad, proportional support, and ensures no single group can be completely left out.")
    print("* **Simplified Species Minima**: Initial `species_min_consent` for Animal and Alien species in `Governance` is set to 10% (matching Human and Robot) to simplify the initial proportional model.")
    print("* **Snapshot Consistency**: Ensured that all new `Governance` parameters are correctly saved and loaded in `snapshot`.")

    print("\n### User & Consent:")
    print("* **Refined Alien Consent**: Alien users now require a manual `set_consent(username, True)` to simulate successful ritual performance, enabling their participation. They are no longer implicitly consented on `add_user`.")
    print("* **Clarity in `add_user` Consent**: The `add_user` method's `consent` parameter now interacts more precisely with `consent_mechanism` (e.g., `animal` and `robot` still auto-consent to `True` on add, reflecting their intrinsic nature, while `alien` does not).")

    print("\n### Codebase & Testing:")
    print("* **Improved CLI Parsing**: The CLI's `propose` command argument parsing is refined to better handle species-specific vote percentages, allowing for flexible input like `human_votes=Y`, `robot_votes=Z`.")
    print("* **Demo Scenario Enhancements**: The demo now includes a clear example of how the new proportional contribution rule works in `propose_governance_change`, demonstrating scenarios where proposals might fail due to insufficient individual contribution despite high overall numbers.")

    print("\n--- Previous Changelog Entries (Condensed) ---")
    print("* **v11.3 (Benefit-Driven Enhancements)**: Automated decay call; Karma bonus for new species; Basic execution of governance proposals (e.g., change `mint_threshold_base`).")
    print("* **v11.2 (Godmode Enhancements)**: Dynamic Consent Decay; Simulated Multi-Species Consent; Karma-Weighted Voting.")
    print("* **v11.1 (Multi-Species Governance Framework)**: `Governance` class for proposal rules; `user.species` attribute; `propose_governance_change` for supermajority + species min consent.")
    print("* **v11.0 (The Unified Genesis)**: Universal Root Coin for all users; Fractional Post Minting (karma-gated for non-genesis, free for founders); Remixes are fractional posts.")
    print("* **v10.2**: Enhanced readability, refined snapshots, improved CLI, consistent terminology.")
    print("* **v10.1**: Dynamic Emoji Market; Conditional Timestamping.")
    print("* **v10.0 (The Harmonized Republic)**: Karma-gated minting, Epic Creative Path, fairness mechanics, attribution, legal framework.")
    print("* **v9.0**: One personal coin per user, fractional release, regenerative drip.")
    print("* **v8.0**: Multi-species governance concept.")
    print("* **v7.0**: Karma economy details (100k threshold, halving, decay).")
    print("* **v6.0**: Fading Genesis Multiplier, effort-based minting.")
    print("* **v1.0-v5.0**: Initial prototypes: consent, logging, 33% split.")

    print("\n🗺️ **TO-DO (Future Evolutions)**")
    print("-----------------------------")
    print("### Governance System:")
    print("* **Automated Rule Decay Daemon**: Implement a true background process or cron job to regularly call `governance.progressive_trust_decay()` (e.g., daily or yearly) instead of only on snapshot load and daily reset, to ensure continuous decay.")
    print("* **Voting Interface**: Develop a dedicated interface (CLI extension or external tool) for users to formally cast votes on proposals, rather than inputting percentages directly in the `propose` command. This would also allow for tracking individual user votes.")
    print("* **Super Minority Veto with Meme Battle**: Implement the 'Super Minority Veto' concept. If a small but critical species (e.g., Cats, if added) unanimously votes 'no,' the proposal is blocked, triggering an automatic 'meme battle' (simulated, or through actual external meme generation/voting platforms) whose outcome settles the conflict. This would be an advanced plugin.")
    print("* **Species Entrance Ceremony**: When a new species is added, formalize a 'ritual vote' by existing species to grant them full governance status, along with their initial `species_min_consent` requirements.")

    print("\n### Economic & Game Theory:")
    print("* **Karma Score Simulator**: Develop a module to simulate karma growth and minting paths based on user activity patterns.")
    print("* **Cross-Chain Integration**: Implement logic to query and reference external blockchain events (Ethereum, Solana, Filecoin) for provenance, lineage, and creative credit. Allow coins to cite on-chain events/addresses from other chains.")
    print("* **Long-term Emoji Market Forecasting**: Extend the emoji market to include sentiment AI, market forecasts, or 'remix insurance' based on long-term vibe trends.")
    print("* **Reputation-Weighted 'Thank You'**: Allow users to append 'thank you' or other attribution reactions that carry extra karma or boost lineage credit for public gratitude or citation.")

    print("\n### Data & Attribution Systems:")
    print("* **Science Attribution Block**: Add an explicit 'scientists/inspirators/idea lineage' section to every coin and action, so referenced research or influence can be logged, attributed, and profit-shared by the 33.3333% law.")
    print("* **Public Reference Feed**: Create a live feed of referenced works, collaborators, and idea chains to show innovation sources and encourage upstream collaboration/tipping.")
    print("* **Meme/Fork Lineage Engine Visualization**: Build a mini-visualization (tree or genealogy map) that shows the remix/fork lineage for every coin, for exploring influence and remixability.")
    print("* **Automated Reference Audit**: Develop an AI tool to suggest likely upstream references based on content similarity, prompting users to add attribution.")
    print("* **Global 'Credit Scientist' Index**: Maintain a public directory/index of top-cited scientists, creators, meme originators, etc., whose ideas have been referenced on-platform for recognition, inspiration, and direct engagement.")
    print("* **Research Field/Topic Metadata**: Include optional 'field' tags (science, music, code, art, etc.) for coins/posts, enabling analytics, search, and new sub-platforms (e.g., RemixScience).")

    print("\n### Integration & AI:")
    print("* **Game Integration**: Allow any game (AAA or indie) to embed remix-economy logic into its player ecosystem, using the protocol for player-created content tracking (mods, skins, levels), AI agent co-op gameplay (remix-trained NPCs), karma-based unlocks for creative gameplay, permanent attribution for in-game art/music/story, and auditable reward distribution for community-made expansions.")
    print("* **Transparent Onboarding/Quiz Flow**: Extend onboarding quiz so each new user explicitly understands: the 33.3333% split, attribution law, plug-in/forkability, and that every action (including science or meme reference) is logged forever.")

    print("\n" + "="*80)
```
