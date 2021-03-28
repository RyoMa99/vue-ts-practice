<template>
  <div class="home">
    <p> {{ greetText }} </p>
    <p>挨拶した回数 : {{count}}回</p>
    <p v-if="isRegulars">いつもありがとうございます</p>
    <Button :greet="greetText" @click="onButtonClicked" class="button">挨拶する</Button>
    <Button :greet="greetText" @click="onButtonClicked">こんにちは</Button>
    <ResetButton v-model="greetText"></ResetButton>
  </div>
</template>

<script lang="ts">
  import { Component, Vue, Watch } from 'vue-property-decorator';
  import Button from "@/components/Button.vue";
  import ResetButton from "@/components/ResetButton.vue";

  @Component({
    components: {
      Button,
      ResetButton
    },
  })
  export default class Home extends Vue {
    private count:number = 0;
    public greetText: string = "Hello";
    
    public get isRegulars(): boolean {

      return this.count >= 5;
    }

    @Watch("count")
    public countCanged(){
      if(this.count === 5){
        alert("常連です");
      }
    }

    public onButtonClicked(count: number){
      this.count = count;
      this.greetText = "こんにちは";
    }
  }
</script>
