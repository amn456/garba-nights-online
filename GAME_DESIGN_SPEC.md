# PROJECT: GARBA NIGHTS ONLINE 🌙🪔

## A 3D Online Multiplayer Indian Festival Social Game for Web Browsers

### 1. ROLE AND OBJECTIVE

Act as a senior multiplayer game developer, Three.js specialist, network programmer, 3D environment designer, UI/UX designer, and backend engineer.

Build a complete, playable, browser-based 3D online multiplayer game called **Garba Nights Online**.

The game should combine:

- An Indian Navratri festival environment.
- A large, explorable 3D world.
- Online multiplayer supporting up to 50 concurrent players in the same world.
- Male and female character selection.
- Garba dancing and social interactions.
- Real-time text chat and optional voice chat.
- Online YouTube music search and synchronized playback.
- Character customization, shops, events, rewards, and leaderboards.

The game must be a real, functional multiplayer application, not just a static 3D scene or UI mockup.

Deliver complete source code, a working backend, setup instructions, and deployment documentation.

---

# 2. TECHNOLOGY STACK

Use the following technologies:

### Frontend

- HTML5
- CSS3
- JavaScript or TypeScript
- Three.js for 3D rendering
- Vite for the development server and production builds
- GLTF/GLB for 3D character models and animations
- Web Audio API only for permitted local audio processing where appropriate

### Multiplayer Backend

- Node.js
- Express
- Socket.IO for real-time networking
- Authoritative server-side validation for important game state
- Server-managed player positions, chat, emotes, music state, and game events

### Persistent Data

Use SQLite for a simple initial deployment or PostgreSQL for a larger deployment.

Store:

- Player profiles
- Character preferences
- Unlocked cosmetic items
- Friend relationships
- Reward history
- Moderation records

Use a persistent database rather than relying exclusively on browser local storage.

### Voice Chat

Use WebRTC for direct peer-to-peer voice communication where practical.

Use a suitable signaling service built on Socket.IO.

For larger voice groups, support an optional SFU architecture, such as LiveKit or mediasoup.

Voice chat must be optional and disabled by default until a player explicitly enables it.

### Music

- YouTube Data API v3 for searching publicly available videos.
- YouTube IFrame Player API for supported playback.
- Socket.IO for broadcasting the current music selection and synchronization information.

Do not download, extract, or redistribute copyrighted music from YouTube.

### Hosting

Design the application so the frontend and backend can be deployed independently.

Support:

- Static frontend hosting.
- A persistent Node.js backend.
- HTTPS and WSS connections.
- Environment variables for API keys and secrets.

Use free hosting options when available, but document their bandwidth, compute, sleep, and concurrent-connection limitations.

---

# 3. GAME IDENTITY AND VISUAL STYLE

Game name: GARBA NIGHTS ONLINE

Genre:
3D multiplayer social festival game.

Primary experience:
Explore a beautiful Indian Navratri festival at night, meet other players, dance Garba, listen to music, participate in events, and make friends.

Visual direction:

- Beautiful stylized 3D graphics.
- Detailed Indian festival decorations.
- High-quality nighttime lighting.
- Traditional Gujarati cultural elements.
- Colorful clothing and expressive characters.
- Optimized geometry, textures, and lighting for browser performance.

Avoid making the game resemble a basic empty prototype.

The world should feel populated, festive, interactive, and alive.

---

# 4. CHARACTER SELECTION

When the player opens the website, display a character selection screen.

Provide two initial character categories:

### Male Character

- Traditional Gujarati Kediyu-inspired outfit.
- Chaniya-style or dhoti-inspired lower clothing where appropriate.
- Customizable colors.
- Multiple hairstyles.
- Accessories.
- Multiple Garba animations.

### Female Character

- Traditional Gujarati Chaniya Choli-inspired outfit.
- Customizable colors.
- Multiple hairstyles.
- Accessories.
- Multiple Garba animations.

Both characters must:

- Have properly rigged skeletons.
- Support idle, walk, run, jump, and dance animations.
- Support animation transitions.
- Synchronize their movements to other players.
- Have visible usernames above their heads.

Allow additional character models and outfits to be added later.

