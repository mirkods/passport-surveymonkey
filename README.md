# passport-surveymonkey

SurveyMonkey authentication strategy for [Passport](http://passportjs.org/).

This module lets you authenticate using SurveyMonkey OAuth in your Node.js applications.
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Usage

#### Configure Strategy

The SurveyMonkey authentication strategy authenticates users using a third-party
account and SurveyMonkey tokens.  The provider's OAuth 2.0 endpoints, as well as
the client identifer and secret, are specified as options.  The strategy
requires a `verify` callback, which receives an access token and profile,
and calls `done` providing a user.
  
    var SurveyMonkeyStrategy = require('passport-surveymonkey').Strategy;

    passport.use(new SurveyMonkeyStrategy({      
        clientID: 'SURVEYMONKEY USERNAME',
        clientSecret: SURVEYMONKEY APP SECRET,
        api_key: SURVEYMONKEY APP_KEY,
        callbackURL: "http://yoursite.com/auth/example/callback"
      },
      function(accessToken, refreshToken, profile, done) {
        User.findOrCreate({ exampleId: profile.id }, function (err, user) {
          return done(err, user);
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'surveymonkey'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/example',
      passport.authenticate('surveymonkey'));

    app.get('/auth/example/callback',
      passport.authenticate('surveymonkey', { failureRedirect: '/login' }),
      function(req, res) {
        // Successful authentication, redirect home.
        res.redirect('/');
      });

## Related Modules

- [passport-oauth1](https://github.com/jaredhanson/passport-oauth1) — OAuth 1.0 authentication strategy
- [passport-http-bearer](https://github.com/jaredhanson/passport-http-bearer) — Bearer token authentication strategy for APIs
- [OAuth2orize](https://github.com/jaredhanson/oauth2orize) — OAuth 2.0 authorization server toolkit


## Credits

  - [Jared Hanson](http://github.com/jaredhanson)
  - [Mirko Di Serafino](http://github.com/mirkods)

## License

[The MIT License](http://opensource.org/licenses/MIT)
