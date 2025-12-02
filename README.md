# TripShepherd - Feed + Map Prototype

A mobile-first web app for discovering local experiences and events through an interactive map and TikTok-style video feed.

# LIVE DEMO
Link: https://mapbasedfeedprtotype.netlify.app/

## ✨ Features

### 🗺️ **Interactive Map**
City-based clustering with thumbnail markers and count badges. Click clusters to view lists, expand into individual markers arranged in circular patterns.

### 🎬 **Vertical Video Feed**
TikTok-style full-screen videos with auto-play/pause based on visibility. Includes social buttons (like, comment, share, save) and rich overlay with location, host, pricing, and booking CTA.

### 📱 **4 View Modes**
- **All Tab**: Card list with "Happening Today" and "Coming Up" sections
- **Experiences/Events**: Vertical video feeds with filtering
- **Live Now**: Real-time experiences with user avatars and pulsing effects

### 🔄 **Smart Synchronization**
Bidirectional sync between map and feed. Click any card to fly to location on map with highlighted marker, or click marker to highlight and scroll to corresponding card.

### 🔴 **Live Now Feature**
Special filter showing live experiences with user avatars instead of thumbnails. Features red pulsing borders, "LIVE" badges, and shows actual participants.

### 📍 **Geolocation Support**
Automatically requests user location to show nearby experiences. Uses Haversine formula to calculate distances within customizable radius (default 10km).

### 🎨 **Glassmorphic Dark Theme**
Modern dark UI (`#000`) with yellow-green accents (`#ccf068`). Features blur effects, smooth transitions, and premium feel throughout the interface.

### 📲 **Mobile-First Design**
Default full-screen map with toggle to switch between map/feed views. Bottom navigation, touch-optimized controls, and responsive layout for all screen sizes.

## 🚀 Quick Start

1. Open `index.html` in a modern browser
2. No installation needed - all dependencies loaded via CDN
3. Click clusters on map or scroll through video feed to explore

## 🔧 Tech Stack

- **HTML5 + CSS3** - Semantic markup with advanced features (backdrop-filter, clip-path, Grid/Flexbox)
- **Vanilla JavaScript** - No frameworks, efficient DOM manipulation, ~3700 lines
- **Leaflet.js 1.9.4** - Interactive maps with CartoDB Dark tiles
- **Intersection Observer API** - Efficient video auto-play at 50% visibility threshold

## 📱 Layout

- **Desktop (>900px)**: Side-by-side layout - Feed (420px) + Map (remaining space)
- **Mobile (≤900px)**: Full-screen map by default, toggle to switch to full-screen feed view

## 📊 Data Structure

```javascript
{
  id: "unique-id",
  title: "Experience Name",
  price: 40.02,
  city: "City Name",
  lat: 40.7532084,
  lng: -73.9807657,
  video: "https://cdn.../video.mp4",
  thumb: "https://cdn.../thumbnail.jpg",
  type: "exp" | "evt",
  status: "today" | "upcoming",
  time: "11:00 AM",
  isLive: true,              // Optional
  liveUsers: [{name, avatar}] // Optional
}
```

## 🚀 Future Improvements

### Code Quality & Architecture
- **Modularization**: Split single HTML file into separate HTML, CSS, and JavaScript modules for better maintainability
- **TypeScript**: Add type safety to prevent runtime errors and improve developer experience
- **State Management**: Implement Redux/Zustand for predictable state updates and easier debugging
- **Component Framework**: Migrate to React/Vue for reusable components and better performance
- **Build Process**: Add webpack/vite for bundling, minification, and optimization

### Features & Functionality
- **Real API Integration**: Replace hardcoded data with backend API calls and proper error handling
- **User Authentication**: Add login/signup with JWT tokens, user profiles, and personalized recommendations
- **Advanced Search**: Implement fuzzy search with autocomplete, filters by date/price/category/rating
- **Booking System**: Full booking flow with calendar, time slots, payment integration, and confirmations
- **Social Features**: Add friends, reviews, ratings, comments, and activity feed
- **Favorites/Wishlist**: Save experiences, create collections, and share with friends
- **Push Notifications**: Real-time alerts for live events, bookings, and friend activity
- **Multi-language**: i18n support for multiple languages and currencies
- **Accessibility**: ARIA labels, keyboard navigation, screen reader support, high contrast mode

### Performance & Optimization
- **Code Splitting**: Lazy load routes and components for faster initial load
- **Image Optimization**: WebP format, responsive images, lazy loading, CDN integration
- **Caching Strategy**: Service workers for offline support and faster repeat visits
- **Progressive Web App**: PWA with install prompt, offline mode, and app-like experience
- **Performance Monitoring**: Add analytics, error tracking (Sentry), and performance metrics

### Map Enhancements
- **Advanced Clustering**: Better clustering algorithm with zoom-level awareness and custom thresholds
- **Heat Maps**: Show density of experiences in different areas
- **Custom Map Styles**: Multiple map themes (dark, light, satellite) with user preference
- **Directions**: Integrate navigation to experience locations
- **Radius Filters**: Draw custom radius on map to filter experiences by distance

### Video Feed Improvements
- **Video Analytics**: Track views, completion rate, engagement metrics
- **Video Quality Selection**: Auto/manual quality selection based on bandwidth
- **Comments & Replies**: Threaded comments on videos with real-time updates
- **Share to Social**: Direct sharing to Instagram, TikTok, Facebook, Twitter
- **Video Upload**: Allow hosts to upload and manage their experience videos

### Testing & Quality
- **Unit Tests**: Jest/Vitest for component and utility testing
- **Integration Tests**: Cypress/Playwright for end-to-end user flows
- **Performance Tests**: Lighthouse CI for automated performance checks
- **Cross-browser Testing**: Ensure compatibility across all major browsers

### Backend Requirements
- **Database**: PostgreSQL for relational data, Redis for caching
- **File Storage**: S3/CloudFront for videos and images
- **Real-time**: WebSockets for live features and notifications
- **Security**: Input validation, XSS protection, rate limiting, HTTPS

## 🐛 Current Limitations

- Single HTML file (3700+ lines) - difficult to maintain and scale
- Hardcoded experience data - no dynamic content updates
- No backend or database - all data stored in memory
- No user authentication - can't save preferences or bookings
- Placeholder avatars (pravatar.cc) - not production-ready
- Limited error handling - assumes all data is valid
- No offline support - requires internet connection
- Browser-only geolocation - less accurate than native apps

## 👥 Credits

**Map Tiles**: CartoDB  
**Font**: Inter (Google Fonts)  
**Icons**: Custom SVG  
**Avatars**: pravatar.cc (placeholder)

---

**Note**: This is a prototype for demonstration purposes. For production use, implement proper backend, authentication, error handling, testing, and security measures.
