# 📺 Adaptive Video Streaming Platform

This project is a **real-time adaptive video streaming system** that delivers optimized video content to users across varying network conditions. It includes components for **frame processing, adaptive bitrate streaming, CDN support**, and **RTT-based congestion control**.

---

## 🧾 Overview

The system captures and processes video files into individual frames, which are stored and delivered to clients via a **Java-based server-client-relay architecture**. It incorporates **congestion control (AIMD)** and **RTT estimation** for smooth adaptive playback. Protocols like **HLS and DASH** are considered for segment-based delivery.

---

## 📁 File Structure

| File / Folder         | Description |
|------------------------|-------------|
| `server/`              | Java-based video streaming server |
| `client/`              | Client for requesting and playing video frames |
| `relay/`               | Relay handler for routing video streams and managing congestion |
| `README.md`            | Documentation for the project (you’re reading it!) |

---

## 🚀 Features

- 🔄 **Adaptive Bitrate Streaming**
- ⏱️ **RTT Estimation** per client
- 📉 **Congestion Control** using AIMD
- 🌐 **Content Delivery Network (CDN)** support
- 🎬 **Frame Extraction using FFmpeg**
- ⚙️ **Client-Server-Relay Architecture**
- 🔐 **User Authentication (optional module)**
- 💻 **Cross-platform Client Support**

---

## 🧠 Architecture

```
[Client]
   ⇅
[Relay Handler] ⇄ [CDN Cache]
   ⇅
[Video Streaming Server]
   ⇅
[Frame Store (video_frames)]
```

---

## ⚙️ How to Run

1. **Extract frames from a video** using FFmpeg:
   ```bash
   ./frame_extractor.sh input_video.mp4
   ```

2. **Start the server**:
   ```bash
   javac server/VideoServer.java
   java server.VideoServer
   ```

3. **Start the relay handler**:
   ```bash
   javac relay/RelayHandler.java
   java relay.RelayHandler
   ```

4. **Start the client**:
   ```bash
   javac client/VideoClient.java
   java client.VideoClient
   ```

---

## 🔐 Congestion Control (AIMD)

- **Additive Increase**: Increases sending rate linearly when no congestion
- **Multiplicative Decrease**: Reduces rate exponentially on RTT spike or frame drop

---

## 🎯 Adaptive Streaming Logic

- RTT is continuously monitored.
- Bitrate levels are adjusted dynamically.
- Clients receive appropriate quality chunks based on current network state.

---

## ☁️ CDN Simulation

- Popular video segments are cached locally at the relay level.
- If not found, the relay fetches from the main server and stores it for future requests.

---

## 📦 Dependencies

- Java 11+
- FFmpeg (for frame extraction)
- Shell (for `frame_extractor.sh`)
- Any OS with Java runtime and Bash support

---

## 🛠️ Future Enhancements

- Integration with **WebSockets** for low-latency control
- Real **HLS/DASH manifest generation**
- **Web-based client** with HTML5 video player
- **Authentication and access logs**