Do not assume external models or animations are automatically available. Include placeholder assets when necessary and clearly document where replacement GLB files should be placed.

---

# 5. AUTOMATIC MULTIPLAYER WORLD

The game must not require users to manually create or join rooms.

When a player clicks PLAY:

1. Connect to the multiplayer server.
2. Authenticate or create a guest session.
3. Assign the player to the shared public world.
4. Spawn the character at an available spawn point.
5. Load the nearby environment.
6. Synchronize the player with other online players.

### Player capacity

Target:

- Maximum 50 concurrent players in the initial world instance.
- A single shared festival experience for all players assigned to that instance.
- Server-side player-capacity enforcement.

If the instance is full, display a friendly waiting message.

If demand exceeds 50 players, the architecture may support additional instances, but clearly explain that separate instances are separate populations.

### Multiplayer synchronization

Synchronize:

- Player position.
- Player rotation.
- Movement state.
- Selected character appearance.
- Current dance animation.
- Emotes.
- Chat messages.
- Player arrival and departure.
- Music selection and playback state.
- Festival event announcements.

Use interpolation and appropriate network update rates to keep remote players smooth.

Do not send unnecessary high-frequency updates for every cosmetic detail.

Validate player movement on the server to reduce cheating.

---

# 6. LARGE OPEN-WORLD FESTIVAL MAP

Create an explorable 3D environment.

The map should be larger than a single dance floor and include interconnected areas.

### Area A: Main Garba Ground

The primary attraction.

Include:

- A large circular dance floor.
- Decorative lights.
- Traditional patterns.
- Festival decorations.
- Space for dozens of characters.
- A central decorative stage.
- Garba dance areas.

Players should be able to walk around the dance floor and join group dances.

### Area B: Main Festival Pandal

Include:

- A beautifully decorated Indian festival pavilion.
- Traditional decorative architecture.
- Flowers and lamps.
- Decorative lighting.
- A central visual attraction.

Treat religious imagery respectfully.

### Area C: DJ and Music Stage

Include:

- A large DJ stage.
- Decorative LED panels.
- Animated light fixtures.
- Speakers.
- Dance floor lighting.
- Announcements for upcoming music events.

### Area D: Food Street

Include decorative stalls inspired by Gujarati street food.

Examples:

- Dhokla stall.
- Fafda-Jalebi stall.
- Chaat stall.
- Drink stall.

Allow players to interact with selected stalls and display menu information.

### Area E: Clothing Market

Create an interactive cosmetic shop where players can preview unlocked outfits and accessories.

### Area F: Garden and Walking Paths

Include:

- Trees.
- Decorative lamps.
- Benches.
- Flower beds.
- Small gathering areas.
- Walking paths connecting the festival zones.

### Area G: Social Gathering Area

Provide space for players to meet, chat, take screenshots, and use emotes.

### Navigation

Implement:

- A minimap.
- Location markers.
- Optional navigation indicators.
- Clearly marked paths.
- Collision detection.
- Spawn points distributed across the world.

The environment should feel open while remaining optimized for browsers.

---

# 7. NIGHTTIME ENVIRONMENT AND LIGHTING

The night environment is a major part of the game's identity.

Create:

- A deep blue nighttime sky.
- Stars.
- A moon.
- Soft moonlight.
- Warm decorative lanterns.
- Traditional diyas.
- Fairy lights.
- Colorful festival lights.
- Decorative buildings.
- Trees with lights.
- A beautifully illuminated main stage.
- Atmospheric depth.

Implement a lighting system that can change the stage lighting during music events.

Include several lighting presets:

1. Warm traditional festival lighting.
2. Blue and purple nighttime lighting.
3. Colorful dance-party lighting.
4. Grand festival celebration lighting.

Use optimized lighting, baked lighting where suitable, and restrained real-time shadows.

Do not use dozens of expensive dynamic shadow lights simultaneously.

Provide graphics settings for lower-powered mobile devices.

---

# 8. THIRD-PERSON PLAYER CONTROLS

Implement a responsive third-person character controller.

### Desktop controls

W: Move forward.

S: Move backward.

A: Move left.

D: Move right.

Shift: Run.

Space: Jump.

