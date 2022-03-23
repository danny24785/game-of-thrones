Changelog
---------

22-03-2022 - Verion 0.0.1:
- Added Changelog 
- Feed added
- Installed vue-axios

22-03-2022 - Verion 0.0.2:
- Commented out feed

22-03-2022 - Verion 0.0.3:
- Only name, gender and/or IsAlive when the record isn't empty
- Wrap character details ul in li of an ordered list, so the list of characters is numbered
- Styling to add some whitespace between characters 

22-03-2022 - Verion 0.0.4:
- Fixed IsAlive bullet, now shows yes if no data, shows no if there is data
- Added location and date of death in parentheses if IsAlive = no
- Added Gender and IsAlive dropdown placeholders for filters

22-03-2022 - Verion 0.0.5:
- Generate options in filter dropdowns from data

22-03-2022 - Verion 0.0.6:
- Added placeholder for reset button

22-03-2022 - Verion 0.0.7:
- Removed unnecessary plugin vue-axios
- Moved the feed to it's own component Feed.vue

22-03-2022 - Verion 0.0.8:
- Changed HelloWorld to Apptitle

22-03-2022 - Verion 0.0.9:
- removed dependence of axios plugin

23-03-2022 - Verion 0.1.0:
- Devided link url up in different parts to make calculations with pages and maxpage possible in the future



# game-of-thrones

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
