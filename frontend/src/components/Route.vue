<template>
  <div id="route" style="width:450px; display:inline-block;">
    <br></br>
      <h1>추천코스</h1>
    <br></br>
      <v-form v-model="valid" ref="form">
        <!-- <v-text-field label="" v-model="placename1" :rules="placename1Rules"></v-text-field> -->
         <v-checkbox label="강남역" v-model="placename1" :value=""></v-checkbox>
        <!-- <v-text-field label="" v-model="placename2" :rules="placename2Rules"></v-text-field> -->
         <v-checkbox label="비트교육센터" v-model="placename2" :value=""></v-checkbox>
        <v-btn @click="submit" :disabled="!valid">확인</v-btn>
      </v-form>
    <pre>{{$data}}</pre>
  </div>
</template>

<script>
  export default {
    data: () => ({
      valid:false,
      // placename1:'강남미술관',
      // placename1Rules: [
      //
      // ],
      // placename2:'비트교육센터',
      // placename2Rules: [
      //
      // ],
      placename1:'',
      placename2:''
    }),
    methods: {
      submit () {
        if(this.$refs.form.validate()) {
          this.$axios.post('/api/course/store', {
            placename1:this.placename1,
            placename2:this.placename2
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
