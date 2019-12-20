<script>
  import Moment from "moment";
  import MomentDurationFormatSetup from "moment-duration-format";

  const startDate = "2015-07-17";
  const today = Moment();
  let nextAnniversaryDate = Moment(`${today.year()}-07-17`);

  if (nextAnniversaryDate.diff(today, "days") < 0) {
    nextAnniversaryDate = nextAnniversaryDate.add(1, "y");
  }

  const etaNextAnniversary = nextAnniversaryDate.diff(today, "days");

  let day = Moment(startDate).format("dddd, MMMM Do YYYY");

  const b = Moment([2019, 11, 19]);

  let difference = Moment.duration(today.diff(startDate));
  momentDurationFormatSetup(Moment);
  typeof Moment.duration.fn.format === "function";
  typeof Moment.duration.format === "function";
  let timeSince = Moment.duration(difference, "hours").format();

  let y1Date = Moment(startDate).add(1, "y");
  let y1ETA = today.diff(y1Date, "days");
  y1ETA = y1ETA > 0 && `+${y1ETA}`;

  const ETA = yearsLater => {
    let laterDate = Moment(startDate).add(yearsLater, "y");
    return today.diff(laterDate, "days");
  };

  const isETAFuture = elapsedTime => {
    console.log(elapsedTime);

    if (elapsedTime >= 0) {
      console.log("Great Scott! It's the future!");
    } else {
      console.log("Great Scott! It's the past!");
    }
    return elapsedTime && elapsedTime >= 0;
  };

  let years = [1, 3, 5, 10];
</script>

<style>
  @import url("https://fonts.googleapis.com/css?family=Lato:300,400,700&display=swap");

  :global(body) {
    background-color: #f1f2f6;
  }

  main {
    margin: 5% auto;
    padding: 20px;
    border-radius: 3px;
    background-color: #ffffff;
    box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.2);

    width: 500px;
    text-align: center;
    font-family: "Lato", sans-serif;
  }

  h1 {
    margin: 0;
    font-weight: 300;
  }

  h2 {
    margin: 20px 0 0;
  }

  .subtitle {
    margin: 4px 0;
    color: rgb(150, 150, 150);
    font-size: 12px;
  }

  ul {
    display: inline-block;
    margin: 20px auto 0;
    padding: 0;
    width: 280px;
    list-style-type: none;
    text-align: left;
  }

  li {
    display: flex;
    font-size: 13px;
  }

  li span {
    flex-grow: 1;
    flex-basis: 0;
  }

  li span:first-child {
    text-align: right;
    margin-right: 10px;
  }

  li span:last-child {
    text-align: left;
  }

  .check {
    text-decoration: line-through;
    color: rgb(150, 150, 150);
  }
</style>

<main>
  <header>
    <h1>DnD</h1>
    <p class="subtitle">Together since {day}.</p>
  </header>

  <div>
    <section class="block-ongoing">
      <h2>{timeSince}</h2>
      <span class="subtitle">{etaNextAnniversary} days till anniversary</span>
    </section>

    <section class="block-anniversaries">
      <ul>
        {#each years as year}
          <li class:check={isETAFuture(ETA(year))}>
            <span>{year} {year > 1 ? `years` : `year`}</span>
            <span>
              {ETA(year)}
              {isETAFuture(ETA(year)) ? `days ago` : `days remaining`}
            </span>
          </li>
        {/each}
      </ul>
    </section>
  </div>
</main>
