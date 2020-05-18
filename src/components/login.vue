<template>
    <div class="login_container">
        <div class="login_box">
            <div class="left_box">
                <img class="heart_logo" src="../assets/images/heart.png" alt="heart logo" />
                <div class="msg">
                    <p>梦想</p>
                    <p>从这里出发</p>
                </div>
            </div>
            <div class="right_box"></div>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="less" scoped>
.login_container{
    width:100%;
    height:100%;
    background-image: url('../assets/images/login-bg.png');
    background-size: cover;
    position: relative;
    .login_box{
        width:830px;
        height:350px;
        position: absolute;
        top:0;
        left:0;
        bottom:0;
        right:0;
        margin:auto;
        display: flex;
        .left_box{
            width:350px;
            height:100%;
            background-color: #409EFF;
            z-index:200;
            border-radius:10px;
            display: flex;
            .heart_logo{
                width:200px;
                height:200px;
                margin-top:50px;
            }
            .msg{
                display: flex;
                flex-direction: column;
                color:#fff;
                margin-top:160px;
                p{
                    line-height: 30px;
                }
            }
        }
        .right_box{
            width:500px;
            height:100%;
            background-color: #fff;
            border-radius:10px;
            margin-left:-20px;
        }
    }
}
</style>