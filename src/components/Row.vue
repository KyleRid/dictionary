<template>
    <div class="row">
        <Word type="verb" :transitive="true">Complain</Word>
        <Word type="verb" :transitive="true">Explostulate</Word>
        <Word type="verb" :transitive="true">Remonstrate</Word>
    </div>
</template>

<script>
import Word from './Word.vue'

export default {
  name: 'Row',
  components: {
    Word,
  }
}
</script>

<style>
.row {
	display: flex;
	align-items: center;
	padding: 10px;
	background-color: rgb(65, 234, 136, 0.7);
}
</style>
