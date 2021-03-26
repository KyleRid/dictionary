<template>
    <div class="row">
      <div class="row__shade">{{this.row.shade}}</div>
      <div class="row__words">
        <Word
          v-for="word in row.word_list"
          :key="word.id"
          :word="word"
          >{{word.lexeme}}</Word>
      </div>
      <div class="row__rows">
        <Row v-for="subrow in row.rows" :row="subrow" :key="subrow.row_id"></Row>
      </div>
        <!-- <Word type="verb" :transitive="true">Explostulate</Word>
        <Word type="verb" :transitive="true">Remonstrate</Word> -->
    </div>
</template>

<script>
import Word from './Word.vue'

export default {
  props: ['row'],
  name: 'Row',
  components: {
    Word,
  },
  mounted() {
    console.log('row', this.row);
  }
}
</script>

<style>
.row__shade {
  padding: 10px;
  font-size: 26px;
  text-transform: uppercase;
}

.row {
	/* background-color: rgb(65, 234, 136, 0.7); */
}

.row__words {
	display: flex;
	align-items: center;
	padding: 10px;
}

.row .row {
  padding-left: 50px;
}
</style>
