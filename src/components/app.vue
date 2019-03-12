<template>
    <div class="app">
        <div class="index1">
            <div class="head">
                <img class="down" v-show="!is" src="../assets/app/down.png" @click="is=true"/>
                <img class="down" v-show="is" src="../assets/app/x.png" style="width: 16px;margin-top: 22px;"
                     @click="is=false"/>
                <img class="logo" @click="scroll(0)" src="../assets/logo.png"/>
            </div>
            <img class="index_logo" :src="img($store.state.messages.index.logo[1].src)"/>
            <div class="index_down" v-show="is">
                <router-link :key="index" :to="item.href" tag="div" @click="hrefLink(item)"
                             v-for="(item,index) in $store.state.messages.index.title">
                    {{item.txt}}
                </router-link>
                <router-link class="head_item" key="310" to="/validators" tag="div">Validators</router-link>
            </div>
        </div>
        <div class="about">
            <div class="index_title" id="#about">
                {{$store.state.messages.about.title}}
                <div></div>
            </div>
            <div class="about_txt">
                <div v-for="item in $store.state.messages.about.txt">
                   <span v-html="item"></span>
                </div>
            </div>
            <img :src="img($store.state.messages.about.img)"/>
        </div>
        <div class="core" id="#core">
            <img class="core_img" src="../assets/app/core.jpg"/>
            <div class="core_title">
                {{$store.state.messages.core.title}}
                <div></div>
            </div>
            <div class="core_txt">
                <div class="core_txt_title">
                    <span class="core_txt_title_info">{{$store.state.messages.core.secondaryTitle}}</span>
                </div>
                <p>{{$store.state.messages.core.infomation}}</p>
                <div class="core_txt_title">
                    <span class="core_txt_title_info_bottom">{{$store.state.messages.core.technologyTitle}}</span>
                </div>
                <p>{{$store.state.messages.core.technologyInfomation}}</p>
            </div>
            <div class="irisnet_info_container">
                <div class="mobilebanner_img_container">
                    <img src="../../public/mobilebanner.jpg">
                </div>
                <div>
                    <p class="irisnet_title">{{$store.state.messages.irisnetInfo.title}}</p>
                    <p class="irisnet_info">{{$store.state.messages.irisnetInfo.irisnetService}}</p>
                    <p class="irisnet_info">{{$store.state.messages.irisnetInfo.irisnetTechnology}}</p>
                    <div class="irisnet_link_btn">
                        <a href="https://www.irisnetwork.cn/" target="_blank">
                            <span>{{$store.state.messages.irisnetInfo.irisnetWebsiteUrl}}</span>
                        </a>
                    </div>
                <p class="irisnet_title">{{$store.state.messages.irisnetInfo.title}}</p>
                <p class="irisnet_info">{{$store.state.messages.irisnetInfo.irisnetInfoItem}}</p>
                <p class="irisnet_info">{{$store.state.messages.irisnetInfo.irisnetInfoIntroduce}}</p>
                <div class="irisnet_link_btn">
                    <a href="https://www.irisnet.org/" target="_blank">
                        <span>{{$store.state.messages.irisnetInfo.irisnetWebsiteUrl}}</span>
                    </a>
                </div>
            </div>
            <div class="index_title" id="#product">
                {{$store.state.messages.product.title}}
                <div></div>
            </div>

            <div class="product" v-for="item in $store.state.messages.product.txt">
                <img :src="img(item.img)"/>
                <div class="product_title">
                    {{item.title}}
                </div>
                <div class="product_title1" v-html="item.title1"></div>
                <div class="product_txt">
                    <div v-html="item.txt"></div>
                </div>
            </div>
        </div>
        <div class="dynamic">
            <img src="../assets/app/dynamic.jpg" style="width: 100%"/>
            <div class="index_title" id="#dynamic">
                {{$store.state.messages.dynamic.title}}
                <div></div>
            </div>
            <a class="dynamic_a" :href="$store.state.messages.dynamic.txt[item-1].href" target="_blank"
               v-for="item in 4">
                <div class="dynamic_left">
                    <div class="pr">
                        <div class="day">
                            <div>{{$store.state.messages.dynamic.txt[item-1].month}}</div>
                            <div>{{$store.state.messages.dynamic.txt[item-1].day}}</div>
                        </div>
                        <img src="../assets/app/day.jpg"/>
                    </div>
                    <div class="pr">
                        <div class="year">
                            <div>{{$store.state.messages.dynamic.txt[item-1].year}}</div>
                        </div>
                        <img src="../assets/app/year.jpg"/>
                    </div>
                </div>
                <div class="dynamic_txt">
                    {{$store.state.messages.dynamic.txt[item-1].title}}
                </div>
                <div class="dynamic_text">
                    {{$store.state.messages.dynamic.txt[item-1].txt}}
                    <div>...</div>
                </div>
            </a>
        </div>
        <div class="partner">
            <div class="index_title" id="#partner">
                {{$store.state.messages.partner.title}}
                <div></div>
            </div>
            <div class="partner_div">
                <div>
                    <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[0]">
                        <img :src="item.img"/>
                    </a>
                </div>
                <div>
                    <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[1]">
                        <img :src="item.img"/>
                    </a>
                </div>
                <div>
                    <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[2]">
                        <img :src="item.img"/>
                    </a>
                </div>
            </div>
            <div class="validator">
                <img src="../assets/app/cosmos.jpg"/>
                <div class="validator_warp">
                    <div v-for="(item,index) in $store.state.messages.validator.txt" :class="{'div':index==2}" :key="index">
                        {{ item}}
                    </div>
                </div>
                <div class="validator_btn">
                    <a :href="$store.state.messages.validator.btnHref" target="_blank">
                        {{ $store.state.messages.validator.btnText}}
                    </a>
                </div>
            </div>
            <div class="index_title index_title1" id="#contact">
                {{$store.state.messages.contact.title}}
                <div></div>
            </div>
            <div class="address">
                {{$store.state.messages.contact.address.val}}
            </div>
            <div class="zip_code">
                {{$store.state.messages.contact.zip_code.txt}}： {{$store.state.messages.contact.zip_code.val}}
            </div>
            <div class="mailbox">
                {{$store.state.messages.contact.mailbox.txt}}：{{$store.state.messages.contact.mailbox.val}}
            </div>
            <div class="qr">
                <img src="../assets/qr.png"/>
                <div>
                    Bianjie_AI
                </div>
            </div>
        </div>
        <div class="copyright">
            版权所有 © 2017上海边界智能科技有限公司 <a href="http://www.miitbeian.gov.cn" target="_blank">沪ICP备17020986号</a>
        </div>
    </div>
