<template>
    <div class="pc">
        <div class="header_container">
            <div class="header_wrap">
                <div class="header_logo_img">
                    <router-link to="#">
                        <img @click="scroll(0)" src="../assets/logo.png">
                    </router-link>
                </div>
                <div class="link_content">
                    <router-link class="header_item" v-for="(item,index) in $store.state.messages.index.title"
                                 :key="index" :to="item.href" tag="div">
                        {{item.txt}}
                    </router-link>
                    <router-link class="header_validator" key="310" to="/validators" tag="div">{{$store.state.messages.validator.headerValidatorBtnText}}</router-link>
                </div>
            </div>
        </div>
        <div class="swiper_content">
            <div class="swiper_wrap">
                <swipe ref="swipe" class="my-swipe" @change="imgChange" :auto="15000" v-if="active">
                    <swipe-item v-for="(item,index) in $store.state.messages.index.logo" :key="index">
                        <a :href="index==1 ? $store.state.messages.validator.irisnetHref : 'javascript:;'" target="_blank" :class="index==1 ? 'active_cursor': 'default_cursor'">
                            <img class="index1_logo" :src="item.src"/>
                        </a>
                        <a :href="$store.state.messages.validator.btnHref" target="_blank" class="index1_logo_btn"
                           v-show="index==0">
                            {{ $store.state.messages.validator.btnText}}
                        </a>
                    </swipe-item>
                </swipe>
                <div class="tool">
                    <img src="../assets/left.png" style="float: left;" @click="prev"/>
                    <img src="../assets/right.png" style="float: right;" @click="next"/>
                </div>
                <div class="mint-swipe-indicators" style="display: block">
                    <div v-for="(item,index) in $store.state.messages.index.logo" :class="{'active':item.active}"
                         class="mint-swipe-indicator" @click="goto(index)"></div>
                </div>
            </div>
        </div>
        <div class="content">
            <div id="#about" class="about_wrap">
                <div class="about_our">
                    <h2 class="about_title">{{$store.state.messages.about.title}}</h2>
                    <div class="about_title_across"></div>
                    <div class="about_text">
                        <div v-for="item in $store.state.messages.about.txt">
                            <div v-html="item">{{item}}</div>
                        </div>
                    </div>
                </div>
                <div class="about_img_content">
                    <img :src="$store.state.messages.about.img"/>
                </div>
            </div>
            <div id="#core" class="core_wrap">
                <div class="core_text_wrap">
                    <div class="core_text_content">
                        <h2>{{$store.state.messages.core.title}}</h2>
                        <div class="core_title_across"></div>
                        <div class="core_text">
                            <p class="core_text_title">{{$store.state.messages.core.secondaryTitle}}</p>
                            <p class="core_service_information">{{$store.state.messages.core.service}}</p>
                            <p class="core_text_title margin_top">{{$store.state.messages.core.technologyTitle}}</p>
                            <p class="core_technology_information">{{$store.state.messages.core.technology}}</p>
                        </div>
                    </div>
                </div>
            </div>
            <div id="#product" class="product_wrap">
                <div class="product_header_title_content">
                    <h2 class="product_header_title">{{$store.state.messages.product.title}}</h2>
                    <div class="core_title_across"></div>
                </div>
                <ul class="product_list_content">
                    <li class="product_item" v-for="item in $store.state.messages.product.txt" >
                        <div ref="product_item_content" class="product_item_content" :style="{background:'url('+ item.bgImg +')'}">
                            <div class="product_title_content">
                                <div class="product_title">
                                    {{item.title}}
                                    <div class="product_content_title_txt1" v-html="item.title1"></div>
                                </div>
                                <div class="item_logo_content">
                                    <img :src="item.img"/>
                                </div>
                            </div>
                            <div class="product_content_txt" v-html="item.txt"></div>
                        </div>
                    </li>
                </ul>
            </div>
            <div id="#dynamic" class="dynamic_title_wrap">
                <div class="dynamic_title_content">
                    <div class="dynamic_title">{{$store.state.messages.dynamic.title}}</div>
                    <div class="about_title_across"></div>
                </div>
                <div class="news_wrap">
                    <div class="news_list_item_content">
                        <div class="news_item_content">
                            <div class="month_day_content">
                                <div class="date_day_content">{{$store.state.messages.dynamic.txt[0].month}}</div>
                                <div class="date_month_content">{{$store.state.messages.dynamic.txt[0].day}}</div>
                            </div>
                            <div class="year_content">{{$store.state.messages.dynamic.txt[0].year}}</div>
                        </div>
                        <div class="news_content">
                            <h4 class="news_title">{{$store.state.messages.dynamic.txt[0].title}}</h4>
                            <div class="news_content_text">{{$store.state.messages.dynamic.txt[0].txt}}</div>
                            <a :href="$store.state.messages.dynamic.txt[0].href" target="_blank"
                               class="view_more_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                    <div class="news_list_item_content right_content">
                        <div class="news_item_content">
                            <div class="month_day_content">
                                <div class="date_day_content">{{$store.state.messages.dynamic.txt[1].month}}</div>
                                <div class="date_month_content">{{$store.state.messages.dynamic.txt[1].day}}</div>
                            </div>
                            <div class="year_content">{{$store.state.messages.dynamic.txt[1].year}}</div>
                        </div>
                        <div class="news_content">
                            <h4 class="news_title">{{$store.state.messages.dynamic.txt[1].title}}</h4>
                            <div class="news_content_text">{{$store.state.messages.dynamic.txt[1].txt}}</div>
                            <a :href="$store.state.messages.dynamic.txt[1].href" target="_blank"
                               class="view_more_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="news_bg_content">
                <div class="news_bg_wrap">
                    <div class="news_bg_list_item_content">
                        <div class="news_bg_item_content">
                            <div class="month_bg_day_content">
                                <div class="date_bg_day_content">{{$store.state.messages.dynamic.txt[2].month}}</div>
                                <div class="date_bg_month_content">{{$store.state.messages.dynamic.txt[2].day}}</div>
                            </div>
                            <div class="year_bg_content">{{$store.state.messages.dynamic.txt[2].year}}</div>
                        </div>
                        <div class="bg_news_content">
                            <h4 class="news_bg_title">{{$store.state.messages.dynamic.txt[2].title}}</h4>
                            <div class="news_bg_content_text">{{$store.state.messages.dynamic.txt[2].txt}}</div>
                            <a :href="$store.state.messages.dynamic.txt[2].href" target="_blank"
                               class="view_bg_more_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                    <div class="news_bg_list_item_content right_content">
                        <div class="news_bg_item_content">
                            <div class="month_bg_day_content">
                                <div class="date_bg_day_content">{{$store.state.messages.dynamic.txt[3].month}}</div>
                                <div class="date_bg_month_content">{{$store.state.messages.dynamic.txt[3].day}}</div>
                            </div>
                            <div class="year_bg_content">{{$store.state.messages.dynamic.txt[3].year}}</div>
                        </div>
                        <div class="bg_news_content">
                            <h4 class="news_bg_title">{{$store.state.messages.dynamic.txt[3].title}}</h4>
                            <div class="news_bg_content_text">{{$store.state.messages.dynamic.txt[3].txt}}</div>
                            <a :href="$store.state.messages.dynamic.txt[3].href" target="_blank"
                               class="view_bg_more_btn">
                                查看更多 <img src="../assets/dynamic_arrow.png"/>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
            <div id="#partner" class="partner_container">
                <div class="partner_wrap">
                    <div class="partner_title_content">
                        <h2 class="partner_title">{{$store.state.messages.partner.title}}</h2>
                        <div class="about_title_across"></div>
                    </div>
                    <div class="partner_img_content">
                        <div class="partner_img">
                            <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[0]">
                                <img :src="item.img" @mouseover="overShow(item)" @mouseout="outHide(item)"/>
                            </a>
                            <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[1]">
                                <img :src="item.img" @mouseover="overShow(item)" @mouseout="outHide(item)"/>
                            </a>
                            <a :href="item.href" target="_blank" v-for="item in $store.state.messages.partner.img[2]">
                                <img :src="item.img" @mouseover="overShow(item)" @mouseout="outHide(item)"/>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
            <div id="#contact" class="contact_container">
                <div class="contact_wrap">
                    <div class="contact_way_content">
                        <span class="contact_title">{{$store.state.messages.contact.title}}</span>
                        <div class="about_title_across"></div>
                        <div class="address_content">
                            <span class="address">{{$store.state.messages.contact.address.txt}}：{{$store.state.messages.contact.address.val}}</span>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="postcode">{{$store.state.messages.contact.zip_code.txt}}：{{$store.state.messages.contact.zip_code.val}}</span>
                        </div>
                        <p class="email">{{$store.state.messages.contact.mailbox.txt}}：{{$store.state.messages.contact.mailbox.val}}</p>
                    </div>
                    <div class="qr_content">
                        <img src="../assets/qr.png"/>
                        <div class="img_alt">
                            Bianjie_AI
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="footer">版权所有 © 2017上海边界智能科技有限公司
            <a href="http://www.miitbeian.gov.cn" target="_blank">沪ICP备17020986号</a>
        </div>
    </div>
</template>

<script>
    import $ from 'jquery'

    export default {
        name: 'Index',
        data() {
            return {
                active: false
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
            imgChange(index, oldIndex) {
                this.$store.state.messages.index.logo.forEach(v => {
                    v.active = false;
                })
                this.$store.state.messages.index.logo[index].active = true
            },
            goto(index) {
                this.$refs.swipe.goto(index)
            },
            next() {
                this.$refs.swipe.next()
            },
            prev() {
                this.$refs.swipe.prev()
            },
        },
        mounted() {
            this.roll();
            this.active = true;
        },
        watch: {
            '$route': 'roll'
        },
    }
</script>

<style scoped lang="less">
 @import "../style/Index";
</style>