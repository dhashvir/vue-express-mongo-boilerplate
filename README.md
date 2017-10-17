# Vue, Express, MongoDB full-stack JS Boilerplate

## Features

**Server-side**
* [x] **[Node.JS](https://nodejs.org)** v6.x.x
* [x] **[Express](https://github.com/expressjs/express)**
* [x] [MongoDB](https://www.mongodb.com/) with [Mongoose](https://github.com/Automattic/mongoose)
* [x] [NodeMailer](https://github.com/nodemailer/nodemailer) with SMTP, MailGun or SendGrid
* [x] [Helmet](https://github.com/helmetjs/helmet)
* [x] [Express-validator](https://github.com/ctavan/express-validator)
* [x] [winston](https://github.com/winstonjs/winston) + 6 transports
* [x] **[GraphQL](http://graphql.org/)** with [Apollo stack](http://www.apollostack.com/)
* [x] [i18next](http://i18next.com/) as the internationalization ecosystem
* [x] **[HTTP/2 Server Push](https://en.wikipedia.org/wiki/HTTP/2_Server_Push)** with [netjet](https://github.com/cloudflare/netjet)
* [x] Bundled server-side code with [Webpack 2](https://webpack.github.io/)

**Client-side**
* [x] **[VueJS 2.x](https://github.com/vuejs/vue)**
* [x] [Vuex](https://github.com/vuejs/vuex)
* [x] [Vue-router](https://github.com/vuejs/vue-router)
* [x] [axios](https://github.com/mzabriskie/axios)
* [x] **[socket.io](https://github.com/socketio/socket.io) connection with namespaces & authorization**
* [x] [vue-websocket](https://github.com/icebob/vue-websocket)
* [x] [Jade](https://github.com/pugjs/pug)
* [x] **[Webpack 2](https://github.com/webpack/webpack)**
* [x] [SCSS](http://sass-lang.com/)
* [x] [PostCSS](https://github.com/postcss/postcss) with precss and autoprefixer
* [x] [Babel](https://babeljs.io/)
* [x] [Passwordless](https://www.sitepoint.com/passwordless-authentication-works/) mode
* [x] [Passport.JS](http://passportjs.org/)
	* Social signup/login with Facebook, Google, Twitter and Github
	* API key authentication for REST API calls
* [x] [Toastr](https://github.com/CodeSeven/toastr)
* [x] [vue-form-generator](https://github.com/icebob/vue-form-generator)

**Supported remote logging services**
* [x] [Papertrail](https://papertrailapp.com/)
* [x] [Graylog](https://www.graylog.org/)
* [x] [LogEntries](https://logentries.com/)
* [x] [Loggly](https://www.loggly.com/)
* [x] [Logsene](https://sematext.com/logsene/)
* [x] [Logz.io](http://logz.io/)

## Usage

Install dependencies
```
$ npm install
```
or
```
yarn
```

For development
```bash
$ npm run dev
```

Build web app scripts and styles:
```bash
$ npm run build
```

For production
```bash
$ npm start
```

## Bundled server-side

If you want to bundle your NodeJS server-side code run webpack on server code with `npm run build && npm run build:server` command. It if was success, run the server: `npm run start:bundle`

If you want to export bundled version copy these folders & files to the new place:

```txt
- server
	- locales
	- public
	- views
	- bundle.js
- package.json
- config.js (optional)
```

Before start, you have to install production dependencies with npm: `npm install --production`

## Obtaining API keys for social signup/login

![Google Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/128px-Google_2015_logo.svg.png)

These are the instructions for Google:

- Visit [Google Cloud Console](https://cloud.google.com/console/project)
- Click on the **Create Project** button
- Enter *Project Name*, then click on **Create** button
- Then click on *APIs & auth* in the sidebar and select *API* tab
- Click on **Google+ API** under *Social APIs*, then click **Enable API**
- Next, under *APIs & auth* in the sidebar click on *Credentials* tab
- Click on **Create new Client ID** button
- Select *Web Application* and click on **Configure Consent Screen**
- Fill out the required fields then click on **Save**
- In the *Create Client ID* modal dialog:
 - **Application Type**: Web Application
 - **Authorized Javascript origins**: http://localhost:3000
 - **Authorized redirect URI**: http://localhost:3000/auth/google/callback
- Click on **Create Client ID** button
- Copy and paste *Client ID* and *Client secret* keys into `config.js` file

![Facebook Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Facebook_New_Logo_%282015%29.svg/128px-Facebook_New_Logo_%282015%29.svg.png)

These are the instructions for Facebook:

- Visit [Facebook Developers](https://developers.facebook.com/)
- Click **My Apps**, then select **Add a New App* from the dropdown menu
- Select **Website** platform and enter a new name for your app
- Click on the **Create New Facebook App ID** button
- Choose a **Category** that best describes your app
- Click on **Create App ID** button
- In the upper right corner click on **Skip Quick Star**
- Copy and paste *App ID* and *App Secret* keys into `config.js` file
 - **Note:** *App ID* is **clientID**, *App Secret* is **clientSecret**
- Click on the *Settings* tab in the left nav, then click on **+ Add Platform**
- Select **Website**
- Enter `http://localhost:3000` under *Site URL*

**Note:** After a successful sign in with Facebook, a user will be redirected back to home page with appended hash `#_=_` in the URL. It is *not* a bug. See this [Stack Overflow](https://stackoverflow.com/questions/7131909/facebook-callback-appends-to-return-url) discussion for ways to handle it.

![GitHub Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/GitHub_logo_2013_padded.svg/128px-GitHub_logo_2013_padded.svg.png)

These are the instructions for GitHub:

- Go to [Account Settings](https://github.com/settings/profile)
- Select **Applications** from the sidebar
- Then inside **Developer applications** click on **Register new application**
- Enter *Application Name* and *Homepage URL*
- For *Authorization Callback URL*: http://localhost:3000/auth/github/callback
- Click **Register application**
- Now copy and paste *Client ID* and *Client Secret* keys into `config.js` file

![Twitter Logo](https://upload.wikimedia.org/wikipedia/en/thumb/9/9f/Twitter_bird_logo_2012.svg/64px-Twitter_bird_logo_2012.svg.png)

These are the instructions for Twitter:

- Sign in at [https://apps.twitter.com/](https://apps.twitter.com/)
- Click **Create a new application**
- Enter your application name, website and description
- For **Callback URL**: http://127.0.0.1:3000/auth/twitter/callback
- Go to **Settings** tab
- Under *Application Type* select **Read and Write** access
- Check the box **Allow this application to be used to Sign in with Twitter**
- Click **Update this Twitter's applications settings**
- Copy and paste *Consumer Key* and *Consumer Secret* keys into `config.js` file

## Windows Install
- Ensure Git is installed. https://git-scm.com/download/win
- Add the following to window Path variable:  
	- C:\Program Files\Git\usr\bin 
	

## License

vue-express-mongo-boilerplate is available under the [MIT license](https://tldrlegal.com/license/mit-license).