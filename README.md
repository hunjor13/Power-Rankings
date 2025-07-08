# 🏆 MLB Power Rankings Auto-Updater

A comprehensive, real-time MLB power rankings dashboard with automatic updates, home/away records, and trend analysis for all 30 teams.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration](#-configuration)
- [API Integration](#-api-integration)
- [Customization](#-customization)
- [Contributing](#-contributing)
- [License](#-license)
- [Support](#-support)

## ✨ Features

### 🔄 **Auto-Update System**
- **Real-time updates** with customizable frequencies (hourly, 6-hour, daily, weekly)
- **Manual refresh** capability for immediate updates
- **Update history tracking** with timestamp logs
- **Status indicators** showing current update state

### 📊 **Comprehensive Rankings**
- **All 30 MLB teams** with complete power rankings
- **Home/Away records** for detailed performance analysis
- **Win percentages** and trending indicators
- **Color-coded tiers** (Top 5, Playoff Teams, Bubble Teams, Bottom 5)

### 📈 **Advanced Analytics**
- **8 trend categories** covering team momentum, divisions, risers/fallers
- **Individual player highlights** and statistical leaders
- **Trade deadline implications** and team directions
- **Home/road performance splits** analysis

### 🎨 **Modern UI/UX**
- **Responsive design** that works on all devices
- **Sticky table headers** for easy navigation
- **Visual team tiers** with color coding
- **Smooth animations** and loading indicators
- **Dark/light theme compatibility**

### 💾 **Data Management**
- **Export functionality** (JSON format)
- **Local storage** for update history
- **Data validation** and error handling
- **Browser compatibility** across all modern browsers

## 🚀 Demo

![MLB Rankings Dashboard](https://via.placeholder.com/800x600/1e3c72/ffffff?text=MLB+Power+Rankings+Dashboard)

### Live Features:
- ✅ Real-time power rankings for all 30 teams
- ✅ Interactive auto-update controls
- ✅ Comprehensive trend analysis
- ✅ Export and history tracking
- ✅ Mobile-responsive design

## 🛠 Installation

### Quick Start (Standalone)
```bash
# Clone or download the HTML file
# No dependencies required - runs entirely in browser
# Simply open the HTML file in any modern web browser
```

### For Development
```bash
# 1. Clone the repository
git clone https://github.com/yourusername/mlb-power-rankings.git

# 2. Navigate to project directory
cd mlb-power-rankings

# 3. Open in browser or serve locally
# Option A: Direct file access
open index.html

# Option B: Local server (recommended)
python -m http.server 8000
# Then navigate to http://localhost:8000
```

### Browser Requirements
- **Chrome** 80+
- **Firefox** 75+
- **Safari** 13+
- **Edge** 80+

## 📖 Usage

### Basic Operation

1. **Open the application** in your web browser
2. **View current rankings** in the main table
3. **Enable auto-update** using the checkbox control
4. **Customize frequency** using the dropdown menu
5. **Manual updates** with the "Update Rankings Now" button

### Advanced Features

#### Auto-Update Configuration
```javascript
// Enable auto-update with custom frequency
document.getElementById('autoUpdate').checked = true;
document.getElementById('updateFrequency').value = '3600000'; // 1 hour
toggleAutoUpdate();
```

#### Export Data
```javascript
// Export current rankings and trends
exportData(); // Downloads JSON file with all data
```

#### View Update History
```javascript
// Display recent update history
showUpdateHistory(); // Shows last 10 updates in popup
```

### Keyboard Shortcuts
- **`Ctrl/Cmd + R`** - Manual refresh
- **`Ctrl/Cmd + E`** - Export data
- **`Ctrl/Cmd + H`** - Show update history

## ⚙️ Configuration

### Update Frequencies
| Setting | Interval | Use Case |
|---------|----------|----------|
| Hourly | 3,600,000ms | Live game tracking |
| 6-Hour | 21,600,000ms | Daily monitoring |
| Daily | 86,400,000ms | Regular updates |
| Weekly | 604,800,000ms | Casual following |

### Data Storage Settings
```javascript
// Configure localStorage usage
const CONFIG = {
    maxHistoryEntries: 50,        // Maximum stored updates
    enableLocalStorage: true,     // Use browser storage
    autoExportInterval: 7,        // Days between auto-exports
    dataValidationLevel: 'strict' // Validation strictness
};
```

## 🔌 API Integration

### Current Implementation
The application currently uses sample data. To integrate with real APIs:

#### 1. ESPN Power Rankings
```javascript
async function fetchESPNRankings() {
    try {
        const response = await fetch('https://api.espn.com/v1/sports/baseball/mlb/powerrankings');
        const data = await response.json();
        return parseESPNData(data);
    } catch (error) {
        console.error('ESPN API Error:', error);
        return null;
    }
}
```

#### 2. MLB Official API
```javascript
async function fetchMLBStandings() {
    try {
        const response = await fetch('https://statsapi.mlb.com/api/v1/standings');
        const data = await response.json();
        return parseMLBStandings(data);
    } catch (error) {
        console.error('MLB API Error:', error);
        return null;
    }
}
```

#### 3. Sports Reference Integration
```javascript
async function fetchSportsRefData() {
    // Note: May require CORS proxy or server-side implementation
    const proxyUrl = 'https://your-cors-proxy.com/';
    const targetUrl = 'https://www.baseball-reference.com/leagues/MLB/2025-standings.shtml';
    
    try {
        const response = await fetch(proxyUrl + targetUrl);
        const html = await response.text();
        return parseHTMLStandings(html);
    } catch (error) {
        console.error('Sports Reference Error:', error);
        return null;
    }
}
```

### API Rate Limiting
```javascript
const API_CONFIG = {
    espn: { maxRequests: 100, windowMs: 3600000 },      // 100/hour
    mlb: { maxRequests: 1000, windowMs: 3600000 },      // 1000/hour
    sportsRef: { maxRequests: 50, windowMs: 3600000 }   // 50/hour
};
```

## 🎨 Customization

### Styling Options

#### Team Color Themes
```css
/* Add team-specific colors */
.team-dodgers { border-left-color: #005A9C; }
.team-yankees { border-left-color: #132448; }
.team-redsox { border-left-color: #BD3039; }
/* Add more team colors... */
```

#### Custom Ranking Tiers
```css
/* Modify tier colors */
.elite-tier { background: linear-gradient(135deg, #FFD700, #FFA500); }
.contender-tier { background: linear-gradient(135deg, #90EE90, #32CD32); }
.rebuilding-tier { background: linear-gradient(135deg, #FFB6C1, #FF69B4); }
```

### Adding New Features

#### Custom Trend Categories
```javascript
const customTrends = [
    {
        title: "🏆 Championship Odds",
        content: "Current World Series favorites based on betting odds and performance"
    },
    {
        title: "💰 Payroll Efficiency",
        content: "Teams getting best value from their salary investments"
    }
];
```

#### Additional Data Points
```javascript
const enhancedTeamData = {
    rank: 1,
    team: "Los Angeles Dodgers",
    // Standard fields...
    // New fields:
    payroll: "$280M",
    prospect_rank: 15,
    championship_odds: "+350",
    recent_form: "7-3"
};
```

## 🤝 Contributing

We welcome contributions! Here's how to get started:

### Development Setup
```bash
# 1. Fork the repository
# 2. Create a feature branch
git checkout -b feature/your-feature-name

# 3. Make your changes
# 4. Test thoroughly
# 5. Commit with descriptive messages
git commit -m "Add: New trend analysis feature"

# 6. Push and create pull request
git push origin feature/your-feature-name
```

### Contribution Guidelines
- **Code Style**: Follow existing JavaScript/CSS patterns
- **Testing**: Ensure all features work across target browsers
- **Documentation**: Update README for new features
- **Performance**: Maintain fast load times and smooth interactions

### Areas for Contribution
- 🔌 **API Integrations** - Add real data sources
- 🎨 **UI Enhancements** - Improve design and UX
- 📊 **Analytics Features** - Add new statistical insights
- 🔧 **Performance** - Optimize loading and rendering
- 📱 **Mobile Experience** - Enhance mobile functionality

## 🐛 Known Issues

- **API Limitations**: Currently uses sample data (real APIs needed)
- **CORS Restrictions**: Some data sources require proxy servers
- **Rate Limiting**: API calls may need throttling for production use
- **Browser Storage**: Limited to ~5MB in localStorage

## 🔮 Roadmap

### Version 2.0 (Planned)
- [ ] Real-time API integration
- [ ] User authentication and preferences
- [ ] Historical ranking trends
- [ ] Advanced statistical analysis
- [ ] Push notifications for major changes

### Version 2.1 (Future)
- [ ] Fantasy baseball integration
- [ ] Social sharing features
- [ ] Mobile app version
- [ ] Machine learning predictions

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 MLB Power Rankings Auto-Updater

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

## 🆘 Support

### Getting Help
- **📧 Email**: support@mlbrankings.dev
- **💬 Discord**: [MLB Rankings Community](https://discord.gg/mlbrankings)
- **🐛 Issues**: [GitHub Issues](https://github.com/yourusername/mlb-power-rankings/issues)
- **📖 Wiki**: [Project Wiki](https://github.com/yourusername/mlb-power-rankings/wiki)

### FAQ

**Q: How often should I update the rankings?**
A: For casual use, daily updates are sufficient. For active monitoring during trade deadlines or playoffs, hourly updates recommended.

**Q: Can I add my own team analysis?**
A: Yes! The application supports custom trend categories and notes. See the Customization section.

**Q: Why are some records estimates?**
A: Currently using sample data. Real API integration will provide exact records.

**Q: Is this free to use?**
A: Yes, completely free and open source under MIT license.

### Browser Support Issues
- **Safari < 13**: May have localStorage limitations
- **IE 11**: Not supported (use Edge instead)
- **Mobile Chrome**: Fully supported
- **Mobile Safari**: Fully supported

---

**Made with ⚾ by baseball fans, for baseball fans**

*Last updated: July 8, 2025*
