[[toc]]

# 1. Core Concept

**Kiubo = a cross‑device encounter engine for games.**  
When two players with the companion app come near each other, something happens in the game world.

The magic is in the *passive*, *serendipitous*, *real‑world* encounter.

Think:  
- StreetPass  
- Pokémon GO Adventure Sync  
- Find My network  
- Bluetooth beacons  
- Distributed presence  

But packaged for Unity devs.


# 2. What It *Does* 

## Player‑Facing

When two players cross paths IRL:

- They “Kiubo” each other  
- Each gets a reward, buff, or collectible  
- The encounter is logged in their Kiubo journal  
- The game can react in unique ways  

Examples:

- **RPG:** “You met 3 adventurers today → +5% XP for 1 hour”  
- **Survival:** “Nearby survivor spotted → shared map intel unlocked”  
- **City builder:** “Kiubo with 10 players → unlock special building”  
- **MMO:** “Encounter streak → cosmetic badge”  
- **AR game:** “Kiubo chain → summon a rare event”  

Kiubo becomes a **social meta‑layer** that any game can plug into.


## Developer‑Facing

A Unity dev imports the Kiubo package and gets:

### A simple API
```csharp
Kiubo.Start();
Kiubo.OnEncounter += (Encounter e) => { GrantReward(e); };
Kiubo.GetEncounterHistory();
Kiubo.Sync();
```

### Cross‑platform mobile SDK
- BLE beaconing  
- BLE scanning  
- Background‑safe encounter logging  
- Privacy‑safe IDs  
- Battery‑optimized scanning  

### Optional backend
- Encounter validation  
- Anti‑spoofing  
- Player linking (PC/console ↔ phone)  
- Analytics  

### Unity editor tools
- Encounter simulator  
- Reward rule editor  
- Encounter heatmap viewer  



# Audience


### Primary
- Community‑driven games  
- Live service games  
- Collecting/progression games  
- AR/exploration games  

### Secondary
- Competitive/event‑driven games  
- Indies seeking differentiation  
- Cross‑platform ecosystems  

### Tertiary
- Fitness games  
- Educational or tourism games  
- Local multiplayer experiences  


---

# 3. Identity & Branding

Kiubo has a *personality*:

- Friendly  
- Social  
- Latin‑American flavor  
- Casual and warm  
- “Hey, I saw you!” energy  

Possible taglines:

- **“Kiubo: When players cross paths, worlds connect.”**  
- **“Turn real‑world encounters into in‑game magic.”**  
- **“Your game, now with serendipity.”**  

Visual identity:

- Rounded shapes  
- Bright colors  
- Motion lines (like someone waving)  
- A mascot or icon shaped like a waving bubble  

---

# 4. Risks and Mitigations 

Kiubo can fail if:

- It fights iOS instead of working with it.  
- It drains battery or data.  
- It’s unreliable under bad networks.  
- It locks devs into your backend.  
- It becomes a PII pipeline.

So the design needs to be:

- **Opportunistic, not constant** (for iOS & battery).  
- **Local‑first, sync‑later** (for reliability).  
- **Backend‑agnostic, protocol‑centric** (for dev control).  
- **Minimal, rotating IDs only** (for security & privacy).


### 1. iOS mobile restrictions

**Main problems:**

- **Background BLE scanning is heavily limited** (time‑sliced, throttled, mode‑dependent).  
- **Background execution requires specific modes** (location, Bluetooth, VOIP, etc.).  
- Apps that “just sit there scanning” will be killed or rejected.

**Mitigations:**

- **Use OS‑blessed patterns:**
  - Register as a **Bluetooth accessory interaction** use case (where appropriate).
  - Use **background modes** only where they clearly match Apple’s guidelines.
- **Design for “opportunistic encounters” instead of constant scanning:**
  - Scan in **short bursts** when:
    - The app is opened.
    - The user performs a relevant action (open map, open Kiubo screen).
    - The OS wakes the app for other reasons (push, location, etc.).
- **Leverage push + server matching:**
  - Let the phone upload encounter “beacons” periodically.
  - Do **co‑presence matching** on the server when BLE is unavailable.
- **Explicit UX:**
  - Make Kiubo an **opt‑in feature** with clear explanation: “Allow nearby encounters for in‑game bonuses.”

**Design principle:**  
Kiubo must **degrade gracefully** on iOS: fewer encounters, not broken behavior.



### 2. Battery and data usage

**Main risks:**

- Continuous BLE scanning → battery drain.  
- Frequent network sync → data usage complaints.  
- Devs fear “this SDK will tank my app’s reviews.”

**Mitigations:**

- **Hard technical limits in the SDK:**
  - Duty‑cycle BLE scanning (e.g., scan 5s every X minutes, configurable).
  - Adaptive scanning: reduce frequency when:
    - Battery is low.
    - No encounters have been seen for a long time.
- **Local‑first design:**
  - Log encounters locally.
  - **Batch sync** to server (e.g., every N encounters or every Y minutes, or on Wi‑Fi only).
- **Configurable policies for devs:**
  - `KiuboPowerProfile.Low/Medium/High`
  - `SyncPolicy.WifiOnly / WifiOrCellular / Manual`
