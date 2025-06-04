<template>
    <div id="contact">
      <h2>Contact</h2>
      <p>Tel : {{ formattedPhone }}</p>
      <p>Email : {{ email }}</p>
    </div>  
    <div id="gitHub">
      <h2>GitHub</h2>
      <p><a :href="gitUrl" target="_blank" @click="gitClicks">Git 으로 이동</a> (총 방문자 수: {{ visitCounter }})</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ContactMe',
    data() {
      return {
        phone: "01012345678",
        email: "hongMan@inga.edu",
        gitUrl: "https://github.com/leeyeoninha/inProg",
        visitCounter: 0,
      };
    },
    computed: {
      formattedPhone() {
        if (this.phone.length === 11) {
          return this.phone.replace(/(\d{3})(\d{4})(\d{4})/, '$1-$2-$3');
        } else if (this.phone.length === 10) {
          return this.phone.replace(/(\d{3})(\d{3})(\d{4})/, '$1-$2-$3');
        } else {
          return this.phone;
        }
      }
    },
    methods: {
      gitClicks() {
        this.visitCounter++;
      }
    }
  };
  </script>
  
  <style scoped>
  div {
    text-align: left;
    border-bottom: 1px solid gray;
    margin-bottom: 10px;
    height: 180px;
  }
  #contact {
    width: 50%;
    float: left;
  }
  #gitHub {
    width: 50%;
    float: right;
  }
  a {
    text-decoration: none;
  }
  </style>
  