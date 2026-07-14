# AMAS Medical - Frontend

AMAS Medical is a React-based frontend application for an AI Medical Availability System. It allows users to search nearby pharmacies, request medicine availability, chat in real time, manage subscriptions, and interact with pharmacy/admin features.

## 🚀 Features

- User authentication UI
- Search tablets/medicines
- Detect user location using browser geolocation
- View nearby available pharmacies
- Real-time chat using Socket.IO
- Payment success and cancel pages
- Subscription pages
- Pharmacy form
- User request management
- Responsive UI with Tailwind CSS
- Deployed on Vercel

## 🛠️ Tech Stack

- React.js
- Vite
- Tailwind CSS
- Redux Toolkit
- React Router DOM
- Axios
- Socket.IO Client
- Lucide React
- ShadCN UI
- Sonner Toast

## 📁 Project Structure

```bash
frontend/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── Redux/
│   ├── utils/
│   │   ├── constant.js
│   │   └── socketClient.js
│   ├── App.jsx
│   └── main.jsx
├── package.json
├── vite.config.js
├── vercel.json
└── README.md
```

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/atifkhanfall2024/AI-Medical-Avalibility-System-Full-Stack-Frontend.git
```

Go to the frontend folder:

```bash
cd AI-Medical-Avalibility-System-Full-Stack-Frontend
```

Install dependencies:

```bash
npm install
```

If dependency conflict occurs, use:

```bash
npm install --legacy-peer-deps
```

## 🔐 Backend URL

In `src/utils/constant.js`, use:

```js
const Backend_URL = "/api";
export default Backend_URL;
```

This allows the frontend to call backend APIs through Vercel rewrites.

## 🔌 Socket.IO Client Setup

Create or update `src/utils/socketClient.js`:

```js
import { io } from "socket.io-client";

export const SocketClient = () => {
  return io(window.location.origin, {
    path: "/socket.io",
    transports: ["polling"],
    withCredentials: true,
  });
};
```

## 🌐 Vercel Configuration

Create `vercel.json` in the root folder, at the same level as `package.json`:

```json
{
  "rewrites": [
    {
      "source": "/socket.io/:path*",
      "destination": "http://65.0.89.63/socket.io/:path*"
    },
    {
      "source": "/api/:path*",
      "destination": "http://65.0.89.63/api/:path*"
    },
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

Replace the IP with your own backend server IP if needed.

## ▶️ Run Locally

```bash
npm run dev
```

Local frontend URL:

```bash
http://localhost:5173
```

## 🏗️ Build Project

```bash
npm run build
```

Preview build:

```bash
npm run preview
```

## 🚀 Deployment on Vercel

1. Push frontend code to GitHub.
2. Go to Vercel.
3. Click **Add New Project**.
4. Import the frontend repository.
5. Select framework as **Vite**.
6. Use these settings:

```bash
Build Command: npm run build
Output Directory: dist
```

7. Click **Deploy**.

## ✅ Production URL

```bash
https://ai-medical-avalibility-system-full.vercel.app
```

## 📍 Location/GPS Note

Browser geolocation works only on secure origins such as:

```bash
https://your-domain.com
```

Because Vercel provides HTTPS automatically, location fetching works on Vercel production.

## 💬 Chat / WebSocket Note

For production, Socket.IO uses:

```js
transports: ["polling"]
```

This avoids HTTPS-to-HTTP WebSocket issues when the frontend is deployed on Vercel and the backend is running on AWS without HTTPS.

## 📦 Useful Commands

```bash
npm install
npm install --legacy-peer-deps
npm run dev
npm run build
npm run preview
```

## 👨‍💻 Author

Muhammad Atif Khan
