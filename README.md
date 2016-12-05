# passport-wunderlist-oauth2
Wunderlist OAuth2 Strategy for Passport

[Passport](http://passportjs.org/) strategy for authenticating with [Wunderlist](https://www.wunderlist.com)
using the OAuth 2.0 API.

This module lets you authenticate using Wunderlist in your Node.js applications.
By plugging into Passport, Wunderlist authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Usage

#### Configure Strategy

The Wunderlist authentication strategy authenticates users using a Wunderlist 
account and OAuth 2.0 tokens.  The strategy requires a `verify` callback, which
accepts these credentials and calls `done` providing a user, as well as
`options` specifying a app ID, app secret, and callback URL.

    var Wunderlist = require('passport-wunderlist-oauth2').Strategy;
    passport.use(new WunderlistStrategy({
        clientID: WUNDERLIST_KEY,
        clientSecret: WUNDERLIST_SECRET,
        callbackURL: "http://localhost:3000/auth/wunderlist/callback"
      }, function (accessToken, refreshToken, profile, done) {
        // store credentials, etc
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'wunderlist'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/wunderlist', passport.authenticate('wunderlist'));

    app.get('/auth/wunderlist/callback',
      passport.authenticate('wunderlist', { failureRedirect: '/login' }),
      function(req, res) {
        // Successul authentication, redirect home.
        res.redirect('/');
      });

## Credits

Created by [Daniel Elsner](https://delsner.github.io/)

Contributor [Paul Gualotuna](http://gualotuna.com)


Code based on passport-meetup-oauth2 [Joe Woodhouse](http://github.com/joewoodhouse)

## License

[The MIT License](http://opensource.org/licenses/MIT)
