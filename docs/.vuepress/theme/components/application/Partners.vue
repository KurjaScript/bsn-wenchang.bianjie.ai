<template>
    <div class="partners_container">
        <div class="title">{{partners.title}}</div>
        <div class="partners_content_container">
            <div class="partners_content">
                <swiper class="partners_list_swiper" :options="swiperOptions">
                    <swiper-slide v-for="(item, index) in partners.partnersList" :key="index">
                        <img :src="item.imgLink" alt="">
                    </swiper-slide>
                </swiper>
            </div>
        </div>
    </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper';
import 'swiper/css/swiper.css';
export default {
    name: "Partners",
    props: ["partners"],
    data() {
        return {
            swiperOptions: {
                spaceBetween: 100,
                centeredSlides: true,
                autoplay: {
                    delay: 2000,
                    disableOnInteraction: false,
                },
                loop: true,
                slidesPerView: 'auto',
                loopedSlides: 5,
                speed: 2000
            }
        }
    },
    components: {
        Swiper,
        SwiperSlide
    },
}
</script>

<style lang="stylus" scoped>
.partners_container {
    width: 100%;
    .title {
        font-size: $fontSize24;
        font-weight: 600;
        color: #000000;
        line-height: 2.4rem;
        text-align: center;
    }
    .partners_content_container {
        margin-top: 1.6rem;
        width: 100%;
        background: url(../../assets/ecoloapp/partners_bg.png) no-repeat center / cover;
        .partners_content {
            box-sizing: border-box;
            margin: 0 auto;
            padding: 3rem 4.8rem 8rem;
            max-width: $contentWidth;
            @media (max-width: 400px) {
                padding: 3rem 1.6rem 8rem;
            }
            ::v-deep .partners_list_swiper {
                margin: 0 auto;
                max-width: $contentWidth;
                .swiper-wrapper {
                    .swiper-slide {
                        width: auto;
                        height: 4.8rem;
                        img {
                            -webkit-filter: grayscale(100%);
                            filter: grayscale(100%);
                            height: 100%;
                            opacity: 0.4;
                            vertical-align: middle;
                            transition: all .2s linear;
                            &:hover {
                                -webkit-filter: grayscale(0%);
                                filter: grayscale(0%);
                                opacity: 1;
                                transition: all .2s linear;
                            }
                        }
                    }
                    .swiper-slide-active {
                        img {
                            -webkit-filter: grayscale(0%);
                            filter: grayscale(0%);
                            opacity: 1;
                        }
                    }
                }
            }
        }
    }
}
</style>