# ICT Indicators - TradingView Pine Script Repository

**Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

This repository contains Pine Script indicators for TradingView based on Inner Circle Trader (ICT) concepts. Pine Script is a domain-specific language that runs exclusively on the TradingView platform - it cannot be compiled or executed locally.

## Working Effectively

### Repository Structure
```
/home/runner/work/ict-indicators/ict-indicators/
├── .git/
├── .gitignore
├── first-presentation-fvg.pine    # ICT First Presentation FVG indicator (680 lines, v6)
├── library.pine                   # ICT Helper utility library (258 lines, v5)  
├── luxalgo-smc-ict-mod.pine      # Smart Money Concepts indicator (1110 lines, v5)
├── opening-range-projections.pine # ICT Opening Range Projections (515 lines, v6)
└── orp/                          # Screenshots and documentation images
    ├── all.png
    ├── opening_price.png
    ├── projections.png
    ├── quadrants.png
    ├── range_highlow.png
    ├── range_swing_highlow.png
    └── sessions.png
```

### Environment Setup
- **No local compilation required** - Pine Script only compiles on TradingView
- **No build tools needed** - These are text files edited with any text editor
- **No package management** - Dependencies are handled through TradingView's import system

### File Relationships and Dependencies
- `library.pine` is a utility library (`library("ICTHelper")`) that can be published to TradingView
- `first-presentation-fvg.pine` imports external library: `import tristanlee85/helpers/1 as helpers`
- All other files are standalone indicators with no local dependencies

## Development Workflow

### 1. Local Development
- Edit `.pine` files directly with any text editor
- **No local syntax validation possible** - Pine Script can only be validated on TradingView
- Use git for version control of source files

### 2. Basic Syntax Validation (Local)
Run these commands to perform basic structure validation:

```bash
# Check Pine Script versions and types
grep -n "//@version" *.pine
grep -n "indicator\|strategy\|library" *.pine

# Verify file encoding is correct
file *.pine

# Count lines in each file
wc -l *.pine
```

**Expected output:**
- All files should show "UTF-8 text" or "ASCII text"  
- Each file should have exactly one `@version` declaration
- Each file should have exactly one `indicator(`, `strategy(`, or `library(` declaration

### 3. Testing and Validation on TradingView

**CRITICAL: All functional testing must be done on TradingView - there is no local execution environment.**

#### Upload and Test Process:
1. **Copy script content** from local `.pine` file
2. **Open TradingView Pine Editor** (requires TradingView account)
3. **Paste code** into Pine Editor
4. **Click "Add to Chart"** - this compiles and validates syntax
5. **If compilation fails:** Fix syntax errors in local file and repeat
6. **If compilation succeeds:** Test functionality on charts

#### Manual Validation Scenarios:
After successfully compiling a script, **ALWAYS** test these scenarios:

**For Indicators (first-presentation-fvg.pine, luxalgo-smc-ict-mod.pine, opening-range-projections.pine):**
- Apply indicator to a chart with liquid market data (e.g., EURUSD, SPY)
- Test on multiple timeframes: 1m, 5m, 15m, 1h, 4h, 1D
- Verify indicator draws expected visual elements (boxes, lines, labels)
- Test different parameter configurations through indicator settings
- Check indicator performance on charts with 1000+ bars of data

**For Libraries (library.pine):**
- Create a test indicator that imports library functions
- Verify all exported functions work as expected
- Test enum types and style utilities

#### Performance Validation:
- **Charts should load within 5-10 seconds** after applying indicator
- **No script timeout errors** should occur during calculation
- **Visual elements should render smoothly** when scrolling chart

## Common Development Tasks

### Adding New Indicators
1. Create new `.pine` file following naming convention: `descriptive-name.pine`
2. Use appropriate Pine Script version (`//@version=6` for new indicators)
3. Start with `indicator()` declaration for overlay indicators
4. Import necessary libraries: `import tristanlee85/helpers/1 as helpers`
5. Test compilation and functionality on TradingView before committing

