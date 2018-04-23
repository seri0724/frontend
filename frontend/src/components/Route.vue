<template>
  <div id="route" style="width:450px; display:inline-block;">
    <br></br>
      <h1>추천코스</h1>
    <br></br>
      <v-form v-model="valid" ref="form">
         <v-checkbox label="김가네" v-model="placename1"></v-checkbox>
         <v-checkbox label="모스버거" v-model="placename2"></v-checkbox>
         <v-checkbox label="미스포아이" v-model="placename3"></v-checkbox>
         <v-checkbox label="비트교육센터" v-model="placename4"></v-checkbox>
        <v-btn @click="submit" :disabled="!valid">확인</v-btn>
      </v-form>
    <pre>{{$data}}</pre>
  </div>
</template>

<script>
  export default {
    data: () => ({
      valid:false,
      // url_id : 21037816
      array:[],
      placename1:'21037816',
      placename2:'13480693',
      placename3:'36022489',
      placename4:'19500744'
    }),
    methods: {
      submit () {
        if(this.$refs.form.validate()) {
          this.$axios.post('/api/course/store', {
            placename1:this.placename1,
            placename2:this.placename2,
            placename3:this.placename3,
            placename4:this.placename4
          }) .then((response) => {
              console.log('routeOK')
              this.result = response.data
              console.log(this.result)
          })
        }
      }
    }
  }
</script>