Mouse: Rotate camera when appropriate.

1–6: Trigger selected emotes or dance animations.

E: Interact with nearby objects.

Enter: Open or focus the chat input.

Esc: Close menus.

### Mobile controls

Provide:

- Virtual movement joystick.
- Camera drag control.
- Jump button.
- Dance button.
- Emote menu.
- Interaction button.
- Chat button.
- Music panel button.

Make the UI responsive to different screen sizes and safe areas.

Allow controls to be used without blocking important gameplay.

---

# 9. GARBA DANCE SYSTEM

Build a dedicated animation system.

Include animation slots for:

- Idle.
- Walking.
- Running.
- Clapping.
- Waving.
- Celebrating.
- Garba Dance 1.
- Garba Dance 2.
- Garba Dance 3.
- Group Garba.
- Funny Dance.

Use actual animation clips when available.

If animation assets are missing, create a clearly identified placeholder system and document the required animation format.

Do not pretend that a dance system is complete when it only changes a button label.

### Dance interaction

Players should be able to:

1. Open the dance menu.
2. Select a dance.
3. Start the animation.
4. Stop or change the dance.
5. See remote players performing the same animation.

Synchronize animation identifiers and start times through the multiplayer server.

Use animation transitions to avoid abrupt movement.

---

# 10. GROUP GARBA

Create a special group-dance interaction.

Players can enter a designated dance area and join a coordinated Garba circle.

Requirements:

- Show available group-dance locations.
- Allow players to join or leave.
- Assign approximate positions around the circle.
- Face characters toward the appropriate direction.
- Synchronize the selected dance animation.
- Support multiple simultaneous dance groups.
- Prevent characters from occupying exactly the same position.
- Show a small indicator when a player joins a group.

Do not force every player into a group.

Players must remain free to explore the rest of the map.

---

# 11. ONLINE TEXT CHAT

Create a real-time multiplayer chat panel.

Features:

- Global public chat.
- Message timestamps.
- Player names.
- Emoji support.
- Scrollable message history.
- Mobile-friendly input.
- Enter-to-send support.
- Optional nearby-player chat.
- Private messaging between accepted friends, if implemented.

### Safety and moderation

Implement:

- Message-length limits.
- Rate limiting.
- Spam protection.
- Mute player.
- Block player.
- Report player.
- Basic inappropriate-language filtering.
- Server-side validation.
- Protection against HTML and script injection.

Render user messages as text rather than executable HTML.

Do not expose email addresses, IP addresses, or private account information to other players.

Provide a clear chat privacy notice.

---

# 12. OPTIONAL VOICE CHAT

Implement optional proximity-based voice chat using WebRTC.

Players should be able to:

- Enable or disable their microphone.
- Mute themselves.
- Mute another player locally.
- See a microphone indicator.
- See who is speaking.
- Use push-to-talk on desktop.
- Control voice volume.

### Proximity behavior

Players should hear other players only within a configurable distance.

As players move farther away, reduce the volume.

Outside the configured range, stop transmitting the listener's proximity audio to the experience.

Use positional audio where practical.

### Privacy and safety

- Voice chat must be disabled by default.
- Require explicit microphone permission.
- Explain what voice chat does before activation.
- Provide immediate mute controls.
- Do not record or store voice conversations by default.
- Provide reporting and blocking controls.
- Respect browser permission policies.
- Use encrypted WebRTC connections.
- Avoid exposing connection credentials.

For larger voice groups, use a suitable SFU rather than relying on a full mesh of peer connections.

If voice chat cannot be fully configured without an external service, provide a working text-chat game first and document the additional voice infrastructure required.

---

# 13. YOUTUBE MUSIC SEARCH AND SYNCHRONIZATION

Create an in-game music player panel.

### Search functionality

Allow users to:

- Enter a song title.
- Search for a singer.
- View available video titles.
- View thumbnails.
- View channel names.
- Select a result.
- Play supported videos using the official YouTube IFrame Player API.

Use the official YouTube Data API v3 for search.

Store API keys securely where possible and restrict keys according to provider guidance.

Never expose privileged server secrets in frontend code.

### Music controls

Include:

