<template>
  <button @click="onClick" class="primary"> <!-- 親コンポーネントでclassを設定していたらマージされる -->
    <slot></slot>
  </button>
</template>

<script lang="ts">
  import { Component, Emit, Prop, Vue } from "vue-property-decorator";

  @Component
  export default class Button extends Vue {
    private count: number = 0;

    @Prop()
    public greet?: string; // ?は設定されないことも示唆 !で絶対設定

    @Emit()
    public click(count: number){
    }

    public onClick(){
      alert(this.greet);
      this.count++;
      this.click(this.count);
    }

  }
</script>