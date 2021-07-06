<script>
  import { minChallengeRating, maxChallengeRating } from './stores.js';

  let minHordeSize = 1;
  let maxHordeSize = 3;
  let minChallengeSlider = 2;
  let maxChallengeSlider = 6;
  let medianChallengeSlider = 4;
  let meanChallengeSlider = 4;

  const challengeRange = returnChallengeRange();

  $: minChallengeRating = challengeRange[minChallengeSlider];
  $: maxChallengeRating = challengeRange[maxChallengeSlider];
  $: medianChallengeRating = challengeRange[medianChallengeSlider];
  $: meanChallengeRating = challengeRange[meanChallengeSlider];

  function updateLevel(store, slider) {
    [store].update(rating => rating = challengeRange[slider])
  }

  function returnChallengeRange() {
    const fractionalVals = [ 0.125, 0.25, 0.5 ];
    const intervalicVals = [...Array(31).keys()];
    const [first, ...rest] = intervalicVals;
    return [first, ...fractionalVals, ...rest];
  }


</script>

<form>
  <fieldset>
    <legend>Horde size</legend>
    <input
      id='min-horde'
      min='1'
      max='50'
      type='range'
      bind:value={minHordeSize}
    />
    <label for='min-horde'>
      Min horde size: {minHordeSize}
    </label>
    <input
      id='max-horde'
      min='1'
      max='50'
      type='range'
      bind:value={maxHordeSize}
    />
    <label for='max-horde'>
      Max horde size: {maxHordeSize}
    </label>
  </fieldset>
  <fieldset>
    <legend>Challenge rating</legend>
    <input
      id='min-challenge'
      min='0'
      max='33'
      step='1'
      type='range'
      bind:value={minChallengeSlider}
    />
    <label for='min-challenge'>
      Minimum challenge rating: {minChallengeRating}
    </label>
    <input
      id='max-challenge'
      bind:min={minChallengeSlider}
      max='33'
      step='1'
      type='range'
      bind:value={maxChallengeSlider}
    />
    <label for='max-challenge'>
      Maxiumum challenge rating: {maxChallengeRating}
    </label>
    <input
      id='median-challenge'
      min={minChallengeSlider}
      max={maxChallengeSlider}
      step='1'
      type='range'
      bind:value={medianChallengeSlider}
    />
    <label for='max-challenge'>
      Median challenge rating: {medianChallengeRating}
    </label>
    <input
      id='mean-challenge'
      min={minChallengeSlider}
      max={maxChallengeSlider}
      step='1'
      type='range'
      bind:value={meanChallengeSlider}
    />
    <label for='max-challenge'>
      Mean challenge rating: {meanChallengeRating}
    </label>
  </fieldset>
</form>

<style>
  form {
    padding: 1em;
  }

  input {
    margin: 1em;
  }

</style>
