<template>
<div class="word" @click="toggleMeaning">
    <div class="word__meta">
        <div class="word__meta-item word-type"
            :class="{
                'word-type_verb': this.word.type === 'verb',
                'word-type_noun': this.word.type === 'noun',
                }">{{this.word.type || 'no type'}}</div>
        <div class="word__meta-item word__meta-item_intransitive" v-if="word.intransitive">
            I
        </div>
        <div class="word__meta-item word__meta-item_transitive" v-if="word.transitive">
            T
        </div>

        <div class="word__meta-item word-style">
            <div class="word-style__formal"  v-if="word.formal">
            F
            </div>
            <div class="word-style__formal"  v-if="word.informal">
                Inf
            </div>
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
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
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
	/* border: 1px solid #eaeaea; */
	margin: 0 5px;
	font-size: 30px;
    flex-direction: column;
    /* background-color: rgb(65, 234, 136, 0.55); */
    box-shadow: 0px 0px 2px 0px rgba(0,0,0,0.75);
    border-radius: 15px;
    transition: 0.25s ease-in-out all;
}

.word:hover {
    cursor: pointer;
    user-select: none;
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
    transition: 0.25s ease-in-out all;
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

.word__meta-item_intransitive {
    padding: 2px 5px;
    border-radius: 5px;
    background-color: #f3f30e;
}

.word__meta-item_transitive {
    padding: 2px 5px;
    border-radius: 5px;
    background-color: #53dc51;
}

.word-type_verb {
    background: #ff6d6d;
    /* color: #ff6d6d; */
    color: black;
    padding: 2px 5px;
    border-radius: 5px;
}

.word-type_noun {
    background-color: rgb(156, 145, 251);
}

.word-style {
    margin-left: auto;
}

.word-style__formal {
    padding: 2px 5px;
    border-radius: 5px;
    background-color: #f3f30e;
}

/* .word__meta-item span { */
    /* font-family: sans-serif; */
/* } */
</style>
