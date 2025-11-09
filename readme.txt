VR Video Menu Prototype – README

Overview:
This project is a browser-based VR prototype built with A-Frame.
It allows users to select from a list of 360° videos inside a VR menu and view them inside a virtual room.
Optional background music can play in both the menu and individual rooms.

The prototype works in desktop mode and in VR headsets.
All content (videos, audio, JSON configuration) is stored locally and loaded dynamically.

Hosting on Netlify:
Netlify is recommended because it supports large static files (such as MP4 video content).

- Option 1: Drag & Drop
    1. Create a free account at https://www.netlify.com/
    2. Prepare your project folder (must contain index.html)
    3. Drag & drop the folder into the Netlify Drop section (dashboard → “Deploy manually”)
    4. Netlify will generate a public link automatically

- Option 2: Git Integration
    1. Push your project folder to GitHub or GitLab
    2. Connect the repository in Netlify under New Site → Import from Git
    3. Set the deployment folder to the root directory
    4. Deploy – Netlify will host it instantly

Important:
- All file paths must match your folder structure
- Videos and audio files should stay in the same relative paths (e.g., /media/)

File Formats:
- Videos: .mp4 (equirectangular 2:1 format for correct 360° mapping)
- Music / Audio: .mp3 – used as optional background music for menu or rooms

Configuring Videos in videos.json:
The file videos.json controls the menu and room content. You can add any number of items.

Example video entry:
{
  "id": 1,
  "title": "Sample Video",
  "src": "media/video1.mp4",
  "music": "media/music1.mp3"
}

Explanation:
- id: Must be unique. Start at 1 and increment (1, 2, 3…)
- title: Name shown under the icon in the menu
- src: Path to the MP4 video file
- music (Optional): Path to the MP3 music file for this video room

Music behavior:
- If no music is specified for a video, the original audio track of the video will play (if present)
- If music is specified, the room will play that audio instead of the video’s original audio
- The menu can also have optional music defined under menuMusic

At the top under menuMusic, you can set the music for the menu.
You can add as many videos as you like – the menu layout adapts automatically (max 4 rows, unlimited icons per row).

Folder Structure (Recommended):
project-folder/
│
├── index.html
├── videos.json
├── media/
│   ├── video1.mp4
│   ├── video2.mp4
│   ├── music1.mp3
│   ├── menuMusic.mp3
│   └── videoicon.png
└── models/
    └── man_sitting.glb

How to Run Locally Before Uploading:
- Keep all files in the correct folders
- Open index.html in the browser (or upload to Netlify for easier testing)

VR Controls:
- Look at a menu icon for 3 seconds to open the desired room
- In a video room, look at the invisible return zone to go back to the menu
    - After 2 seconds, the loading ring becomes visible
    - After a total of 5 seconds, it returns automatically
