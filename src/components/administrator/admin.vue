<template>

    <div id="admin" >
        <div id="header">
            <img src="../../assets/img/logo.jpg" class="logo">
            <p class="title">某高校教学管理系统</p>
            <input type="button" class="logout" value="退出登录" @click="logout">
            <p class="user_role">角色： 管理员</p>
            <p class="user_name">用户：{{ admin.username}}</p>
            <img src="../../assets/img/user_logo.png" class="user_logo">   
        </div>
        <div id="content">
            <div class="left-bar  color_darkgray">
                <ul>
                    
                    <li>
                        <img src="../../assets/img/icon_i.png" alt="">
                        <router-link to="/administrator/adminInfo">
                            <input type="button" value="个人信息" class="menu-item">
                        </router-link>
                    </li>
                
                    <li>
                        <img src="../../assets/img/icon_book.jpg" alt="">
                        <router-link to="/administrator/addCourse">
                            <input type="button" value="发布选课" class="menu-item">
                        </router-link>                  
                    </li>
                    <li>
                        <img src="../../assets/img/icon_half.png" alt="">
                        <router-link to="#">
                            <input type="button" value="发布课表" class="menu-item">
                        </router-link>                  
                    </li>
                    <li>
                        <img src="../../assets/img/icon_attention.png" alt="">
                        <router-link to="#">
                            <input type="button" value="发送通知" class="menu-item">
                        </router-link>                  
                    </li>
                    <li>
                        <img src="../../assets/img/icon_document.png" alt="">
                        <router-link to="/administrator/addDocument">
                            <input type="button" value="录入信息" class="menu-item">
                        </router-link>
                    </li>
                    <li>
                        <img src="../../assets/img/icon_people.jpg" alt="">
                        <router-link to="#">
                            <input type="button" value="注销教师/学生账号" class="menu-item">
                        </router-link>
                    </li>
                    <li>
                        <img src="../../assets/img/icon_key.jpg" alt="">
                        <router-link to="/administrator/changPassword">
                            <input type="button" value="修改密码" class="menu-item">
                        </router-link>
                    </li>
                </ul>
            </div>
            <div class="right-content">
                <div class="top-bar color_darkgray"></div>
                <div class="content_bck color_darkgray clearfix">
                    <div class="content_white_bck color_white clearfix">
                        <canvas id="left_circular" class="circular"></canvas>
                        <canvas id="right_circular" class="circular"></canvas>     
                        <div class="operation">
                            <router-view v-bind:getUser="admin" ></router-view>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    name:'Admin_content',
    data(){
        return{
            admin: {
                username: this.getUser.username,
                role: this.getUser.role,
                account: this.getUser.user_account
            },
        }
    },
    methods:{
        logout(){
            this.$emit("Logout",false);
            this.$router.push('/');           
        }
    },
    // 从APP组件中获取getUser传递过来的值user
    props:[
        'getUser'
    ],
    mounted(){

        //在帆布上画两个绿色的小圆点
        var l_canvas = document.getElementById("left_circular");
        var l_ctx = l_canvas.getContext('2d');

        var r_canvas = document.getElementById("right_circular");
        var r_ctx = r_canvas.getContext("2d");

        l_canvas.width = 30;
        l_canvas.height = 30;
        l_ctx.beginPath();
        l_ctx.arc(10, 10, 10, 0, Math.PI * 2, true);
        l_ctx.fillStyle = "#2E8B57";
        l_ctx.fill();
        l_ctx.strokeStyle = "#2E8B57";
        l_ctx.stroke();

        r_canvas.width = 30;
        r_canvas.height = 30;
        r_ctx.beginPath();
        r_ctx.arc(10, 10, 10, 0, Math.PI * 2, true);
        r_ctx.fillStyle = "#2E8B57";
        r_ctx.fill();
        r_ctx.strokeStyle = "#2E8B57";
        r_ctx.stroke();
    }
}
</script>

<style>
@import "../../assets/css/administrator.css";
@import "../../assets/css/color.css";

#content{
    position: relative;
    top: 0%;
}
</style>