- Search.
- Play.
- Pause.
- Resume.
- Volume.
- Current song title.
- Current playback status.

Respect YouTube playback requirements, advertisements, regional restrictions, and user interaction requirements.

Do not download YouTube audio, extract MP3 files, bypass advertisements, or remove required player branding.

### Global DJ system

Create a server-managed DJ role.

The DJ can:

- Search for a video.
- Select a result.
- Start a song.
- Pause or resume playback.
- Change the selected video.

Ordinary players can request songs.

The DJ can approve requests.

Only authorized users should control global music.

### Music synchronization

When a song is selected:

1. Broadcast the selected video ID.
2. Broadcast the server timestamp.
3. Broadcast the intended playback start time.
4. Initialize the player for each client.
5. Compare the local playback position with the expected position.
6. Correct meaningful playback drift where permitted.
7. Synchronize new arrivals with the current music state.

Account for network latency and browser autoplay restrictions.

Do not claim perfectly simultaneous playback: YouTube embeds may load at different speeds and may be interrupted by ads or restrictions.

If playback is blocked on a client, show a clear message and let the user activate playback manually.

---

# 14. FRIENDS SYSTEM

Create a social friends interface.

Features:

- Search players by username.
- Send friend requests.
- Accept or decline requests.
- Remove friends.
- View online status.
- View friends currently in the festival.
- Invite friends to a group dance.
- Optionally navigate toward a friend's location.

Only allow friend invitations and direct messages according to privacy settings.

Do not reveal a player's exact location to users who are not permitted to see it.

---

# 15. CHARACTER CUSTOMIZATION

Build a character customization screen.

Allow players to preview:

- Outfit colors.
- Hairstyles.
- Accessories.
- Decorative clothing variations.
- Available dance emotes.

Use a data-driven cosmetic inventory so additional items can be added without rewriting the entire game.

### Unlock system

Players can unlock cosmetic items using earned in-game currency.

Do not require payment for the basic experience.

Do not give cosmetic purchases gameplay advantages.

Validate unlocks on the server.

---

# 16. IN-GAME CURRENCY AND DAILY REWARDS

Create a simple virtual currency system.

Players can earn coins through:

- Daily login rewards.
- Festival events.
- Dance competitions.
- Participation milestones.

Coins can unlock selected cosmetic items.

Implement:

- Coin balance.
- Reward history.
- Daily reward claim.
- Cosmetic shop.
- Server-side reward validation.

Prevent clients from simply assigning themselves unlimited coins.

Avoid real-money purchases in the initial version.

---

# 17. DANCE BATTLES

Create an optional dance competition.

A player can invite another player to a dance battle.

The system should:

1. Ask both players to accept.
2. Move them to a designated battle area.
3. Play a selected dance sequence.
4. Allow spectators to watch.
5. Allow spectators to vote.
6. Determine the winner.
7. Award cosmetic progression points or coins.
8. Return participants to the festival.

Add a cooldown to prevent reward farming.

Keep voting fair and avoid allowing repeated votes from the same player.

---

# 18. FESTIVAL EVENTS AND FIREWORKS

Create scheduled or triggered festival events.

Examples:

- Grand Garba Night.
- Special DJ performance.
- Fireworks show.
- Group Garba celebration.
- Festival lighting show.

Display an announcement before an event begins.

Synchronize event timing through the server.

Use optimized particle effects for fireworks.

Allow lower graphics settings to disable expensive effects.

Do not overload the server by broadcasting every particle individually. Generate decorative effects locally from synchronized event instructions.

---

# 19. PHOTO MODE

Implement a screenshot/photo mode.

Features:

- Hide most UI.
- Adjust camera angle.
- Select a camera distance.
- Trigger supported character poses.
- Take screenshots.
- Return to normal gameplay.

Provide a group-photo mode for players standing together.

Do not upload screenshots automatically.

If a screenshot-sharing feature is added later, ask the player before uploading.

---

# 20. LEADERBOARDS

Create a leaderboard interface with categories such as:

- Dance battle victories.
- Festival event participation.
- Unlocked cosmetics.
- Group Garba participation.

Avoid leaderboards that encourage harassment or excessive repetitive play.

