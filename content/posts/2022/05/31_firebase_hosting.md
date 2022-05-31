---
title: "Firebase設定"
date: "2022-05-31"
tags: ["Firebase"]

---

WebViewを使うとして、MDMMLのJS版を公開する場所をFirebase Hostingにした。

久しぶりにFirebase使ったらオプションが色々増えている気がする。

```sh
$ firebase init

     ######## #### ########  ######## ########     ###     ######  ########
     ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
     ######    ##  ########  ######   ########  #########  ######  ######
     ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
     ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

  /home/umemak/workspace/mdmml_js

? Which Firebase features do you want to set up for this directory? Press Space to select features, then Enter to confirm your choices. Hostin
g: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys, Hosting: Set up GitHub Action deploys

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add, 
but for now we'll just set up a default project.

? Please select an option: Use an existing project
? Select a default Firebase project for this directory: mdmml-285c0 (mdmml)
i  Using project mdmml-285c0 (mdmml)

=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? public
? Configure as a single-page app (rewrite all urls to /index.html)? No
? Set up automatic builds and deploys with GitHub? Yes
✔  Wrote public/404.html
✔  Wrote public/index.html

i  Detected a .git folder at /home/umemak/workspace/mdmml_js
i  Authorizing with GitHub to upload your service account to a GitHub repository's secrets store.

Waiting for authentication...

✔  Success! Logged into GitHub as umemak

? For which GitHub repository would you like to set up a GitHub workflow? (format: user/repository) umemak/mdmml_js

✔  Created service account github-action-487458244 with Firebase Hosting admin permissions.
✔  Uploaded service account JSON to GitHub as secret FIREBASE_SERVICE_ACCOUNT_MDMML_285C0.
i  You can manage your secrets at https://github.com/umemak/mdmml_js/settings/secrets.

? Set up the workflow to run a build script before every deploy? Yes
? What script should be run before every deploy? npm ci && npm run build

✔  Created workflow file /home/umemak/workspace/mdmml_js/.github/workflows/firebase-hosting-pull-request.yml
? Set up automatic deployment to your site's live channel when a PR is merged? Yes
? What is the name of the GitHub branch associated with your site's live channel? main

✔  Created workflow file /home/umemak/workspace/mdmml_js/.github/workflows/firebase-hosting-merge.yml

i  Action required: Visit this URL to revoke authorization for the Firebase CLI GitHub OAuth App:
https://github.com/settings/connections/applications/89cf50f02ac6aaed3484
i  Action required: Push any new workflow file(s) to your repo

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...

✔  Firebase initialization complete!
```
GitHub Actionsとの連携も入れてみた。

https://mdmml-285c0.web.app/

良さそう。
