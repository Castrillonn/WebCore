
<template>
    <SectionTemplate :section-data="props.sectionData">
        <!-- Swiper -->
        <swiper
            class="testimonials-swiper px-1"
            :slidesPerView="4"
            :spaceBetween="10"
            :pagination="{clickable: true}"
            :modules="[Pagination]"
            :grab-cursor="true"
            :prevent-clicks-propagation="true"
            :breakpoints = "{
                0:    {slidesPerView: 1},
                768:  {slidesPerView: 2},
                1400: {slidesPerView: 4}
            }">

            <!-- Slide Items -->
            <swiper-slide v-for="item in props.sectionData['items']">
                <Testimonial :testimonial-data="item"/>
            </swiper-slide>
        </swiper>
    </SectionTemplate>
</template>

<script setup>
import SectionTemplate from "./templates/SectionTemplate.vue"
import Testimonial from "./components/Testimonial.vue"

import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/pagination'
import { Pagination } from 'swiper/modules'

/**
 * @property {Object} sectionData
 */
const props = defineProps({
    sectionData: Object
})
</script>

<style lang="scss" scoped>
@import "/src/scss/_theming.scss";

.swiper {
    height: 100%;
    .swiper-slide {
        margin-bottom: 60px;
        height: auto !important;
    }
}
</style>