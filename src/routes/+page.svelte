<script>
  import { onMount } from 'svelte';
  import dayjs from 'dayjs';
  import "./global.css";

  let days = 0;
  let hours = 0;
  let minutes = 0;
  let seconds = 0;

  const date1 = dayjs("2023-08-02T17:20:45");
  onMount(() => {
    const interval = setInterval(() => {
      const date2 = dayjs();
      days = date2.diff(date1, 'day')
      hours = date2.subtract(days, 'day').diff(date1, 'hour') 
      minutes = date2.subtract(days, 'day').subtract(hours, 'hour').diff(date1, 'minute')
      seconds = date2.subtract(days, 'day').subtract(hours, 'hour').subtract(minutes, 'minute').diff(date1, 'second')
    }, 1000);

    return () => {
      clearInterval(interval);
    };
  });
</script>

<main>
  <div><span>{days}</span> <span>{days === 1 ? 'Tag' : 'Tage'}</span></div>
  <div><span>{hours}</span> <span>{hours === 1 ? 'Stunde' : 'Stunden'}</span></div>
  <div><span>{minutes}</span> <span>{minutes === 1 ? 'Minute' : 'Minuten'}</span></div>
  <div><span>{seconds}</span> <span>{seconds === 1 ? 'Sekunde' : 'Sekunden'}</span></div>
</main>

<style>
  main {
    width: 800px;
    max-width: 800px;
    height: 100vh;
    display: flex;
    font-family: 'Lobster', cursive;
    justify-content: space-around;
    width: 100%;
    font-size: 2rem;
    margin: 5rem 0;
    color: #ffb;
  }

  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }

  span:first-child {
    font-size: 5rem;
    font-weight: bold;
    animation: fadeIn 1s;
  }

  @keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
  }

  span:last-child {
    font-size: 1.5rem;
    font-weight: normal;
    animation: fadeIn 1s;
  }
</style>
