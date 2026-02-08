# Family Task Manager PWA

A Progressive Web App designed for families with children aged 6-12. Parents can manage tasks, calendars, and messages for the whole family, while children have a simplified, kid-friendly interface for their own tasks and activities.

## ✨ Features

### 👨‍👩‍👧‍👦 Family Management
- **Parent-Child Accounts**: Role-based access with different permissions
- **Family Creation**: Parents create families and add child users
- **Multi-Child Support**: Manage multiple children in one family

### ✅ Tasks Module
- **Collapsible Task Creation**: Clean UI with "New Task" button to reduce clutter
- **Task Assignment**: Parents assign to anyone, children assign to themselves only
- **Categories**: Home, School, Chores, Health, Other (with color coding)
- **Due Dates**: Track when tasks need completion
- **Archive System**: Mark tasks complete and view archive history
- **CRUD Operations**: Create, edit, complete, restore, and delete tasks

### 📅 Personal Calendar
- **Individual Calendars**: Each family member has their own calendar
- **Parent Visibility**: Parents can view all family members' calendars
- **Child Privacy**: Children only see their own events
- **Event Management**: Add, edit, delete events with date/time
- **Monthly View**: Navigate through months with prev/next controls

### 💬 Message Board
- **Family Communication**: Shared message board for all family members
- **Real-time Updates**: See messages as they're posted
- **Delete Permissions**: Parents can delete any message, children delete their own
- **Character Limit**: 500 characters per message

### 📱 Progressive Web App (PWA)
- **Installable**: Add to home screen on mobile/desktop
- **Offline Support**: Works without internet connection
- **Service Worker**: Caches app shell for fast loading
- **Responsive Design**: Works on all devices (mobile, tablet, desktop)
- **Push-Ready**: Architecture supports future push notifications

### 🎨 Comic-Style UI (Optional)
- **Kid-Friendly Design**: Playful, colorful interface
- **Large Buttons**: Touch-friendly for children
- **Bold Typography**: Easy-to-read fonts
- **Visual Hierarchy**: Clear separation of sections

## 🛠️ Tech Stack

### Frontend
- **Vanilla JavaScript** (ES6+ modules)
- **CSS3** (CSS Variables, Flexbox, Grid)
- **HTML5** (Semantic markup)

### Backend
- **Firebase Authentication**: User registration and login
- **Cloud Firestore**: Real-time NoSQL database
- **Firebase Hosting Ready**: Deployable to Firebase

### PWA
- **Service Worker**: Cache-first strategy
- **Web App Manifest**: Installable app metadata
- **Offline Detection**: Visual feedback when offline

## 🚀 Getting Started

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Firebase account (free tier works)
- Node.js (optional, for local development server)

### Firebase Setup

1. **Create a Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Click "Add Project"
   - Follow the setup wizard

2. **Enable Authentication**
   - In Firebase Console, go to Authentication
   - Enable "Email/Password" sign-in method

3. **Create Firestore Database**
   - Go to Firestore Database
   - Click "Create Database"
   - Start in **Test Mode** (or Production Mode with rules)

4. **Configure Firebase in Your App**
   - Open `firebase.js`
   - Replace the config object with your Firebase project credentials:
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

5. **Deploy Firestore Security Rules**
   - Copy contents from `FIRESTORE_RULES.txt`
   - Paste into Firestore Rules tab in Firebase Console
   - Click "Publish"

6. **Create Composite Indexes**
   - When you first use tasks/calendar, Firestore will show error links
   - Click the links to auto-create required indexes
   - Required indexes:
     - `tasks`: `(familyId, status, createdAt)`
     - `tasks`: `(familyId, status, assignedUserUid, createdAt)`
     - `events`: `(familyId, userUid, datetime)`

### Local Development

1. **Clone/Download the Project**
   ```bash
   cd familyTaskApp
   ```

2. **Serve with a Local Server**
   
   **Option A: Python**
   ```bash
   python -m http.server 8000
   ```
   
   **Option B: Node.js (http-server)**
   ```bash
   npx http-server -p 8000
   ```
   
   **Option C: VS Code Live Server**
   - Install "Live Server" extension
   - Right-click `index.html` → "Open with Live Server"

3. **Open in Browser**
   ```
   http://localhost:8000
   ```

### First-Time Usage

1. **Register as Parent**
   - Click "Register" tab
   - Enter email and password (min 6 characters)
   - Click "Register"

2. **Create Family**
   - After registration, enter a family name
   - Click "Create Family"

3. **Add Child Users** (optional)
   - Go to "Family Settings" (⚙️ in sidebar)
   - Fill out "Add Child User" form:
     - Child's email
     - Child's password
     - Your password (to confirm)
   - Click "Add Child User"

4. **Start Using the App**
   - Navigate using the sidebar
   - Create tasks, events, and messages!

## 📁 Project Structure

```
familyTaskApp/
├── index.html              # Main HTML structure
├── styles.css              # All CSS styling
├── app.js                  # Main application logic
├── auth.js                 # Authentication module
├── firebase.js             # Firebase configuration
├── manifest.json           # PWA manifest
├── service-worker.js       # Service worker for offline support
├── FIRESTORE_RULES.txt     # Firestore security rules
└── README.md               # This file
```

## 📚 User Roles & Permissions

