# Kamehameha

Powerfull model layer like Kamehameha in Dragon Ball. Inspired by ReactiveX and
dvajs.

## Install

```bash
npm i --save kamehameha
```

## Example

```js
import khh from kamehameha;
const app = khh();
app.model({
  namespace: 'count',
  obserables: {
    click: (observe) => {
      $('.button').on('click', (ev) => {
        observe.next(ev);
      }, false);
    },
    state: (observe) => {
      // init value
      const value = 0;
      observe.next(value);
      this.ob('click').subscribe(ev => {
        // update value
        if ($(ev.target).attr('key') === 'add') {
          observe.next(++value);
        } else {
          observe.next(--value);
        }
      });
    },
  },
  effects: [
    this.observe('state').subscribe(state => {
      $('#count').text(state);
    });
  ]
});
```
