<template>
    <div :id="id">
        <slot />
    </div>
</template>

<script>
import priorityNav from 'priority-nav';

let existsOnPage = false;

export default {

    props: {
        options: { type: Object, default: () => ({ }) }
    },

    data: () => ({
        id: `priority__${Math.random().toString(26).substr(2)}`,
    }),

    mounted() {
        if (existsOnPage) {
            throw new Error('Only one priority nav is allowed per page.');
        }
        existsOnPage = true;

        const options = JSON.parse(JSON.stringify(this.options));
        options.mainNav = `#${this.id} > *`;
        options.mainNavWrapper = `#${this.id}`;
        options.moved = e => this.$emit('moved', e);
        options.movedBack = e => this.$emit('moved-back', e);

        priorityNav.init(options);
    },

    beforeDestroy() {
        priorityNav.destroy();
        existsOnPage = false;
    }
}
</script>


<style lang="css">
    /*
 * Core styles for PriorityNav.js
 * These styles are not optional and should always be included
 *
 * Free to use under the MIT License.
 * http://twitter.com/GijsRoge
 */
.priority-nav {
  white-space: nowrap;
  /*
    * Makes sure the menu's are inline-block so they don't take up
    * the entire width of its parent. This will break the plugin.
    */
}

.priority-nav > ul {
  display: inline-block;
}

.priority-nav > ul > li {
  display: inline-block;
  width: 200px;
 }

.priority-nav-has-dropdown .priority-nav__dropdown-toggle {
  position: relative;
}

.priority-nav__wrapper {
  position: relative;
}

.priority-nav__dropdown {
  position: absolute;
  visibility: hidden;
}

.priority-nav__dropdown.show {
  visibility: visible;
}

.priority-nav__dropdown-toggle {
  visibility: hidden;
  position: absolute;
}

.priority-nav-is-visible {
  visibility: visible;
}

.priority-nav-is-hidden {
  visibility: hidden;
}
</style>