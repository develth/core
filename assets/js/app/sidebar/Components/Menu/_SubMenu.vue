<template>
  <ul class="link--menu">
    <li v-if="item.link_new !== null" class="link--actions">
      <a :href="item.link_new" data-patience="virtue">
        <i class="fas fa-fw fa-magic mr-2"></i
        ><span>{{ labels['action.new'] }}</span>
      </a>
      <a :href="item.link_listing" data-patience="virtue">
        <i class="fas fa-fw" :class="item.icon"></i>
        <span>{{ labels['action.view'] }} {{ item.name }}</span>
      </a>
    </li>
    <!-- eslint-disable vue/no-use-v-if-with-v-for -->
    <li
      v-for="(subitem, index) in item.submenu"
      v-if="item.submenu !== null"
      :key="index"
    >
      <!-- eslint-enable -->
      <a :href="subitem.editLink" data-patience="virtue">
        <i class="fas fa-fw mr-2" :class="subitem.icon"></i>
        <!-- eslint-disable-next-line vue/no-v-html -->
        <span v-if="subitem.name" v-html="subitem.name"></span>
        <span v-else><em>(Untitled)</em></span>
      </a>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'SubMenu',
  props: {
    item: Object,
    labels: Object,
  },
};
</script>
