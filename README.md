[![build](https://travis-ci.org/mozilla/browser.html.svg?branch=master)](https://travis-ci.org/mozilla/browser.html)

*browser.html* is a platform research project closely related to [Servo](https://github.com/servo/servo). It's not a product.
We are exploring future UI paradigms strictly only because we are curious what future needs
will be on our platform and processes to build our platform, which we want to evolve.

#### Setup

Due to library dependencies (sockit-to-me) the only supported node versions are 0.10 and 0.12.

```sh
npm install --no-optional
npm start
```

#### Runtime (Gecko)

Browser.html needs a special build of B2G desktop called *Graphene*.
Build this branch: https://hg.mozilla.org/projects/larch with
`--enable-application=b2g/graphene`.

In the future, we want `browser.html` to be able to run on top of Servo.


#### Running in Servo

First, build [Servo](https://github.com/servo/servo).

Then, start the front-end local server:

    npm run build-server

Finally, start Servo with the browser.html flags turned on in either debug (`-d`) or release (`-r`) mode:

    ./mach run -r -- -b --pref dom.mozbrowser.enabled http://localhost:6060


#### Using WebIDE

The easiest way to use developer tools with Browser.html is to select the "Remote Runtime" option in WebIDE.
By default you should be able to connect to the running browser at: localhost:6000.


### Integration Tests
Run integration tests with `./test/runall.sh`. You need to have a graphene gecko binary symlinked in the root of the repository.

```
ln -s ../gecko/obj-graphene/dist/Graphene.app graphene
```
