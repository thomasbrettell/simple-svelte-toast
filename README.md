# Simple Svelte Toast

A very simple implementation of a toast component in Svelte.  
The component is intended to be copied into your project rather than installed via NPM.

## Usage

```html
<script>
  import Toast, { toast } from "./components-or-whereever/Toast.svelte";
</script>

<button
    on:click={() => {
        toast.show("Toast message", {
            x: "left",
            y: "top",
            type: 'success'
        });
    }}
>
    Show toast!
</button>
```

- Copy the code from [Toast.svelte](https://github.com/thomasbrettell/simple-svelte-toast/blob/master/src/lib/Toast.svelte) into your project.
- Mount the component somewhere (probably near the root) in your application.
- Import the toast store from `Toast.svelte` and call `.show` to create a toast.

It should be very easy to alter the functionality or the design of the component by editing the code directly.
