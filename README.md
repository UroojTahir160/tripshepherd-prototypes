# TripShepherd - Feed + Map Prototype

A modern, mobile-first web application for discovering and exploring local experiences and events through an interactive map and video feed interface.

## 🌟 Features

### Core Functionality

#### 1. **Interactive Map with Location Clustering**
- **City-based Grouping**: Experiences and events are automatically grouped by city
- **Thumbnail Markers**: Each cluster displays a circular thumbnail image from the first experience
- **Count Badges**: Red notification badges show the number of items in each location
- **Expandable Clusters**: Click a cluster to see a popup list of all experiences in that city
- **Individual Markers**: Click an experience in the popup to expand into individual map markers arranged in a circle pattern

#### 2. **Multiple View Modes**
- **All Tab**: Shows both experiences and events in a traditional card list view with "Happening Today" and "Coming Up" sections
- **Experiences Tab**: Vertical video feed (TikTok/Reels style) showing only experiences
- **Events Tab**: Vertical video feed showing only events
- **Live Now Tab**: Shows live experiences with user avatar markers instead of thumbnails

#### 3. **Vertical Video Feed**
- Full-screen vertical video cards
- Auto-play/pause based on visibility (Intersection Observer)
- Smooth snap scrolling
- Social interaction buttons (like, comment, share, save) with counts
- Rich overlay with:
  - Location chip with icon
  - Host information
  - Experience description
  - Pricing details with "Choose time" button

#### 4. **Mobile-First Design**
- **Default View**: Full-screen map
- **Map/Feed Toggle**: Switch between map-only or feed-only views
- **Responsive Navigation**: Bottom navigation bar with:
  - Home
  - Feed
  - Create (center action button)
  - Search
  - Profile
- **Optimized Touch**: All interactive elements sized for easy tapping

#### 5. **Card-to-Map Synchronization**
- Click any card in the feed → automatically switches to map view
- Map flies to the experience location
- Marker highlights with glow animation
- Summary bar updates with experience details

#### 6. **Live Now Feature**
- Special "Live Now" filter tab with pulsing red dot
- Shows user avatars instead of cluster icons
- Red pulsing border animation on avatars
- "LIVE" badge on each user avatar
- Filter to show only currently live experiences

#### 7. **Smart Map Interactions**
- **Hover Popups**: Hover over markers to see experience title, price, and "View" button
- **Click to Focus**: Click marker to highlight and show details
- **Auto-close Popups**: Click anywhere on map to close cluster popups
- **Zoom Controls**: Custom +/- buttons and "View All" control
- **Smooth Animations**: All transitions use cubic-bezier easing

#### 8. **View All / Show Less**
- "Happening Today" section shows 10 items by default
- "Coming Up" section shows 10 items by default
- Click "View All" to expand and see all items with scrollable list
- Click "Show Less" to collapse back to 10 items
- Automatically hides "View All" if section has ≤10 items

## 🎨 Design System

### Color Palette
```css
--primary: #ccf068        /* Yellow-green accent */
--bg-dark: #000000        /* Pure black background */
--bg-card: #0a0a0a        /* Card background */
--text-white: #ffffff     /* Primary text */
--text-muted: #999999     /* Secondary text */
--text-dim: #666666       /* Tertiary text */
```

### Typography
- **Font Family**: Inter (Google Fonts)
- **Weights**: 400, 500, 600, 700, 800
- **Sizing**: Responsive with mobile-optimized scales

## 📱 Responsive Behavior

### Desktop (>900px)
- Side-by-side layout (420px feed + remaining map)
- Fixed feed header
- Persistent filter tabs
- Larger interactive elements

### Mobile (≤900px)
- **Default**: Full-screen map view
- **Toggle**: Switch between map-only or feed-only
- Feed slides up from bottom
- Optimized padding and spacing
- Touch-friendly button sizes (44px minimum)
- Bottom navigation always visible

## 🗺️ Map Features

### Technology
- **Library**: Leaflet.js 1.9.4
- **Tiles**: CartoDB Dark theme
- **Custom**: No default zoom controls (custom UI)

### Marker Types

#### 1. Cluster Markers (Default)
- Circular thumbnail image (64px)
- Yellow border (4px)
- Count badge (top-right, red)
- City label below
- Hover scale effect

#### 2. Live User Avatars (Live Now mode)
- User profile pictures (50px circular)
- Red border with pulsing animation
- "LIVE" badge at bottom
- Shows actual participants

#### 3. Individual Markers (After expansion)
- Heart emoji (❤️) for experiences
- Star emoji (⭐) for events
- Pulsing glow animation
- Hover popups with details