### Modifying Existing Indicators  
1. **Always backup original** before making changes
2. **Test changes incrementally** - upload frequently to TradingView for validation
3. **Verify backward compatibility** - ensure existing chart setups still work
4. **Update version comments** if making significant changes

### Library Development (library.pine)
1. Use `library("LibraryName")` declaration
2. Export functions with `export` keyword
3. Document all exported functions with `@function` comments
4. **Publish to TradingView** to make available for import in other scripts
5. **Update import statements** in dependent scripts after publishing new library version

### Documentation Updates
1. **Capture screenshots** of indicator behavior and save in `orp/` directory
2. Use PNG format for images: `descriptive-name.png`
3. **Update indicator descriptions** in Pine Script comments for TradingView publication
4. **Document parameter changes** in commit messages

## Time Expectations

- **Local file editing:** Immediate (no compilation)
- **TradingView upload/compilation:** 5-30 seconds per script
- **Manual testing per indicator:** 5-15 minutes depending on complexity
- **Screenshot documentation:** 2-5 minutes per image
- **Full validation cycle:** 15-45 minutes per modified script

## Validation Requirements

### Before Committing Changes:
1. **Verify syntax** - Script must compile successfully on TradingView
2. **Test core functionality** - Run through complete user scenarios
3. **Performance check** - Ensure no timeouts or rendering issues
4. **Cross-timeframe testing** - Verify behavior on different chart timeframes
5. **Parameter validation** - Test different input configurations

### Git Best Practices:
```bash
# Check status and diff before committing
git status
git diff

# Add only Pine Script files and documentation
git add *.pine orp/*.png

# Commit with descriptive message
git commit -m "Add [feature] to [indicator-name] - tested on TradingView"

# Push changes
git push
```

## Troubleshooting

### Common Pine Script Issues:
- **Compilation errors:** Can only be diagnosed on TradingView Pine Editor
- **Runtime errors:** Usually related to data access or calculation limits
- **Performance issues:** May require optimization for large datasets or complex calculations

### When TradingView Access is Limited:
- **Focus on code structure** and style improvements
- **Perform text-based validation** using grep and syntax analysis
- **Document changes thoroughly** for later testing
- **Avoid major functional changes** without ability to test

### Import/Library Issues:
- **External imports** (like `tristanlee85/helpers/1`) require TradingView account access
- **Local library.pine** must be published to TradingView before it can be imported
- **Version mismatches** between Pine Script versions can cause import failures

## File Reference

### Current Repository Files:

#### first-presentation-fvg.pine
- **Type:** Indicator (overlay)
- **Version:** Pine Script v6  
- **Dependencies:** `import tristanlee85/helpers/1 as helpers`
- **Purpose:** Identifies and highlights first fair value gaps after session starts
- **Lines:** 680

#### library.pine  
- **Type:** Library
- **Version:** Pine Script v5
- **Dependencies:** None
- **Purpose:** Utility functions for ICT concepts (enums, detection functions, style utilities)
- **Lines:** 258

#### luxalgo-smc-ict-mod.pine
- **Type:** Indicator (overlay)
- **Version:** Pine Script v5
- **Dependencies:** None  
- **Purpose:** Modified Smart Money Concepts indicator with ICT enhancements
- **Lines:** 1110

#### opening-range-projections.pine
- **Type:** Indicator (overlay)  
- **Version:** Pine Script v6
- **Dependencies:** None
- **Purpose:** Projects opening range levels and targets
- **Lines:** 515

## Quick Reference Commands

```bash
# Repository overview
ls -la
find . -name "*.pine" | wc -l

# Check all Pine Script versions
grep -h "//@version" *.pine

# Find all indicators vs libraries
grep -l "^indicator(" *.pine
grep -l "^library(" *.pine

# Check for dependencies
grep -n "import " *.pine

# View file statistics
wc -l *.pine

# Check file encoding
file *.pine
```

**Remember: This is a Pine Script repository. All compilation, testing, and runtime validation must be performed on the TradingView platform. Local development is limited to text editing and basic syntax analysis.**