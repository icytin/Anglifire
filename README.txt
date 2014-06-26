
_Note: While angular, angularFire, and Firebase can be used client-side-only, and it's possible to create
apps that don't require a backend server at all, we recommend hosting the project files using a local
webserver during development to avoid issues with security restrictions (sandbox) in browsers. The
sandbox implementation varies between browsers, but quite often prevents things like cookies, xhr,
etc to function properly when an html page is opened via `file://` scheme instead of `http://`._

 1. Open app/js/config.js and add your Firebase URL
 1. Go to your Firebase URL and enable email/password authentication under the Auth tab

### Serving pages during development

You can pick one of these options:

* serve this repository with your webserver
* install node.js and run `node scripts/web-server.js`. It´s important to run from the root of the catalog. For example:
C:\wwwroot\Anglifier>node scripts/web-server.js
Http Server running at http://localhost:8080/

Then navigate your browser to `http://localhost:<port>/app/index.html` to see the app running in
your browser.


### Running the app in production

Make sure you set up security rules for your Firebase! An example for this
seed can be found in `config/security-rules.json`

Go to your Forge (open your Firebase URL in the browser) and add your sites domain name under
Auth -> Authorized Request Origins. This allows simple login to work from your web site as well as localhost.

The rest really depends on how complex is your app and the overall infrastructure of your system, but
the general rule is that all you need in production are all the files under the `app/` directory.
Everything else can be omitted.

Angular apps are really just a bunch of static html, css and js files that just need to be hosted
somewhere, where they can be accessed by browsers.

If your Angular app is talking to the backend server via xhr or other means, you need to figure
out what is the best way to host the static files to comply with the same origin policy if
applicable. Usually this is done by hosting the files by the backend server or through
reverse-proxying the backend server(s) and a webserver(s).
