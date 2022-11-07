<script lang="ts">
  import CreateAlarm from "./lib/CreateAlarm.svelte";
    import ThemePicker from "./lib/ThemePicker.svelte";
</script>

<main>
  <ThemePicker></ThemePicker>
  <CreateAlarm />

  <section>
    <h1>What's the 20-20-20 rule?</h1>
    <p>
      Every <strong>20</strong> minutes spent using a screen, you should try to
      look away at something that is <strong>20</strong> feet (6 meters) away
      from you for a total of <strong>20</strong> seconds.
    </p>
  </section>
</main>

<style>
</style>
