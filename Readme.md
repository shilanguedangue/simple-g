# Simple G #
Simple G is a Zend Framework based PHP application that displays
Google Calendars in a flexible, easy-to-integrate-into-your-site way!

It is released under an MIT style license (found at the end of this document)
and was developed by the people at Simple Station Inc.

Simple G was designed with flexibility and portability in mind. The interface
can easily be themed with CSS, and the Lightbox-style popups can be replaced
or eliminated with no ill effects.

All of the markup is XHTML 1.0 Strict, and the CSS is valid level 2, 2.1 and 3.

In fact, even in a text based browser, with no JavaScript or CSS, the default
Simple G pages should be perfectly usable, and all the links will still work.

http://www.simplestation.com


---



# Setup #

To get going with this you're going to need:
  1. A Google(R) or Google Apps(R) account
  1. Apache with `mod_php5` (or equivalent php5.1+ webhosting capabilities)

### Step 1 ###
From your Google Account, you'll need the ID of the calendar you want to
display. To quote the Google documentation:
> "The calendar ID is available on the calendar settings page, next to the
> Calendar Address buttons. If you're subscribing to a user's primary calendar,
> the id will just be the user's email address."
> http://code.google.com/apis/calendar/developers_guide_protocol.html

If the calendar is shared as "public" that's all you'll need from the Google
Account. Otherwise, you'll need the username and password for the account, too.

Take this information (calendar id, account, password) and fill in the
appropriate sections of the `"./config.ini"` file in this directory.

### Step 2 ###
Set up Apache to serve the `"./public"` subdirectory as the `DocumentRoot`.

### Step 3 ###
Voila! You should be able to connect to `http://localhost/` or wherever you
are hosting from, and view the events of your calendar using Simple G.


---



# Customization #

In the above Setup section, we installed the default, stand-alone version of
Simple G. While it's functional in this state (and easily deployed, in this
configuration, as a subdomain of an existing site), you probably want to
integrate it with the theme and content of an existing site.

Have no fear, this is a Simple process!

If you want to host the calendar in a subdirectory of your site, rather than a
subdomain, this is also very easily accomplished. Simply copy the whole Simple G
installation to a folder outside of your `DocumentRoot`, then symlink the
`"./public/"` directory to wherever on your site you want to host the calendar.
Finally, make one edit to the `"./public/.htaccess"` file: update `RewriteBase` to
be the name of the subdirectory.

For example, if my existing `DocumentRoot` was `~/www/mysite`, and I had installed
the Simple G files to `~/www/simpleg`, I might run the following command:
> `ln -sf  ~/www/simpleg/public  ~/www/mysite/calendar`

Then I would edit `"./public/.htaccess"` and replace the `RewriteBase` line with:
> `RewriteBase /calendar/`

With these two simple steps, you've got a working Simple G at
`http://localhost/calendar`, or wherever you're hosting your site.

If you're happy with the calendar's functionality, but would like to change
the look of it, most changes can be accomplished by editing the view scripts
in `"./views/layouts/"` and `"./views/scripts/"` and the CSS in `"./public/styles/"`


---



# Further Customization and Integration with an Existing ZF Application #
For anybody so inclined, the rest of the code can be modified to suit your
needs. The `"./library/Simple/View/Helper/Calendar.php"` file contains the basic
elements of the calendar display.

The view scripts in `"./views/"` describe the layout and other information on the
page.

Integration with Moodalbox can be enabled or disabled by including or excluding
the `"scripts/moodalbox-1.2.1.js"` JavaScript file.

If you've already got a site based on the Zend Framework, integrating Simple G
should be a snap. It's pretty much self-contained, and you should be familiar
with the concepts like Views, View Helpers, Controllers and Routes.

Simple G only uses one controller, and has a very simple bootstrap file. All
Routes are contained within the bootstrap file at `"./public/index.php"`.


---



# Acknowledgements #

Simple G includes a few Open Source software packages, and we'd like to thank
the creators for sharing them with the world.

The Zend Framework (1.6.0) (http://framework.zend.com) is the PHP framework on
which this application is based.

They keep a list of top contributors here
http://framework.zend.com/community/contributors but many more contribute to
the project, if on a smaller scale.

The Blueprint CSS framework provides the resets and the foundation for our
custom stylesheets. It was written by Olav Bjørkøy (http://www.bjorkoy.com).

MooTools (http://mootools.net) is the JavaScript framework upon which all of
our JavaScript effects are built. They keep a list of developers here:
http://mootools.net/developers

Moodalbox is the Lightbox-esque JavaScript library developed by Răzvan Brateş
(http://www.e-magine.ro/web-dev-and-design/36/moodalbox/). It's built upon
MooTools, and has some modifications by Rhydian Roberts
(http://www.voidsystems.co.uk/moodalbox) and some custom Simple Station
edits.


---



# License #
Copyright (c) 2008 Simple Station Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.