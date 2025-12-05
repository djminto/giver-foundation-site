# The Giver Foundation Website

A modern, full-stack web application for The Giver Foundation - a community-focused organization dedicated to making a difference by providing support and assistance to those in need.

## 🌟 Features

### User Features
- **User Authentication**: Secure registration and login system
- **Report Submission**: Submit detailed reports about community issues or needs
- **Legal pages**: `terms.html`, `privacy.html` (Jamaica DPA aligned)
- **Admin Dashboard**: Comprehensive overview of all foundation activities
### Design Features
- **Modern 3D UI**: Beautiful 3D effects on login/register pages
- **Smooth Animations**: Framer Motion animations throughout
- **Responsive Design**: Works perfectly on all devices
- **Gradient Designs**: Modern color schemes matching the logo
- **Professional Layout**: Clean, intuitive navigation

## 🚀 Tech Stack

### Frontend
- **React 18** - UI library
- **React Router** - Navigation
- **Framer Motion** - Animations
- **Axios** - HTTP client
- **React Icons** - Icon library
- **React Toastify** - Notifications
- **Vite** - Build tool

### Backend
- **Node.js** - Runtime environment
- **Express** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Nodemailer** - Email service

## 📋 Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)
- npm or yarn
- Git

## 🛠️ Installation

### 1. Clone the repository
```bash
cd "C:\Users\Daniel Minto\OneDrive\Desktop\The Giver Foundation website"
```

### 2. Install dependencies
```bash
npm install
```

### 3. Environment Setup
Create a `.env` file in the root directory:

```env
# Database
MONGODB_URI=mongodb://localhost:27017/giver-foundation
# Or use MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/giver-foundation

# JWT Secret (change this to a random string)
JWT_SECRET=your_super_secret_jwt_key_here_change_this

# Email Configuration (for Gmail)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_password

# Admin Credentials (founder email)
ADMIN_EMAIL=founder@giverfoundation.org

# Server
PORT=5000
NODE_ENV=development
```

### 4. Set up Gmail for emails (Optional but recommended)
1. Go to your Google Account settings
2. Enable 2-Factor Authentication
3. Generate an App Password
4. Use that App Password in the `.env` file

### 5. Start MongoDB
If using local MongoDB:
```bash
mongod
```

Or use MongoDB Atlas (cloud database - free tier available)

### 6. Run the application

**Development mode (runs both frontend and backend):**
```bash
npm run dev
```

**Or run separately:**

Frontend:
```bash
npm run client
```

Backend:
```bash
npm run server
```

### 7. Access the application
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## 👤 Admin Access

To access admin features:
1. Register with the email specified in `ADMIN_EMAIL` in your `.env` file
2. You'll automatically be assigned admin role
3. Access the dashboard at `/dashboard`

## 📁 Project Structure

```
The Giver Foundation website/
├── Image/                      # Logo and images
│   └── Logo.jpeg
├── src/                        # Frontend source
│   ├── components/            # React components
│   │   ├── Navbar.jsx
│   │   ├── Footer.jsx
│   │   ├── ProtectedRoute.jsx
│   │   └── AdminRoute.jsx
│   ├── context/              # React context
│   │   └── AuthContext.jsx
│   ├── pages/                # Page components
│   │   ├── Home.jsx
│   │   ├── About.jsx
│   │   ├── Report.jsx
│   │   ├── Contact.jsx
│   │   ├── HowItWorks.jsx
│   │   ├── Login.jsx
│   │   ├── Register.jsx
│   │   ├── Testimonials.jsx
│   │   ├── Donation.jsx
│   │   ├── Profile.jsx
│   │   └── Dashboard.jsx
│   ├── App.jsx               # Main app component
│   ├── main.jsx              # Entry point
│   └── index.css             # Global styles
├── server/                    # Backend source
│   ├── models/               # Database models
│   │   ├── User.js
│   │   ├── Report.js
│   │   ├── Donation.js
│   │   ├── Testimonial.js
│   │   └── Contact.js
│   ├── routes/               # API routes
│   │   ├── auth.js
│   │   ├── reports.js
│   │   ├── donations.js
│   │   ├── testimonials.js
│   │   ├── contact.js
│   │   ├── users.js
│   │   └── admin.js
│   ├── middleware/           # Custom middleware
│   │   └── auth.js
│   ├── utils/                # Utility functions
│   │   └── email.js
│   └── server.js             # Express server
├── index.html                # HTML template
├── package.json              # Dependencies
├── vite.config.js           # Vite configuration
└── .env.example             # Environment variables template
```

## 🎨 Color Scheme

The website uses a modern gradient color scheme:
- Primary: Purple gradient (#667eea to #764ba2)
- Secondary: Pink gradient (#f093fb to #f5576c)
- Accent: Blue gradient (#4facfe to #00f2fe)
- Success: Green (#34a853)
- Warning: Yellow (#fbbc04)
- Danger: Red (#ea4335)

## 📧 Email Notifications

The system automatically sends emails for:
- **Report Submission**: Confirmation to user
- **Report Status Update**: When admin approves/denies
- **Donation Received**: Thank you email with receipt
- **Contact Form**: Confirmation message

## 🔐 Security Features

- JWT-based authentication
- Password hashing with bcrypt
- Protected routes for authenticated users
- Admin-only routes for sensitive operations
- CORS enabled
- Input validation

## 🚀 Deployment

### Frontend (Vercel/Netlify)
1. Build the project: `npm run build`
2. Deploy the `dist` folder

### Backend (Heroku/Railway/Render)
1. Set environment variables
2. Deploy the root directory
3. Ensure MongoDB connection string is set

### Database (MongoDB Atlas)
1. Create a free cluster
2. Get connection string
3. Update MONGODB_URI in .env

## 📱 Pages Overview

1. **Home** - Hero section, stats, features, CTA
2. **About** - Mission, values, team members
3. **How It Works** - Step-by-step process, FAQs
4. **Report** - Submit incident reports
5. **Donation** - Make contributions
6. **Testimonials** - User reviews and ratings
7. **Contact** - Contact form and information
8. **Login/Register** - Authentication with 3D design
9. **Profile** - User account management
10. **Dashboard** - Admin panel (admin only)

## 🤝 Contributing

This is a custom project for The Giver Foundation. For contributions or modifications, please contact the development team.

## 📄 License

© 2024 The Giver Foundation. All rights reserved.

## 👨‍💻 Developer

**Made by MintoWebDesign** 💻

For support or questions, contact the development team.

## 🙏 Acknowledgments

- The Giver Foundation team
- All contributors and supporters
- Open-source community

---

**Note**: Remember to change all default passwords and secrets before deploying to production!
