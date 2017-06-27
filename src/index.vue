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
            <div style="margin-left:30;position:absolute;top:30;left:0;right:0;border-radius: 50;background-color: dimgrey;width: 130;height: 60;flex-direction:row;align-items: center;justify-content: center">
                <text style="color: white">上海</text>
                <image style="height: 50;width: 50;" :src="next"></image>
            </div>
        </div>

        <!-- 新版房 -->
        <div style="height: 350;">
            <div  style="height: 150;flex-direction: row;margin-top: 20;margin-left: 20;margin-right: 20;justify-content: center;align-items: center;">
                <div v-for="itm in itemList" style="flex: 1;align-items: center">
                    <image style="height: 88;width: 88" :src="itm.icon"></image>
                    <text style="margin-top: 25;font-size: 25">{{itm.title}}</text>
                </div>
            </div>
            <!-- 房市头条-->
            <div style="margin-top: 50;flex-direction: row;margin-left: 20;justify-content: center;align-items: center">
                <div style="flex: 0.2;border-right-width: 1;border-right-color:#e4e4e4;align-items: center">
                    <image style="height: 80;width: 80" :src="fangshitout"></image>
                </div>
                <div style="flex: 1;margin-left: 10">
                        <marquee :step="marquee.height * 2" :count="marquee.list.length" :interval="marquee.interval" :duration="marquee.duration" :style="{height: marquee.height * 2,paddingLeft: 10,paddingRight: 10}">
                            <div v-for="(item,i) in marquee.list" :key="i" :style="{height: marquee.height * marquee.length,paddingTop: marquee.height * 0.5,paddingBottom: marquee.height * 0.5,overflow: 'hidden'}">
                                <text :style="{height: marquee.height,color: 'rgb(60, 118, 61)',fontSize: 25}">{{item.text}}</text>
                            </div>
                        </marquee>
                </div>
            </div>
        </div>
        <!-- 分割线 -->
        <div style="background-color: #f9f9f9;height: 25"></div>

        <!-- 产品 -->
        <div style="height: 800;background-color: white">
            <div style="flex: 1;margin: 15" >

                <div style="flex-direction: row;height: 200">
                    <div style="flex: 1;flex-direction: row;margin-right:15;margin-bottom:15;background-color: #FAFAFA;justify-content: center;align-items: center">
                        <div>
                            <text style="color: #5D5C5C">旅居地产</text>
                            <text style="color: #FC908C;font-size: 25">首付6万起</text>
                        </div>
                         <image style="width: 150;height: 150":src="project"/>
                    </div>
                    <div style="flex: 1;flex-direction: row;margin-bottom:15;background-color: #FAFAFA;justify-content: center;align-items: center">
                        <div>
                            <text style="color: #5D5C5C">350万新房</text>
                            <text style="color: #B6B6B5;font-size: 25">刚需安家首选</text>
                        </div>
                        <image style="width: 150;height: 150":src="project"/>
                    </div>
                </div>
                <!-- 开盘-->
                <div style="flex-direction: row;height: 200;">
                    <div v-for="(fang,i) in loipang" style="flex: 1;background-color: #FAFAFA;margin-right: 10;margin-top: 10">
                        <div style="justify-content: center;align-items: center;flex-direction: column;">
                            <text style="color: #5D5C5C">{{fang.title}}</text>
                            <text style="font-size:25;color: #AEB0AD;margin-top: 10;margin-bottom: 30">{{fang.text}}</text>
                            <image style="width: 140;height: 140;border-radius: 100" :src="fang.icon"/>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    var api = require("./api.js");
    module.exports = {
        data: {
            next:api.apiurl.path+'/next.png',
            loipang:[{title:'独家返现',text:'返现特惠楼盘',icon:api.apiurl.path+'/342.jpg'},{title:'最新开盘',text:'抢房要乘早',icon:api.apiurl.path+'/1152435847.jpg'}
            ,{title:'210万起',text:'低总价地铁房',icon:api.apiurl.path+'/dgdf4.jpg'},{title:'首付22万起',text:'自住收租双赢',icon:api.apiurl.path+'/3454545.jpg'}],
            project:api.apiurl.path+'/ic_negotiationic_price.png',
            loupan:api.apiurl.path+'/342.jpg',
            marquee: {
                height: 40,
                duration: 500,
                interval: 1000,
                list: [
                    {text: '三个因素决定:房贷利率只升不降! 炒房客该歇菜了'},
                    {text: '北京的中介都卖小城市的房子了能不能买认准两点'},
                    {text: '坐收张江、迪士尼渔翁之利 浦东外环房价将达7万²'},
                    {text: '贷款买二手房 这4比钱你都是准备好了么？'},
                    {text: '为啥总有人在房价大涨后抢房?'},
                    {text: '抓住买房的最好时机,为你身下几十万'}
                ]
            },
            fangshitout:api.apiurl.path+'/ic_house_head_lines.png',
            xinfang:api.apiurl.path+'/ic_menu_01.png',
            serachicon:api.apiurl.path+'/ic_search_gray2.png',
            logoUrl: api.apiurl.path+'/bg_trade_area_hot_house_02.png',
            itemList:[{title:"新房",icon:api.apiurl.path+'/ic_menu_01.png'},{title:"二手房",icon:api.apiurl.path+'/ic_menu_02.png'},
                {title:"地图找房",icon:api.apiurl.path+'/ic_find_by_map.png'},{title:"贷款",icon:api.apiurl.path+'/ic_menu_04.png'},{title:"暖城公寓",icon:api.apiurl.path+'/ic_menu_08.png'}]
        },
        components: {
            marquee: require('./include/marquee.vue')
        },
        methods: {
        }
    }
</script>

<style>

</style>