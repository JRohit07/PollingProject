# 🚀 Quick Start - Vercel + Railway Deployment

## TL;DR - Fastest Deployment (5 minutes)

### 1. Backend (Railway)

1. Go to [railway.app](https://railway.app) → Sign up with GitHub
2. "New Project" → "Deploy from GitHub repo" → Select your repo
3. Set root directory to `polling-backend`
4. Add environment variables:
   - `NODE_ENV=production`
   - `PORT=5000`
   - `CLIENT_URL=https://your-frontend-url.vercel.app` (update after frontend deploy)

### 2. Frontend (Vercel)

1. Go to [vercel.com](https://vercel.com) → Sign up with GitHub
2. "New Project" → Import from GitHub → Select your repo
3. Set root directory to `frontend`
4. Add environment variables:
   - `REACT_APP_SERVER_URL=https://your-backend-url.railway.app`
   - `REACT_APP_SOCKET_URL=https://your-backend-url.railway.app`

### 3. Update CORS

1. Copy your Vercel URL
2. Go back to Railway → Update `CLIENT_URL` with your Vercel URL
3. Railway will auto-redeploy

## 🛠️ Local Development

```bash
# Install dependencies
npm run install:all

# Start both frontend and backend
npm run dev

# Or start individually
npm run start:backend  # Backend on :5000
npm run start:frontend # Frontend on :3000
```

## 🔧 Environment Variables

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

## 🆘 Need Help?

1. Check `DEPLOYMENT.md` for detailed instructions
2. Run `./deploy.sh` for step-by-step guide
3. Verify environment variables are set correctly
4. Check CORS configuration matches your URLs

## ✅ Health Checks

- Backend: `https://your-backend-url.railway.app/health`
- Frontend: Should load without console errors
- Socket connection: Check browser dev tools

---

**Total deployment time: ~5-10 minutes** ⚡
