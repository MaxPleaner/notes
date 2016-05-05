---

**Hello world**

var five = require("johnny-five");
var board = new five.Board();
board.on("ready", function() {
  var led = new five.Led(13);
  led.blink(500);
})

---

**Dependencies**

_OSX_

- Node >= 0.10.x
- Xcode
- `npm install -g node-gyp`

_Linux_

- `apt-get install nodejs`
- `apt-get install nodejs-legacy`
- `apt-get install build-essential`

---

**Install**

`npm install johnny-five`

---

**Control System**

- Board > Components
- Component > Controller (Device)