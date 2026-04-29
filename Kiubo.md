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

---

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

---

## Developer‑Facing

A Unity dev imports the Kiubo package and gets:

### **A simple API**
```csharp
Kiubo.Start();
Kiubo.OnEncounter += (Encounter e) => { GrantReward(e); };
Kiubo.GetEncounterHistory();
Kiubo.Sync();
```

### **Cross‑platform mobile SDK**
- BLE beaconing  
- BLE scanning  
- Background‑safe encounter logging  
- Privacy‑safe IDs  
- Battery‑optimized scanning  

### **Optional backend**
- Encounter validation  
- Anti‑spoofing  
- Player linking (PC/console ↔ phone)  
- Analytics  

### **Unity editor tools**
- Encounter simulator  
- Reward rule editor  
- Encounter heatmap viewer  

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

# 7. Kiubo — Business Model
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

# 8. Why It Could Succeed**
Because it gives Unity devs:

- A social mechanic they can’t build alone  
- A feature players *love*  
- A way to add real‑world magic to any genre  
- A cross‑platform system that works with PC/console games  
- A unique selling point for their game  

And because **no one else is offering this**.

