<script>
  import Toast, { toast } from "./lib/DemoToast.svelte";
</script>

<div class="center">
  <h1>Simple Svelte Toast</h1>
  <div class="types-grid">
    <button
      on:click={() => {
        toast.show("success", {
          type: "success",
        });
      }}
    >
      success
    </button>

    <button
      on:click={() => {
        toast.show("error", {
          type: "error",
        });
      }}
    >
      error
    </button>

    <button
      on:click={() => {
        toast.show("warning", {
          type: "warning",
        });
      }}
    >
      warning
    </button>

    <button
      on:click={() => {
        toast.show("anything you want", {
          type: "custom",
        });
      }}
    >
      anything you want
    </button>
  </div>

  <div class="positions-grid">
    <button
      on:click={() => {
        toast.show("left - top", {
          x: "left",
          y: "top",
        });
      }}
    >
      left - top
    </button>

    <button
      on:click={() => {
        toast.show("center - top", {
          x: "center",
          y: "top",
        });
      }}
    >
      center - top
    </button>

    <button
      on:click={() => {
        toast.show("right - top", {
          x: "right",
          y: "top",
        });
      }}
    >
      right - top
    </button>

    <button
      on:click={() => {
        toast.show("left - center", {
          x: "left",
          y: "center",
        });
      }}
    >
      left - center
    </button>

    <button
      on:click={() => {
        toast.show("center - center", {
          x: "center",
          y: "center",
        });
      }}
    >
      center - center
    </button>

    <button
      on:click={() => {
        toast.show("right - center", {
          x: "right",
          y: "center",
        });
      }}
    >
      right - center
    </button>

    <button
      on:click={() => {
        toast.show("center - bottom");
      }}
    >
      center - bottom
    </button>

    <button
      on:click={() => {
        toast.show("left - bottom", {
          x: "left",
        });
      }}
    >
      left - bottom
    </button>

    <button
      on:click={() => {
        toast.show("right - bottom", {
          x: "right",
        });
      }}
    >
      right - bottom
    </button>
  </div>
</div>

<Toast />

<style>
  h1 {
    text-align: center;
  }

  .center {
    margin: auto;
  }

  .types-grid {
    display: flex;
    gap: 1rem;
    justify-content: center;
    margin-bottom: 2rem;
  }

  .positions-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: min(3vw, 1rem);
  }
</style>