### 👨 Parent
- ✅ View all family members' tasks and calendars
- ✅ Assign tasks to any family member
- ✅ Create/edit/delete any task
- ✅ Create/edit/delete any calendar event
- ✅ Delete any message
- ✅ Add child users to family
- ✅ Access Family Settings

### 👧 Child
- ✅ View only their own tasks
- ✅ Assign tasks only to themselves
- ✅ Create/edit/delete their own tasks
- ✅ View only their own calendar
- ✅ Create/edit/delete their own events
- ✅ Delete only their own messages
- ❌ Cannot access Family Settings
- ❌ Cannot view other members' personal data

## 🎯 Recent Updates

### Collapsible Create Task Card
**Problem**: Task form was always visible, creating visual clutter for children.

**Solution**: Implemented collapsible task creation:
- "➕ New Task" button shows by default
- Form expands when button clicked
- Auto-focuses on title input
- "Save Task" saves and collapses form
- "Cancel" button clears and collapses form
- Smooth CSS animations for expand/collapse

**Benefits**:
- ✅ Cleaner interface
- ✅ Less overwhelming for children
- ✅ Clear call-to-action
- ✅ Better UX flow

## 🎨 UI/UX Features

- **Responsive Sidebar**: Persistent on desktop, hamburger on mobile
- **Section Navigation**: Click sidebar links to switch views
- **Real-time Updates**: Changes reflect immediately
- **Error Handling**: Clear error messages
- **Loading States**: Visual feedback during operations
- **Touch-Friendly**: Large buttons and inputs for mobile
- **Accessible**: Semantic HTML and ARIA labels

## 🔒 Security

### Firestore Rules
The app uses role-based security rules:
- Users can only access their own family's data
- Children can only read/write their own assignments
- Parents have full access to family data
- All writes require authentication

### Authentication
- Firebase Authentication handles user security
- Passwords hashed by Firebase
- Re-authentication required for sensitive operations (adding children)

## 🚀 Deployment

### Option 1: Firebase Hosting

```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login to Firebase
firebase login

# Initialize Firebase in your project
firebase init hosting

# Deploy
firebase deploy
```

### Option 2: Static Hosting (Netlify, Vercel, etc.)
- Simply upload all files to your hosting provider
- Ensure `firebase.js` has correct production config
- No build step required (vanilla JS)

## 📱 PWA Installation

### Desktop
1. Open the app in Chrome/Edge
2. Look for install icon in address bar
3. Click "Install" prompt
4. App opens in standalone window

### Mobile (Android)
1. Open in Chrome
2. Click "Add to Home Screen" (or use in-app install button)
3. App appears on home screen like native app

### Mobile (iOS)
1. Open in Safari
2. Tap Share button
3. Select "Add to Home Screen"

## 🧪 Testing

### Test Parent Account
1. Register with parent email
2. Create family
3. Add child user
4. Create tasks assigned to different members
5. View child's calendar
6. Post messages and delete any message

### Test Child Account
1. Login with child credentials
2. Try to assign task to someone else (should fail)
3. View calendar (should only see own events)
4. Try to access Family Settings (should be hidden)
5. Try to delete parent's message (should not have delete button)

## 🐛 Known Issues & Limitations

- **Edit Task Dialog**: Currently uses `window.prompt()` (not ideal UX, could be replaced with modal)
- **No Email Verification**: Users can register without email confirmation
- **No Password Reset**: Must be manually added via Firebase Auth
- **Composite Indexes**: Must be created manually in Firebase Console
- **Offline Editing**: Changes made offline don't sync when back online (limitation of current architecture)

## 🔮 Future Enhancements

- [ ] Replace prompt dialogs with proper modals
- [ ] Add task categories with custom colors
- [ ] Implement drag-and-drop for task prioritization
- [ ] Add file attachments to tasks
- [ ] Push notifications for task reminders
- [ ] Weekly/Daily calendar views
- [ ] Family achievements and rewards system
- [ ] Dark mode support
- [ ] Multi-language support
- [ ] Export tasks/events to CSV
- [ ] Recurring tasks and events

## 💡 Tips for Parents

1. **Start Simple**: Add one child at a time
2. **Use Categories**: Color-code tasks by type
3. **Set Due Dates**: Help children understand time management
4. **Check Archive**: Review completed tasks together
5. **Message Board**: Use for positive reinforcement and family updates

## 💡 Tips for Children

1. **Check Tasks Daily**: Look for new assignments
2. **Complete Tasks**: Check them off when done
3. **Use Calendar**: Add homework due dates and activities
4. **Ask Questions**: Use message board to communicate with family

## 🤝 Contributing

This is a personal family project, but feel free to:
- Fork and modify for your own use
- Report bugs via issues
- Suggest features
- Share improvements

## 📄 License

This project is provided as-is for personal and educational use.

## 🙏 Acknowledgments

- Firebase for backend services
- Modern browser APIs for PWA capabilities
- Families everywhere trying to stay organized!

## 📞 Support

For issues or questions:
1. Check Firebase Console for errors
2. Review browser console for JavaScript errors
3. Verify Firestore rules are deployed
4. Ensure indexes are created
5. Check that Firebase config is correct

---

**Built with ❤️ for families who want to stay organized and connected!**

