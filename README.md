# hs-doodle

This is my take on Doodle FED code challenge.

It uses Vue (and VueCli and useful libraries for convenience).

There are several small details that would need to be worked more thoroughly (styling, unescaping strings) but the core functionality is there. The biggest issue with this approach for me is that the API is not returning messages in reverse chronological order as it was supposed to, which is rendering the content "upside down".

To run this project, simply follow the instructions below.

Start by cloning the project from git to your local machine:

Open you terminal and navigate (``` cd ```) to the destination where you wish to clone the project to.

Next, clone it by running the command:

```
git clone https://github.com/henser/hs-doodle.git
```

Afterwards get inside the project folder:

```
cd hs-doodle
```
Then, you'll need to install the dependencies by running (make sure you have [npm](https://www.npmjs.com/) globally installed in your system)
```
npm install
```
And finally, just run serve to compile (also hot-reloads for development if you wish to do some changes)
```
npm run serve
```


Just for the record, other commands unnecessary for this project would be:

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


Any questions, you know where to reach me.
