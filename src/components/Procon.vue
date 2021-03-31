<template>
      <input class="mainInput" ref="focusMe" type="text" v-model="inputValue">
  <div class="container">
      <div class="prosBox box">
        <button class='addButt' @click="addPro"><h2>+</h2></button>
        <h1 v-if="pros.length === 0">Pros?</h1>
        <!-- <h1 v-else>Pros:</h1> -->
        <ul>
            <li :id="index" @click="reset" ref="liRef" class="liItem" v-for="(value, index) in pros" v-bind:key="value" >
                <div class="buttBox">
                <button @click="makeSmall" class= 'lilButt'>-</button>
                <button @click="makeBig" class='lilButt'>+</button>
                </div>
                <p>{{ value }}</p>
                <button class="del" @click="deletePros">X</button>
            </li>
        </ul>
      </div>
      <div class="consBox box">
        <button class="addButt red" @click="addCon"><h2>+</h2></button>
        <h1 v-if="cons.length === 0">Cons?</h1>
        <!-- <h1 v-else>Cons:</h1> -->
        <ul>
            <li :id="index" @click="reset" ref="liRef" class="liItem" v-for="(value, index) in cons" v-bind:key="value" >
                <div class="buttBox">
                <button @click="makeSmall" class= 'lilButt c'>-</button>
                <button @click="makeBig" class='lilButt c'>+</button>
                </div>
                <p>{{ value }}</p>
                <button class="del" @click="deleteCons">X</button>
            </li>
        </ul>
      </div>
  </div>
</template>

<script>

export default {
    name: "Procon",
    data() {
        return {
            pros: [],
            cons: [],
            inputValue: ''
        }
    },
    mounted() {
        this.$nextTick(() => this.$refs.focusMe.focus())
    },
    methods: {
        addPro() {
            if (this.inputValue != '') {
                this.pros.push(this.inputValue);
            this.inputValue = '';
            this.$refs.focusMe.focus();
            }
        },
        addCon() {
            if (this.inputValue != '') {
                this.cons.push(this.inputValue)
            this.inputValue = '';
            this.$refs.focusMe.focus();
                }
        },
        makeSmall(e) {
            if( e.target.parentNode.parentNode.classList.contains('bigger')) {
            e.target.parentNode.parentNode.classList.remove('bigger');
            }
            e.target.parentNode.parentNode.classList.add('smaller');
        },
        makeBig(e) {
            if( e.target.parentNode.parentNode.classList.contains('smaller')) {
            e.target.parentNode.parentNode.classList.remove('smaller');
            }
            e.target.parentNode.parentNode.classList.add('bigger');
        },
        deletePros(e) {
            var index = (e.target.parentNode.id);
            this.pros.splice(index, 1);
        },
        deleteCons(e) {
            var index = (e.target.parentNode.id);
            this.cons.splice(index, 1);

        },
        reset(e) {
            if( e.target.classList.contains('smaller')) {
            e.target.classList.remove('smaller');
            } else if( e.target.classList.contains('bigger')) {
                e.target.classList.remove('bigger');
            } else if (e.target.parentNode.classList.contains('smaller')) {
                e.target.parentNode.classList.remove('smaller');
            } else if (e.target.parentNode.classList.contains('bigger')) {
                e.target.parentNode.classList.remove('bigger');

        }

    }
}
}

</script>

<style scoped>
    .container{
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        width: 90%;
        margin: auto;
    }
    .box{
        display:flex;
        flex-direction: column;
        width: 50%;
        text-align: center;
    }
    .mainInput {
        height: 10vh;
        padding: 0rem 1rem;
        margin: 2rem;
        width: 50%;
        background-color: rgb(214, 230, 231);
        font-size: 2em;
    }
    ul {
        margin-block-start: 1em;
    margin-block-end: 0;
    margin-inline-start: 0;
    margin-inline-end: 1em;
    padding-inline-start: 0px;
        list-style: none;
    }
    h2{
        font-size: 1.5em;
    }
    
    .liItem {
        font-size: 1.7rem;
        color: white;
        margin-top: 12px;
        display: flex;
        height: 3em;
        justify-content: space-between;
        overflow: hidden;
    }
    .liItem p {
        width: 100%;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        hyphens: auto;
        margin: auto;
        padding: auto;
    }
    .liItem p:hover {
        width: 90%;
        overflow: visible;
        overflow-wrap:break-word;
        white-space: normal;
        background-color: rgb(90, 90, 90);
        z-index: 3;
        padding: 10px;
    }
    .liItem:hover {
        overflow: visible;
    }
    .prosBox li {
        background-color: rgb(36, 114, 108);
    }
    .consBox li {
        background-color: rgb(138, 58, 44);
    }
    .smaller {
        height: 1.3em;
    }
    .bigger {
        max-height: none;
        height: 5.5em;
    }
    .addButt{
        border: none;
        background-color: rgb(129, 204, 174);
        width: 3.8rem;
        align-self: center;
        border-radius: 2.1rem;
    }
    .red{
        background-color: rgb(241, 144, 144);
    }
    .buttBox {
        margin: 0;
        padding: 0;
        display: flex;
        flex-direction: column;
        height: 100%;
    }
    .lilButt {
        height: 100%;
        position: relative;
        float: left;
        /* left: -3.5rem; */
        border: none;
        background-color: black;
        color: white;
        font-size: .8em;
    }
    .del {
        position: relative;
        right: 0;
        height: 1.8em;
        border: none;

    }
    .lilButt.c{
        position: relative;
        left: auto;
        /* right: 0; */
    }

    @media only screen and (max-width: 800px) {
    
        .container{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 100vw;
        margin: 0;
    }
        input {
            margin: .3em;
            margin-top: 0
        }
        h1 {
            margin: 0;
        }
        /* .addButt{
            width: 4rem;    
        } */
    
    
    }

    

</style>
