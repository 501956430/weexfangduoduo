<template>

    <div class="rootview">
        <!-- 头部 -->
        <div class="header" style="height: 356;background-color: brown">
            <image style="height: 356;width: 750;" :src="logoUrl"></image>
            <div style="position: absolute;left:0;right:0;bottom:40;flex-direction: row;height: 70">
                <div style="flex: 1;border-radius: 50;margin-right: 30;margin-left: 30;background-color: white;flex-direction:row;justify-content: flex-start;align-items: center">
                     <image :src="serachicon" style="width: 40;height: 35;margin-left: 30"></image>
                     <input placeholder="请输入小区名，楼盘，商圈名" style="color:gray;margin-left: 10;height:70;text-align:left;line-height:70;width: 560"/>
                 </div>
            </div>
            <!-- 定位 -->
            <div style="margin-left:30;position:absolute;top:30;left:0;right:0;border-radius: 50;background-color: dimgrey;width: 130;height: 60;align-items: center;justify-content: center">
                <text style="color: white">上海 v</text>
            </div>
        </div>

        <!-- 新版房 -->
        <div style="height: 300;flex-direction: row">


        </div>

    </div>
</template>

<script>
    var api = require("./api.js");
    export default {
        data: {
            serachicon:api.apiurl.path+'/ic_search_gray2.png',
            logoUrl: api.apiurl.path+'/bg_trade_area_hot_house_02.png',
            target: 'World',
        },
        methods: {
            update: function (e) {
                this.target = 'Weex'
                console.log('target:', this.target)
            }
        }
    }
</script>

<style>

</style>