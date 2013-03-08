Shopify Theme Sync for node
==================

A tool to automatically sync themes from your local file system to your hosted Shopify shops.

**I've used this tool for about 30 hours now and only had to restart the process once. However, it is still under development and may not be entirely stable. Use at your own peril.**

## Install and Configuration

 0. Clone (then run `npm install`) or just `npm install` me onto your local machine or Cloud9IDE environment

 1. rename `config-example.json` to `config.json`.

 2. edit the properties of `config.json` to match your Shopify shops' *private app* credentials (you can do this by going to https://{yourshop}.myshopify.com/admin/apps/private) then point the config file's `directory` property to your themes' folders.

 3. Run the command `npm start` (or `node app`) and start editing your Shopify templates!

## Options

Check `config-example.json` for examples on applying these options. The defaults are:

 {
 	"interval": 500, // the default interval used when checking files for modification
 	"ignoreDotFiles": true, // ignore dotfiles by default.
 }

## To Actually Edit Templates:

You'll first need to install the template into your Shopify store then download and extract the zip file for the template.
For now, each template for your shop *must* be named after its template ID, e.g., `3981452` and  `4870543`.

If your config file's `directory` property is `/home/websites/shopname/` you should have directory tree similar to:


    /home/websites/shopname/3981452
                                  ./assets
                                  ./config
                                  ...etc
    /home/websites/shopname/4870543
                                  ./assets
                                  ./config
                                  ...etc

## TODO

 1. Handle `errors` from Shopify properly (errors are currently treated as "success").
 2. Notify user after successful/failed action without having to switch to the Terminal/Prompt to check status.
 3. Add config option to automatically minify JavaScript, CSS, and/or HTML (w/liquid), and optimize asset images on the fly.
 4. Allow sub-directories within theme folders for better file organization. We can "fake" sub directories by replacing the "/" (forward slash) character with a magic string, like "_DIR_" (Shopify doesn't allow special characters in filenames, otherwise I'd just use a solidus `/`), i.e., the resource `assets/css/main.css` would be referenced and uploaded as `assets__DIR__css__DIR__main.css`
 5. Add config option to automatically download themes from a Shopify store to local disk.