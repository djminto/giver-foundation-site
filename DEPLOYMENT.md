# Deployment Guide - The Giver Foundation Website

## 🌐 Deploying to Production

This guide will help you deploy your website so it's accessible on the internet.

## 📋 Pre-Deployment Checklist

Before deploying, make sure:
- [ ] All features work locally
- [ ] Environment variables are configured
- [ ] MongoDB database is set up (use MongoDB Atlas for production)
- [ ] Email service is configured
- [ ] Logo and images are optimized
- [ ] Admin email is correctly set

## 🗄️ Step 1: Set Up MongoDB Atlas (Database)

1. **Create Account**
   - Go to https://www.mongodb.com/cloud/atlas
   - Sign up for free

2. **Create Cluster**
   - Click "Build a Database"
   - Choose FREE tier
   - Select your preferred region
   - Click "Create Cluster"

3. **Create Database User**
   - Go to "Database Access"
   - Add new database user
   - Set username and password
   - Save credentials

4. **Allow Access**
   - Go to "Network Access"
   - Click "Add IP Address"
   - Click "Allow Access from Anywhere" (0.0.0.0/0)
   - Confirm

5. **Get Connection String**
   - Click "Connect" on your cluster
   - Choose "Connect your application"
   - Copy the connection string
   - Replace `<password>` with your password
   - Save this for later

## 🚀 Step 2: Deploy Backend (Railway - Free)

Railway is a great free option for hosting the backend.

1. **Prepare Repository**
   ```powershell
   # Initialize git if not already done
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Push to GitHub**
   - Create a new repository on GitHub
   - Push your code:
   ```powershell
   git remote add origin YOUR_GITHUB_URL
   git push -u origin main
   ```

3. **Deploy on Railway**
   - Go to https://railway.app/
   - Sign up with GitHub
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Choose your repository
   - Select the root directory

4. **Configure Environment Variables**
   In Railway, add these variables:
   ```
   MONGODB_URI=your_mongodb_atlas_connection_string
   JWT_SECRET=your_secure_random_string
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASSWORD=your-app-password
   ADMIN_EMAIL=founder@giverfoundation.org
   PORT=5000
   NODE_ENV=production
   ```

5. **Set Start Command**
   - In Railway settings
   - Set start command to: `node server/server.js`

6. **Get Your Backend URL**
   - Railway will provide a URL like: `https://your-app.railway.app`
   - Save this URL

## 🎨 Step 3: Deploy Frontend (Vercel - Free)

Vercel is perfect for React applications.

1. **Update API URLs**
   
   Create `src/config.js`:
   ```javascript
   export const API_URL = import.meta.env.PROD 
     ? 'https://your-backend-url.railway.app/api'
     : '/api';
   ```

   Update `src/context/AuthContext.jsx` to use this URL for axios.

2. **Install Vercel CLI**
   ```powershell
   npm install -g vercel
   ```

3. **Deploy to Vercel**
   ```powershell
   vercel
   ```
   
   Follow the prompts:
   - Set up and deploy? Yes
   - Which scope? Your account
   - Link to existing project? No
   - Project name? the-giver-foundation
   - Directory? ./
   - Override settings? No

4. **Configure Environment Variables**
   In Vercel dashboard:
   - Go to Project Settings > Environment Variables
   - Add:
     ```
     VITE_API_URL=https://your-backend-url.railway.app/api
     ```

5. **Get Your Frontend URL**
   - Vercel provides: `https://the-giver-foundation.vercel.app`
   - Or connect your custom domain

## 🔗 Step 4: Connect Frontend to Backend

1. **Update CORS in Backend**
   
   In `server/server.js`:
   ```javascript
   app.use(cors({
     origin: [
       'http://localhost:3000',
       'https://the-giver-foundation.vercel.app',
       'https://your-custom-domain.com'
     ],
     credentials: true
   }));
   ```

2. **Redeploy Backend**
   - Push changes to GitHub
   - Railway will auto-deploy

