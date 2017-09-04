---
title: Customizing the User Interface
index: 5000
icon: page
---

Some of the Clarive application web interface look-and-feel can be customized by the user in the `[env].yml` file.

There are 2 basic customizations available:

- **Logo files** - the logo shown on the top left of the screen
- **CSS files** - one or more cascading stylesheet files

### File Location in the Server

We recommend that custom files (logos or CSS stylesheets) reside withing a plugin `/public/` folder or a feature `/root`
folder in the Clarive web server node.

In general, the browser will attempt to load the file from a URL, therefore custom files can reside anywhere under the
Clarive main URL.

For example, if the logo file resides physically in the `CLARIVE_BASE/features/myfeature/root/mylogo.png`, then you
should be able to load the file through the following URL:

    http://myclariveserver/mylogo.png

### Changing the logo files

To change the application logo files, 6 different `[env].yml` config keys are available:

    logo_file: /path/to/logo.png
    logo_width: 150
    logo_narrow_file: /path/to/narrow-logo.png
    logo_narrow_width: 30
    login_logo: /path/to/login-logo.png
    login_logo_width: 180

The logo file will be shown as a source of a `img` tag in the application.

The width is optional, but it allows you to easily resize a logo without having to edit the image file (which usually
requires aditional tools).

- `logo_file` - Is the logo shown in the top left of the main application navigation menu
- `logo_width` - Is the optional logo width ot apply to the `logo_file`
- `logo_narrow_file` - Is the logo shown in the top left of the main application navigation menu when in narrow mode
- `logo_narrow_width` - Is the optional logo width ot apply to the `logo_narrow_file`
- `login_logo` - Is the logo shown in the login page of the application.
- `login_logo_width` - Is the optional logo width ot apply to the `login_logo`

### Add a text next to the logo

This is a perfect strategy to better identify your Clarive instance in case you have more than one instance installed.
Or simply to customize the instance info.

Add the following entry to your `[env].yml` file:

    logo_text: MY INSTANCE

Restart and refresh the instance. The text will show up next to the top-left logo in the application navigation menu.

### Custom CSS

Custom CSS is a convenient and powerful way to add custom styles to the Clarive application HTML.

To add your styles to the Clarive web application, use the following `[env].yml` file entry:

    custom_css: /path/to/mystyles.css
