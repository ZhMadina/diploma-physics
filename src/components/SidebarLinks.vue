<template>
  <div>
    <router-link
        :to="{ name: 'content', params: { slug: node.slug } }"
        class="node"
        :class="{ child: depth !== 0 }"
        :style="{ marginLeft: `${depth * 20}px` }"
        exact-active-class="active"
        @click="expanded = true"
    >

      <div class="node__item">
        <i :class="node.icon" v-if="depth === 0" />
        <div v-else>
          <i class="fa-solid fa-circle" v-if="route.params.slug === node.slug" />
          <i class="fa-regular fa-circle" v-else></i>
        </div>

        {{ node.title }}
      </div>
      <i
          class="fa-solid fa-chevron-right"
          v-if="hasChildren"
          :class="['node__icon', { 'rotate-90': expanded }]"
          @click.stop="nodeClick"
      ></i>

    </router-link>
    <toggle-animation>
      <div v-if="expanded">
        <sidebar-links
            v-for="child in node.children"
            :key="child.title"
            :node="child"
            :depth="depth + 1"
        />
      </div>
    </toggle-animation>
  </div>
</template>

<script>
import {computed, ref} from "vue"
import ToggleAnimation from "@/components/DropdownAnimation.vue"
import {useRoute} from "vue-router";

export default {
  name: "SidebarLinks",
  components: { ToggleAnimation},
  props: {
    node: {
      type: Object,
      default: () => ({}),
    },
    depth: {
      type: Number,
      default: 0,
    },
    expand: {
      type: Boolean,
      default: false
    },
  },
  setup(props, {emit}) {
    const expanded = ref(props.expand)
    const route = useRoute()

    const hasChildren = computed(
        () => props.node.children && props.node.children.length
    )

    const nodeClick = () => {
      emit('nodeClick', props.node)
      expanded.value = !expanded.value
      if (!hasChildren.value) {
        console.log("last child")
      }
    }

    return {expanded, hasChildren, route, nodeClick}
  },
}
</script>
<style scoped lang="scss">
.node {
  display: flex;
  gap: 16px;
  justify-content: space-between;
  align-items: center;
  padding: 8px 16px;
  color: #535353;
  font-size: 14px;
  line-height: 20px;
  text-decoration: none;

  &__item {
    display: flex;
    gap: 12px;
    align-items: center;
    cursor: pointer;
    i.fa-circle {
      font-size: 12px;
    }
  }
  &.child.active {
    color: #365f91;
    font-weight: 500;
  }
  &:not(.child).active {
    background-color: #365f91;
    color: #FFFFFF;
  }

  &__icon {
    transition: 0.3s ease;
  }


  &.router-link-active {

    svg {
      stroke: white;
    }
  }
}

</style>


