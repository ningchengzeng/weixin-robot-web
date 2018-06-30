<template>
    <div>
        <mu-appbar color="primary" title="忘记密码">
          <mu-button slot="left" icon @click="goBack">
            <mu-icon value="keyboard_arrow_left"></mu-icon>
          </mu-button>
          <mu-button slot="right" flat  @click="submit">
              <mu-icon value="done"></mu-icon>
          </mu-button>
        </mu-appbar>
        <mu-container style="content">
            <br/>
            <hr/>
            <br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/><br/>
            <hr/>
        </mu-container>
    </div>
</template>

<script>
export default {
  name: "forget",
  methods: {
    goBack (){
        this.$router.push('/reg')
    }
  }
}
</script>

<style>
.content{
  flex: 1;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
</style>
