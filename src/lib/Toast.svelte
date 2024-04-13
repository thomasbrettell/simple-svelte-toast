<script context="module">
  import { writable } from "svelte/store";

  const TOAST_DURATION = 3000;

  const optionDefaults = { type: "success", y: "bottom", x: "center" };

  const createToastStore = () => {
    const { subscribe, set } = writable(null);

    let id = 0;
    let timeoutId = null;

    return {
      subscribe,
      show: (message, options) => {
        options = { ...optionDefaults, ...options };

        clearTimeout(timeoutId);
        set({ id, message, ...options });
        id++;
        timeoutId = setTimeout(() => set(null), TOAST_DURATION);
      },
    };
  };

  export const toast = createToastStore();
</script>

<script>
  import { fly, scale } from "svelte/transition";
</script>

{#if $toast}
  {#key $toast.id}
    <div
      in:fly|global={{
        y: 50,
      }}
      out:scale|global
      class={`toast ${$toast.type} x-${$toast.x} y-${$toast.y}`}
    >
      {$toast.message}
    </div>
  {/key}
{/if}

<style>
  .toast {
    background-color: #0070f3;
    color: white;
    padding: 10px;
    border-radius: 5px;
    position: fixed;
    font-size: 14px;
    z-index: 1000;
    font-family:
      system-ui,
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      Oxygen,
      Ubuntu,
      Cantarell,
      "Open Sans",
      "Helvetica Neue",
      sans-serif;
  }

  .toast.x-left {
    left: 20px;
    transform: none;
  }

  .toast.x-right {
    right: 20px;
    left: auto;
    transform: none;
  }

  .toast.y-top {
    top: 20px;
    bottom: auto;
  }

  .toast.y-bottom {
    bottom: 20px;
    top: auto;
  }

  .toast.x-center {
    left: 50%;
    transform: translateX(-50%);
  }

  .toast.y-center {
    top: 50%;
  }

  .toast.warning {
    background-color: #f5a623;
  }

  .toast.error {
    background-color: #e00;
  }

  .toast.success {
    background-color: #0070f3;
  }

  .toast.custom {
    animation: 3s ease 0s infinite normal none running MoveBG;

    background: linear-gradient(
        270deg,
        rgb(255, 0, 0),
        rgb(255, 245, 0),
        rgb(0, 255, 5),
        rgb(0, 246, 255),
        rgb(0, 10, 255),
        rgb(226, 0, 255)
      )
      0% 0% / 600% 600%;
  }
</style>
