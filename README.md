# 🔗 Linktree Clone Template

A single-file, multilingual Linktree clone with SEO-friendly static HTML links. Features dark glassmorphism design, language switcher, QR code generation, social sharing, and smooth animations.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap&logoColor=white)
![jQuery](https://img.shields.io/badge/jQuery-3.7-0769AD?logo=jquery&logoColor=white)

## 🌐 Live Demo

**[View Live Demo →](https://www.ediware.eu/bio_links_demo.html)**
**[View Reel Demo →](https://www.ediware.net/link-bio.html)**

## ✨ Features

- **🌍 Multilingual Support** – CSS-based language switching (EN/FR by default, easily extensible)
- **🔍 SEO-Friendly** – All links are static HTML `<a href>` tags, fully crawlable by search engines
- **🎨 Glassmorphism Design** – Modern dark theme with blur effects and gradient backgrounds
- **📱 Fully Responsive** – Mobile-first design, works on all devices
- **📤 Social Sharing** – Share via WhatsApp, Facebook, X, LinkedIn, Telegram, Email, SMS
- **📷 QR Code Generator** – Dynamic QR code with download option
- **⚡ Single File** – Everything in one HTML file, no build process required
- **🎭 Smooth Animations** – Fade-in effects and hover interactions
- **✅ Verified Badge** – Optional verification badge on avatar
- **🔗 Customizable Links** – Different links per language, or shared across all

## 🚀 Quick Start

1. **Download** the `linktree-template.html` file
2. **Open** it in your favorite code editor
3. **Customize** your content (see Configuration section below)
4. **Upload** to your web server

That's it! No dependencies to install.

## 📁 File Structure

```
linktree-template.html    # Single file containing everything
├── <head>                # Meta tags, CDN links, CSS
├── <body>                # HTML structure
│   ├── Language Switcher
│   ├── Profile Header (Avatar, Name, Bio)
│   ├── Links List (per language)
│   ├── Social Icons
│   ├── Share/QR Buttons
│   └── Footer
├── Modals                # Share & QR Code modals
└── <script>              # JavaScript (language detection, QR, sharing)
```

## ⚙️ Configuration

### 1. Profile Information

Edit the profile section in HTML:

```html
<!-- Avatar -->
<img src="YOUR_IMAGE_URL" alt="Photo de profil" class="avatar">

<!-- Name -->
<h1 class="profile-name">Your Name</h1>

<!-- Handle -->
<p class="profile-handle">@yourhandle</p>

<!-- Bio (per language) -->
<p class="profile-bio" data-lang="en">Your English bio here</p>
<p class="profile-bio" data-lang="fr">Votre bio en français ici</p>
```

### 2. Links

Each link is duplicated per language. Edit or add links in the `.links-container`:

```html
<!-- English Link -->
<a href="https://yoursite.com" class="link-item" data-lang="en" target="_blank">
    <i class="bi bi-globe link-icon"></i>
    <span class="link-text">My Website</span>
    <i class="bi bi-arrow-up-right link-external"></i>
</a>

<!-- French Link -->
<a href="https://yoursite.com/fr" class="link-item" data-lang="fr" target="_blank">
    <i class="bi bi-globe link-icon"></i>
    <span class="link-text">Mon Site Web</span>
    <i class="bi bi-arrow-up-right link-external"></i>
</a>
```

#### Link in one language only

Simply create the link only for that language:

```html
<!-- This podcast link only appears in French -->
<a href="https://podcast.example.com/fr" class="link-item" data-lang="fr" target="_blank">
    <i class="bi bi-mic link-icon"></i>
    <span class="link-text">🎙️ Mon podcast en français</span>
    <i class="bi bi-arrow-up-right link-external"></i>
</a>
```

#### Link common to all languages

Remove the `data-lang` attribute:

```html
<!-- This link is always visible -->
<a href="https://youtube.com/@example" class="link-item" target="_blank">
    <i class="bi bi-youtube link-icon"></i>
    <span class="link-text">YouTube</span>
    <i class="bi bi-arrow-up-right link-external"></i>
</a>
```

### 3. Social Icons

Edit the social icons section:

```html
<div class="social-icons">
    <a href="https://instagram.com/YOUR_HANDLE" class="social-icon" target="_blank" title="Instagram">
        <i class="bi bi-instagram"></i>
    </a>
    <!-- Add more icons... -->
</div>
```

**Available icons:** `bi-instagram`, `bi-twitter-x`, `bi-linkedin`, `bi-facebook`, `bi-tiktok`, `bi-youtube`, `bi-twitch`, `bi-discord`, `bi-github`, `bi-pinterest`, `bi-snapchat`, `bi-spotify`, `bi-whatsapp`, `bi-telegram`, `bi-threads`

Browse all icons: [Bootstrap Icons](https://icons.getbootstrap.com/)

### 4. Colors

Customize the color scheme by editing CSS variables in `:root`:

```css
:root {
    /* Background gradient */
    --bg-gradient-start: #0f0c29;
    --bg-gradient-middle: #302b63;
    --bg-gradient-end: #24243e;
    
    /* Buttons */
    --btn-background: rgba(255, 255, 255, 0.08);
    --btn-background-hover: rgba(255, 255, 255, 0.15);
    --btn-border: rgba(255, 255, 255, 0.18);
    --btn-text: #ffffff;
    
    /* Text */
    --text-primary: #ffffff;
    --text-secondary: rgba(255, 255, 255, 0.75);
    --text-muted: rgba(255, 255, 255, 0.5);
}
```

## 🌍 Language Management

### How it works

1. The `<body>` receives a class like `lang-en` or `lang-fr`
2. CSS rules show/hide elements based on their `data-lang` attribute
3. JavaScript detects browser language and applies the correct class
4. User selection is saved in `localStorage`

### Add a new language

1. **Add CSS rules:**

```css
body.lang-de [data-lang="de"] { display: block !important; }
body.lang-de span[data-lang="de"] { display: inline !important; }
body.lang-de a.link-item[data-lang="de"] { display: flex !important; }
```

2. **Add the flag button:**

```html
<button class="lang-btn" data-lang="de" title="Deutsch" aria-label="Deutsch">🇩🇪</button>
```

3. **Add the language to JavaScript:**

```javascript
const LANGUAGES = ['en', 'fr', 'de'];

const SHARE_TEXTS = {
    'en': 'Check out my profile!',
    'fr': 'Découvrez mon profil !',
    'de': 'Schau dir mein Profil an!'
};
```

4. **Add HTML content** with `data-lang="de"` for all translatable elements

### Use only one language

1. Keep only one language in the HTML
2. Add `single-lang` class to hide the switcher:

```html
<div class="language-switcher single-lang" id="languageSwitcher">
```

## 🔍 SEO Optimization

Add these meta tags in the `<head>` section after `<title>`:

```html
<!-- SEO Meta Tags -->
<meta name="description" content="Your bio description here">
<meta name="keywords" content="your, keywords, here">
<meta name="author" content="Your Name">
<meta name="robots" content="index, follow">

<!-- Open Graph / Facebook -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://yourdomain.com/">
<meta property="og:title" content="@yourhandle - Profile">
<meta property="og:description" content="Your bio description here">
<meta property="og:image" content="https://yourdomain.com/og-image.jpg">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:url" content="https://yourdomain.com/">
<meta name="twitter:title" content="@yourhandle - Profile">
<meta name="twitter:description" content="Your bio description here">
<meta name="twitter:image" content="https://yourdomain.com/og-image.jpg">

<!-- Canonical URL -->
<link rel="canonical" href="https://yourdomain.com/">
```

**Recommended OG image size:** 1200x630px

## 📦 Dependencies (via CDN)

All dependencies are loaded from CDN, no installation required:

| Library | Version | Purpose |
|---------|---------|---------|
| [Bootstrap](https://getbootstrap.com/) | 5.3.2 | CSS framework & modals |
| [Bootstrap Icons](https://icons.getbootstrap.com/) | 1.11.1 | Icon library |
| [jQuery](https://jquery.com/) | 3.7.1 | DOM manipulation |
| [QRCode.js](https://github.com/davidshimjs/qrcodejs) | 1.0.0 | QR code generation |
| [Google Fonts](https://fonts.google.com/) | - | Plus Jakarta Sans font |

## 🎨 Customization Examples

### Light Theme

```css
:root {
    --bg-gradient-start: #f8f9fa;
    --bg-gradient-middle: #e9ecef;
    --bg-gradient-end: #dee2e6;
    --btn-background: rgba(0, 0, 0, 0.05);
    --btn-border: rgba(0, 0, 0, 0.1);
    --btn-text: #212529;
    --text-primary: #212529;
    --text-secondary: rgba(0, 0, 0, 0.7);
}
```

### Gradient Accent

```css
:root {
    --bg-gradient-start: #1a1a2e;
    --bg-gradient-middle: #16213e;
    --bg-gradient-end: #0f3460;
}
```

### Remove Verified Badge

Simply delete this HTML block:

```html
<div class="verified-badge"><i class="bi bi-check-lg"></i></div>
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 💡 Credits

- Design inspired by [Linktree](https://linktr.ee/)
- Icons by [Bootstrap Icons](https://icons.getbootstrap.com/)
- Font by [Google Fonts](https://fonts.google.com/specimen/Plus+Jakarta+Sans)

---

Made with ❤️ by [Loïc](https://www.ediware.eu)
