# SteadyRead

**Visual stabilization for reading with hand tremors**

SteadyRead is a free, open-source web application that helps people with hand tremors read comfortably on mobile devices. It uses motion sensors to detect device shake and counter-stabilizes the content in real-time, keeping text visually steady despite hand movement.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Accessibility](https://img.shields.io/badge/accessibility-WCAG_2.1-purple)

## 🎯 The Problem

Millions of people worldwide experience hand tremors due to conditions like:
- Essential Tremor (the most common movement disorder)
- Parkinson's Disease  
- Cerebellar disorders
- Medication-induced tremors
- Age-related trembling

Reading from mobile devices becomes challenging when your hands shake - the text moves constantly, causing eye strain, fatigue, and difficulty comprehending content.

## ✨ The Solution

SteadyRead acts like image stabilization for your reading content. It:

1. **Detects motion** using your device's accelerometer
2. **Calculates offset** from device shake in real-time
3. **Counter-moves content** in the opposite direction
4. **Smooths movement** to prevent overcorrection

The result? Text that appears to float in space, staying relatively still despite hand tremors.

## 🚀 Features

### Phase 1 (Current)
- ✅ **Real-time stabilization** - Sub-frame motion compensation
- ✅ **Adjustable sensitivity** - Fine-tune from 10-50 to match tremor intensity
- ✅ **Lexend font** - Research-backed typography for readability and dyslexia
- ✅ **Auto text scaling** - Larger text when stabilization is active
- ✅ **Drift correction** - Prevents content from wandering off-center
- ✅ **Clean reading mode** - Distraction-free interface
- ✅ **PWA support** - Installable as a native-like app
- ✅ **Settings panel** - Customize behavior
- ✅ **Debug mode** - Technical information for troubleshooting
- ✅ **Zero data collection** - Runs entirely in browser
- ✅ **Works offline** - No internet needed after initial load

### Coming Soon (Phase 2)
- 🔄 URL input for loading any webpage
- 🔄 Full browser functionality (bookmarks, history, navigation)
- 🔄 Multiple sensitivity presets
- 🔄 Custom font options
- 🔄 Color theme selection
- 🔄 Export/import settings

## 📱 Compatibility

**Supported Devices:**
- iOS 13+ (iPhone, iPad)
- Android 5.0+ with motion sensors
- Any device with accelerometer and modern browser

**Best Experience:**
- iOS Safari
- Chrome/Edge on Android
- Devices with 60Hz+ refresh rate

**Note:** Some browsers may not support motion sensors or require HTTPS to access them.

## 🎨 Design Principles

### Accessibility First
- **WCAG 2.1 AA compliant** typography
- **High contrast** text on clean backgrounds
- **Lexend font** - designed for improved reading speed and dyslexia
- **Generous spacing** - 1.9-2.0 line height, 0.02-0.03em letter spacing
- **Minimum 20px font** (26px when stabilizing)

### Privacy & Trust
- **No tracking** - zero analytics or data collection
- **No accounts** - no login required
- **No servers** - everything runs locally
- **Open source** - code is public and auditable

### Performance
- **60 FPS target** - smooth, responsive stabilization
- **Low latency** - sub-16ms motion processing
- **Battery efficient** - optimized algorithms
- **Progressive Web App** - fast load, works offline

## 🛠️ Installation

### For Users

**Option 1: Direct Use (Easiest)**
1. Visit the hosted version at [your-url-here]
2. Tap "Add to Home Screen" on iOS or "Install App" on Android
3. Grant motion sensor permissions when prompted
4. Start reading!

**Option 2: Self-Host**
1. Download `steadyread.html` and `manifest.json`
2. Host on any HTTPS server (required for motion sensors)
3. Access from your mobile device

**Option 3: Local Testing**
```bash
# Simple Python server
python3 -m http.server 8000

# Or use any local server
npx serve
```

### For Developers

```bash
# Clone repository
git clone https://github.com/your-username/steadyread.git
cd steadyread

# Open in browser
# No build process needed - it's pure HTML/CSS/JS!
```

## 📖 Usage

1. **Enable Stabilization**
   - Tap the "Enable Stabilization" button
   - Grant motion sensor permission (iOS will prompt)
   - The app begins stabilizing content

2. **Adjust Sensitivity**
   - Use the slider to tune stabilization strength
   - Lower (10-20) for mild tremors
   - Higher (30-50) for pronounced shaking
   - Experiment to find what works for you

3. **Read Comfortably**
   - Content automatically scales to larger text
   - Gently shake your device to test
   - Text should remain relatively stable

4. **Customize Settings**
   - Tap the gear icon (⚙️) for settings
   - Toggle large text mode on/off
   - Enable/disable drift correction
   - Turn on debug mode to see technical details

## 🧪 How It Works

### The Algorithm

```javascript
// Simplified version of the stabilization logic

1. Read accelerometer data (acceleration in X, Y, Z)
2. Calculate target velocity: -acceleration × sensitivity × 0.1
3. Apply smoothing: velocity = velocity × 0.85 + target × 0.15
4. Update offset: offset += velocity
5. Apply drift correction: offset × 0.995 (gradually recenter)
6. Limit offset: max ±50px (prevent excessive drift)
7. Transform content: translate(offsetX, offsetY)
8. Repeat at 60 FPS
```

### Key Parameters

- **Sensitivity**: 10-50 (default 25)
  - Controls how much movement is compensated
  
- **Smoothing**: 0.85 (85%)
  - Higher = smoother but more lag
  - Lower = more responsive but jittery

- **Drift Correction**: 0.995
  - Gradually returns content to center
  - Prevents accumulating error over time

- **Max Offset**: 50px
  - Prevents content from drifting too far
  - Balances stabilization with content visibility

## 🔬 Research & Evidence

This project is built on scientific research about:

1. **Hand Tremors & Reading**
   - Small fonts are particularly difficult for tremor patients
   - Visual stabilization significantly improves reading comfort
   - Real-time compensation reduces eye strain

2. **Typography for Accessibility**
   - Sans-serif fonts improve readability for visual impairments
   - Lexend specifically designed for reading speed and dyslexia
   - Larger text (20-26px) improves legibility

3. **Motion Stabilization**
   - Camera stabilization principles apply to UI
   - Low-latency processing essential (< 16ms)
   - Smoothing filters prevent overcorrection

### References
- [Support System to Improve Reading Activity in PD and ET Patients](https://pmc.ncbi.nlm.nih.gov/articles/PMC5469529/)
- [Good Fonts for Dyslexia - Research Study](https://blog.dyslexia.com/good-fonts-for-dyslexia-an-experimental-study/)
- [WCAG 2.1 Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

## 🤝 Contributing

We welcome contributions! This project exists to help people, and community input makes it better.

### Ways to Contribute

1. **Test & Report**
   - Use the app if you have tremors
   - Report bugs or issues
   - Share your experience

2. **Improve Code**
   - Optimize stabilization algorithm
   - Add new features
   - Fix bugs
   - Improve documentation

3. **Spread the Word**
   - Share with support groups
   - Tell healthcare providers
   - Write about your experience

### Development Guidelines

- Keep it simple - single HTML file when possible
- Maintain accessibility standards
- Test on real devices with tremors
- Document all changes
- No external dependencies (keep it lightweight)

## 🎯 Roadmap

### Phase 2: Full Browser
- [ ] URL input and webpage loading
- [ ] Browser controls (back, forward, refresh)
- [ ] Bookmarks system
- [ ] Reading list
- [ ] History

### Phase 3: Advanced Features
- [ ] Multiple sensitivity presets
- [ ] Custom font selection
- [ ] Theme customization (dark mode, colors)
- [ ] Reading statistics
- [ ] Cloud sync (optional)

### Phase 4: Platform Expansion
- [ ] Native iOS app
- [ ] Native Android app
- [ ] Desktop version
- [ ] Browser extension

## 📄 License

MIT License - Free to use, modify, and distribute.

See [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Staybl** - Inspiration from their iPad stabilization browser
- **Essential Tremor Foundation** - Resources and awareness
- **Parkinson's Foundation** - Research and education
- **Lexend Font** - Open source accessible typography
- **The accessibility community** - For guidance and standards

## 💬 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/your-username/steadyread/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-username/steadyread/discussions)
- **Email**: info.projectfennec@gmail.com

## ⚠️ Disclaimer

SteadyRead is an assistive tool, not a medical device. It does not diagnose, treat, or cure any medical condition. Always consult healthcare professionals for medical advice.

## 🌟 Star Us!

If SteadyRead helps you or someone you know, please star the repository! It helps others discover the project.

---

**Made with ❤️ for the accessibility community**

*"Making the digital world readable for everyone"*
