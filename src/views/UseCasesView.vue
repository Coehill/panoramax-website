<template>
  <main>
    <section class="section">
      <h1 class="use-cases-section-title">
        {{ $t('pages.useCases.main_title') }}
      </h1>
      <p class="main-description">
        {{ $t('pages.useCases.main_description') }}
      </p>
      <img
        src="@/assets/images/use-case.png"
        loading="lazy"
        :alt="$t('pages.useCases.alt_main_image')"
        class="img-use-cases"
      />
    </section>
    <section class="section">
      <h2 class="use-cases-section-title">
        {{ $t('pages.useCases.subtitle_use_cases') }}
      </h2>
      <ul class="use-cases-list">
        <li
          v-for="useCase in useCases"
          :key="useCase.title"
          class="use-case-item"
        >
          <UseCaseCard
            :title="useCase.title"
            :description="useCase.description"
            :image="useCase.image"
          />
        </li>
      </ul>
      <div class="entry-carousel">
        <Carousel>
          <Slide v-for="slide in useCasesSlider" :key="slide.description">
            <div class="carousel__item">
              <div class="wrapper-legend">
                <span class="legend">{{ slide.description }}</span>
              </div>
              <img
                :src="img(slide.image.url)"
                :alt="slide.image.alt"
                class="carousel-item-img"
              />
            </div>
          </Slide>

          <template #addons>
            <Navigation />
            <Pagination />
          </template>
        </Carousel>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import UseCaseCard from '@/components/UseCasesCard.vue'
import type { Image } from '@/interfaces/index'
import { useI18n } from 'vue-i18n'
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

const { t } = useI18n()
interface UseCaseData {
  title: string
  description: string
  image: Image
}
interface UseCaseSlider {
  description: string
  image: Image
}
function img(name: string): string {
  return new URL(`../assets/images/${name}`, import.meta.url).toString()
}
const useCasesSlider = <UseCaseSlider[]>[
  {
    description: t('pages.useCases.userCase_img_1.description'),
    image: {
      url: t('pages.useCases.userCase_img_1.image.url'),
      alt: t('pages.useCases.userCase_img_1.image.alt')
    }
  },
  {
    description: t('pages.useCases.userCase_img_2.description'),
    image: {
      url: t('pages.useCases.userCase_img_2.image.url'),
      alt: t('pages.useCases.userCase_img_2.image.alt')
    }
  },
  {
    description: t('pages.useCases.userCase_img_3.description'),
    image: {
      url: t('pages.useCases.userCase_img_3.image.url'),
      alt: t('pages.useCases.userCase_img_3.image.alt')
    }
  }
]
const useCases = <UseCaseData[]>[
  {
    title: t('pages.useCases.useCase_1.title'),
    description: t('pages.useCases.useCase_1.description'),
    image: {
      url: t('pages.useCases.useCase_1.image.url'),
      alt: t('pages.useCases.useCase_1.image.alt')
    }
  },
  {
    title: t('pages.useCases.useCase_2.title'),
    description: t('pages.useCases.useCase_2.description'),
    image: {
      url: t('pages.useCases.useCase_2.image.url'),
      alt: t('pages.useCases.useCase_2.image.alt')
    }
  },
  {
    title: t('pages.useCases.useCase_3.title'),
    description: t('pages.useCases.useCase_3.description'),
    image: {
      url: t('pages.useCases.useCase_3.image.url'),
      alt: t('pages.useCases.useCase_3.image.alt')
    }
  },
  {
    title: t('pages.useCases.useCase_4.title'),
    description: t('pages.useCases.useCase_4.description'),
    image: {
      url: t('pages.useCases.useCase_4.image.url'),
      alt: t('pages.useCases.useCase_4.image.alt')
    }
  }
]
</script>

<style scoped>
.section {
  padding: 3rem 15%;
}
.section:nth-child(even) {
  background-color: var(--white);
}
.section:nth-child(odd) {
  background-color: var(--grey);
}
.use-cases-section-title {
  font-family: SFPro-Bold;
  font-size: 2.8rem;
  color: var(--blue-dark);
  margin-bottom: 4rem;
}
.use-cases-list {
  display: flex;
  flex-wrap: wrap;
}
.use-case-item {
  flex: calc(50% - 10rem);
}
.use-case-item:nth-child(odd) {
  margin-right: 10rem;
}
.main-description {
  font-size: 1.4rem;
  color: var(--grey-dark);
  white-space: pre-line;
  margin-bottom: 2rem;
}
.img-use-cases {
  width: 100%;
  border-radius: 3rem;
}
.entry-carousel {
  padding: 2rem 6rem;
  background-color: var(--blue-ligth);
  border-radius: 2rem;
}
.wrapper-legend {
  padding: 0.5rem;
  position: absolute;
  top: 1rem;
  left: 1rem;
  background-color: var(--blue-dark);
  border-radius: 0.5rem;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
.legend {
  font-size: 1.2rem;
  color: var(--white);
}
.carousel-item-img {
  height: 100%;
  width: 100%;
  object-fit: contain;
  border-radius: 2rem;
}
@media (max-width: 1324px) {
  .section {
    padding: 3rem 10%;
  }
}
@media (max-width: 768px) {
  .section {
    padding: 2rem;
  }
  .use-case-item {
    flex: calc(50% - 2rem);
  }
  .use-case-item:nth-child(odd) {
    margin-right: 2rem;
  }
}
@media (max-width: 500px) {
  .legend {
    font-size: 1rem;
  }
  .entry-carousel {
    padding: 1rem;
  }
  .carousel__prev {
    left: -4rem;
  }
  .carousel__next {
    right: -4rem;
  }
  .use-cases-section-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  .main-description {
    font-size: 1.4rem;
  }
  .use-case-item {
    flex: 100%;
  }
}
</style>
<style>
.carousel__item {
  width: 100%;
  background-color: var(--blue-semi-ligth);
  border-radius: 2rem;
  display: flex;
  justify-content: center;
  position: relative;
}
.carousel__prev {
  left: -6rem;
}
.carousel__next {
  right: -6rem;
}
.carousel__next,
.carousel__prev {
  background-color: var(--blue);
  color: var(--white);
  border-radius: 50%;
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}
.carousel__next:hover,
.carousel__prev:hover {
  color: var(--white);
  opacity: 0.8;
}

@media (max-width: 500px) {
  .carousel__prev {
    left: -4rem;
  }
  .carousel__next {
    right: -4rem;
  }
}
</style>
