# ICT Indicators

A collection of TradingView Pine Script indicators based on Inner Circle Trader (ICT) concepts.

## Performance Optimization

This repository has been optimized for performance with caching headers for static assets:

### Implemented Optimizations

1. **HTML Meta Cache Control**: Added `<meta http-equiv="Cache-Control" content="max-age=31536000">` for 1-year caching
2. **Server-Level Caching**: Configured `.htaccess` with appropriate cache headers for different file types
3. **Image Optimization**: All PNG documentation images use lazy loading and optimal caching
4. **GitHub Pages Ready**: Configured with `_config.yml` for optimal hosting

### Cache Configuration

- **Images (PNG, JPG, etc.)**: Cached for 1 year (31,536,000 seconds)
- **CSS/JS files**: Cached for 1 year
- **HTML files**: Cached for 1 hour for content updates

### Static Assets

The following static assets are optimized with caching headers:

- `orp/all.png` (305KB) - Complete indicator overview
- `orp/opening_price.png` (231KB) - Opening price levels
- `orp/projections.png` (252KB) - Price projections
- `orp/quadrants.png` (210KB) - Quadrant analysis
- `orp/range_highlow.png` (93KB) - Range high/low
- `orp/range_swing_highlow.png` (91KB) - Swing ranges
- `orp/sessions.png` (83KB) - Session analysis

## Indicators Available

### 1. Opening Range Projections (ORP)
- Multiple session support (Midnight, NY AM, NY PM)
- User-defined session times
- Range high/low projections
- Quadrant levels

### 2. First Presentation FVG
- Fair Value Gap identification
- Session-based resets
- Multiple timeframe support

### 3. LuxAlgo SMC ICT Modified
- Smart Money Concepts integration
- ICT methodology implementation

### 4. ICT Helper Library
- Utility functions for ICT concepts
- Reusable components for indicator development

## Usage

1. Copy the Pine Script code from the `.pine` files
2. Import into TradingView
3. Configure parameters as needed
4. View documentation at the hosted page for visual examples

## Performance Benefits

With the implemented caching headers:
- **Faster loading**: Static assets cached locally for 1 year
- **Reduced bandwidth**: Repeat visits don't re-download images
- **Better user experience**: Near-instant loading of documentation images
- **SEO optimized**: Proper meta tags and performance optimization

## License

Mozilla Public License 2.0