</template>

<script>
    let FastClick = '';
    if (process.env.VUE_ENV === 'client') {
        FastClick = require('fastclick')
    }
    export default {
        name: "app",
        data() {
            return {
                is: false
            }
        },
        methods: {
            img(src) {
                src = src.split('public/')[0] + 'public/app/' + src.split('public/')[1];
                return src;
            },
            roll() {
                this.is = false;
                if (document.getElementById(this.$route.hash)) {
                    this.scroll(document.getElementById(this.$route.hash).offsetTop - 80)
                }
            },
            scroll(top) {
                $('body,html').animate({
                        scrollTop: top
                    }, 500
                );
            },
            isClick() {
                this.is = true;
            }
        },
        mounted() {
            this.$store.state.messages.index.title = this.$store.state.messages.index.title.reverse()
            this.$store.state.messages.index.title.forEach(v => {
                v.href = 'app' + v.href.split('/')[1];
            })
            this.roll();
            if ('addEventListener' in document) {
                document.addEventListener('DOMContentLoaded', function () {
                    FastClick.attach(document.body);
                }, false);
            }
        },
        watch: {
            '$route': 'roll'
        }
    }
</script>

<style lang='less' scoped>
    .app {
        .index1 {
            text-align: center;
            overflow: hidden;
            position: relative;
            flex: 1;

            .head {
                position: relative;
                position: fixed;
                top: 0;
                text-align: center;
                width: 100%;
                background: rgb(11, 36, 62);
                z-index: 10;
                .down {
                    position: absolute;
                    left: 0;
                    width: 20px;
                    margin-top: 20px;
                    margin-left: 30px;
                }
                .logo {
                    width: 100px;
                }
                .en {
                    position: absolute;
                    right: 0;
                    width: 20px;
                    margin-top: 20px;
                    margin-right: 30px;
                }
            }
            .index_logo {
                margin-top: 62px;
                width: 100%;

            }
            .index_btn {
                position: absolute;
                left: 50%;
                margin-left: -15px;
                bottom: 14%;
                cursor: pointer;
                z-index: 2;
                width: 30px;
            }
            .index_down {
                position: fixed;
                width: 100%;
                height: 100%;
                background: #fff;
                top: 0;
                z-index: 3;
                padding-top: 60px;

                div {
                    height: 60px;
                    line-height: 60px;
                    text-align: left;
                    text-indent: 62px;
                    color: #696e75;
                    border-bottom: 1px solid #f4f4f4;
                }
            }

        }
        .index_title {
            text-align: center;
            color: #0e2e4e;
            font-size: 18px;
            margin-top: 42px;
            padding-bottom: 32px;
            position: relative;
            div {
                position: absolute;
                width: 40px;
                height: 2px;
                background: #153e65;;
                left: 50%;
                margin-left: -20px;
                top: 32px;
            }
        }
        .about {
            text-align: center;
            img {
                width: 315px;
                padding-bottom: 42px;
            }
            .about_txt {
                margin: 0 30px;
                padding-bottom: 50px;
                font-size: 14px;
                line-height: 26px;
                color: #696e75;
                div {
                    text-indent: 30px;
                    text-align: justify;
                }
            }
        }
        .core {
            .core_img {
                width: 100%;
            }
            p{
                text-indent: 20px;
            }
            .core_txt {
                margin: 40px 30px 0 30px;
                padding-bottom: 40px;
                font-size: 14px;
                line-height: 26px;
                color: #696e75;
                .core_txt_title{
                    margin-bottom: 10px;
                    margin-top: 20px;
                }
                .core_txt_title_info{
                    color: #1d61a5;
                }
                .core_txt_title_info_bottom{
                    margin-top: 10px;
                    border-radius: 4px;
                    color: #1d61a5;
                }

            }
            .product {
                text-align: center;
                img {
                    width: 100px;
                }
                .product_title {
                    color: #1d61a5;
                    font-size: 18px;
                    margin-top: 8px;
                }
                .product_title1 {
                    color: #1d61a5;
                    font-size: 14px;
                    margin-top: 4px;
                    padding-bottom: 10px;
                }
                .product_txt {
                    margin: 0 30px;
                    padding-bottom: 40px;
                    font-size: 14px;
                    line-height: 26px;
                    color: #696e75;
                    div {
                        text-indent: 30px;
                        text-align: justify;
                    }
                }
            }
            .core_title{
                text-align: center;
                margin-top: 30px;
                color: #0e2e4e;
                font-size: 18px;
                position: relative;
                div {
                    position: absolute;
                    width: 40px;
                    height: 2px;
                    background: #153e65;;
                    left: 50%;
                    margin-left: -20px;
                    top: 32px;
                }
            }
        }
        .dynamic {
            .dynamic_a {
                display: block;
                margin: 0 30px;
                border-bottom: 1px solid #ccced0;
                height: 100px;
                overflow: hidden;
                margin-top: 20px;
                .dynamic_left {
                    float: left;
                    width: 76px;
                    height: 100%;
                    font-size: 0;
                    margin-top: 6px;
                    color: #fff;
                    .pr {
                        position: relative;
                        img {
                            width: 44px;
                        }
                        .day {
                            position: absolute;
                            font-size: 12px;
                            text-align: center;
                            width: 44px;
                            top: 2px;
                        }
                        .year {
                            position: absolute;
                            font-size: 12px;
                            text-align: center;
                            width: 44px;
                            top: 10px;
                        }
                    }

                }
                .dynamic_txt {
                    font-size: 14px;
                    color: #1d61a5;
                    line-height: 26px;
                    text-align: justify;
                    overflow: hidden;
                    text-overflow: ellipsis;
                    white-space: nowrap;
                }
                .dynamic_text {
                    font-size: 14px;
                    color: #696e75;
                    line-height: 26px;
                    overflow: hidden;
                    height: 48px;
                    position: relative;
                    div {
                        position: absolute;
                        bottom: -4px;
                        right: 0;
                        background: #fff;
                        width: 14px;
                    }

                }
                &:last-child {
                    border-bottom: none;
                }
            }
        }
        .partner {
            background: #eeeeee;
            margin-top: 42px;
            padding-top: 42px;
            .index_title {
                margin-top: 0;
            }
            .partner_div {

                text-align: left;
                font-size: 0;
                margin: 20px 10px 0 10px;
                div{
                    width:100%;
                    margin-bottom: 10px;
                    a{
                        display: inline-block;
                        width: 25%;
                        text-align: center;
                    }
                }
                img {
                    width: 80px;
                }
            }
            .index_title1 {
                margin-top: 42px;
            }
            .partner_div1 {
                text-align: center;
                color: #0e2e4e;
                font-size: 18px;
                padding-bottom: 32px;
                position: relative;
                margin-top: 42px;
            }
            .address {
                width: 72%;
                margin: 0 auto;
                text-align: center;
                font-size: 14px;
                color: #72777e;
            }
            .zip_code {
                text-align: center;
                font-size: 14px;
                color: #72777e;
                margin-top: 10px;
            }
            .mailbox {
                text-align: center;
                font-size: 14px;
                color: #72777e;
                margin-top: 10px;
            }
            .qr {
                text-align: center;
                margin-top: 20px;
                color: #72777e;
                font-size: 14px;
                padding-bottom: 46px;
                img {
                    width: 110px;
                }
                div {
                    margin-top: 4px
                }
            }
        }
        .validator {
            img {
                width: 100%;
                margin-top: 40px;
            }
            .validator_warp {
                text-align: center;
                margin-top: 20px;
                div {
                    font-size: 14px;
                    line-height: 26px;
                    color: #696e75;
                }

            }
            .validator_btn {
                margin-top: 30px;
                text-align: center;
                a {
                    text-align: center;
                    cursor: pointer;
                    font-size: 14px;
                    color: #fff;
                    background: #1d61a5;
                    border-radius: 6px;
                    padding: 10px 40px;
                }
            }
        }
        .copyright {
            height: 50px;
            background: #0b253e;
            font-size: 12px;
            color: #4d96e0;
            text-align: center;
            line-height: 50px;
	    a {
		background: #0e2e4e;
	      color: #4d96e0;
	    }
        }
    }
    .irisnet_info_container{
        text-align: center;
        .irisnet_title{
            text-indent: 0 !important;
            text-align: center;
            margin-top: 20px;
            font-size: 22px;
            color: #696e75;
        }
        .irisnet_info{
            text-indent: 0 !important;
            text-align: center;
            font-size: 14px;
            height: 26px;
            line-height: 26px;
            color: #696e75;
        }
        .irisnet_link_btn{
            text-align: center;
            margin-top: 30px;
            a{
                text-align: center;
                cursor: pointer;
                font-size: 14px;
                color: #fff;
                background: #1d61a5;
                border-radius: 6px;
                padding: 10px 20px;
            }
        }
        .mobilebanner_img_container{
            width: 100%;
            img{
                width: 100%;
            }
        }
    }

    html, body {
        min-width: auto !important;
    }
</style>