### Clustering Logic
```javascript
// Groups by city name
groupByLocation(items) {
  const key = item.city.toLowerCase().trim();
  // All "New York" items → single cluster
  // All "Toronto" items → single cluster
  // etc.
}
```

### Expansion Animation
- Markers spread in circular pattern
- Staggered animation (50ms delay each)
- Smooth fly-to with zoom
- Individual markers clickable

## 🎬 Video Feed

### Features
- Full viewport height cards
- Smooth snap scrolling
- Auto-play when 50% visible
- Auto-pause when scrolled away
- Muted by default (tap to unmute)
- Poster image while loading

### Overlay Content
- Location chip (dark blur background)
- Host avatar and name
- Experience description
- Pricing box with:
  - Experience title (yellow)
  - Price per person (white, large)
  - Duration/time
  - "Choose time" button

### Social Actions
- **Like**: Heart icon with count
- **Comment**: Chat bubble with count
- **Share**: Network icon with share count
- **Save**: Bookmark icon with save count
- All with shadow effects for visibility
- Positioned vertically on right side

## 📊 Data Structure

### Experience/Event Object
```javascript
{
  id: "unique-id",
  title: "Experience Name",
  price: 40.02,
  city: "City Name",
  lat: 40.7532084,
  lng: -73.98076569999999,
  video: "https://cdn.../video.mp4",
  thumb: "https://cdn.../thumbnail.jpg",
  type: "exp" | "evt",           // Experience or Event
  status: "today" | "upcoming",  // Timing status
  time: "11:00 AM",
  isLive: true,                  // Optional: if currently live
  liveUsers: [                   // Optional: live participants
    { 
      name: "Sarah M.", 
      avatar: "https://i.pravatar.cc/150?img=1" 
    }
  ]
}
```

## 🔧 Technical Implementation

### Key Technologies
- **HTML5**: Semantic markup
- **CSS3**: Advanced features (backdrop-filter, clip-path, CSS Grid/Flexbox)
- **Vanilla JavaScript**: No frameworks
- **Leaflet.js**: Interactive maps
- **Intersection Observer API**: Video auto-play/pause

### Performance Optimizations
- CSS transitions instead of JavaScript animations
- Lazy video loading with poster images
- Efficient DOM updates
- Event delegation where possible
- Debounced map updates

## 🚀 Getting Started

### Prerequisites
- Modern web browser
- Internet connection (for CDN resources)

### Installation
1. Clone or download the repository
2. Open `index.html` in a web browser
3. No build process required!

### Data Source
The prototype uses embedded data in the `experiences` array. To connect to a real API:

```javascript
// Replace the experiences array with:
async function fetchExperiences() {
  const response = await fetch('YOUR_API_ENDPOINT');
  const data = await response.json();
  return data.experiences;
}
```

## 🎯 User Flows

### Discovering Experiences

#### Flow 1: Map-First Discovery
1. User opens app → sees map with clustered location markers
2. Clicks on a city cluster (e.g., "New York")
3. Popup shows list of experiences in that city
4. Clicks on an experience → markers expand in circle
5. Clicks individual marker → views details

#### Flow 2: Feed-First Discovery
1. User toggles to "Feed" view
2. Scrolls through vertical video feed
3. Sees experience video with overlay details
4. Clicks card → switches to map, highlights location
5. Can explore nearby experiences

#### Flow 3: Live Discovery
1. User clicks "Live Now" tab
2. Map shows user avatars instead of thumbnails
3. Pulsing red borders indicate live activity
4. Click avatar → see live experience details
5. Join or view participants

### Filtering

- **All**: Shows all experiences and events in card list
- **Experiences**: Shows only experiences in video feed
- **Events**: Shows only events in video feed
- **Live Now**: Shows only live experiences with user avatars

### Mobile Gestures
- **Tap cluster**: Open popup
- **Tap outside**: Close popup
- **Swipe up/down**: Scroll through video feed
- **Tap toggle**: Switch map/feed view
- **Tap card**: Navigate to map location

## 📐 Layout Structure

```
Desktop:
┌─────────────────────────────────────────┐
│ Feed (420px)    │    Map (Remaining)    │
│                 │                       │
│ [Brand]         │  [Toggle] [Controls]  │
│ [Filters]       │                       │
│                 │    🗺️ Map Area        │
│ [Cards/Videos]  │                       │
│                 │    [Summary Bar]      │
│                 │                       │
└─────────────────────────────────────────┘
│        Bottom Navigation Bar            │
└─────────────────────────────────────────┘

Mobile:
┌─────────────────┐
│ [Brand]         │
│ [Filters]       │
│ [Map/Feed]      │  ← Toggle buttons
│                 │
│  Full Map       │  ← Default view
│  or             │
│  Full Feed      │  ← Toggle view
│                 │
│ [Summary/Info]  │
└─────────────────┘
│ [Bottom Nav]    │
└─────────────────┘
```

