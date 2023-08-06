<script>
  import { onMount } from 'svelte';
  import dayjs from 'dayjs';
  //let date = 
  //$: time = (new Date() - date)
  //let date = new Date();
  //$: time = new Date()


  let time;
  let hours = 0;
  let days = 0;
  let minutes = 0;
  let seconds = 0;

  //let time = new Date() - new Date();
  const date1 = dayjs("2023-08-02T17:20:45");
  //const date2 = dayjs();

  //$: hours = time.getHours();
  //$: minutes = time.getMinutes();
  //$: seconds = time.getSeconds();


  //$: hours = date2.diff(date1, 'hours');
  //$: days = Math.floor(hours / 24);
  //$: hours2 = hours - (days * 24);

  //console.log('Days: ', days);
  //console.log('Hours: ', hours);

  onMount(() => {
    const interval = setInterval(() => {
      const date2 = dayjs();
      //time = date2.diff(date1);
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

<span>
  <div>{days} Tage</div>
  <div>{hours} Stunden</div>
  <div>{minutes} Minuten</div>
  <div>{seconds} Sekunden</div>
</span>
