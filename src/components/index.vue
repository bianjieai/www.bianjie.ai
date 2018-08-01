<template>
    <div class="pc">
        <div class="index1">
            <div class="head_warp">
                <div class="center head">
                    <router-link to="#" tag="div" class="head_img">
                        <img @click="scroll(0)" src="../assets/logo.png"/>
                    </router-link>
                    <div class="head_Language">
                        <span class="head_language_seleted">CN</span>/<span>EN</span>
                    </div>
                    <router-link class="head_item" v-for="(item,index) in $store.state.messages.index.title"
                                 :key="index" :to="item.href" tag="div">
                        {{item.txt}}
                    </router-link>
                </div>
            </div>
            <swipe ref="swipe" class="my-swipe" @change="imgChangge" :auto="15000" v-if="is" style="height: 100%">
                <swipe-item v-for="(item,index) in $store.state.messages.index.logo" :key="index">
                    <img class="index1_logo" :src="item.src"/>
                    <a :href="$store.state.messages.validator.btnHref" target="_blank" class="index1_logo_btn"
                       v-show="index==1">
                        {{ $store.state.messages.validator.btnText}}
                    </a>
                </swipe-item>
            </swipe>
            <div class="tool">
                <img src="../assets/left.png" style="float: left;" @click="prev"/>
                <img src="../assets/right.png" style="float: right;" @click="next"/>
            </div>
            <div class="mint-swipe-indicators" style="display: block">
                <div v-for="(item,index) in $store.state.messages.index.logo" :class="{'is-active':item.is}"
                     class="mint-swipe-indicator" @click="goto(index)"></div>
            </div>
        </div>
        <div class="about">
            <div class="center">
                <div class="about_content" id="#about">
                    <div class="about_title">
                        {{$store.state.messages.about.title}}
                        <div class="about_title_across"></div>
                    </div>
                    <div class="about_txt">
                        <div v-for="item in $store.state.messages.about.txt">
                            {{item}}
                        </div>
                    </div>
                </div>
                <div class="about_img">
                    <img :src="$store.state.messages.about.img"/>
                </div>
            </div>
        </div>
        <div class="core">
            <div class="center">
                <div class="core_title">
                    {{$store.state.messages.core.title}}
                    <div class="core_title_across"></div>
                </div>
                <div class="core_txt">
                    {{$store.state.messages.core.txt}}
                </div>
                <div id="#product" class="core_title product">
                    {{$store.state.messages.product.title}}
                    <div class="core_title_across"></div>
                </div>
                <div class="product_warp">
                    <div class="product_warp_div" v-for="item in $store.state.messages.product.txt">
                        <img :src="item.bgImg"/>
                        <div class="product_content">
                            <div class="product_content_title">
                                <div class="product_content_title_txt">
                                    {{item.title}}<br>
                                    <div class="product_content_title_txt1" v-html="item.title1"></div>
                                </div>

                                <div class="product_content_title_img">
                                    <img :src="item.img"/>
                                </div>
                            </div>
                            <div class="product_content_txt" v-html="item.txt">

                            </div>
                        </div>
                    </div>
                </div>
                <div id="#dynamic" class="core_title dynamic">
                    {{$store.state.messages.dynamic.title}}
                    <div class="core_title_across dynamic_title_across"></div>
                </div>
                <div class="dynamic_warp">
                    <div class="dynamic_content">
                        <div class="dynamic_img">
                            <img src="../assets/date.png"/>
                            <div class="dynamic_date">
                                <div class="dynamic_day">{{$store.state.messages.dynamic.txt[0].month}}</div>
                                <div class="dynamic_month">{{$store.state.messages.dynamic.txt[0].day}}</div>
                            </div>
                            <div class="dynamic_year">
                                {{$store.state.messages.dynamic.txt[0].year}}
                            </div>
                        </div>
                        <div class="dynamic_txt">
                            <div class="dynamic_txt_title">
                                {{$store.state.messages.dynamic.txt[0].title}}
                            </div>
                            <div class="dynamic_txt_txt">
                                {{$store.state.messages.dynamic.txt[0].txt}}
                            </div>
                            <a :href="$store.state.messages.dynamic.txt[0].href" target="_blank"
                               class="dynamic_txt_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                    <div class="dynamic_content" style="margin-left: 90px">
                        <div class="dynamic_img">
                            <img src="../assets/date.png"/>
                            <div class="dynamic_date">
                                <div class="dynamic_day">{{$store.state.messages.dynamic.txt[1].month}}</div>
                                <div class="dynamic_month">{{$store.state.messages.dynamic.txt[1].day}}</div>
                            </div>
                            <div class="dynamic_year">
                                {{$store.state.messages.dynamic.txt[1].year}}
                            </div>
                        </div>
                        <div class="dynamic_txt">
                            <div class="dynamic_txt_title">
                                {{$store.state.messages.dynamic.txt[1].title}}
                            </div>
                            <div class="dynamic_txt_txt">
                                {{$store.state.messages.dynamic.txt[1].txt}}
                            </div>
                            <a :href="$store.state.messages.dynamic.txt[1].href" target="_blank"
                               class="dynamic_txt_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="dynamic_warp dynamic_warp2">
                    <div class="dynamic_content">
                        <div class="dynamic_img">
                            <img src="../assets/date.png"/>
                            <div class="dynamic_date">
                                <div class="dynamic_day">{{$store.state.messages.dynamic.txt[2].month}}</div>
                                <div class="dynamic_month">{{$store.state.messages.dynamic.txt[2].day}}</div>
                            </div>
                            <div class="dynamic_year">
                                {{$store.state.messages.dynamic.txt[2].year}}
                            </div>
                        </div>
                        <div class="dynamic_txt">
                            <div class="dynamic_txt_title">
                                {{$store.state.messages.dynamic.txt[2].title}}
                            </div>
                            <div class="dynamic_txt_txt">
                                {{$store.state.messages.dynamic.txt[2].txt}}
                            </div>
                            <a :href="$store.state.messages.dynamic.txt[2].href" target="_blank"
                               class="dynamic_txt_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                    <div class="dynamic_content" style="margin-left: 90px">
                        <div class="dynamic_img">
                            <img src="../assets/date.png"/>
                            <div class="dynamic_date">
                                <div class="dynamic_day">{{$store.state.messages.dynamic.txt[3].month}}</div>
                                <div class="dynamic_month">{{$store.state.messages.dynamic.txt[3].day}}</div>
                            </div>
                            <div class="dynamic_year">
                                {{$store.state.messages.dynamic.txt[3].year}}
                            </div>
                        </div>
                        <div class="dynamic_txt">
                            <div class="dynamic_txt_title">
                                {{$store.state.messages.dynamic.txt[3].title}}
                            </div>
                            <div class="dynamic_txt_txt">
                                {{$store.state.messages.dynamic.txt[3].txt}}
                            </div>
                            <a :href="$store.state.messages.dynamic.txt[3].href" target="_blank"
                               class="dynamic_txt_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="bg"></div>
        <div class="bgcr"></div>
        <div class="partner">
            <div class="center" id="#partner">
                <div class="partner_title">
                    {{$store.state.messages.partner.title}}
                    <div class="partner_title_across"></div>
                </div>
                <div class="partner_img">
                    <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img">
                        <img :src="item.img" @mouseover="overShow(item)" @mouseout="outHide(item)"/>
                    </a>
                </div>
                <div class="contact" id="#contact">
                    <div class="partner_title contact_title">
                        {{$store.state.messages.contact.title}}
                        <div class="partner_title_across"></div>
                    </div>
                    <div class="contact_txt">
                        <div>
                            {{$store.state.messages.contact.address.txt}}：{{$store.state.messages.contact.address.val}}
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                            {{$store.state.messages.contact.zip_code.txt}}：{{$store.state.messages.contact.zip_code.val}}
                        </div>
                        <div class="contact_txt_10">
                            {{$store.state.messages.contact.mailbox.txt}}：{{$store.state.messages.contact.mailbox.val}}
                        </div>
                    </div>
                    <div class="contact_qr">
                        <img src="../assets/qr.png"/>
                        <div>
                            Bianjie_AI
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="copyright">
            版权所有 © 2017上海边界智能科技有限公司 <a href="http://www.miitbeian.gov.cn" target="_blank">沪ICP备17020986号</a>
        </div>
    </div>
