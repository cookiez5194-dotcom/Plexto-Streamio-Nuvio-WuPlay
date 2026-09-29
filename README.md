# 💜 Shoko’s PlexBridge Presents…
## Your Plex. Your shows. Your movie night. 🍿

Bring your own **Plex movies and TV shows into Stremio and Nuvio**, with library catalogs in Discover and your Plex files as playback sources.

🐳 Runs in the background using Docker.  
🏠 Uses your own Plex server and media.  
💸 No cloud hosting subscription needed for this local setup.

---

## 🧰 What you need

Before starting, make sure you have:

- A Windows PC with **Plex Media Server** installed and working.
- Movies or TV shows already added to your Plex libraries.
- **Stremio or Nuvio** on your playback device.
- Your PC and playback device connected to the **same home network**.
- The **Shoko’s PlexBridge ZIP**, extracted to a permanent folder.

**This add-on connects to your existing Plex server. It does not provide movies or create a Plex library for you.**

---

## 1️⃣ Install the two things we need

### Node.js

Download and install **Node.js 22 or newer**:

👉 https://nodejs.org/

Node.js runs our Windows setup launcher.

### Docker Desktop

Download and install **Docker Desktop for Windows**:

👉 https://www.docker.com/products/docker-desktop/

Follow the installer’s prompts. Use the **WSL 2 backend / Linux containers** option. Restart Windows if requested.

Open Docker Desktop and wait until its engine is running.

💡 You don’t need to type anything into Docker’s AI chat or manually create a container. Our launcher handles the container setup.

---

## 2️⃣ Tell Docker to start automatically

In Docker Desktop:

1. Open **Settings ⚙️**.
2. Select **General**.
3. Enable **Start Docker Desktop when you sign in to your computer**.
4. Apply the change if prompted.

This lets Docker start after you sign into Windows.

---

## 3️⃣ Extract the ZIP

1. Right-click the Shoko’s PlexBridge ZIP.
2. Choose **Extract All**.
3. Put the extracted files somewhere permanent, such as:

`C:\ShokoPlexBridge`

4. Open the folder containing **START-DOCKER-WINDOWS.bat**.

📌 Don’t run the files from inside the ZIP. Extract them first!

### Already using the older version?

Copy your existing **`config.json`** into this folder before starting.

That file remembers your Plex connection and private installation link. With it in place, the launcher skips the setup questions.

Close the old bridge terminal before starting Docker, then jump to **Step 8**.

---

## 4️⃣ Start the setup

Double-click:

**START-DOCKER-WINDOWS.bat**

A black window will open. On your first run, it asks for your Plex details.

Let’s go through them one at a time. 👇

---

## 5️⃣ Enter your Plex server address

You’ll see:

