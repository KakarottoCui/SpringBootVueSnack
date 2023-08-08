<template>
    <div class="adminHome">
        <el-menu
//微信：egvh56ufy7hh ，QQ：821898835
import { mapMutations, mapState } from 'vuex';
export default {
    name: "AdminHome",
    data() {
      return {
        activeIndex: '1',
      };
    },
    computed:{
        ...mapState('user',['admin'])
    },
    watch:{
        admin(val){
            if(val==null){
                this.$router.push("/login")
            }
        }
    },
    methods:{
        exit(){
            sessionStorage.removeItem("admin");
            this.deleteAdmin();          
        },
        ...mapMutations('user',['deleteAdmin'])  //将this.deleteAdmin映射为this.$store.state.commit('user/deleteAdmin')
    }
}
</script>

<style scoped>
.adminHome{
    position: relative;
    background-color: #f4f4f4;
    color: #846e6e;
    min-height: 100vh;
}
a{  
    text-decoration: none;
    color: #fff;
}
.loginSpan{
    position: absolute;
    right: 70px;
    top: 15px;
}
</style>