Validate all scores and rewards on the server.

Prevent clients from submitting arbitrary leaderboard values.

---

# 21. MUSIC AND STAGE LIGHTING

Connect stage lighting effects to the music experience.

Use:

- Color transitions.
- Rotating decorative lights.
- Pulsing stage materials.
- Timed lighting presets.
- Synchronized festival event changes.

Where permitted, use playback timing to trigger simple visual effects.

Do not assume direct access to raw YouTube audio data or implement unauthorized audio extraction.

Keep effects visually attractive but optimized.

---

# 22. USER INTERFACE DESIGN

Create a polished, responsive user interface.

### Main menu

Include:

- Game logo.
- Play button.
- Character selection.
- Settings.
- Friends.
- Music.
- Help.

### In-game HUD

Display:

- Player name.
- Online player count.
- Minimap.
- Chat button.
- Friends button.
- Dance/emote menu.
- Music player.
- Settings.
- Microphone toggle.

### UI style

Use:

- Dark navy backgrounds.
- Warm gold accents.
- Traditional Indian decorative motifs.
- Festival-inspired typography.
- Smooth but lightweight transitions.
- Clear readable text.
- Responsive layouts.

Avoid excessive UI clutter.

On mobile, collapse less important panels into menus.

---

# 23. PERFORMANCE OPTIMIZATION

The target is a browser game that remains playable on ordinary computers and modern mobile devices.

Implement:

- Level of detail for distant models.
- Frustum culling.
- Instanced rendering for repeated decorations.
- Compressed textures.
- Optimized GLB assets.
- Efficient network messages.
- Interpolation for remote characters.
- Configurable graphics quality.
- Limited real-time shadows.
- Efficient asset loading.
- Cleanup of disconnected players.
- Client-side decorative effects.

Use spatial interest management so clients receive detailed updates for nearby players while distant players use lower update rates or simplified representations.

The 50-player target must be load-tested rather than assumed.

---

# 24. SECURITY AND RELIABILITY

Implement:

- Server-side input validation.
- Rate limits.
- Secure session handling.
- WebSocket origin checks.
- Protection against chat injection.
- Server-side reward validation.
- Basic reconnect handling.
- Graceful disconnection.
- Safe environment-variable management.
- Production error logging without exposing secrets.

Do not trust the client to decide its own rewards, permissions, or privileged music controls.

Do not store private API keys in public frontend files.

Include basic moderation and abuse-reporting tools.

---

# 25. DEVELOPMENT PHASES

Build the game in working stages.

### Phase 1: Playable 3D Prototype

- Three.js scene.
- Nighttime environment.
- One playable character.
- Movement and camera.
- Basic collision.
- Placeholder animations.

### Phase 2: Multiplayer

- Node.js server.
- Socket.IO connections.
- Player spawning.
- Player movement synchronization.
- Player names.
- Shared world.
- Capacity limit.

### Phase 3: Social Features

- Global text chat.
- Mute and block.
- Player list.
- Friends system.
- Emotes.

### Phase 4: Music

- YouTube search.
- Embedded player.
- DJ permissions.
- Playback-state broadcasting.
- Drift correction.

### Phase 5: Festival Gameplay

- Garba animations.
- Group dancing.
- Dance battles.
- Festival events.
- Fireworks.

### Phase 6: Progression

- Character customization.
- Cosmetic shop.
- Virtual currency.
- Daily rewards.
- Leaderboards.

### Phase 7: Voice Chat

- WebRTC signaling.
- Microphone permissions.
- Proximity audio.
- Push-to-talk.
- Mute and reporting.

### Phase 8: Production

- Performance testing.
- Security review.
- Deployment.
- Mobile testing.
- Documentation.

Every phase must build on the previous phase without breaking existing features.

---

# 26. REQUIRED PROJECT STRUCTURE

Organize the source code into maintainable modules.

Example:

