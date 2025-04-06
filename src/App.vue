<template>
  <div>{{ greet }} {{ name }}</div>
  <div v-text="channel"></div>
  <div v-html="channel"></div>
  <div v-html="hack"></div>

  <!-- v-bind can be shortened to : -->

  <h2 v-bind:id="headingId">Heading</h2>
  <h2 :id="headingId">Heading with shorthand v-bind</h2>

  <!-- Two ways of referencing an object -->
  <button v-bind="{ disabled: isDisabled }">I am disabled</button>
  <button v-bind:disabled="isDisabled">I am disabled too</button>

  <!-- Classes -->
  <h2 class="underline">Underlined text</h2>
  <h2 class="underline" v-bind:class="status">Status</h2>

  <h2 v-bind:class="isPromoted && 'promoted'">Promoted Movie</h2>
  <h2 v-bind:class="isSoldOut ? 'sold-out' : 'new'">Soldout? movie</h2>
  <h2 v-bind:class="['promoted', 'new']">Newly promoted movie</h2>
  <h2 v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold-out' : 'new']">
    Array conditional movie
  </h2>
  <h2
    v-bind:class="{
      promoted: isPromoted,
      new: !isSoldOut,
      'sold-out': isSoldOut,
    }"
  >
    Object conditional movie
  </h2>
  <h2
    v-bind:style="{
      color: highlightColor,
      fontSize: headerSize + 'px',
      padding: '10px',
    }"
  >
    Inline style
  </h2>
  <h2 v-bind:style="headerStyleObject">Style Object</h2>
  <div v-bind:style="[baseStyleObject, successStyleObject]">Success style</div>
  <div v-bind:style="[baseStyleObject, dangerStyleObject]">Danger style</div>

  <!-- Conditional rendering -->
  <h2 v-if="num === 0">The number is zero</h2>
  <!-- v-else can be use only after v-if -->
  <h2 v-else>The number is not zero</h2>

  <!-- v-else-if can be used multiple times -->
  <h2 v-if="num === 0">The number is zero</h2>
  <h2 v-else-if="num < 0">The number is negative</h2>
  <h2 v-else-if="num > 0">The number is positive</h2>
  <h2 v-else>It is not a number</h2>

  <!-- using a template to wrap multiple elements -->
  <template v-if="display">
    <h2>Wrapped content in a template - no div!</h2>
    <h2>Vishwas</h2>
    <h2>Codevolution</h2>
    <h2>Vue</h2>
  </template>

  <!-- v-show -->
  <h2 v-show="showElement">Using v-show</h2>
  <!-- v-if mounts the element in the DOM if condition is true, whereas v-show just shows or hides the element, but always keeps it in the DOM -->
  <h2 v-if="showElement">Using v-show</h2>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      greet: 'Hello',
      name: 'Batman',
      channel: '<b>Codevolution</b>',
      hack: `<a href="#" onclick="alert('You have been hacked!')">Win a prize!</a>`,
      headingId: 'heading',
      isDisabled: true,
      status: 'danger',
      isPromoted: true,
      isSoldOut: true,
      highlightColor: 'orange',
      headerSize: 60,
      headerStyleObject: {
        color: 'orange',
        fontSize: '60px',
        padding: '10px',
      },
      baseStyleObject: {
        fontSize: '50px',
        padding: '10px',
      },
      successStyleObject: {
        color: 'green',
        backgroundColor: 'lightgreen',
        border: '1px solid green',
        padding: '20px',
      },
      dangerStyleObject: {
        color: 'red',
        backgroundColor: 'salmon',
        border: '1px solid red',
      },
      num: '0',
      display: true,
      showElement: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.new {
  color: olivedrab;
}

.sold-out {
  color: crimson;
}
</style>
