# P5 Wrapper...

`var P5Wrapper = require('react-p5-wrapper');`
or
```
import P5Wrapper from 'react-p5-wrapper';
 
<P5Wrapper sketch={sketch} />
```

Sketch could look like this:

```
export default function sketch (p) {
  let rotation = 0;
 
  p.setup = function () {
    p.createCanvas(600, 400, p.WEBGL);
  };
 
  p.myCustomRedrawAccordingToNewPropsHandler = function (props) {
    if (props.rotation){
      rotation = props.rotation * Math.PI / 180;
    }
  };
 
  p.draw = function () {
    p.background(100);
    p.noStroke();
    p.push();
    p.rotateY(rotation);
    p.box(100);
    p.pop();
  };
};
```

In the Example above you see the myCustomRedrawAccordingToNewPropsHandler function. This function is called if Properties of the wrapper component are changing. In this case the Wrapper Component would be integrated like this: <P5Wrapper sketch={sketch} rotation={rotation}/>.

Properties

- sketch: This is the Sketch Script which should be executed in the P5 Canvas
- You can add as many custom Properties as you want
