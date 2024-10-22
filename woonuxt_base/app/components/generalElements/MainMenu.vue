<script setup lang="ts">
const { wishlistLink } = useAuth();

const links = [
  { to: '/', text: 'messages.general.home' },
  { to: '/products', text: 'messages.general.allProducts' },
  { to: '/categories', text: 'messages.shop.category', count: 2 },
  { to: '/contact', text: 'messages.general.contact' },
  { to: wishlistLink, text: 'Wishlist', class: 'lg:hidden', prefetch: false },
  { to: '/my-account', text: 'My Account', class: 'lg:hidden', prefetch: false },
];
</script>

<template>
  <nav class="flex flex-wrap items-center justify-center gap-6 p-4">
    <NuxtLink
      v-for="link in links"
      :key="link.to"
      :to="link.to"
      :class="[
        'relative text-lg font-medium text-stone-700 transition-colors duration-300 hover:text-primary',
        'before:absolute before:bottom-0 before:left-0 before:w-full before:h-0.5 before:-mb-2',
        'before:bg-primary before:transform before:scale-x-0 before:origin-left',
        'before:transition-transform before:duration-300 hover:before:scale-x-100',
        link.class
      ]"
      activeClass="text-primary before:scale-x-100"
      :prefetch="link.prefetch !== false"
    >
      {{ $t(link.text, link.count) }}
    </NuxtLink>
  </nav>
</template>