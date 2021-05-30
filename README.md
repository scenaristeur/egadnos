# egadnos

--
- vue create egadnos
- (npm rune serve -> npm run dev)
- vue-config.js / src/registerSErviceWorker
- npm run build
- git add dist -f && git commit -m "Initial dist subtree commit"

- git add . && git commit -m "ajout de dist"
- git push --set-upstream origin main
- git subtree push --prefix dist origin gh-pages
- npm git scripts

- bootstrap-vue


# questionnaire
-- > score de satisfaction https://www.myfeelback.com/fr/blog/questionnaire-system-usability-scale-experience-client


# exemple paramétré
http://scenaristeur.github.io/egadnos?service={"name": "Egadnos", "logo": "https://scenaristeur.github.io/cdr/img/header-bg.jpg", "pod": "https://egadnos.solidweb.org", "url": "http://scenaristeur.github.io/egadnos", "confidentialite": "public"}

--> exemple de résultats pour un sondage ppublic : https://egadnos.solidweb.org/public/egadnos/

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run dev
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
