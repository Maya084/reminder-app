<script lang="ts">
  import { onDestroy, onMount } from "svelte";

  const time = 1200000;
  // const time=10000;
  let btn: HTMLButtonElement;
  let interval;

  function createAlarm(): void {
    //ask for permission
    Notification.requestPermission().then((perm) => {
      if (perm === "granted") {
        //if permission is granted create a notification and then start a timer
        startNotifications();
      }
    });
  }

  //starts interval every 20 minutes
  function startNotifications(): void {
    createNotif();
    //disable button so user can't create many intervals
    btn.disabled = true;
    interval = setInterval(() => {
      //create notification when timer runs out
      createNotif();
    }, time);
  }

  //creates a new push notification
  const createNotif = () => {
    new Notification("Look away!", {
      body: "It's time to look away from the screen for 20 seconds",
      vibrate: [200, 100, 200],
      icon: "src/assets/eye.png",
    });
  };

  onMount(() => {
    if (Notification.permission === "granted") {
      startNotifications();
    }
  });

  onDestroy(() => {
    interval = null;
  });
</script>

<div class="card">
  <!-- on:click={createAlarm} bind:this={btn} -->

  <button class="card-content" on:click={createAlarm} bind:this={btn}
    >Create a reminder</button
  >
</div>

<style>
  button {
    all: unset;
  }

  button:hover:not(:disabled) {
    cursor: pointer;
  }


  .card {
    background-color: var(--section-bg-color);
    border-radius: 10px;
    width: 200px;
    height: 50px;
    position: relative;

    /* center */
    left: 50%;
    transform: translateX(-50%);
  }

  .card-content {
    background-color: var(--section-bg-color);
    border-radius: inherit;
    color: var(--main-color);
    inset: 1px;
    position: absolute;
  }

  .card::before {
    content: "";
    inset: 0px;
    position: absolute;
    border-radius: inherit;
    background: linear-gradient(
      45deg,
      transparent 5%,
      var(--accent-color) 50%,
      transparent 99%
    );
    z-index: 0;
    opacity: 0;
  }
  .card:hover::before {
    opacity: 1;
  }

</style>
