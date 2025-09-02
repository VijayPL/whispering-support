# whispering-support

Press shortcut → speak → get text. Free and open source ❤️

Whispering is an open-source speech-to-text application. Press a keyboard shortcut, speak, and your words will transcribe, transform, then copy and paste at the cursor.

I really like hands-free voice dictation. For years, I relied on transcription tools that were *almost* good, but they were all closed-source. Even those claiming to be “local” or “on-device” were still black boxes that left me wondering where my audio really went.

So I built Whispering. It’s open-source, local-first, and most importantly, transparent with your data. Your data is stored locally on your device, and your audio goes directly from your machine to a local provider (Speaches, owhisper, etc.) or your chosen cloud provider (Groq, OpenAI, ElevenLabs, etc.) without any middleman or vendor lock-in. For me, the features were good enough that I left my paid tools behind (I used Superwhisper and Wispr Flow before).

Productivity apps should be open-source and transparent with your data, but they also need to match the UX of paid, closed-software alternatives. I hope Whispering is near that point. I use it for several hours a day, from coding to thinking out loud while carrying pizza boxes back from the office.

Here’s an overview:

https://youtu.be/1jYgBMrfVZs?si=T0uXiAKewasK5qmz

                                                                                                                              *Click to watch: Complete setup and usage guide (5 min)*

                                                                         *Note: We recently added support for Whisper C++, which isn't included in the video. For setup, see the docs below.*

There are plenty of transcription apps out there, each with their own strengths. Whispering has a few tricks up its sleeve, like a voice-activated mode for truly hands-free operation (no button holding), and customizable AI transformations with any prompt/model. The space is full of great ideas, but I just wanted to add some extra competition from the OSS ecosystem.

Built with Svelte 5 and Tauri, so it's tiny (~22MB) and starts instantly. The codebase is well-documented and designed to be understood and audited. That way, you know where your audio goes, how it's processed, and what data is stored. And finally, the cost savings. When you cut out the middleman, you pay providers directly:

|             **Service** | **Cost per Hour** |  **Light Use (20 min/day)** | **Moderate Use (1 hr/day)** | **Heavy Use (3 hr/day)** |  **Traditional Tools** |
| --- | --- | --- | --- | --- | --- |
| `distil-whisper-large-v3-en` (Groq) | $0.02 | $0.20/month | $0.60/month | $1.80/month | $15-30/month |
| `whisper-large-v3-turbo` (Groq) | $0.04 | **$0.40/month** | $1.20/month | $3.60/month | $15-30/month |
| `gpt-4o-mini-transcribe` (OpenAI) | $0.18 | $1.80/month | $5.40/month | $16.20/month | $15-30/month |
| Local | $0.00 | $0.00/month | **$0.00/month** | $0.00/month | $15-30/month |

We're hoping that together in the open-source, local-first community, we can build something better than any closed-source alternative. The code is open-source because I believe that fundamental tools shouldn't require trusting a black box. Companies pivot, get acquired, or shut down. But open source is forever. ❤️