garba-nights-online/
├── client/
│ ├── index.html
│ ├── package.json
│ ├── vite.config.js
│ ├── src/
│ │ ├── main.js
│ │ ├── game/
│ │ │ ├── Game.js
│ │ │ ├── World.js
│ │ │ ├── Environment.js
│ │ │ ├── Lighting.js
│ │ │ └── CameraController.js
│ │ ├── player/
│ │ │ ├── PlayerController.js
│ │ │ ├── CharacterLoader.js
│ │ │ └── AnimationController.js
│ │ ├── multiplayer/
│ │ │ ├── NetworkClient.js
│ │ │ └── RemotePlayers.js
│ │ ├── ui/
│ │ │ ├── MainMenu.js
│ │ │ ├── CharacterSelection.js
│ │ │ ├── ChatUI.js
│ │ │ ├── MusicUI.js
│ │ │ ├── FriendsUI.js
│ │ │ └── SettingsUI.js
│ │ └── systems/
│ │ ├── DanceSystem.js
│ │ ├── GroupDance.js
│ │ ├── MusicSync.js
│ │ └── PhotoMode.js
│ └── public/
│ └── assets/
│ ├── models/
│ ├── animations/
│ ├── textures/
│ ├── environment/
│ └── ui/
├── server/
│ ├── package.json
│ ├── src/
│ │ ├── index.js
│ │ ├── WorldManager.js
│ │ ├── PlayerManager.js
│ │ ├── ChatManager.js
│ │ ├── MusicManager.js
│ │ ├── EventManager.js
│ │ └── Moderation.js
│ └── database/
├── .env.example
├── README.md
└── DEPLOYMENT.md

You may adjust the structure if a better architecture is justified.

Do not create empty files that are presented as complete features.

---

# 27. DELIVERABLES

Provide:

1. Complete frontend source code.
2. Complete multiplayer backend.
3. Database setup and schema.
4. Working movement controls.
5. Working player synchronization.
6. Working global text chat.
7. Functional music-search integration.
8. Functional music playback synchronization logic.
9. Character selection.
10. A playable nighttime festival environment.
11. Working dance and emote controls.
12. Mobile controls.
13. Optional voice-chat implementation or a clearly documented integration plan.
14. Environment-variable example file.
15. Installation instructions.
16. Local development instructions.
17. Production deployment instructions.
18. Troubleshooting guide.
19. Asset replacement instructions.
20. A checklist for verifying multiplayer with multiple browser sessions.

Include exact commands for installing dependencies and running the client and server.

Clearly distinguish implemented features from placeholders.

Never claim that an external API, voice service, model, or hosting service is configured when it is not.

If a required API key is missing, explain how to obtain and configure it.

---

# 28. FINAL ACCEPTANCE TESTS

The game is not considered complete until these tests are performed:

TEST 1:
Open the game in two separate browser sessions and verify that both players can see each other.

TEST 2:
Move one player and verify that the other client receives smooth movement updates.

TEST 3:
Send a chat message and verify that the other player receives it.

TEST 4:
Trigger a dance animation and verify that the other player sees the correct animation.

TEST 5:
Select a YouTube result and verify that playback works where browser and YouTube policies permit it.

TEST 6:
Verify that the music manager distributes the current video ID and playback state to connected players.

TEST 7:
Verify that new players can synchronize with the current world state.

TEST 8:
Verify that the server enforces the 50-player instance capacity.

TEST 9:
Verify that players can mute, block, and report other players.

TEST 10:
Verify that the world remains usable on a mobile browser.

TEST 11:
Verify that the game handles disconnections and reconnects without leaving ghost players.

TEST 12:
Verify that the server rejects unauthorized music-control and reward requests.

TEST 13:
Test performance with increasing numbers of simulated or real clients.

TEST 14:
Verify that microphone access is opt-in and can be disabled immediately.

TEST 15:
Verify that all required setup instructions work on a clean development environment.

---

# FINAL INSTRUCTION

Start by building a genuinely playable Phase 1 and Phase 2, including the 3D nighttime festival, character movement, shared multiplayer world, player synchronization, and text chat.

Then integrate the remaining systems incrementally.

Prioritize stable networking, enjoyable movement, beautiful visuals, and working interactions over unnecessary complexity.

The final result should feel like a small online Indian festival world where players can meet, explore, dance, chat, listen to music, and participate in shared events.

Do not merely describe the game or provide pseudocode. Create the actual project files and working implementation wherever the development environment allows.