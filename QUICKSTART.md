# Quick Start Guide - The Giver Foundation Website

## 🚀 Get Started in 5 Minutes

### Step 1: Install Node.js
If you don't have Node.js installed:
1. Visit https://nodejs.org/
2. Download and install the LTS version
3. Verify installation: Open PowerShell and run `node --version`

### Step 2: Install MongoDB
Choose one option:

**Option A: Local MongoDB (Windows)**
1. Download from https://www.mongodb.com/try/download/community
2. Install with default settings
3. MongoDB will run automatically as a Windows service

**Option B: MongoDB Atlas (Cloud - Recommended for beginners)**
1. Go to https://www.mongodb.com/cloud/atlas
2. Sign up for free
3. Create a free cluster (takes 3-5 minutes)
4. Click "Connect" and get your connection string
5. Use it in the `.env` file

### Step 3: Configure the Project
1. Open the `.env` file in the project folder
2. Update these values:

```env
# If using local MongoDB, leave as is:
MONGODB_URI=mongodb://localhost:27017/giver-foundation

# If using MongoDB Atlas, replace with your connection string:
# MONGODB_URI=mongodb+srv://youruser:yourpassword@cluster.mongodb.net/giver-foundation

# Change this to something secure:
JWT_SECRET=my_super_secret_key_12345

# For email features (optional for testing):
EMAIL_USER=your-email@gmail.com
EMAIL_PASSWORD=your-app-password

# Set your admin email:
ADMIN_EMAIL=your-email@example.com
```

### Step 4: Install Dependencies
Open PowerShell in the project folder and run:
```powershell
npm install
```

This will take 2-3 minutes to download all required packages.

### Step 5: Start the Application
Run this command:
```powershell
npm run dev
```

You should see:
```
Server running on port 5000
MongoDB Connected
VITE ready in XXX ms
```

### Step 6: Open in Browser
1. Open your browser
2. Go to: http://localhost:3000
3. You should see the beautiful homepage!

### Step 7: Create Admin Account
1. Click "Register" in the navigation
2. Fill in the form
3. **Important**: Use the same email you set as `ADMIN_EMAIL` in the `.env` file
4. After registering, you'll have admin access and can see the Dashboard

## 🎯 Test the Features

### As a Regular User:
1. Register with any email
2. Submit a report (Report page)
3. Make a donation (Donation page)
4. Leave a testimonial (Testimonials page)
5. Update your profile (Profile page)

### As an Admin:
1. Register with the ADMIN_EMAIL
2. Access the Dashboard
3. View all reports and donations
4. Approve or deny reports
5. See statistics

## 📧 Email Setup (Optional)

If you want email notifications to work:

1. Go to your Google Account: https://myaccount.google.com/
2. Enable 2-Factor Authentication
3. Go to App Passwords: https://myaccount.google.com/apppasswords
4. Generate a new app password for "Mail"
5. Copy the 16-character password
6. Add it to your `.env` file as `EMAIL_PASSWORD`

## ❓ Common Issues

### "MONGODB connection error"
- Make sure MongoDB is running (if local)
- Check your connection string in `.env`
- If using Atlas, check your network access settings

### "Port 3000 already in use"
- Close other applications using port 3000
- Or change the port in `vite.config.js`

### "Module not found"
- Run `npm install` again
- Delete `node_modules` folder and run `npm install`

### Pages not loading
- Make sure both frontend and backend are running
- Check the browser console for errors
- Verify the backend is on port 5000

## 🎨 Customization

### Change Colors
Edit `src/index.css` and modify the CSS variables:
```css
:root {
  --primary-color: #1a73e8;
  --secondary-color: #34a853;
  /* etc... */
}
```

### Update Logo
Replace `Image/Logo.jpeg` with your logo (keep the same name or update references)

### Modify Content
- Home page: `src/pages/Home.jsx`
- About page: `src/pages/About.jsx`
- Team members: Edit the `team` array in `About.jsx`

## 📱 Access on Mobile

1. Find your computer's IP address:
```powershell
ipconfig
```
Look for "IPv4 Address" (e.g., 192.168.1.100)

2. On your phone (connected to same WiFi):
   - Open browser
   - Go to: http://YOUR_IP_ADDRESS:3000
   - Example: http://192.168.1.100:3000

## 🚀 Next Steps

1. **Test all features** - Click through every page
2. **Customize content** - Update text, images, team info
3. **Set up email** - So notifications work
4. **Add real data** - Create test reports and donations
5. **Deploy** - When ready, deploy to Vercel/Netlify (frontend) and Render/Railway (backend)

## 💡 Tips

- Keep the terminal window open while using the site
- Any changes to code will auto-reload the page
- Check terminal for any error messages
- Use browser DevTools (F12) to debug issues

## 🆘 Need Help?

If you encounter issues:
1. Check the terminal for error messages
2. Look in the browser console (F12)
3. Make sure all dependencies are installed
4. Verify MongoDB is running
5. Check the `.env` file is configured correctly

---

**Ready to make a difference! 🌟**

The website is now running and ready to help your community!