- **Transparent metrics:**
  - Provide devs with **battery & data usage estimates** in docs and sample analytics.

**Design principle:**  
Kiubo must be **resource‑polite by default**, with “aggressive” modes opt‑in and clearly labeled.



### 3. Offline vs online, and reliability of “did Kiubo happen?”

**Main risks:**

- Player: “We were next to each other, why didn’t it trigger?”  
- Dev: “I can’t debug if encounters are lost.”  
- Network flakiness causing desync between phone and game account.

**Mitigations:**

- **Local truth first:**
  - When two phones detect each other, **that encounter is final** on the device.
  - It gets a **local encounter ID**, timestamp, and minimal peer ID.
- **Deferred sync:**
  - If offline, encounters are queued.
  - When online, they sync to the server and then to the game account.
- **Idempotent server API:**
  - Encounters have unique IDs.
  - Re‑sending the same encounter is safe (server ignores duplicates).
- **Clear states in API:**
  - `EncounterStatus.LocalOnly`, `Synced`, `RewardGranted`.
- **Game‑side UX:**
  - “You had 3 Kiubos while offline—rewards will sync when you’re online.”

**Design principle:**  
**Encounter detection and logging must not depend on network.** Online is for validation and rewards, not for deciding if Kiubo “happened.”



### 4. Full developer control and server agnosticism

**Main risks:**

- Lock‑in: devs don’t want to depend on your SaaS.  
- Legal/compliance: some studios must self‑host.  
- Tech stack diversity: Unity on client, anything on server.

**Mitigations:**

- **Open, documented HTTP API spec:**
  - Define a **minimal, stable JSON schema**:
    - `POST /encounters`
    - `GET /encounters`
    - `POST /linkPlayer`
  - No tech assumptions: just HTTP + JSON.
- **Reference implementations:**
  - Sample servers in Node, Go, Python, etc.
  - Docker compose example.
- **Pluggable backend in Unity SDK:**
  - Default: “Kiubo Cloud” (your SaaS).
  - Custom: dev provides base URL + auth + handlers.
- **No hidden logic:**
  - All encounter semantics are client‑visible.
  - Server is just validation + reward logic.

**Design principle:**  
Kiubo is a **protocol + client SDK**, not “our servers or nothing.”



### 5. Data security and PII avoidance

**Main risks:**

- Being responsible for PII.  
- Regulatory exposure (GDPR, etc.).  
- Devs misusing Kiubo payload to send sensitive data.

**Mitigations:**

- **Fixed, minimal payload by design:**
  - Kiubo peer ID (random, rotating, non‑reversible).
  - Encounter ID.
  - Timestamp.
  - Optional coarse context (e.g., “mode”, not GPS).
- **No built‑in fields for:**
  - Names, emails, phone numbers, IPs, GPS coordinates.
- **Rotating identifiers:**
  - Use **ephemeral IDs** (like exposure notification systems).
  - Server can map ephemeral → player account, but SDK never exposes stable IDs to other clients.
- **Custom data as dev responsibility:**
  - If devs want to attach game‑specific data, they:
    - Do it via their own server.
    - Not via Kiubo’s encounter payload.
- **Clear legal stance in docs:**
  - “Kiubo is not intended for transmitting PII. The SDK does not expose fields for PII. Any additional data you attach on your own backend is your responsibility.”

**Design principle:**  
Kiubo’s **core protocol is PII‑hostile by design**—you literally can’t misuse it for personal data without going out of your way.



# 5. Technical Modes

Kiubo can support multiple encounter modes:

### Mode A — BLE Encounter Mode (default)
Closest to StreetPass.  
Phones detect each other via BLE.

### Mode B — Co‑Presence Mode
Phones log location → server matches players who were in the same place.

### Mode C — Event Mode
QR/NFC scanning for conventions or meetups.

### Mode D — Party Mode
Local Wi‑Fi discovery for LAN‑like encounters.

### Mode E — Cloud‑Linked Mode
PC/console players link their account to the phone app.

---

# 6. Game Design Patterns
Kiubo enables new mechanics:

### **1. Encounter Streaks**
Meet someone daily → escalating rewards.

### **2. Encounter Types**
- Stranger  
- Friend  
- Guildmate  
- Rival  
- Rare encounter (low probability)  

### **3. Encounter Collections**
Like StreetPass puzzle pieces.

### **4. Encounter‑Triggered Events**
Boss spawns, loot drops, buffs.

### **5. Encounter Economy**
Encounters generate a currency (“Kiubits”?).

### **6. Encounter Social Graph**
Players build a map of who they’ve crossed paths with.

---

# 7. Business Model
You can monetize Kiubo as:

### Asset Store Package
- $50–$150  
- One‑time purchase  
- Includes Unity plugin + mobile SDK  

### SaaS Backend (optional)
- Free tier: 10k encounters/month  
- Paid tiers for bigger games  
- Analytics dashboard  

### Enterprise License
For studios needing custom features.

---

# 8. Why It Could Succeed
Because it gives Unity devs:

- A social mechanic they can’t build alone  
- A feature players *love*  
- A way to add real‑world magic to any genre  
- A cross‑platform system that works with PC/console games  
- A unique selling point for their game  

And because **no one else is offering this**.

