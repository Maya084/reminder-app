<script lang="ts">
  let btn: HTMLButtonElement;

  function createAlarm(): void {
    Notification.requestPermission().then((perm) => {
      if (perm === "granted") {
        createNotif();
        startNotifications();
        btn.disabled = true;
      }
    });
  }

  function startNotifications(): void {
    setInterval(() => {
      createNotif();
    }, 120000);
  }

  const createNotif = () => {
    new Notification("Look away!", {
      body: "It's time to look away from the screen for 20 seconds",
      vibrate: [200, 100, 200],
    });
  };
</script>

<button on:click={createAlarm} bind:this={btn}>Create alarm</button>
