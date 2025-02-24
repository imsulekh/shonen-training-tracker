# shonen-training-tracker
"Train like Goku. Grind like Asta. Level up like an MC."

📝 Project Overview
The Shonen Training Tracker is a gamified fitness and self-improvement platform that lets users train like anime protagonists and gain XP, levels, and special abilities based on real-life workouts, study sessions, and discipline-building tasks.

💪 Train hard. Become overpowered. Unlock ultimate techniques.

🔥 If you slack off? Your XP drops, and the system treats you like a side character.

🎯 Core Features

1️⃣ User Registration & MC Classification
Users register and get assigned a Shonen MC Type based on their training goals:
🏋️ Brawler (Strength-focused) – Like Baki or Goku
⚡ Speedster (Agility-focused) – Like Killua or Rock Lee
📚 Strategist (Intelligence-focused) – Like Light Yagami or Lelouch
💥 Balanced (All-around Growth) – Like Deku
MC Classification determines XP scaling & skill progression.

2️⃣ Training & XP System
Users earn XP by completing real-world training activities:

Activity	XP Gain	Notes
Running 1 km	+20 Agility XP	Speed-focused MCs get a bonus
Lifting Weights	+30 Strength XP	Brawlers gain extra XP
Studying 1 Hour	+40 Intelligence XP	Strategists gain extra XP
Martial Arts	+50 Fighting XP	Unlocks new attack moves
Waking up early	+10 Discipline XP	Consistency matters
Skipping Training	-50 XP	You get weaker.
⚡ Combo Training Bonus

If you train multiple days in a row, you get streak bonuses (stored in Redis).
Miss 3 days? You lose your streak and take a “Plot Armor Nerf” (XP penalty).

3️⃣ Skill Tree & Level Progression
As users level up, they unlock new skills & abilities based on their MC type.

Example Progression:

Lvl 5: "Tenacity" – Gain XP faster when training at low energy
Lvl 10: "Shonen Rage Boost" – XP doubles if you’re behind schedule
Lvl 15: "Plot Armor" – Gain XP even on skipped days (limited uses)
Redis caches XP multipliers & streaks for instant calculations.

XP is stored persistently in PostgreSQL.

4️⃣ Rival System (Battle Other MCs)
Users can challenge others to a training duel.
System compares total XP, streaks, & strength levels to determine a winner.
Winner gains XP, loser gets a “Training Arc Buff” (temporary XP boost to catch up).
AWS Lambda asynchronously calculates battles to prevent slow responses.

5️⃣ Boss Battles & Weekly Challenges
Every week, users face an AI-generated “Villain” (e.g., "Laziness Demon" or "Procrastination Overlord").
Completing specific workouts defeats the boss and grants rare rewards.
Failing to defeat the boss? XP penalty + embarrassing in-game cutscene.
Redis caches boss stats to keep challenge results instant.

6️⃣ Training Logs & Analytics Dashboard
Users get detailed stats on their training progress.
Dashboard includes:
Total XP
Strength, Agility, Intelligence breakdown
Weekly progress graph
Training streaks & buffs
Frontend uses React with real-time updates via WebSockets.

🛠 Tech Stack & System Design
🔧 Backend (Golang)
gRPC + REST API for seamless communication.
Gin/Fiber framework for fast, efficient request handling.
🗄️ Database (PostgreSQL)
Stores users, XP levels, training logs, skills, battles.
Used for permanent progress tracking.
⚡ Caching (Redis)
Caches XP streaks, boss battle progress, active buffs.
Ensures instant level calculations & leaderboard updates.
☁️ Cloud (AWS Services)
AWS Lambda – Handles battle calculations, boss fights.
AWS S3 – Stores training log images, profile pics, battle replays.
AWS DynamoDB – (Optional) Stores temporary event-based game data.
🎨 Frontend (React + WebSockets)
Real-time XP & level-up animations.
Leaderboard UI with ranking system.
