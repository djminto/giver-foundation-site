# Troubleshooting Guide - The Giver Foundation Website

## 🔍 Common Issues and Solutions

### Installation Issues

#### "npm install" fails
**Problem**: Package installation errors

**Solutions**:
1. Check Node.js version:
   ```powershell
   node --version
   ```
   Should be v14 or higher

2. Clear npm cache:
   ```powershell
   npm cache clean --force
   npm install
   ```

3. Delete node_modules and try again:
   ```powershell
   Remove-Item -Recurse -Force node_modules
   Remove-Item package-lock.json
   npm install
   ```

#### "Cannot find module" errors
**Problem**: Missing dependencies

**Solution**:
```powershell
npm install
```

### Running the Application

#### "EADDRINUSE: Port already in use"
**Problem**: Port 3000 or 5000 is occupied

**Solutions**:
1. Find and kill the process:
   ```powershell
   # For port 3000
   netstat -ano | findstr :3000
   taskkill /PID [PID_NUMBER] /F

   # For port 5000
   netstat -ano | findstr :5000
   taskkill /PID [PID_NUMBER] /F
   ```

2. Or change the port in `vite.config.js`:
   ```javascript
   server: {
     port: 3001, // Changed from 3000
   }
   ```

#### "npm run dev" does nothing
**Problem**: Scripts not running

**Solutions**:
1. Check if concurrently is installed:
   ```powershell
   npm install concurrently --save-dev
   ```

2. Run frontend and backend separately:
   ```powershell
   # Terminal 1
   npm run client

   # Terminal 2
   npm run server
   ```

### Database Issues

#### "MongooseServerSelectionError"
**Problem**: Cannot connect to MongoDB

**Solutions**:
1. If using local MongoDB:
   ```powershell
   # Check if MongoDB is running
   Get-Service MongoDB

   # Start if not running
   Start-Service MongoDB
   ```

2. If using MongoDB Atlas:
   - Check connection string in `.env`
   - Verify network access (allow 0.0.0.0/0)
   - Check database user permissions
   - Ensure password doesn't have special characters (or URL encode them)

#### "Authentication failed"
**Problem**: Wrong MongoDB credentials

**Solution**:
1. Verify credentials in MongoDB Atlas
2. Regenerate database user password
3. Update connection string in `.env`
4. Make sure to URL encode password if it contains special characters

### Authentication Issues

#### "Token is not valid"
**Problem**: JWT token issues

**Solutions**:
1. Clear browser localStorage:
   - Open DevTools (F12)
   - Go to Application > Local Storage
   - Clear all items
   - Refresh page

2. Check JWT_SECRET in `.env`:
   ```env
   JWT_SECRET=a_very_long_secure_random_string
   ```

3. Log out and log in again

#### "Cannot register/login"
**Problem**: Registration or login fails

**Solutions**:
1. Check backend is running (should see "Server running on port 5000")
2. Check MongoDB connection
3. Open browser console (F12) for error messages
4. Verify email format is correct
5. Ensure password is at least 6 characters

#### "Access denied. Admin only."
**Problem**: Cannot access admin dashboard

**Solutions**:
1. Verify email matches ADMIN_EMAIL in `.env`
2. Delete existing account and re-register with admin email
3. Check user role in MongoDB:
   ```javascript
   // In MongoDB Compass or Shell
   db.users.find({ email: "your-admin@email.com" })
   // Should show role: "admin"
   ```

### Email Issues

#### Emails not sending
**Problem**: Email notifications not working

**Solutions**:
1. For Gmail, enable App Passwords:
   - Go to Google Account > Security
   - Enable 2-Factor Authentication
   - Generate App Password
   - Use 16-character password in `.env`

2. Check email configuration:
   ```env
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASSWORD=your-16-char-app-password
   ```

3. For development, emails are logged to console if credentials missing

4. Check server logs for email errors

### Frontend Issues

#### "Blank white page"
**Problem**: Page doesn't load

**Solutions**:
1. Check browser console (F12) for errors
2. Verify backend is running on port 5000
3. Check if MongoDB is connected
4. Clear browser cache and hard refresh (Ctrl+Shift+R)

#### "Network Error" or "Failed to fetch"
**Problem**: Cannot connect to backend

**Solutions**:
1. Verify backend is running:
   ```powershell
   # Should see "Server running on port 5000"
   ```

2. Check proxy in `vite.config.js`:
   ```javascript
   server: {
     proxy: {
       '/api': 'http://localhost:5000'
     }
   }
   ```

3. Try accessing backend directly:
   - Open browser
   - Go to: http://localhost:5000/api/testimonials
   - Should see JSON response

#### Components not rendering
**Problem**: UI elements missing

