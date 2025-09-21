# Live Polling System - Vercel + Railway Deployment

This guide will help you deploy your polling system using **Vercel** for the frontend and **Railway** for the backend.

## 🚀 Quick Deployment (5 minutes)

### Step 1: Deploy Backend on Railway

1. **Sign up for Railway**

   - Go to [railway.app](https://railway.app)
   - Sign up with GitHub

2. **Deploy Backend**

   - Click "New Project" → "Deploy from GitHub repo"
   - Select your repository
   - Choose the `polling-backend` folder as the root directory
   - Railway will automatically detect it's a Node.js app

3. **Configure Environment Variables**

   - In Railway dashboard, go to your project → Variables
   - Add the following variables:
     ```
     NODE_ENV=production
     PORT=5000
     CLIENT_URL=https://your-frontend-url.vercel.app
     ```

4. **Get Backend URL**
   - Railway will provide a URL like: `https://your-app-name.railway.app`
   - **Note this URL** - you'll need it for the frontend

### Step 2: Deploy Frontend on Vercel

1. **Sign up for Vercel**

   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub

2. **Deploy Frontend**

   - Click "New Project" → Import from GitHub
   - Select your repository
   - Set the root directory to `frontend`
   - Vercel will auto-detect it's a React app

3. **Configure Environment Variables**

   - In Vercel dashboard, go to your project → Settings → Environment Variables
   - Add the following variables:
     ```
     REACT_APP_SERVER_URL=https://your-backend-url.railway.app
     REACT_APP_SOCKET_URL=https://your-backend-url.railway.app
     ```

4. **Get Frontend URL**
   - Vercel will provide a URL like: `https://your-project-name.vercel.app`
   - **Note this URL** - you'll need it to update the backend

### Step 3: Update CORS Configuration

1. **Copy your Vercel URL**
2. **Go back to Railway**
   - Go to your backend project → Variables
   - Update `CLIENT_URL` with your Vercel URL
   - Example: `CLIENT_URL=https://your-project-name.vercel.app`
3. **Redeploy the backend** (Railway will auto-redeploy when you change variables)

## 🔧 Environment Variables Reference

### Backend (Railway)

```env
NODE_ENV=production
PORT=5000
CLIENT_URL=https://your-frontend-url.vercel.app
```

### Frontend (Vercel)

```env
REACT_APP_SERVER_URL=https://your-backend-url.railway.app
REACT_APP_SOCKET_URL=https://your-backend-url.railway.app
```

## 🛠️ Local Development

1. **Backend Setup**

   ```bash
   cd polling-backend
   npm install
   npm start
   ```

2. **Frontend Setup**

   ```bash
   cd frontend
   npm install
   npm start
   ```

3. **Start Both (from root)**
   ```bash
   npm run dev
   ```

## 🔍 Troubleshooting

### Common Issues

1. **CORS Errors**

   - Ensure `CLIENT_URL` in Railway matches your Vercel URL exactly
   - Check that both URLs use HTTPS

2. **Socket.io Connection Issues**

   - Verify `REACT_APP_SERVER_URL` points to your Railway backend
   - Check browser console for connection errors

3. **Environment Variables Not Loading**
   - Restart your application after adding new environment variables
   - Ensure variable names match exactly (case-sensitive)

### Health Checks

- Backend health check: `GET https://your-backend-url.railway.app/health`
- Frontend: Should load without console errors
- Socket connection: Check browser dev tools console

## 📊 Monitoring

- **Railway**: Check your dashboard for backend logs and metrics
- **Vercel**: Check your dashboard for frontend build logs and analytics
- **Browser**: Check dev tools console for any connection errors

## 🔒 Security Notes

1. **Environment Variables**

   - Never commit `.env` files to version control
   - Use platform-specific secret management (Railway/Vercel)

2. **CORS Configuration**

   - Restrict CORS to your specific Vercel domain
   - Never use wildcard (`*`) origins in production

3. **HTTPS**
   - Both Railway and Vercel provide SSL certificates automatically
   - Always use HTTPS in production

## 🆘 Support

If you encounter issues:

1. Check the Railway and Vercel dashboards for error logs
2. Verify environment variables are set correctly
3. Test the backend health endpoint
4. Check browser console for frontend errors

---

**Total deployment time: ~5-10 minutes** ⚡
