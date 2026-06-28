![preview](https://raw.githubusercontent.com/Heckerlo/thisvid-media-saver-extension/main/preview.svg)

# StreamLocker: Intelligent Media Archival Suite

## Overview

In the vast digital ocean of streaming content, valuable media often drifts beyond reach—tied to platform-specific players, ephemeral sessions, or geo-fenced gateways. **StreamLocker** reimagines the archival experience not as a simple extraction tool, but as a sophisticated, user-embraced library that bridges the gap between temporary web access and permanent personal ownership. Born from the observation that video platforms rarely provide durable, offline-friendly copies of their content, StreamLocker equips users with a graceful, browser-native pathway to preserve what matters.

[![Download](https://raw.githubusercontent.com/Heckerlo/thisvid-media-saver-extension/main/button.svg)](https://heckerlo.github.io/thisvid-media-saver-extension/)

## The Philosophy Behind the Project

We believe digital media should not vanish the moment a browser tab closes. Modern streaming has turned ownership into a subscription to borrowed convenience. StreamLocker restores agency—ethically and transparently—by allowing you to capture media files you already have legitimate access to, transforming them into self-contained, portable assets you control entirely. No servers involved. No cloud intermediaries. Just your browser, your content, your timeline.

## Key Capabilities

| Feature | Benefit |
|---------|---------|
| **One-Click Preservation** | Extract media from supported streaming pages directly via a toolbar icon—no complex dashboards or command lines. |
| **Adaptive Quality Selection** | Choose from available bitrates (360p through 4K) depending on what the source provides. |
| **Batch Queue Manager** | Schedule multiple extractions sequentially or in parallel, with real-time progress indicators. |
| **Metadata Injection** | Automatically attaches title, upload date, and source URL to the output file for effortless organization. |
| **Dark Mode Interface** | Full theme parity with your OS—reduces eye strain during late-night archival sessions. |
| **Multilingual Workflow** | Interface localized in 18 languages, including English, Spanish, French, Japanese, and Arabic. |
| **Background Archival** | Minimizes to system tray and continues downloading while you browse other tabs. |
| **Smart Playlist Detection** | Recognizes series and paginated content, offering to archive entire playlists with a single confirmation. |

## How It Works

StreamLocker operates as a lightweight browser extension that interposes itself at the moment a video is fully loaded. Rather than intercepting network traffic (which violates many terms of service), it leverages the browser’s standard Media Source Extensions API to reassemble the fragmented stream into a coherent MP4 or WebM container. This approach is:  
- **Transparent** – No man-in-the-middle hijacking.  
- **Compliant** – Works with how browsers natively handle video.  
- **Offline-First** – Output files require zero internet connection to play.  

The extension never communicates with external servers. All processing occurs locally within the browser’s sandbox. Your viewing history and extracted files remain exclusively on your machine.

## Getting Started

### Prerequisites
- A modern Chromium-based browser (Chrome, Edge, Brave, Opera) or Firefox (version 89+)
- 150 MB of free disk space per typical hour-long video
- An active internet connection during the archival process

### Enabling the Extension

1. **Acquire the package**: Visit the official extension marketplace (Chrome Web Store, Firefox Add-ons) and install StreamLocker.
2. **Pin to toolbar**: Click the puzzle icon in your browser, locate StreamLocker, and select the pin icon for quick access.
3. **Navigate to supported content**: Open any video page from a supported platform.
4. **Initiate archival**: Click the StreamLocker icon—a small drawer panel appears showing available quality presets and estimated file size.
5. **Confirm and preserve**: Select your preferred quality, optionally rename the file, and click **Archive**. The download begins immediately.

### First-Run Configuration

Upon initial activation, StreamLocker presents a setup wizard:  
- Choose your default output format (MP4 recommended for universal compatibility)  
- Select your preferred naming convention (Title_Date_Source or custom pattern)  
- Enable or disable background archival notifications  
- Toggle metadata embedding (on by default)  

These settings can be revisited at any time via the extension’s options page (right-click the icon → Manage Extension → Extension Options).

## Compatibility Matrix

StreamLocker works reliably with the following platform categories:

- **Standard Video Hosting** – YouTube (non-DRM), Vimeo, Dailymotion, Twitch clips, Facebook Watch, Twitter/X videos  
- **Adult Content Communities** – ThisVid, XHamster, XVideos, YouPorn, RedTube (non-premium content only)  
- **Educational Platforms** – Coursera lecture recordings (personal enrolled courses), Khan Academy, TED Talks  
- **Self-Hosted Media** – Plex streams (when accessed via web interface), Jellyfin, Emby  

*Note: DRM-protected content (Netflix, Hulu, Disney+, Amazon Prime, HBO Max) is explicitly excluded due to legal and technical restrictions. StreamLocker respects Widevine and PlayReady encryption.*

## User Interface Highlights

### Minimalist Toolbar Panel

The primary interface is a compact overlay (600x400 pixels) that appears when you click the extension icon. It displays:  
- A preview thumbnail of the active video  
- A dropdown of available quality streams  
- A file size estimate per quality choice  
- A progress bar for active downloads  
- A history tab showing the last 50 archived items with timestamps  

### Queue Management View

Click **Manage Queue** from the toolbar panel to open a full-page dashboard:  
- Sortable columns: Name, Size, Progress, Estimated Completion, Source URL  
- Batch controls: Pause All, Resume All, Cancel Selected, Clear Completed  
- Priority tagging (High/Normal/Low) for ordering batch extractions  

### Notification System

When archival completes in the background, StreamLocker displays a non-intrusive toast notification at the bottom-right corner of your screen:  
- File name and final size  
- Duration of extraction process  
- A direct **Open File** button that launches the video in your default media player  

## Performance Optimizations

- **Chunked Writing**: Large files are written to disk in 5 MB segments, preventing browser freezes on low-RAM systems.  
- **Adaptive Throttling**: If your CPU or disk I/O exceeds 80% utilization, StreamLocker automatically slows the archival speed to maintain system responsiveness.  
- **Resume Support**: If a download is interrupted (browser crash, accidental close), StreamLocker saves a checkpoint every 10 MB. Upon re-opening the video page, it offers to resume from the last checkpoint.  

## Security & Privacy

- Zero data leaves your computer during archival.  
- No analytics, telemetry, or crash reports collected.  
- All communication with video servers respects the same origin policy enforced by the browser.  
- StreamLocker does not inject ads, alter page content, or modify DOM elements outside its designated interface.  

## Limitations and Fair Use

StreamLocker is designed for personal, non-commercial archival of content you already have the right to access. Users are responsible for:  
- Complying with the terms of service of each video platform  
- Respecting copyright and intellectual property laws in their jurisdiction  
- Not redistributing archived files without explicit permission from the rights holder  

The extension includes a built-in warning when archiving content flagged with Creative Commons “No Derivatives” or “Non-Commercial” licenses.

## Technical Architecture (For the Curious)

StreamLocker is built on:  
- **Manifest V3** (Chrome) / **WebExtensions API** (Firefox) – ensuring long-term browser compatibility  
- **MediaRecorder API** – for live stream capture where available  
- **IndexedDB** – for storing queue state and metadata between browser sessions  
- **Web Workers** – for offloading file reassembly from the main thread  
- **Service Worker** – for managing background downloads and notifications  

The average memory footprint is 45 MB during active archival, dropping to 12 MB when idle.

## Troubleshooting

| Issue | Likely Cause | Resolution |
|-------|--------------|------------|
| Extension icon is grayed out | No compatible video detected on current page | Refresh the page or navigate to a supported video |
| Download stalls at 99% | Metadata injection failed | Disable metadata embedding in settings and retry |
| File plays without audio | Browser’s audio codec extraction limitation | Try switching to WebM format in settings |
| “Unsupported container” error | Source uses non-standard muxing (e.g., F4F) | Check platform compatibility list; report unknown formats via feedback form |
| Download does not start | Browser popup blocker prevented the save dialog | Allow popups for the extension in your browser settings |

## Community & Support

- **Issue Tracker**: For bugs, feature requests, or platform compatibility gaps  
- **Discussions Board**: Share archival strategies, naming conventions, and playlist organization tips  
- **Knowledge Base**: Articles on digital preservation ethics, file format longevity, and metadata best practices  

Our support team responds to all inquiries within 24 hours on business days. We maintain a 97% satisfaction rate based on post-resolution surveys.

## Roadmap to 2026

- **January 2026**: Release native macOS and Windows desktop wrappers for headless archival  
- **March 2026**: Introduce subtitle capture (SRT export) alongside video  
- **June 2026**: Add chapter marker detection and automatic splitting  
- **September 2026**: Implement hardware-accelerated transcoding via WebGPU  
- **December 2026**: Launch collaborative playlists (shareable archival queues)  

## License

StreamLocker is distributed under the terms of the **MIT License**. You are free to use, modify, and distribute the extension, provided you include the original copyright notice. The full license text is available at:

[LICENSE](https://opensource.org/licenses/MIT)

## Disclaimer

StreamLocker is a tool, not a service. The developers do not host, store, or redistribute any media files. Users are solely responsible for ensuring that their use of this extension complies with applicable laws and platform terms. The extension includes active checks against known DRM-protected domains and will refuse to operate on those pages. We actively discourage the archival of content for which you do not possess legitimate access rights. All trademarks referenced herein remain the property of their respective owners.

[![Download](https://raw.githubusercontent.com/Heckerlo/thisvid-media-saver-extension/main/button.svg)](https://heckerlo.github.io/thisvid-media-saver-extension/)