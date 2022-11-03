<script lang="ts">
  import { onDestroy, onMount } from "svelte";

  const time = 72000000;
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
      icon: '/src/assets/eye.png'
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

<button on:click={createAlarm} bind:this={btn}>Create a reminder</button>
