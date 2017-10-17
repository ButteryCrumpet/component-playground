<template>
  <div class="hello">
    <codfiy hi="Decode this"></codfiy>
  </div>
</template>

<script>
import Codify from '@/components/codify';

export default {
  name: 'Base',
  data() {
    return {
      msg: 'Hiyooo',
    };
  },
  conponents: {
    Codify,
  },
};
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
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
