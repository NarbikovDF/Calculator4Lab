<template>
    <Page  class="bg">
     <ActionBar title="Калькулятор"/>
         <GridLayout class="keyboard" columns="*, *, *, *" rows="*, *, *, *, *, *">
            <Label textWrap="true" class="result" v-model="result" row="0" col="0" colSpan="4"/>/>
            <Button  class="symbols" text="AC" @tap="del()" row="1" col="0" colSpan="3"/>
            <Button  class="symbols" text="/" @tap="input('/')" row="1" col="3"/>
            <Button  class="numbers" text="7" @tap="input('7')" row="2" col="0"/>
            <Button  class="numbers" text="8" @tap="input('8')" row="2" col="1"/>
            <Button  class="numbers" text="9" @tap="input('9')" row="2" col="2"/>
            <Button  class="symbols" text="*" @tap="input('*')" row="2" col="3"/>
            <Button  class="numbers" text="4" @tap="input('4')" row="3" col="0"/>
            <Button  class="numbers" text="5" @tap="input('5')" row="3" col="1"/>
            <Button  class="numbers" text="6" @tap="input('6')" row="3" col="2"/>
            <Button  class="symbols" text="-" @tap="input('-')" row="3" col="3"/>
            <Button  class="numbers" text="1" @tap="input('1')" row="4" col="0"/>
            <Button  class="numbers" text="2" @tap="input('2')" row="4" col="1"/>
            <Button  class="numbers" text="3" @tap="input('3')" row="4" col="2"/>
            <Button  class="symbols" text="+" @tap="input('+')" row="4" col="3"/>
            <Button  class="numbers" text="0" @tap="input('0')" row="5" col="0"/>
            <Button  class="numbers" text="." @tap="input('.')" row="5" col="1"/>
            <Button  class="equally" text="=" @tap="calc()" row="5" col="2" colSpan="2"/>
         </GridLayout>
    </Page>
</template>

<script >
   export default  {
    data() {
        return {
            result: '',
      }
    },
    methods:{
            input: function(char){
                this.result = this.result.toString();
                this.result += char;
            },
            calc: function(){
                try{
                    this.result = eval(this.result);
                    if (isNaN(this.result)) {
                        throw new Error();
                  }
                }
                catch{
                    this.result = 'invalid input';
                }
            },
            del: function(){
                this.result = '';
            }
    }
  }
</script>

<style scoped>
    .bg{
    background-color: #323433;
    }
    .result{
        font-size: 35px;
        overflow-wrap: break-word;
        color: #ffffff;
        text-align: right;
    }
    .numbers {
        background-color: #808080;
        color: white;
    }
    .symbols {
        background-color: #CD853F;
        color: white;
    }
    .equally {
        background-color: #4682B4;
        color: white;
    }
</style>
