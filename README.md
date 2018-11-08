# The Meteor 1.8 dev build process doesn't include changes to postcss

## Steps to see the error
```
git clone https://github.com/mcissel/postcssBuild.git
cd postcssBuild
meteor npm install
meteor
```

Then Change the content of /imports/style.css and save. The terminal says `Client modified -- refreshing (x2)`, but the UI _doesn't_ change

## Steps to create this repo
```
meteor create --react postcssBuild
cd postcssBuild

meteor remove standard-minifier-css && meteor add juliancwirko:postcss
meteor npm install -s autoprefixer postcss-easy-import postcss@^6.0.22 postcss-load-config@^1.2.0
```
add the file /imports/style.css with
```
body {
  background-color: beige;
}
```
add the following to the top of /client/main.css:
```
@import "../imports/style";
```
run `meteor`

