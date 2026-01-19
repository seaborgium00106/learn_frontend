# Quick Start Guide

Get the Social Network Frontend up and running in 5 minutes!

## ⚡ Quick Setup

### Step 1: Install Dependencies

```bash
cd frontend
npm install
```

### Step 2: Start the Backend

Make sure your Spring Boot backend is running on `http://localhost:9090`

```bash
cd ../backend
mvn spring-boot:run
```

### Step 3: Set User ID (Important!)

Open your browser console (F12) and run:

```javascript
localStorage.setItem('auth-storage', JSON.stringify({ 
  state: { currentUserId: 1, isAuthenticated: true }, 
  version: 0 
}));
```

### Step 4: Start Frontend

```bash
cd frontend
npm run dev
```

Visit: `http://localhost:5173`

## 🎯 First Steps

### 1. Create Some Test Data

You need users and posts in your backend first. Use these curl commands:

```bash
# Create User 1
curl -X POST http://localhost:9090/api/v1/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Alice", "email": "alice@example.com"}'

# Create User 2
curl -X POST http://localhost:9090/api/v1/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Bob", "email": "bob@example.com"}'

# Create User 3
curl -X POST http://localhost:9090/api/v1/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Charlie", "email": "charlie@example.com"}'

# Add friendships (User 1 friends with User 2 and 3)
curl -X POST http://localhost:9090/api/v1/friendships \
  -H "Content-Type: application/json" \
  -d '{"userId": 1, "friendId": 2}'

curl -X POST http://localhost:9090/api/v1/friendships \
  -H "Content-Type: application/json" \
  -d '{"userId": 1, "friendId": 3}'

# Create posts by User 2
curl -X POST http://localhost:9090/api/v1/posts \
  -H "Content-Type: application/json" \
  -d '{"content": "Hello from Bob!", "authorId": 2}'

# Create posts by User 3
curl -X POST http://localhost:9090/api/v1/posts \
  -H "Content-Type: application/json" \
  -d '{"content": "Charlie here! Having a great day.", "authorId": 3}'
```

### 2. Navigate the App

Now you can:
- 📝 **Create posts** on the home page
- 👀 **View your timeline** (posts from friends Bob and Charlie)
- 👥 **Manage friends** - Go to Friends page
- 🔍 **Search users** - Go to Search page
- 👤 **View profiles** - Click on user names

### 3. Switch Users

To login as a different user:

```javascript
// In browser console
localStorage.setItem('auth-storage', JSON.stringify({ 
  state: { currentUserId: 2, isAuthenticated: true }, 
  version: 0 
}));
// Refresh the page
```

## 🎨 Features to Try

### Timeline
- ✅ View posts from friends
- ✅ Paginate through posts
- ✅ See who posted via which friend

### Posts
- ✅ Create new posts
- ✅ Delete your own posts
- ✅ View posts on user profiles

### Friends
- ✅ View your friends list
- ✅ Remove friends
- ✅ Add new friends from search
- ✅ Check friendship status on profiles

### User Profiles
- ✅ View user information
- ✅ See all posts by a user
- ✅ Add/remove as friend
- ✅ Navigate between profiles

## 🐛 Troubleshooting

### Problem: "Network Error"

**Solution:** Backend is not running
```bash
cd backend
mvn spring-boot:run
```

### Problem: "Please log in" message

**Solution:** Set user ID in localStorage (see Step 3)

### Problem: Empty timeline

**Solution:** 
1. Create friendships for your user
2. Make sure friends have posts
3. Refresh the page

### Problem: Blank page

**Solution:**
1. Check browser console for errors (F12)
2. Make sure all dependencies are installed: `npm install`
3. Try clearing cache: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)

## 📱 Pages Overview

| Page | URL | Purpose |
|------|-----|---------|
| Home / Timeline | `/` | View posts from friends, create posts |
| Friends List | `/friends` | View and manage your friends |
| Search Users | `/search` | Find and add new friends |
| User Profile | `/profile/:userId` | View user info and posts |

## 🔄 Common Tasks

### Log out and log in as different user

```javascript
// Logout
localStorage.clear();

// Login as user 2
localStorage.setItem('auth-storage', JSON.stringify({ 
  state: { currentUserId: 2, isAuthenticated: true }, 
  version: 0 
}));
```

### Clear all local data

```javascript
localStorage.clear();
sessionStorage.clear();
```

### Check current user

```javascript
JSON.parse(localStorage.getItem('auth-storage'))
```

## 🎓 Next Steps

1. ✅ Read the full `README.md` for detailed documentation
2. ✅ Check `DEVELOPMENT.md` for architecture and patterns
3. ✅ Explore the codebase in `src/` directory
4. ✅ Customize the theme in `src/styles/theme.ts`
5. ✅ Add new features following the existing patterns

## 📞 Need Help?

- Check browser console for errors (F12)
- Verify backend is running on port 8080
- Ensure you've set user ID in localStorage
- Check `README.md` for more details

---

Happy coding! 🚀