## 🎨 Animation Details

### Map Markers
- **Shine Animation**: 2.5s ease-in-out infinite pulse
- **Expand Animation**: 0.3s scale from 0 with overshoot
- **Hover Scale**: 1.08x with shadow increase

### Video Actions
- **Icon Hover**: 1.1x scale
- **Like Toggle**: Fill animation with color change
- **Smooth Transitions**: 0.2s cubic-bezier

### UI Transitions
- **Feed Expand/Collapse**: 0.3s cubic-bezier(0.4, 0, 0.2, 1)
- **Card Hover**: 0.2s lift with shadow
- **Button Press**: Scale down to 0.95x

### Live Indicators
- **Live Dot**: 2s pulse (opacity + scale)
- **Avatar Border**: 2s pulsing glow with expanding ring

## 🔍 Advanced Features

### Geolocation Integration
```javascript
// Automatically requests user location on load
requestUserLocation()

// Calculate distances
calculateDistance(lat1, lon1, lat2, lon2)

// Get nearby experiences (10km radius)
getNearbyExperiences(userLat, userLng, 10)
```

### Intersection Observer
```javascript
// Auto-play videos when 50% visible
const observer = new IntersectionObserver(callback, {
  threshold: 0.5
});
```

## 📋 File Structure

```
project/
├── index.html          # Main application file (single HTML file)
├── README.md           # This file
└── data.json          # Optional: External data source
```

## 🔄 State Management

### Global State Variables
```javascript
let experiences = [];           // All experiences data
let map = null;                 // Leaflet map instance
let markerMap = {};            // Map of marker IDs to Leaflet markers
let activeTypeFilter = "all";  // Current filter: all/exp/evt/live
let isVideoMode = false;       // Video feed active?
let userLocation = null;       // User's GPS coordinates
const sectionStates = {        // View All expansion states
  today: { expanded: false, limit: 10 },
  upcoming: { expanded: false, limit: 10 }
};
```
## 🐛 Known Limitations

1. **Single File**: All code in one HTML file (good for prototyping, not for production)
2. **Hardcoded Data**: Experiences embedded in JavaScript (should use API)
3. **No Backend**: All client-side (no persistence)
4. **Limited Error Handling**: Assumes all data is valid
5. **Avatar Service**: Using placeholder service (pravatar.cc)

## 🚀 Future Enhancements

### Potential Features
- [ ] Real API integration
- [ ] User authentication
- [ ] Booking flow
- [ ] Search functionality
- [ ] Filter by date/price/category
- [ ] Social features (friends, reviews)
- [ ] Favorites/wishlist
- [ ] Push notifications for live events
- [ ] Advanced search with autocomplete
- [ ] Multi-language support

### Technical Improvements
- [ ] Split into modular files (HTML/CSS/JS)
- [ ] Add build process (webpack/vite)
- [ ] TypeScript for type safety
- [ ] State management (Redux/Zustand)
- [ ] Component framework (React/Vue)
- [ ] Progressive Web App (PWA)
- [ ] Offline support
- [ ] Performance monitoring

### Why Single HTML File?
- **Prototyping Speed**: Quick iterations
- **Easy Sharing**: Single file to send/demo
- **No Build Step**: Open and run immediately
- **Self-contained**: All assets referenced via CDN

### Why Vertical Video Feed?
- **Modern UX**: Familiar TikTok/Reels pattern
- **Engagement**: Full-screen immersive content
- **Mobile-First**: Optimized for phone use
- **Discovery**: Easy swipe through options

### Why City Clustering?
- **Reduced Clutter**: Fewer markers on map
- **Logical Grouping**: By location makes sense
- **Scalability**: Works with hundreds of experiences
- **Better UX**: Clear organization

### Why Glassmorphic Design?
- **Modern**: Current design trend
- **Depth**: Creates visual layers
- **Readability**: Dark blur improves text contrast
- **Premium Feel**: Professional appearance

## 🎓 Learning Resources

### Technologies Used
- [Leaflet.js Documentation](https://leafletjs.com/)
- [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
- [CSS clip-path](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path)
- [Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)

## 👥 Credits

- **Map Tiles**: CartoDB
- **Icons**: Custom SVG icons
- **Fonts**: Inter by Rasmus Andersson (Google Fonts)
- **Avatar Placeholders**: pravatar.cc

---

**Note**: This is a prototype for demonstration purposes. For production use, implement proper error handling, data validation, backend integration, and security measures.

