<template>
  <div id="app">

    <div class="jumbotron jumbotron-fluid">
      <div class="container">
        <h1 class="display-4">Animações</h1>
        <p class="lead">Treinando transição/animação de elementos/components no Vue.</p>
      </div>
    </div>

    <div class="container">

      <button class="btn btn-primary mb-3" @click="mostrar =! mostrar">Alterar</button>

      <transition name="fade">

        <div class="alert alert-primary" v-if="mostrar">Animações no Vue com fade</div>

      </transition>

      <transition name="zoom">

        <div class="alert alert-primary" v-if="mostrar">Animações no Vue com zoom</div>

      </transition>   

       <transition 
       
        @before-enter="beforeEnter"
        @enter="enter"
        @after-enter="afterEnter"
        @enter-cancelled="enterCancelled"
        
        @beforeLeave="beforeLeave"
        @leave="leave"
        @afterLeave="afterLeave"
        @leaveCancelled="leaveCancelled">

        <div class="alert alert-primary" v-if="mostrar">Animações no Vue com JS</div>

      </transition> 
    
    </div>
  </div>
</template>

<script>
export default {
  data (){
    return {
      mostrar:true
    }   
  },
  methods:{
    beforeEnter(el){
      console.log('beforeEnter')
    },
    enter(el, done){
      console.log('enter')
      done()
    },
    afterEnter(el){
      console.log('afterEnter')
    },
    enterCancelled(el){
      console.log('enterCancelled')
    },

    beforeLeave(el){
      console.log('beforeLeave')
    },
    leave(el, done){
      console.log('leave')
      //enceramos a animação com função done.
      done()  
    },
    afterLeave(el){
      console.log('afterLeave')
    },
    leaveCancelled(el){
      console.log('leaveCancelled')
    }

  }
}
</script>

<style scoped>

  .zoom-enter, .zoom-leave-to{
    transform: scale(0);
  }

  .zoom-enter-active, .zoom-leave-active{
    transition: transform 0.5s;
  }

  .zoom-enter-to, .zoom-leave {
    transform: scale(1);
  }

  .fade-enter, .fade-leave-to{
    opacity: 0;
  }

  .fade-enter-active, .fade-leave-active{
    transition: opacity 1s;
  }

  .fade-enter-to, .fade-leave {
    opacity: 1;
  }

</style>