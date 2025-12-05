# The Giver Foundation Website

A modern, full-featured website for The Giver Foundation with both static HTML and React versions.

## 🚀 Two Ways to Run This Website

### Option 1: Static HTML with Live Server (Simplest)

Perfect for quick viewing and testing without any setup!

**Steps:**
1. Open this folder in VS Code
2. Right-click on `index.html`
3. Select "Open with Live Server"
4. OR click the "Go Live" button in the bottom-right corner

Your website will open at `http://127.0.0.1:5500`

**All Pages:**
- `index.html` - Home page
- `about.html` - About page with team
- `how-it-works.html` - Process explanation
- `report.html` - Report submission
- `donate.html` - Donations
- `testimonials.html` - User reviews
- `contact.html` - Contact form
- `login.html` - Login (3D styled)
- `register.html` - Registration (3D styled)

### Option 2: Full React App with Backend (Advanced)

For the complete experience with database, authentication, and API.

**Prerequisites:**
- Node.js installed (✅ Already installed)
- MongoDB installed (✅ Already installed)

**Steps:**
1. Make sure MongoDB is running
2. Configure `.env` file with your settings
3. Open terminal in this folder
4. Run: `npm run dev`
5. Visit `http://localhost:3000`

## 📁 Project Structure

```
.
├── index.html              # Static homepage (for Live Server)
├── about.html              # Static about page
├── *.html                  # All other static pages
├── css/                    # Styles for static pages
├── js/                     # JavaScript for static pages
├── Image/                  # Logo and images
│
├── src/                    # React source code
├── server/                 # Backend API
├── package.json            # Dependencies
└── static/                 # Original static files (backup)
```

## ✨ Features

### Static HTML Version:
- ✅ Works with VS Code Live Server
- ✅ No installation required
- ✅ All pages fully functional
- ✅ Forms save to localStorage
- ✅ Modern animations
- ✅ Mobile responsive
- ✅ 3D styled auth pages

### React Version:
- ✅ Full authentication system
- ✅ MongoDB database integration
- ✅ Admin dashboard
- ✅ Email notifications
- ✅ User profiles
- ✅ Report management
- ✅ Donation tracking

## 🎨 Customization

### Change Colors:
Edit `css/style.css` and update the CSS variables:
```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #7c3aed;
    /* ... */
}
```

### Change Logo:
Replace `Image/Logo.jpeg` with your logo (keep the same name)

## 📝 Forms

**Static HTML version:** Forms save data to browser's localStorage for demonstration.

**To connect to a backend:**
1. Open the JavaScript files in `js/` folder
2. Uncomment the fetch API calls
3. Replace URLs with your API endpoints

## 🌐 Deployment

### Deploy Static HTML:
- **Netlify**: Drag and drop this folder
- **GitHub Pages**: Push to GitHub, enable Pages
- **Vercel**: Import project
- **Any hosting**: Upload via FTP

### Deploy React App:
See `DEPLOYMENT.md` for detailed instructions

## 🔧 Technologies

- HTML5, CSS3, JavaScript (Vanilla)
- React 18 (optional)
- Node.js + Express (optional)
- MongoDB (optional)
- Font Awesome 6.4.0
- Google Fonts (Poppins)

## 💡 Recommendation

**For quick testing:** Use the Static HTML version with Live Server  
**For production:** Use the React version with backend

## 📞 Support

- Email: info@giverfoundation.org
- Phone: (555) 123-4567

---

**Made by MintoWebDesign** 💻  
© 2025 The Giver Foundation