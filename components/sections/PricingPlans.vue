<template>
    <div class="mt-[100px] lg:mt-[137px] lg:pb-6">
        <PageTitle>
            <template v-slot:title><span
                    class="text-secondary">{{$t('pricing.title1')}}</span>{{$t('pricing.title2')}}</template>
            <template v-slot:text>{{$t('pricing.description')}}</template>
        </PageTitle>
        <div class="flex items-center justify-center pt-[78px] lg:pt-[105px] pb-10 lg:pb-16">
            <span class="text-base text-primary cursor-pointer w-[70px] text-right" @click="isYearlySelected=false"
                :class="{'font-semibold' : !isYearlySelected}">{{$t('pricing.toggleInput.monthly')}}</span>
            <label for="toggle" class="inline-flex mx-4 relative items-center cursor-pointer">
                <input type="checkbox" value="" id="toggle" class="sr-only peer" v-model="isYearlySelected">
                <div
                    class="w-11 h-6 bg-secondaryVariant rounded-full peer peer-focus:ring-3 peer-focus:ring-secondaryVariant2 dark:peer-focus:ring-red-800 dark:bg-gray-700 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-0.5 after:left-0.5 after:bg-white after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-red-600">
                </div>
            </label>
            <div class="relative w-[70px]">
                <span
                    class="text-base text-primary cursor-pointer underline underline-offset-[6px] decoration-secondary"
                    :class="{'font-semibold' : isYearlySelected}"
                    @click="isYearlySelected=true">{{$t('pricing.toggleInput.yearly')}}</span>
                <div
                    class="absolute w-max text-center text-secondary bottom-[60%] left-[10%] sm:left-[25%] lg:left-[40%]">
                    <span class="font-normal text-[14px] leading-[22px]">{{$t('pricing.toggleInput.absolute')}}</span>
                    <img class="mx-auto" src="/assets/images/arrow.png" alt="">
                </div>
            </div>
        </div>
        <div class="space-y-12 px-4 lg:px-10 xl:px-[124px] lg:grid lg:grid-cols-3 lg:gap-x-8 lg:space-y-0">
            <PriceCard v-for="(card, index) in cards" :key="'PriceCard' + index" :title="card.title" :price=card.price
                :frequency="card.frequency" :description="card.description" :features="card.features" :cta="card.cta"
                :mostPopular=card.mostPopular></PriceCard>
        </div>
    </div>
</template>

<script setup>
import PageTitle from '../PageTitle.vue';
import PriceCard from '../PriceCard.vue';
import { ref } from "vue";
import { useI18n } from "vue-i18n";
const { t } = useI18n();

const isYearlySelected = ref(false);

const cards = [
    {
        title: t('pricing.cards.free.title'),
        price: 0,
        frequency: t('pricing.cards.free.frequency'),
        description: t('pricing.cards.free.description'),
        features: [
            { text: t('pricing.cards.free.features.text1') },
            { text: t('pricing.cards.free.features.text2') },
            { text: t('pricing.cards.free.features.text3') },
            { text: t('pricing.cards.free.features.text4') }
        ],
        cta: 'Get started',
        mostPopular: false,
    },
    {
        title: t('pricing.cards.unlimited.title'),
        price: 25,
        frequency: t('pricing.cards.unlimited.frequency'),
        description: t('pricing.cards.unlimited.description'),
        features: [
            { text: t('pricing.cards.unlimited.features.text1') },
            { text: t('pricing.cards.unlimited.features.text2') },
            { text: t('pricing.cards.unlimited.features.text3') },
            { text: t('pricing.cards.unlimited.features.text4') },
            { text: t('pricing.cards.unlimited.features.text5') },
        ],
        cta: t('pricing.cards.unlimited.button'),
        mostPopular: true,
    },
    {
        title: t('pricing.cards.enterprise.title'),
        description: t('pricing.cards.enterprise.description'),
        features: [
            { text: t('pricing.cards.enterprise.features.text1') },
            { text: t('pricing.cards.enterprise.features.text2') },
            { text: t('pricing.cards.enterprise.features.text3') },
            { text: t('pricing.cards.enterprise.features.text4') },
            { text: t('pricing.cards.enterprise.features.text5') },
            { text: t('pricing.cards.enterprise.features.text6'), isBold: true },
            { text: t('pricing.cards.enterprise.features.text7'), isBold: true }
        ],
        cta: t('pricing.cards.enterprise.button'),
        mostPopular: false,
    },
];
</script>