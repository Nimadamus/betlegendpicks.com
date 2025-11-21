# BetLegend Picks Tracker

A live sports betting picks tracker that automatically displays your picks from Google Sheets on your website.

## Features

- Real-time data sync from Google Sheets
- Separate tabs for each sport (NFL, NHL, NBA, NCAAF, NCAAB)
- Live statistics dashboard showing:
  - Total picks
  - Wins and losses
  - Total units won/lost
- Auto-refresh every 60 seconds
- Mobile responsive design
- Color-coded results (green for wins, red for losses)

## Setup Instructions

### 1. Make Your Google Sheet Public

For the website to display your picks, you need to share your Google Sheet publicly:

1. Open your Google Sheet: https://docs.google.com/spreadsheets/d/1izhxwiiazn99SRqcK8QpUE4pfvDRIFpgSyw5ZlMsvmY/edit
2. Click the "Share" button in the top right corner
3. Under "General access", click "Restricted"
4. Change it to "Anyone with the link"
5. Make sure the permission is set to "Viewer"
6. Click "Done"

### 2. Google Sheet Structure

Your Google Sheet should have the following columns (in order):

| Column | Description |
|--------|-------------|
| A | Date (e.g., 11/20/2025) |
| B | Pick (e.g., "Lakers +9.5") |
| C | Units (e.g., -135, +110) |
| D | Confidence (e.g., 1, 2, 3) |
| E | League (e.g., NFL, NHL, NBA, NCAAF, NCAAB) |
| F | Sport (e.g., Football, Basketball, Hockey) |
| G | Status (e.g., POSTED, GRADED) |
| H | Result (e.g., "Posted successfully", "Win", "Loss") |
| I | Win (optional) |
| J | Loss (optional) |
| K | Notes (optional) |

### 3. Using Multiple Sheets

The website supports multiple sheets for different sports:
- Sheet1 (main sheet with all picks)
- NFL
- NHL
- NBA
- NCAAF
- NCAAB
- To Be Graded

The website filters picks based on the "League" column (Column E), so make sure each pick has the correct league assigned.

### 4. How It Works

1. When you add or grade picks in your Google Sheet
2. The website automatically fetches the latest data
3. Picks appear on betlegendpicks.com within 60 seconds (or click the refresh button)
4. Users can filter by sport using the tabs
5. Statistics update automatically

### 5. Grading Picks

When you grade a pick:
1. Update the "Status" column to "GRADED"
2. Update the "Result" column with the outcome
3. The units will automatically show as positive (win) or negative (loss)
4. The website will display the graded pick with color coding

## Deployment

This site is hosted on GitHub Pages. Any changes pushed to the repository will automatically be deployed.

To deploy updates:
```bash
git add .
git commit -m "Update website"
git push origin main
```

## Troubleshooting

### Picks Not Showing

1. Make sure your Google Sheet is shared publicly (see Setup Instructions #1)
2. Check that the Sheet ID in index.html matches your sheet
3. Verify your sheet has the correct column structure
4. Check browser console for errors (F12 → Console tab)

### Data Not Updating

- Click the refresh button to manually update
- Check if your Google Sheet is still shared publicly
- Clear your browser cache and reload the page

## Technical Details

- Built with vanilla JavaScript (no dependencies)
- Uses Google Sheets CSV export for data fetching
- Auto-refreshes every 60 seconds
- Fully responsive design
- Works on all modern browsers

## Support

If you encounter issues, check:
1. Google Sheet sharing settings
2. Column structure matches the expected format
3. Browser console for error messages
