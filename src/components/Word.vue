<template>
<div class="word" @click="toggleMeaning">
    <div class="word__meta">
        <div class="word__meta-item word__type">{{this.word.type}}</div>
        <div class="word__meta-item word__transitivity">
            <span class="word__intransitive" v-if="word.intransitive">I</span>
            <span class="word__transitive" v-if="word.transitive">T</span>
            <span class="word__formal" v-if="word.formal">F</span>
        </div>
    </div>
    <slot></slot>
    <div class="word__shade">{{this.word.shade}}</div>
</div>
<div class="word-meaning" :class="{'show': showMeaning}">
    <div class="word-meaning__title">Meaning
        <button class="word-meaning__close" @click="toggleMeaning">
            <i class="fas fa-times"></i>
        </button>
    </div>
    <div class="word-meaning__body">
        <p class="word-meaning__entry" v-for="(meaning, key) in word.meaning" :key="key">{{++key}}: {{meaning}}</p>
    </div>
</div>
</template>

<script>
// import vClickOutside from 'v-click-outside'
export default {
    props: [
        'type',
        'transitive',
        'intransitive',
        'word',
    ],
    directives: {
        //  clickOutside: vClickOutside.directive
    },
    name: 'Word',
    data() {
        return {
            showMeaning: false,
        }
    },
    methods: {
        toggleMeaning() {
            this.showMeaning = !this.showMeaning;
        },
        closeMeaning() {
            console.log('close meaning');
            this.showMeaning = false;
        }
    },
    mounted() {
        console.log(this.word);
    }
}
</script>

<style>
.word__shade {
    font-size: 16px;
    font-weight: bold;
    /* font-family: sans-serif; */
    margin-top: 5px;
}

.word-meaning {
    position: absolute;
    visibility: hidden;
    opacity: 0;
    transition: 0.25s ease-in-out all;
    padding: 20px;
    background: white;
    border-radius: 10px;
    /* bottom: -100px; */
    max-width: 1000px;
    min-width: 545px;
    z-index: 1;
    top: 50%;
    left: 50%;
    transform: translate(-50%);
    box-shadow: 0px 0px 13px 0px rgba(0,0,0,0.75);
}

.word-meaning__close {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: transparent;
    border: none;
    font-size: 20px;
    transition: 0.25s ease-in-out all;
}

.word-meaning__entry {
    margin-top: 0;
    margin-bottom: 10px;
}

.word-meaning__close:hover {
    cursor: pointer;
    color: rgb(65, 234, 136, 0.7);
    transition: 0.25s ease-in-out all;

}

.word-meaning.show {
    visibility: visible;
    opacity: 1;
    transition: 0.25s ease-in-out all;
}

.word-meaning__title {
    font-size: 20px;
    text-transform: uppercase;
    text-align: center;
    /* font-family: sans-serif; */
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
}

.word-meaning__body {
    padding: 10px;
    background: white;
    border-radius: 10px;
    bottom: -100px;
}

.word {
	display: flex;
	position: relative;
	padding: 25px 10px 10px;
	border: 1px solid #eaeaea;
	margin: 0 5px;
	font-size: 30px;
    flex-direction: column;
}

.word:hover {
    cursor: pointer;
    user-select: none;
}

.word__meta {
    display: flex;
    position: absolute;
    top: 10px;
    text-transform: uppercase;
    font-weight: bold;
    margin-bottom: 5px;
    font-size: 14px;
}

.word__meta-item {
    margin-right: 5px;
    /* font-family: sans-serif; */
}

/* .word__meta-item span { */
    /* font-family: sans-serif; */
/* } */
</style>
