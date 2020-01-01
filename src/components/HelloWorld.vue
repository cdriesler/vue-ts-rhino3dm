<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2 v-if="isLoaded">{{ pointCountMessage }}</h2>
    <h2 v-else>Loading rhino3dm...</h2>
    <button v-if="isLoaded" @click="addPoint"> add point </button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import rhino3dm, { Point3dList } from 'rhino3dm';

export default Vue.extend({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      pointList: {} as Point3dList,
      pointCount: 0,
      isLoaded: false,
    }
  },
  created() {
    rhino3dm().then(Rhino => {
      const pointList = new Rhino.Point3dList(0);

      pointList.add(1, 1, 1);
      pointList.add(2, 2, 2);

      this.pointList = pointList;
      this.pointCount = pointList.count;

      this.isLoaded = true;
    });
  },
  methods: {
    addPoint(): void {
      this.pointList.add(3,3,3);
      this.pointCount = this.pointList.count;

      // IMPORTANT: rhino3dm() must successfully resolve at least once before we can run the below methods synchronously
    }
  },
  computed: {
    pointCountMessage(): string {
      return `${this.pointCount} points in list!`
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
