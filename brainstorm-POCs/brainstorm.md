# Brainstorm

## Dev Environment

- For now creating a desktop app looks pretty complex and requires installing a
  bunch of Windows dependencies, so *pivot* to creating a web app and maybe
  extract later using [Tauri](https://tauri.app/)?
- [Development options &
  overview](https://learn.microsoft.com/en-us/windows/apps/get-started/?tabs=winappsdk-winui%2Crnw)
    - .NET MAUI -
      https://learn.microsoft.com/en-us/dotnet/maui/get-started/installation?view=net-maui-8.0&tabs=vswin
    - Progressive Web Apps? -
      https://learn.microsoft.com/en-us/microsoft-edge/progressive-web-apps-chromium/
- React - https://reactnative.dev/ -
	https://microsoft.github.io/react-native-windows/docs/getting-started
- Electron - [Build cross-platform desktop apps with JavaScript, HTML, and CSS
	| Electron (electronjs.org)](https://www.electronjs.org/) - Cons: memory
	hog and running a chromium instance is highly inefficient

## APIs and Getting Items

- Application that fetches all the game you own from every platform you
	authenticate. Start **one at a time** 
    - Steam
        - Acquiring key: https://steamcommunity.com/dev
        - API: https://developer.valvesoftware.com/wiki/Steam_Web_API#GetUserStatsForGame_.28v0002.29
	- Playstation
        - Seems difficult? No public API and may either need to be part of
          their developer portal to get access to the docs, or may need to use
          a wrapper

    - GoG: https://gogapidocs.readthedocs.io/en/latest/account.html
    - Epic games
    - Humble Bundle
    - IndieGala
    - etc
- Site for getting game information
  [IGDB](https://api-docs.igdb.com/#getting-started)

### Item Storage

- Storing things is tricky... since DBs are shared between people in a web app,
  it seems stupid to build a DB per user. In this case, it would make sense to
  build a DB per platform maybe, or a centralized one, that contains info about
  all games. The problem is storing the images, or maybe just store links to
  the game images and download them on the client side?
    - In this case, the users can have some sort of JSON that points to which
      games they own locally
    - It doesn't make sense to store still images in the DB, but links woould
      risk things getting outdated
        - Might having a script that updates the DB nightly/weekly
  
## UI

- Collects the games in a nice UI - GoG Interface is kiiiinda real nice
- Shows icon next to games or in right sidebar about which platforms the game
  is owned on
    - Maybe store links?
    - Might also be able to overlay the game item, the cover, with the
      platforms that it's being owned on?
    - Create some mockups
- Enables creation of lists/groups/categories - Select items and add them to a
  "current selection" thing - When the user is done, click "create group"
  button - Of course, allow games to exist in multiple lists
- Figure out a game DB you can talk to and fetch some game metadata 
- Figure out how authentication and game fetching works...
- Fetch game tags (co-op, deckbuilder, roguelike, etc.) from somewhere...
- Mobile app?  - Ez with React Native, but I'm not doing that...
- Select a random game (maybe do some animations) - Maybe based on mood/tags
	too?
- Refetch - Next to every authenticated service - "refetch all" button - Fetch
	based on some time interval? Daily/weekly...
- Backend Flask + Python - Make calls to REST API points and let Python do the
	rest - https://flask.palletsprojects.com/en/1.1.x/