Heroku buildpack: precompiled pdftk
======================

Based on https://github.com/millie/heroku-buildpack-ruby-pdftk,
but modified for use with https://github.com/ddollar/heroku-buildpack-multi.

How to install:

1) Download PDFTK source (compiled for Heroku's Cedar Stack) from http://github.com/millie/pdftk-source

2) Upload the tar.gz to your own S3 bucket.  Make it public.  Remember the S3 URL of the tar.gz file.

3) Clone this repo to your own.

4) Update lib/custom/pdftk.rb source_url method to return the S3 URL from step 2.

5) Add your cloned repo to your project's .buildpacks file.

6) Add config vars to heroku like so

```bash
heroku config:set \
BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git \
PATH=[your current PATH var]:/app/vendor/pdftk/bin \
LD_LIBRARY_PATH=[your current LD_LIBRARY_PATH var (if you have set before)]:/app/vendor/pdftk/lib
```