</template>


<script>
    import $ from 'jquery'

    export default {
        name: 'index',
        data() {
            return {
                is: false
            }
        },
        methods: {
            roll() {
                if (document.getElementById(this.$route.hash)) {
                    //window.scrollTo(0, document.getElementById(this.$route.hash).offsetTop-80)

                    this.scroll(document.getElementById(this.$route.hash).offsetTop - 140)
                }
            },
            scroll(top) {
                $('body,html').animate({
                        scrollTop: top
                    }, 500
                );
            },
            overShow(item) {
                item.src = item.img;
                item.img = item.img_selected;
            },
            outHide(item) {
                item.img = item.src;
            },
            imgChangge(index, oldIndex) {
                this.$store.state.messages.index.logo.forEach(v => {
                    v.is = false;
                })
                this.$store.state.messages.index.logo[index].is = true
            },
            goto(index) {
                this.$refs.swipe.goto(index)
            },
            next() {
                this.$refs.swipe.next()
            },
            prev() {
                this.$refs.swipe.prev()
            }
        },
        mounted() {
            this.roll();
            this.is = true;
        },
        watch: {
            '$route': 'roll'
        },
    }
</script>


<style lang='less'>

    html, body {
        min-width: 1200px;
    }

    @media (max-height: 930px) {
        .index1_logo {
            width: 1000px !important;

        }
    }

    @media (max-height: 800px) {
        .index1_logo {
            width: 760px !important;

        }
    }

    @media (max-height: 660px) {
        .index1_logo {
            width: 620px !important;

        }
    }

    .pc {
        .mint-swipe-indicators {
            bottom: 6%;
            display: none;
            .is-active {
                background: #4d96df;
                opacity: 1;
            }
        }
        .mint-swipe-indicator {
            cursor: pointer;
            width: 100px;
            height: 2px;
            background: #4d96df;
            opacity: 0.3;
            border-radius: unset;
        }

        .index1 {
            background: #0b253e;
            flex: 1;
            height: 100vh;;
            text-align: center;
            overflow: hidden;
            position: relative;
            .tool {
                width: 1200px;
                position: absolute;
                top: 50%;
                left: 50%;
                margin-left: -600px;
                height: 60px;
                margin-top: -30px;
                z-index: 2;
                img {
                    cursor: pointer;
                }
            }
            .head_warp {
                position: fixed;
                background: #0b243e;
                z-index: 10;
                width: 100%;
                .head {
                    height: 80px;
                    .head_img {
                        float: left;
                        cursor: pointer;
                    }
                    .head_item {
                        float: right;
                        height: 80px;
                        line-height: 80px;
                        color: #729bc4;
                        padding: 0 24px;
                        cursor: pointer;
                        &:hover {
                            color: #4d96e0;
                        }
                    }
                    .head_Language {
                        float: right;
                        height: 80px;
                        line-height: 80px;
                        padding: 0 24px;
                        cursor: pointer;
                        color: #729bc4;
                        font-size: 12px;
                        font-weight: bold;
                        span {
                            color: #4d96e0;
                            &:hover {
                                color: #94c0ec;
                            }
                        }
                    }
                    .head_language_seleted {
                        color: #94c0ec !important;
                    }
                }
            }
            .index1_logo {
                width: 1200px;
                padding-top:80px;
            }
            .index1_logo_btn {
                cursor: pointer;
                font-size: 14px;
                line-height: 40px;
                color: #fff;
                width: 140px;
                position: absolute;
                bottom: 10%;
                left: 50%;
                margin-left: -70px;
                height: 40px;
                background: #1d61a5;
                border-radius: 6px;
                &:hover {
                    background: #11385f;
                }
            }
            .index1_btn {
                position: absolute;
                bottom: 4%;
                cursor: pointer;
                margin-left: -16px
            }
        }

        .about {
            background: #fff;
            height: 460px;
            .about_content {
                float: left;
                margin-left: 50px;
                margin-top: 96px;
                width: 406px;
                .about_title {
                    font-size: 28px;
                    color: #153e65;
                    position: relative;
                    letter-spacing: 2px;
                    .about_title_across {
                        height: 3px;
                        width: 70px;
                        background: #153e65;
                        margin-top: 20px
                    }
                }
                .about_txt {
                    margin-top: 40px;
                    color: #696e75;
                    letter-spacing: 2px;
                    line-height: 28px;
                    font-size: 15px;
                    text-indent: 34px;
                    text-align: justify
                }
            }
            .about_img {
                float: right;
                margin-top: 172px;
                img {
                    height: 248px;
                }
            }
        }
        .bg {
            height: 930px;
            background: #fff;
        }
        .bgcr {
            height: 460px;
            background: url('../../public/dynamicPc.jpg') no-repeat center center;
            background-color: #0e2e4e;
        }
        .core {
            background: url('../../public/corePc.jpg') no-repeat center center;
            width: 100%;
            background-color: #0e2e4e;
            height: 850px;
            .core_title {
                margin-top: 90px;
                color: #94c0ec;
                font-size: 28px;
                position: relative;
                margin-left: 50px;
                letter-spacing: 2px;
                .core_title_across {
                    height: 3px;
                    width: 60px;
                    background: #94c0ec;
                    margin-top: 20px
                }
            }
            .core_txt {
                width: 406px;
                margin-left: 50px;
                text-indent: 34px;
                text-align: justify;
                color: #fff;
                margin-top: 40px;
                letter-spacing: 2px;
                line-height: 28px;
                font-size: 15px;
            }
            .product {
                margin-top: 270px;
            }
            .product_warp {
                overflow: hidden;
                margin-top: 40px;
                .product_warp_div {
                    float: left;
                    margin-right: 40px;
                    position: relative;
                    .product_content {
                        position: absolute;
                        width: 100%;
                        height: 100%;
                        top: 0;
                        .product_content_title {
                            margin-top: 50px;
                            margin-left: 50px;
                            overflow: hidden;
                            .product_content_title_txt {
                                color: #1d61a5;
                                font-size: 22px;
                                float: left;
                                margin-top: 50px;
                                font-weight: bold;
                                position: relative;
                                .product_content_title_txt1 {
                                    font-size: 12px;
                                    width: 136px;
                                    margin-top: 10px;
                                    position: absolute;
                                    span {
                                        font-weight: bold
                                    }
                                }
                            }
                            .product_content_title_img {
                                float: right;
                                margin-right: 50px
                            }
                        }
                        .product_content_txt {
                            margin-top: 38px;
                            text-indent: 34px;
                            text-align: justify;;
                            line-height: 28px;
                            margin-left: 50px;
                            width: 270px;
                            color: #696e75
                        }
                    }
                }
                .product_warp_div:last-child {
                    margin-right: 0;
                }

            }
            .dynamic {
                margin-top: 90px;
                color: #0e2e4e;
                .dynamic_title_across {
                    background: #0e2e4e
                }
            }
            .dynamic_warp {
                margin-left: 50px;
                overflow: hidden;
                .dynamic_content {
                    width: 500px;
                    height: 170px;
                    margin-top: 40px;
                    float: left;
                    .dynamic_img {
                        float: left;
                        position: relative;
                        .dynamic_date {
                            position: absolute;
                            top: 0;
                            width: 100%;
                            height: 100%;
                            text-align: center;
                            color: #fff;
                            .dynamic_month {
                                font-size: 24px;
                            }
                            .dynamic_day {
                                font-size: 15px;
                                margin-top: 8px
                            }
                        }
                        .dynamic_year {
                            background: #0b243e;
                            height: 60px;
                            width: 62px;
                            margin-top: -4px;
                            color: #fff;
                            text-align: center;
                            line-height: 60px;
                            font-size: 15px
                        }
                    }
                    .dynamic_txt {
                        margin-left: 40px;
                        float: left;
                        .dynamic_txt_title {
                            color: #1d61a5;
                            font-weight: bold;
                            width: 380px;
                            overflow: hidden;
                            text-overflow:ellipsis;
                            white-space: nowrap;
                        }
                        .dynamic_txt_txt {
                            margin-top: 24px;
                            text-indent: 30px;
                            width: 370px;
                            font-size: 14px;
                            color: #696e75;
                            line-height: 28px;
                            text-align: justify;
                            height: 80px;
                            overflow: hidden;
                        }
                        .dynamic_txt_btn {
                            font-size: 14px;
                            color: #1d61a5;
                            line-height: 28px;
                            position: relative;
                            margin-top: 14px;
                            cursor: pointer;
                            display: block;
                            img {
                                position: absolute;
                                top: 0;
                                margin-top: 7px;
                                margin-left: 6px
                            }
                        }
                    }
                }
            }
            .dynamic_warp2 {
                margin-top: 120px;
                .dynamic_txt_title {
                    color: #94c0ec !important;
                }
                .dynamic_txt_txt {
                    color: #fff !important;
                }
                .dynamic_txt_btn {
                    color: #94c0ec !important;
                }
            }
        }

        .partner {
            background: #eee;
            .partner_title {
                font-size: 28px;
                color: #0e2e4e;
                position: relative;
                letter-spacing: 2px;
                margin-top: 84px;
                margin-left: 50px;
                .partner_title_across {
                    height: 3px;
                    width: 70px;
                    background: #0e2e4e;
                    margin-top: 20px;
                }
            }
            .partner_img {
                margin-left: 50px;
                margin-top: 20px;
                img {
                    margin-top: 20px;
                    margin-right: 20px;
                    cursor: pointer;
                }
            }
            .contact {
                position: relative;
                margin-left: 50px;
                padding-bottom: 50px;
                .contact_title {
                    margin-left: 0;
                }
                .contact_txt {
                    margin-top: 36px;
                    color: #72777e;
                    font-size: 14px;
                    .contact_txt_10 {
                        margin-top: 10px
                    }
                }
                .contact_qr {
                    position: absolute;
                    right: 38px;
                    top: 0;
                    div {
                        text-align: center;
                        color: #72777e;
                        margin-top: 4px
                    }
                }
            }
        }

        .copyright {
            height: 90px;
            background: #0e2e4e;
            text-align: center;
            line-height: 90px;
            color: #4d96e0;

	    a {
		background: #0e2e4e;
	      color: #4d96e0;
	    }
        }
    }
</style>  