3. **Update Frontend API Calls**
   
   Update axios base URL in `src/context/AuthContext.jsx`:
   ```javascript
   axios.defaults.baseURL = 'https://your-backend-url.railway.app';
   ```

## ✅ Step 5: Testing

Test these features:
- [ ] User registration
- [ ] User login
- [ ] Admin login (with ADMIN_EMAIL)
- [ ] Submit a report
- [ ] Make a donation
- [ ] Leave a testimonial
- [ ] Contact form
- [ ] Admin dashboard access
- [ ] Email notifications

## 🎯 Alternative Deployment Options

### Backend Alternatives:
- **Render** (https://render.com) - Free tier
- **Heroku** (https://heroku.com) - Paid after free tier ends
- **DigitalOcean** (https://digitalocean.com) - $5/month

### Frontend Alternatives:
- **Netlify** (https://netlify.com) - Free tier
- **GitHub Pages** - Free (requires build setup)
- **Cloudflare Pages** - Free

## 🔒 Security Checklist

Before going live:
- [ ] Change all default passwords
- [ ] Use strong JWT secret
- [ ] Enable HTTPS (automatic on Vercel/Railway)
- [ ] Set secure environment variables
- [ ] Limit MongoDB IP access if possible
- [ ] Enable 2FA on all accounts
- [ ] Review CORS settings

## 📧 Gmail Setup for Production

1. Create a dedicated email for the foundation
2. Enable 2-Factor Authentication
3. Generate App Password
4. Use in production environment variables
5. Test email sending

## 🌐 Custom Domain (Optional)

### For Vercel (Frontend):
1. Go to Project Settings > Domains
2. Add your domain
3. Update DNS records as instructed
4. Wait for SSL certificate

### For Railway (Backend):
1. Go to Settings > Domains
2. Add custom domain
3. Update DNS records
4. SSL is automatic

## 📊 Monitoring

### Track Your Application:
- **Vercel Analytics** - Built-in for frontend
- **Railway Logs** - Monitor backend
- **MongoDB Atlas Monitoring** - Database metrics
- **Google Analytics** - User tracking

## 🔄 Continuous Deployment

Both Vercel and Railway support auto-deployment:
1. Push to GitHub
2. Services automatically detect changes
3. Build and deploy new version
4. No manual intervention needed

## 💰 Cost Estimates

### Free Tier Usage:
- **MongoDB Atlas**: 512MB storage (free forever)
- **Vercel**: Unlimited deployments (free)
- **Railway**: $5 credit/month (free tier)

### When to Upgrade:
- More than 500MB data → Upgrade MongoDB ($9/month)
- Heavy traffic → Consider Railway Pro ($5+/month)
- Commercial use → Vercel Pro ($20/month)

## 🆘 Troubleshooting Deployment

### "Build Failed"
- Check build logs
- Verify all dependencies are in package.json
- Test build locally: `npm run build`

### "API Connection Failed"
- Verify backend URL is correct
- Check CORS settings
- Ensure backend is deployed and running

### "MongoDB Connection Error"
- Verify connection string
- Check MongoDB Atlas IP whitelist
- Ensure database user has correct permissions

### "Email Not Sending"
- Verify email credentials
- Check app password is correct
- Test with a simple email

## 📱 Post-Deployment

1. **Test on Multiple Devices**
   - Desktop browser
   - Mobile phone
   - Tablet

2. **Share with Team**
   - Send URL to team members
   - Get feedback
   - Make adjustments

3. **Set Up Admin Account**
   - Register with admin email
   - Verify dashboard access
   - Test report management

4. **Create Initial Content**
   - Add real team members
   - Update about page
   - Add sample testimonials

## 🎉 Launch Checklist

- [ ] All features tested in production
- [ ] Admin account created
- [ ] Email notifications working
- [ ] Custom domain configured (if applicable)
- [ ] Monitoring set up
- [ ] Backup strategy in place
- [ ] Documentation updated
- [ ] Team trained on admin panel

---

**Congratulations! 🎊**

Your website is now live and ready to make a difference in your community!

For questions or support, refer to the main README.md file.