**Note**: Whispering is designed for quick transcriptions, not long recordings. For extended recording sessions, we recommend using a dedicated recording app. Check out our friends at [Hyprnote](https://github.com/fastrepl/hyprnote)

# **Install Whispering**

Set up Whispering and be ready to transcribe in about two minutes.

## Step 1: Download Whispering

**🍎 macOS**

**Download Options**

| **Architecture** | **Download** | **Requirements** |
| --- | --- | --- |
| **Apple Silicon** | [Whispering_7.3.0_aarch64.dmg](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_aarch64.dmg) | M1/M2/M3/M4 Macs |
| **Intel** | [Whispering_7.3.0_x64.dmg](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_x64.dmg) | Intel-based Macs |

> Not sure which Mac you have? Click the Apple menu → About This Mac. Look for "Chip" or "Processor":
> 
> - Apple M1/M2/M3/M4 → Use Apple Silicon version
> - Intel Core → Use Intel version

🖥️ **Windows
Download Options**

| **Installer Type** | **Download** | **Description** |
| --- | --- | --- |
| **MSI Installer** | [Whispering_7.3.0_x64_en-US.msi](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_x64_en-US.msi) | Recommended Standard Windows installer |
| **EXE Installer** | [Whispering_7.3.0_x64-setup.exe](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_x64-setup.exe) | Alternative installer option |

**Installation**

1. Download the `.msi` installer (recommended)
2. Double-click to run the installer
3. If Windows Defender appears: Click "More Info" → "Run Anyway"
4. Follow the installation wizard

Whispering will appear in your Start Menu when complete.

**🐧 Linux**

**Download Options**

| **Package Format** | **Download** | **Compatible With** |
| --- | --- | --- |
| **AppImage** | [Whispering_7.3.0_amd64.AppImage](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_amd64.AppImage) | All Linux distributions |
| **DEB Package** | [Whispering_7.3.0_amd64.deb](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_amd64.deb) | Debian, Ubuntu, Pop!_OS |
| **RPM Package** | [Whispering-7.3.0-1.x86_64.rpm](https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering-7.3.0-1.x86_64.rpm) | Fedora, RHEL, openSUSE |

**Quick Install Commands**

**AppImage (Universal)**

```
wget https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_amd64.AppImage
chmod +x Whispering_7.3.0_amd64.AppImage
./Whispering_7.3.0_amd64.AppImage
```

**Debian/Ubuntu**

```
wget https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering_7.3.0_amd64.deb
sudo dpkg -i Whispering_7.3.0_amd64.deb
```

**Fedora/RHEL**

```
wget https://github.com/epicenter-so/epicenter/releases/download/v7.3.0/Whispering-7.3.0-1.x86_64.rpm
sudo rpm -i Whispering-7.3.0-1.x86_64.rpm
```

      **Links not working?** Find all downloads at [GitHub Releases](https://github.com/epicenter-so/epicenter/releases/latest)

**Try in Browser (No Download)**

[**🚀 Open Whispering Web App →**](https://whispering.epicenter.so/)

No installation needed! Works in any modern browser.

> Note: The web version doesn't have global keyboard shortcuts, but otherwise works great for trying out Whispering before installing.
> 

## Step 2: **Choose Your Transcription Method & Test**

**🏠 Option A: Local Transcription (Whisper C++)**
💡 **Why local?** 100% private, runs offline, no API costs, works on any hardware

**Install FFmpeg**

Whisper C++ needs FFmpeg to convert audio to 16kHz format:

**🍎 macOS:**

```
brew install ffmpeg
```

🖥️ **Windows:**

```
# Using Chocolatey
choco install ffmpeg

# Or using Scoop
scoop install ffmpeg
```

**🐧 Linux:**

```
# Ubuntu/Debian
sudo apt install ffmpeg

# Fedora
sudo dnf install ffmpeg

# Arch
sudo pacman -S ffmpeg
```

**Test Your Setup:**

1. Open Whispering
2. Click **Settings** (⚙️) → **Transcription**
3. Select **Whisper C++** from the dropdown
4. Choose a model (start with `Small`)
5. Click **Download** button next to the model → Wait for download to complete
6. Make sure the model shows as **activated**
7. Click record and say "Testing Whispering"

**🎉 Success!** Your words are now in your clipboard. Paste anywhere!

**☁️ Option B: Cloud Transcription (Groq)**

> 💡 Why Groq? Fastest transcription, super accurate, generous free tier, as cheap as $0.02/hour
> 

**Get Your Free API Key:**

1. Visit [console.groq.com/keys](https://console.groq.com/keys)
2. Sign up (free, no credit card) → Create API key → Copy it

**Test Your Setup**

1. Open Whispering
2. Click **Settings** (⚙️) → **Transcription**
3. Select **Groq** → Paste your API key
4. Choose a model (`distil-whisper-large-v3-en` is fastest)
5. Click record and say "Testing Whispering"

**🎉 Success!** Your words are now in your clipboard. Paste anywhere!

**Having trouble? Common issues & fixes**

### **Quick Fixes**

- **No transcription?** → Double-check API key in Settings
- **Shortcut not working?** → Bring Whispering to foreground (see macOS section below)
- **Wrong provider selected?** → Check Settings → Transcription

### **Platform-Specific Issues**

**macOS: Global shortcut stops working?**

This happens due to macOS App Nap, which suspends background apps to save battery.

**Quick fixes:**

1. Use Voice Activated mode for hands-free operation (recommended)
2. Bring Whispering to the foreground briefly to restore shortcuts
3. Keep the app window in the foreground (even as a smaller window)

**Best practice:** Keep Whispering in the foreground in front of other apps. You can resize it to a smaller window or use Voice Activated mode for minimal disruption.

**Accidentally rejected microphone permissions?**

If you accidentally clicked "Don't Allow" when Whispering asked for microphone access, here's how to fix it:

**🍎 macOS**

1. Open **System Settings** → **Privacy & Security** → **Privacy** → **Microphone**
2. Find **Whispering** in the list
3. Toggle the switch to enable microphone access
4. If Whispering isn't in the list, reinstall the app to trigger the permission prompt again

🖥️ **Windows**

If you accidentally blocked microphone permissions, use the Registry solution:

**Registry Cleanup (Recommended)**

1. Close Whispering
2. Open Registry Editor (Win+R, type `regedit`)
3. Use Find (Ctrl+F) to search for "Whispering"
4. Delete all registry folders containing "Whispering"
5. Press F3 to find next, repeat until all instances are removed
6. Uninstall and reinstall Whispering
7. Accept permissions when prompted
- Alternative solutions
    
    **Delete App Data:** Navigate to `%APPDATA%\..\Local\com.bradenwong.whispering` and delete this folder, then reinstall.
    
    **Windows Settings:** Settings → Privacy & security → Microphone → Enable "Let desktop apps access your microphone"
    

       See [Issue #526](https://github.com/epicenter-so/epicenter/issues/526) for more details

### Step 3: **Power User Features**

Take your transcription experience to the next level with these advanced features:

**🎯 Custom Transcription Services**

Choose from multiple transcription providers based on your needs for speed, accuracy, and privacy:

**🚀 Groq (Recommended)**

- **API Key:** [console.groq.com/keys](https://console.groq.com/keys)
- **Models:** `distil-whisper-large-v3-en` ($0.02/hr), `whisper-large-v3-turbo` ($0.04/hr), `whisper-large-v3` ($0.06/hr)
- **Why:** Fastest, cheapest, generous free tier

**🎯 OpenAI**

- **API Key:** [platform.openai.com/api-keys](https://platform.openai.com/api-keys) ([Enable billing](https://platform.openai.com/settings/organization/billing/overview))
- **Models:** `whisper-1` ($0.36/hr), `gpt-4o-transcribe` ($0.36/hr), `gpt-4o-mini-transcribe` ($0.18/hr)
- **Why:** Industry standard

**🎙️ ElevenLabs**

- **API Key:** [elevenlabs.io/app/settings/api-keys](https://elevenlabs.io/app/settings/api-keys)
- **Models:** `scribe_v1`, `scribe_v1_experimental`
- **Why:** High-quality voice AI

**🏠 Speaches (Local)**

- **API Key:** None needed!
- **Why:** Complete privacy, offline use, free forever

**🤖 AI-Powered Transformations**

Transform your transcriptions automatically with custom AI workflows:

**Quick Example: Format Text**

1. Go to **Transformations** (📚) in the top bar
2. Click "Create Transformation" → Name it "Format Text"
3. Add a **Prompt Transform** step:
    - Model: `Claude Sonnet 3.5` (or your preferred AI)
    - System prompt: `You are an intelligent text formatter specializing in cleaning up transcribed speech. Your task is to transform raw transcribed text into well-formatted, readable content while maintaining the speaker's original intent and voice.

Core Principles:

1. Preserve authenticity: Keep the original wording and phrasing as much as possible
2. Add clarity: Make intelligent corrections only where needed for comprehension
3. Enhance readability: Apply proper formatting, punctuation, and structure.

Formatting Guidelines:

Punctuation & Grammar:

- Add appropriate punctuation (periods, commas, question marks)
- Correct obvious transcription errors while preserving speaking style
- Fix run-on sentences by adding natural breaks
- Maintain conversational tone and personal speaking patterns

Structure & Organization:

- Create paragraph breaks at natural topic transitions
- Use bullet points or numbered lists when the speaker is listing items
- Add headings if the content has clear sections
- Preserve emphasis through italics or bold when the speaker stresses words

Intelligent Corrections:

- Fix homophones (e.g., "there/their/they're")
- Complete interrupted thoughts when the intention is clear
- Remove excessive filler words (um, uh) unless they add meaning
- Correct obvious misspeaks while noting significant ones in [brackets]

Special Handling:

- Technical terms: Research and correct spelling if unclear
- Names/places: Make best guess and mark uncertain ones with [?]
- Numbers: Convert spoken numbers to digits when appropriate
- Time references: Standardize format (e.g., "3 PM" not "three in the afternoon")

Preserve Original Intent:

- Keep colloquialisms and regional expressions
- Maintain the speaker's level of formality
- Don't "upgrade" simple language to sound more sophisticated
- Preserve humor, sarcasm, and emotional tone

Output Format: Return the formatted text with:

- Clear paragraph breaks
- Proper punctuation and capitalization
- Any structural elements (lists, headings) that improve clarity
- [Bracketed notes] for unclear sections or editorial decisions
- Original meaning and voice intact

Remember: You're a translator from spoken to written form, not an editor trying to improve the content. Make it readable while keeping it real.`

- User prompt: `Here is the text to format:

{{input}}` 4. Save and select it in your recording settings

**What can transformations do?**

- Fix grammar and punctuation automatically
- Translate to other languages
- Convert casual speech to professional writing
- Create summaries or bullet points
- Remove filler words ("um", "uh")
- Chain multiple steps together

**Example workflow:** Speech → Transcribe → Fix Grammar → Translate to Spanish → Copy to clipboard

Setting up AI providers for transformations

You'll need additional API keys for AI transformations. Choose from these providers based on your needs:

**🧠 OpenAI**

- **API Key:** [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- **Models:** `gpt-4o`, `gpt-4o-mini`, `o3-mini` and more
- **Why:** Most capable, best for complex text transformations

**🤖 Anthropic**

- **API Key:** [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys)
- **Models:** `claude-opus-4-0`, `claude-sonnet-4-0`, `claude-3-7-sonnet-latest`
- **Why:** Excellent writing quality, nuanced understanding

**✨ Google Gemini**

- **API Key:** [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
- **Models:** `gemini-2.5-pro`, `gemini-2.5-flash`, `gemini-2.5-flash-lite`
- **Why:** Free tier available, fast response times

**⚡ Groq**

- **API Key:** [console.groq.com/keys](https://console.groq.com/keys)
- **Models:** `llama-3.3-70b-versatile`, `llama-3.1-8b-instant`, `gemma2-9b-it`, and more
- **Why:** Lightning fast inference, great for real-time transformations

**🎙️ Voice Activity Detection (VAD)**

Hands-free recording that starts when you speak and stops when you're done.

**Two ways to enable VAD:**

**Option 1: Quick toggle on homepage**

- On the homepage, click the **Voice Activated** tab (next to Manual)

**Option 2: Through settings**

1. Go to **Settings** → **Recording**
2. Find the **Recording Mode** dropdown
3. Select **Voice Activated** instead of Manual

**How it works:**

- Press shortcut once → VAD starts listening
- Speak → Recording begins automatically
- Stop speaking → Recording stops after a brief pause
- Your transcription appears instantly

Perfect for dictation without holding keys!

**⌨️ Custom Shortcuts**

Change the recording shortcut to whatever feels natural:

1. Go to **Settings** → **Recording**
2. Click on the shortcut field
3. Press your desired key combination
4. Popular choices: `F1`, `Cmd+Space+R`, `Ctrl+Shift+V`

**How is my data stored?**

Whispering stores as much data as possible locally on your device, including recordings and text transcriptions. This approach ensures maximum privacy and data security. Here's an overview of how data is handled:

1. **Local Storage**: Voice recordings and transcriptions are stored in IndexedDB, which is used as blob storage and a place to store all of your data like text and transcriptions.
2. **Transcription Service**: The only data sent elsewhere is your recording to an external transcription service—if you choose one. You have the following options:
    - External services like OpenAI, Groq, or ElevenLabs (with your own API keys)
    - A local transcription service such as Speaches, which keeps everything on-device
3. **Transformation Service (Optional)**: Whispering includes configurable transformation settings that allow you to pipe transcription output into custom transformation flows. These flows can leverage:
    - External Large Language Models (LLMs) like OpenAI's GPT-4, Anthropic's Claude, Google's Gemini, or Groq's Llama models
    - Hosted LLMs within your custom workflows for advanced text processing
    - Simple find-and-replace operations for basic text modifications
    
    When using AI-powered transformations, your transcribed text is sent to your chosen LLM provider using your own API key. All transformation configurations, including prompts and step sequences, are stored locally in your settings.
    

You can change both the transcription and transformation services in the settings to ensure maximum local functionality and privacy.

### 📚 Additional Resources

- [Epicenter Whispering GitHub Repository](https://github.com/epicenter-so/epicenter/tree/main/apps/whispering)
- [Whispering: Open-Source Speech-to-Text App Boosts Privacy and User Control](https://www.webpronews.com/whispering-open-source-speech-to-text-app-boosts-privacy-and-user-control/)
- [Whispering | Product Hunt Launch Dashboard](https://hunted.space/dashboard/whispering)

## Transcription should be free, open, and accessible to everyone. Join us in making it so.
