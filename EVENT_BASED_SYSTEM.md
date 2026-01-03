# Event-Based Image Display System

## Overview
The Petal Dome website now features an **automatic event-based image display system** that dynamically shows relevant images in the hero section based on upcoming events and holidays.

## How It Works

### Automatic Image Switching
The system automatically displays images based on:
1. **Current Date** - Calculates which event is coming up next
2. **Event Proximity** - Shows event images within a configurable window (e.g., 21 days before Valentine's Day)
3. **Smart Fallback** - If no specific event is upcoming, shows generic occasion images

### Current Events Configuration

| Event | Date | Image | Display Window |
|-------|------|-------|----------------|
| **Valentine's Day** | Feb 14 | `Valentine Day.jpeg` | 21 days before |
| **Easter** | ~April 20 | `Happy Birthday.png` (temp) | 14 days before |
| **Mother's Day** | ~May 11 | `Gallery1.jpg` | 14 days before |
| **Thanksgiving** | ~Nov 28 | `ThanksGiving.jpeg` | 21 days before |
| **Christmas** | Dec 25 | `MerryChristmas.jpg` | 30 days before |
| **New Year** | Jan 1 | `welcome-2026.jpeg` | 14 days before |
| **Generic Events** | Always available | Various | Year-round |

### Example Timeline for Valentine's Day 2026
- **Jan 3 - Jan 23**: Shows generic/other event images
- **Jan 24 - Feb 14**: Automatically shows Valentine's Day image
- **Feb 15+**: Switches to next upcoming event

## Technical Implementation

### Location
The system is implemented in [index.html](index.html) lines 494-660 using vanilla JavaScript.

### Key Features
- **Zero Dependencies**: Pure JavaScript, no external libraries needed
- **Automatic Updates**: Checks and updates daily if page remains open
- **Error Handling**: Falls back to Thanksgiving image if event image fails to load
- **Debug Console**: Logs which event is currently displayed (check browser console)
- **Performance**: Runs once on page load, minimal performance impact

### Code Structure
```javascript
const events = [
    {
        name: "Valentine's Day",
        month: 2,           // February (1-12)
        day: 14,
        image: "images/Valentine Day.jpeg",
        message: "Celebrate love with romantic petal dome arrangements",
        daysBefore: 21      // Show 3 weeks before event
    },
    // ... more events
];
```

## How to Add New Events

1. **Open** [index.html](index.html)
2. **Find** the `events` array (around line 498)
3. **Add** a new event object:

```javascript
{
    name: "Father's Day",
    month: 6,           // June
    day: 21,
    image: "images/FathersDay.jpeg",
    message: "Honor Dad with elegant petal dome gifts",
    daysBefore: 14      // Start showing 2 weeks before
}
```

4. **Upload** the corresponding image to `images/` folder
5. **Save** and refresh the website

## How to Modify Event Display Windows

To change when an event starts showing:
1. **Find** the event in the `events` array
2. **Change** the `daysBefore` value:
   - `7` = 1 week before
   - `14` = 2 weeks before
   - `21` = 3 weeks before
   - `30` = 1 month before

## Image Optimization Status

| Image | Size | Status |
|-------|------|--------|
| `Valentine Day.jpeg` | 61KB | ✅ Optimized |
| `welcome-2026.jpeg` | 51KB | ✅ Optimized |
| `MerryChristmas.jpg` | 156KB | ✅ Good |
| `ThanksGiving.jpeg` | 521KB | ✅ Good |
| `Happy Birthday.png` | 2.7MB | ⚠️ Could be optimized |

### Recommendation
Consider optimizing `Happy Birthday.png` by:
- Converting to JPEG format
- Compressing to ~200KB or less
- Using tools like TinyPNG or ImageOptim

## Testing the System

### Check Current Display
1. Open [index.html](index.html) in a browser
2. Open browser console (F12)
3. Look for: `Displaying: [Event Name]`

### Test Specific Dates
Temporarily modify line 575 to test different dates:
```javascript
// Original
const today = new Date();

// Test Valentine's Day display (set to Jan 24)
const today = new Date(2026, 0, 24);  // Month is 0-indexed
```

## Benefits

### For Business
- **Timely Marketing**: Automatically promotes relevant occasions
- **Increased Sales**: Customers see products relevant to upcoming events
- **Reduced Maintenance**: No manual image updates needed
- **Professional Appeal**: Website always shows current/upcoming events

### For Customers
- **Relevant Content**: See products for upcoming celebrations
- **Inspiring Ideas**: Get reminded of upcoming gift-giving occasions
- **Better Experience**: Fresh, timely content on every visit

## Maintenance

### Regular Updates
- **Quarterly**: Review event dates (especially Easter which varies)
- **Annually**: Update New Year image with correct year
- **As Needed**: Add new occasions based on customer demand

### Monitoring
Check browser console on live site to verify:
- Correct event is displaying
- No image loading errors
- System is functioning properly

## Future Enhancements

### Potential Additions
1. **Multiple Images Per Event**: Rotate through several Valentine's images
2. **Regional Events**: Different events for different locations
3. **A/B Testing**: Track which event images drive more orders
4. **Admin Panel**: Easy GUI to add/edit events without code changes
5. **Analytics Integration**: Track which events get most engagement

## Support

### Common Issues

**Q: Wrong image is showing**
- Check the date calculation in browser console
- Verify event dates are correct in the events array
- Ensure `daysBefore` values are appropriate

**Q: Image not loading**
- Check image path is correct
- Verify image file exists in `images/` folder
- Check browser console for errors
- System will fallback to Thanksgiving image

**Q: Want to force a specific image**
- Comment out the automatic system
- Set image manually in HTML (line 487)

## Files Modified

- ✅ [index.html](index.html) - Added event-based display system
- ✅ [EVENT_BASED_SYSTEM.md](EVENT_BASED_SYSTEM.md) - This documentation

## Changelog

### January 3, 2026
- ✅ Implemented automatic event-based image display system
- ✅ Added Valentine's Day image to repository
- ✅ Created 9 event configurations (Valentine's, Christmas, New Year, etc.)
- ✅ Added smart fallback system for generic events
- ✅ Implemented error handling for missing images
- ✅ Added documentation

---

**Ready to Go**: The system is live and will automatically show Valentine's Day content starting January 24, 2026!