**Solutions**:
1. Check import paths are correct
2. Verify all CSS files are imported
3. Check for console errors
4. Ensure all dependencies installed

### Upload/Form Issues

#### "Cannot submit report"
**Problem**: Form submission fails

**Solutions**:
1. Check if logged in (reports require authentication)
2. Fill all required fields (marked with *)
3. Check file size if uploading images
4. Check browser console for errors

#### Images not displaying
**Problem**: Logo or images not showing

**Solutions**:
1. Verify logo exists at `Image/Logo.jpeg`
2. Check file name matches exactly (case-sensitive)
3. Use correct path in components: `/Image/Logo.jpeg`

### Styling Issues

#### Styles not applying
**Problem**: CSS not working

**Solutions**:
1. Verify CSS file is imported in component
2. Check CSS file path is correct
3. Clear browser cache
4. Check for CSS syntax errors
5. Verify class names match

#### Animations not working
**Problem**: Framer Motion animations not showing

**Solutions**:
1. Verify framer-motion is installed:
   ```powershell
   npm install framer-motion
   ```

2. Check component imports:
   ```javascript
   import { motion } from 'framer-motion';
   ```

3. Try disabling browser motion preferences

### Performance Issues

#### "Application is slow"
**Problem**: Poor performance

**Solutions**:
1. Clear browser cache
2. Check Network tab in DevTools for slow requests
3. Verify MongoDB query performance
4. Check for console errors or warnings
5. Restart development server

#### "Too many re-renders"
**Problem**: React infinite loop

**Solutions**:
1. Check useEffect dependencies
2. Verify state updates are not causing loops
3. Check for circular imports

## 🐛 Debugging Tips

### Check Browser Console
Always open DevTools (F12) and check:
- Console tab for errors
- Network tab for failed requests
- Application tab for localStorage issues

### Check Server Logs
Look at the terminal running the server for:
- Error messages
- Request logs
- MongoDB connection status

### Common Console Errors

#### "Cannot read property of undefined"
**Cause**: Trying to access data before it loads

**Solution**: Add optional chaining:
```javascript
// Instead of: user.name
// Use: user?.name
```

#### "React Hook useEffect has a missing dependency"
**Solution**: Add dependency or disable warning if intentional:
```javascript
// eslint-disable-next-line react-hooks/exhaustive-deps
```

#### "Failed to compile"
**Solution**: 
- Check for syntax errors
- Verify all imports are correct
- Save the file again

## 📱 Testing Checklist

When troubleshooting, test these systematically:

### Backend
- [ ] Server starts without errors
- [ ] MongoDB connects successfully
- [ ] Can register a new user
- [ ] Can login with credentials
- [ ] Can submit a report (when logged in)
- [ ] Can make a donation
- [ ] Admin can access dashboard

### Frontend
- [ ] Home page loads
- [ ] Navigation works
- [ ] All pages accessible
- [ ] Forms validate properly
- [ ] Buttons respond
- [ ] Animations play
- [ ] Mobile responsive

### Integration
- [ ] Login sets token in localStorage
- [ ] Protected routes redirect properly
- [ ] API calls return data
- [ ] Errors show toast notifications
- [ ] Email notifications sent

## 🆘 Getting Help

If you're still stuck:

1. **Check the error message carefully**
   - Copy the exact error
   - Search online for the error

2. **Review the relevant files**
   - Check the file mentioned in the error
   - Review related documentation

3. **Test in isolation**
   - Test the backend alone
   - Test the frontend alone
   - Identify which part is failing

4. **Check the guides**
   - README.md for overview
   - QUICKSTART.md for setup
   - DEPLOYMENT.md for production

5. **Verify your setup**
   - Node.js version correct
   - MongoDB running
   - Environment variables set
   - Dependencies installed

## 💡 Prevention Tips

To avoid issues:
- Always keep terminal open to see errors
- Check both frontend and backend terminals
- Save files before testing
- Clear cache when testing changes
- Keep dependencies updated
- Don't modify node_modules
- Use version control (git)
- Test one feature at a time

## 🔄 Reset Everything

If all else fails, complete reset:

```powershell
# Stop all servers (Ctrl+C in terminals)

# Delete generated files
Remove-Item -Recurse -Force node_modules
Remove-Item package-lock.json

# Reinstall
npm install

# Clear browser data
# In browser: Ctrl+Shift+Delete > Clear all

# Restart MongoDB (if local)
Restart-Service MongoDB

# Start fresh
npm run dev
```

---

**Remember**: Most issues are either:
1. Missing dependencies
2. Wrong environment variables
3. Server not running
4. MongoDB not connected
5. Wrong file paths

Check these first! 🔍
