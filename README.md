# Cricket Clash – mobile app project

A cricket stat-card game: Stat Battle and Initial Match modes (each player has their own pile; match the initial of the other pile's top card to win both piles), special ability cards, 227 players, choose 20 to 226 cards, play vs CPU or a friend on the same phone.

## What is in this folder
- `www/` – the whole game (index.html), plus manifest, service worker (offline play) and icons.
- `capacitor.config.json`, `package.json` – ready for packaging as a real Android app.

## Option 1 – Easiest: install as a phone app (PWA / APK)
1. Upload the contents of `www/` to any free HTTPS host (GitHub Pages, Netlify, Cloudflare Pages).
2. Open the link on your phone in Chrome, tap the menu, then "Install app" / "Add to Home screen".
3. For a Play Store style APK/AAB, paste your link into https://www.pwabuilder.com and download the Android package.

## Option 2 – Android app with Capacitor
Requires Node.js and Android Studio.
1. `npm install`
2. `npm run android` (adds the Android project, syncs `www/`, and opens Android Studio)
3. In Android Studio press Run, or Build > Generate Signed Bundle/APK.
Change `appId` in `capacitor.config.json` to your own (for example `com.yourname.cricketclash`) before publishing.

iPhone apps need a Mac with Xcode (`npm i @capacitor/ios && npx cap add ios`). The PWA route works on iPhone Safari via Share > Add to Home Screen.

## Test on your computer
`npm run serve` (or open `www/index.html` directly; offline caching only works over https or localhost).

## Editing players
Open `www/index.html` and find `var RAW=`. Each line is:
`Name,COUNTRY,Role,Matches,Runs,Average,StrikeRate,Centuries,Wickets`
Roles: Batter, Opener, Wicketkeeper, All-rounder, Power hitter, Fast bowler, Spinner.
Country codes with colours are defined in `var NAT=`. Add a new code there for a new team.

## Important notes
- **Stats are approximate.** They are rough one-day career figures written from memory, and many associate-nation numbers are estimates. Check them against ESPNcricinfo before you rely on them.
- **Real names:** fine for friends and personal use. If you sell the app or put it on a store, real player names (and any photos) may need licences or permission. Consider fictional names for a commercial release.
- **Online mode** works only in the Claude-hosted version. In the installed app the "Friend, online" option shows a message instead. Adding online play to your own app needs your own server (for example Firebase or a WebSocket server).
- Fonts load from Google Fonts when online; offline, the game falls back to system fonts.
