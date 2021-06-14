<template>
  <div >
    <QuizQuestion :data="data"/>
  </div>
</template>

<script>
import QuizQuestion from './QuizQuestion.vue'
import datos from "../data.json"
export default {

  components: {
      QuizQuestion
  },
  data(){
    return{
      data: datos
          }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5a5a5a;
  margin-top: 60px;
}
body{
  background: #efefef;

}
h1{
    width: 100%;
}
h2{
    color:#fff;
}
.container{
    position: relative;
    display: flex;
    flex-direction: column;
    max-width: 600px;
    background: #fff;
    margin: 1rem auto;
    border-radius: 20px;
    overflow: hidden;
}
@media (max-width: 640px) {
  .container {
    max-width: 500px;
  }
}
.title{
    background: #5acfc9;
}
.info{
    background: #5acfc9;
    padding: 1rem 2rem;
    color: white;
    display: flex;
    justify-content: space-between;
    margin-top: 1.5rem;
}
.question{
  padding: 1.5rem 2rem;
  font-size: 1.2rem;
}
.options{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.answer{
  background: #fa9f42;
  padding: 0.8rem 2rem;
  margin: 0.8rem 2rem;
  border-radius: 5px;
  color: #fff;
  cursor: pointer;
}
.hover:hover{
    background: #5acfc9;
}
.next{
  background: #5acfc9;
  padding: 0.5rem 2rem;
  border-radius: 50px;
  margin: 10px;
  border: 1px solid #5acfc9;
  color: #fff;
  font-size: 1.2rem;
  cursor: pointer;
}
.reset{
  background: #fff;
  padding: 0.5rem 2rem;
  border-radius: 50px;
  margin: 10px;
  border: 1px solid #5acfc9;
  color: #5acfc9;
  font-size: 1.2rem;
  cursor: pointer;
}

.corrects{
    display: flex;
    justify-content: center;
    padding: 1rem 0.5rem;
    font-size: 1.2rem;
    color: #fff;
    background: #5acfc9;
    margin-top: 1.5rem;
}
.popup{
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    
    align-items: center;
    position: fixed; 
    z-index: 1; 
    left: 0;
    top: 0;
    width: 100%; 
    height: 100%; 
    overflow: auto; 
    background-color: rgb(255, 255, 255); 
    background-color: rgba(255, 255, 255, 0.8); 
}
.check{
    width: 200px;
    height: 200px;
    border-radius: 50%;
    margin-top: 12rem;
    color: #fff;
    background: #8ad879;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    font-size: 5rem;
    cursor: pointer;
}
.invisible{
    visibility: hidden;
}
.correct{
    background: #8ad879;
    visibility: visible;
}
.incorrect{
    background: #f3533a;
    visibility: visible;
}
.finish{
    position: absolute;
    background: #5acfc9;
    visibility: visible;
    width: 100%;
    height: 100%;
    color: #fff;
    display: flex;
    border-radius: 30px;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    font-size: 2.5rem;
}


</style>
