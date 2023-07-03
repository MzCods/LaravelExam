<template>
  <div class="content">
    <b-row>
      <b-col cols="12">
        <h2>Événements tendances</h2>
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="12">
        <Trending />
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="12">
        <h2>Des sports</h2>
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="12">
        <SportsCards />
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="12">
        <h2>Amusement / Divertissement</h2>
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="12">
        <FunCards />
      </b-col>
    </b-row>
  </div>
</template>

<script>
import Trending from '@/components/TrendingUser.vue';
import SportsCards from '@/components/SportsCardsUser.vue';
import FunCards from '@/components/FunCardsUser.vue';

export default {
  components: {
    Trending,
    SportsCards,
    FunCards,
  },
};
</script>
