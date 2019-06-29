<template>
  <div :id="id">
    <template v-if="render">
      <slot />
    </template>
  </div>
</template>

<script>
// The checker
const checkIfInView = el => {
  const scroll = window.scrollY || window.pageYOffset;
  const boundsTop = el.getBoundingClientRect().top + scroll;

  const viewport = {
    top: scroll,
    bottom: scroll + window.innerHeight
  };

  const bounds = {
    top: boundsTop + 300,
    bottom: boundsTop + el.clientHeight
  };

  return (
    (bounds.bottom >= viewport.top && bounds.bottom <= viewport.bottom) ||
    (bounds.top <= viewport.bottom && bounds.top >= viewport.top)
  );
};
export default {
  name: 'vue-render-on-scroll',
  data() {
    return {
      id: null,
      render: false,
      listnerAdded: false
    };
  },
  methods: {
    addListner(elementId) {
      let vi = this;
      let interval = setInterval(() => {
        if ( document.readyState == 'complete' ) {
          const tester = document.querySelector(elementId);
          let check = checkIfInView(tester);
          if (check) {
            vi.render = true;
            clearInterval(interval);
          } else {
          }
        }
      }, 200);
    }
  },
  created() {
    let vi = this;
    vi.id =
      "renderOnScrollId" +
      Math.random()
        .toString(36)
        .substring(2, 15) +
      Math.random()
        .toString(36)
        .substring(2, 15);
    vi.addListner("#" + vi.id);
  }
};
</script>

<style>
</style>
