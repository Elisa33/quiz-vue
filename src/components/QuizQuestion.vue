<template lang="">
    <div class="container">
        <div class="title">
            <h2>Question {{index +1}}/10</h2>
        </div>
        <div class="question">{{items[index]['question']}}</div>

        <div  :for="key" v-for="answer,key of items[index]['incorrect_answers']" :key="key">
            <div class="answer hover" 
            value="wrong" 
            @click="answered">
            {{answer }} 
            </div>
         </div>
        <div class="answer hover" 
        value="right"
        @click="answered">
            {{items[index]['correct_answer'] }}
        </div>
        <div class="info">
            <span class="datum">{{items[index]['category']}}</span>
            <span class="datum">Type: {{items[index]['type']}}</span>
            <span class="datum">Difficulty: {{items[index]['difficulty']}}</span>
        </div>
        <!-- popup -->
        <div class="popup" @click="next"  :class="{'invisible': popup == 0 }">
            <div class="check" :class="{'correct': popup == 1, 'incorrect': popup ==2}" v-show="index < 9">{{icon}}</div>
            <button class="next" v-show="index < 9">Next</button>
        </div>
        <div class="finish" v-show="index == 9">
            <span>Correct Answers:</span>
            <span>{{correctA}}/10</span>
            <button class="reset" @click="reset">Reset</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'QuizQuestion',
    props:['data'],
    data(){
    
    return{
      index: 0,
      selected:'',
      correctA:0,
      popup: 0,
      icon: '',
      
      items: this.data
          }
  },
     methods:{
        unescape(string) {
            this.icon = document.querySelector(".check");
            this.icon.innerHTML = string;
        },
        answered(e){
        this.selected = e.target.attributes.value.value;

        if(this.selected == "right"){
            this.correctA++;
            this.popup = 1;
            this.icon = this.unescape("&check;")
        }else{
            this.popup = 2;
            this.icon = this.unescape("&#x2E3;");
        }

        },
        popreset(){
            this.popup = 0;
        },
        next(){
            this.index++;
            this.popup = 0;
        },
        reset(){
            this.index = 0;
            this.correctA = 0;
        }
  }
}
</script>

<style lang="">


    
</style>