**Plex server URL [http://127.0.0.1:32400]:**

### Plex runs on this same PC?

Just press **Enter**. ✅

### Plex runs on another PC?

Enter that computer’s local IP address with port `32400`.

Example:

`http://192.168.1.50:32400`

Use the actual address of the computer running Plex.

💡 When Plex runs on this PC, the Docker version automatically handles the connection from the container. You can keep the default address during setup.

---

## 6️⃣ Find your Plex token 🔑

Your Plex token is a private access key that lets the bridge connect to your library.

To find it:

1. Open **Plex in your web browser** and sign in.
2. Open a movie or episode from **your own library**.
3. Click **⋯ → Get Info → View XML**.
4. A page containing XML text will open.
5. Look at the **browser’s address bar**, not the text on the page.
6. Find `X-Plex-Token=`.
7. Copy only the letters and numbers immediately after the `=`.
8. Stop before any `&` if one appears.
9. Paste the token into the setup window and press **Enter**.

For example, if the address contains:

`X-Plex-Token=EXAMPLE123`

You would paste only:

`EXAMPLE123`

⚠️ That is an example, not a working token.

🔒 **Keep your actual token private. Don’t share it or post screenshots showing it.** The setup window displays what you enter.

---

## 7️⃣ Enter your bridge address and choose libraries

### A. Find this PC’s local IP address

On the PC running Shoko’s PlexBridge:

1. Leave the setup window open.
2. Press **Win + R**.
3. Type `cmd` and press **Enter**.
4. Type `ipconfig` and press **Enter**.
5. Find **IPv4 Address** under your connected Wi-Fi or Ethernet adapter.

Ignore adapters marked **Media disconnected**.

### B. Enter the bridge address

Return to setup.

If your IPv4 address were `192.168.1.50`, you would enter:

`http://192.168.1.50:7000`

**Replace the example IP with your own PC’s IPv4 address.**

This address lets your TV or phone reach the bridge.

### C. Listening port

At:

**Local listening port [7000]:**

Just press **Enter**.

### D. Add-on name

At:

**Add-on name [My Plex]:**

Type:

`Shoko Plex`

Then press **Enter**.

You can choose another name if you prefer.

### E. Library selection

Setup will display your Plex libraries with numbers beside them.

At:

**Library IDs separated by commas [all]:**

- To include **all movie and TV libraries**, simply press **Enter**.
- To include only specific libraries, enter their displayed numbers separated by commas.

Example: `1,3,5` — only if those are the library IDs you want.

---

## 8️⃣ Let Docker do its thing 🐳

The launcher will now download the required base image, build the bridge, and start its container.

The first run may take a few minutes. Lots of scrolling text is normal.

Wait until you see:

**Bridge is running in the background. You can close this window.**

You should also see the container reported as **Healthy**.

✅ That means the bridge process started. Next, check its connection to Plex.

---

## 9️⃣ Open your private installation page 💜

The launcher prints an address ending in:

`/configure`

Copy the **entire address** and open it in your browser.

If it wraps onto two lines in the terminal, it is still one address.

You’ll see the purple and pink **Shoko’s PlexBridge** page. Check that it reports your libraries connected.

### Install in Stremio

1. Click **Install in Stremio**.
2. Allow your browser to open Stremio if asked.
3. Confirm installation in Stremio.

### Install in Nuvio

1. Click **Copy private link**.
2. Open Nuvio’s **Addons** section.
3. Choose the option to add an add-on by URL.
4. Paste the complete copied link and confirm.

The add-on link ends in **`/manifest.json`**.

📌 Use the link from the page’s copy button. The browser address ending in `/configure` is the setup page, not the add-on manifest.

If copying doesn’t work, click the link field, press **Ctrl + A**, then **Ctrl + C**.

---

## 🔟 Pick something to watch 🍿

In Stremio or Nuvio:

1. Open **Discover**.
2. Choose **Movies** or **Series**.
3. Select one of your **Shoko Plex** libraries.
4. Open a movie or choose an episode.
5. Select the **Shoko Plex** playback source.

Enjoy! 💜

---

## 🌙 Can I close the black window now?

**Yes! Once Docker startup succeeds, you can close the launcher window.**

For playback to keep working:

- Your PC must stay **on and awake**.
- **Plex Media Server** must keep running.
- **Docker Desktop’s engine** must keep running.

Closing Docker’s dashboard window is different from choosing **Quit Docker Desktop**. Don’t quit Docker while you need the bridge.

Turning off your monitor is fine. Putting the PC to sleep stops access.

---

## 🔄 What happens after restarting Windows?

After you sign in, Docker should start automatically if you enabled that setting.

The bridge is configured to restart with Docker **unless you deliberately stopped it**.

If you stopped it manually, run **START-DOCKER-WINDOWS.bat** to start it again.

You do not need to reinstall the add-on on your TV every time.

---

## 🎛️ Your handy buttons

| File | What it does |
|---|---|
| **START-DOCKER-WINDOWS.bat** | Sets up or starts the bridge in Docker |
| **STOP-DOCKER-WINDOWS.bat** | Stops the bridge |
| **STATUS-DOCKER-WINDOWS.bat** | Shows container status and recent logs |
| **config.json** | Stores your private connection settings |
| **DOCKER-GUIDE.md** | More Docker help |
| **ADVANCED.md** | Technical details and troubleshooting |

**Use START-DOCKER-WINDOWS.bat for Docker mode.** The separate START-WINDOWS.bat runs the original version that needs its terminal window left open.

---

## 🆘 Something isn’t working?

### “Docker is not running”

Open Docker Desktop, wait for its engine to start, then run the launcher again.

### “Port is already allocated”

The original bridge or another program may still be using port `7000`.

Close the old bridge terminal and try again.

### The container is healthy, but no Plex libraries connect

“Healthy” confirms the bridge responds. It doesn’t confirm Plex is reachable.

Check that Plex is running, your server address and token are correct, and your firewall allows the connection.

### It works on the PC, but not the TV

Check that:

- The TV and PC are on the same home network.
- Your bridge address uses the PC’s **local IPv4 address**, not `127.0.0.1` or `localhost`.
- Windows Firewall allows access to the bridge port on your private network.
- Your PC’s local IP address hasn’t changed.

### A movie appears, but won’t play

This version uses **direct play**. It doesn’t convert video or audio formats.

Try a known H.264/AAC MP4 file to help distinguish a connection problem from a format your player doesn’t support.

### Setup asks all the questions again

Check that your original **`config.json`** is in the same folder as the launcher.

If you lost it, complete setup again. A new configuration creates a new private link, so replace the old add-on installation in your player.

---

## 📦 Sharing with friends

Share the **original ZIP and these instructions**.

Each person connects their own Plex server and generates their own installation link.

**Do not share your personal:**

- `config.json`
- Plex token
- Private installation or manifest link

Those provide access to your Plex setup.

---

## 🏠 A few things to know

- This guide covers playback on your **home network**. Watching away from home needs additional setup.
- Docker running locally does not create a cloud video-traffic bill.
- This version supports **direct play**, without transcoding or Plex watched-status synchronization.
- Keep the extracted folder in place; Docker uses its configuration file.
- Back up `config.json` somewhere private to preserve your setup.

---

**Made with 💜 for better movie nights.**

**© 2026 Shoko’s PlexBridge. All rights reserved.**

Permission is granted to share the original, unmodified distribution and this guide for personal use, retaining this notice.

An independent community project. Not affiliated with or endorsed by Plex, Stremio, Nuvio, or Docker. Their names and trademarks belong to their respective owners.

### 🍿 Grab a snack. Pick a movie. Let Shoko bridge the gap.
