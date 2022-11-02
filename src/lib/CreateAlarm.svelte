<script lang="ts">
  // const time=72000000;
  const time=3000;
  let btn: HTMLButtonElement;

  function createAlarm(): void {
    //ask for permission
    Notification.requestPermission().then((perm) => {
      if (perm === "granted") {
        //if permission is granted create a notification and then start a timer
        createNotif();
        startNotifications();
        //disable button so user can't create many intervals
        btn.disabled = true;
      }
    });
  }

  //starts interval every 20 minutes
  function startNotifications(): void {
    setInterval(() => {
      //create notification when timer runs out
      createNotif();
    }, time);
  }

  //creates a new push notification
  const createNotif = () => {
    new Notification("Look away!", {
      body: "It's time to look away from the screen for 20 seconds",
      vibrate: [200, 100, 200],
      
    });
  };

</script>

<button on:click={createAlarm} bind:this={btn}>Create a reminder</button>
