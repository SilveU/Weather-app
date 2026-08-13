# Atmosphere Weather App

A modern, high-fidelity weather dashboard built with HTML and raw CSS. 

Live Demo: [https://silveu.github.io/Weather-app/](https://silveu.github.io/Weather-app/)

## Current UI Implementation
This project currently focuses on providing a premium UI/UX experience. The interface is fully built and structured:
- **Architecture**: Raw HTML5 & CSS3. No external frameworks or libraries.
- **Layout System**: Advanced 12-column CSS Grid for precise dashboard widget placement.
- **Assets**: 100% inline scalable SVGs mapped to CSS variables (`currentColor`) for dynamic styling.
- **Theming**: A robust CSS custom properties (`:root`) design system ready for theme switching.
- **Components**:
  - Expandable search header.
  - Primary location weather card.
  - 4-grid conditions widget (Humidity, UV, Wind, Visibility).
  - 7-day horizontal forecast view.

## Roadmap (To-Do)
The UI layout is complete, but the app needs logic and dynamic data:
- [ ] **API Integration**: Connect to a live weather provider (e.g., OpenWeatherMap) to fetch real-time data.
- [ ] **Search Logic**: Implement the location search functionality.
- [ ] **Interactive Radar**: Replace the radar placeholder with a working Map API (e.g., Leaflet.js).
- [ ] **Mobile Responsiveness**: Add media queries to stack the grid widgets properly on mobile screens.
- [ ] **State Management**: JavaScript to handle dynamic DOM updates, day switching, and active states.
