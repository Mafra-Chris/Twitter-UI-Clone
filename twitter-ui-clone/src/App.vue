<template>
  <div id="app" class="flex container h-screen w-full">
    <div
      class="w-1/5 border-r border-lighter px-8 py-2 flex flex-col justify-between"
    >
      <div>
        <button
          class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue"
        >
          <i class="fab fa-twitter"></i>
        </button>
        <div>
          <button
            v-for="tab in tabs"
            v-bind:key="tab"
            @click="id = tab.id"
            :class="`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${
              id === tab.id ? 'text-blue' : ''
            }`"
          >
            <i :class="`${tab.icon} text-2xl mr-4 text-left`"></i>
            <p class="text-lg font-semibold text-left">{{ tab.title }}</p>
          </button>
        </div>
        <button
          class="text-white bg-blue rounded-full font-semibold focus:outline-none w-full p-3 hover:bg-darkblue"
        >
          Tweet
        </button>
      </div>
      <div class="w-full">
        <button class="flex items-center w-full hover:bg-lighblue rounded-full p-2 focus:outline-none">
          <img src="profile.jpg" class="w-12 h-10 rounded-full" />
          <div class="ml-4">
            <p class="text-sm font-bold leading-tight">Chris Mafra</p>
            <p class="text-sm leading-tight">@chris</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      tabs: [
        { icon: "fas fa-home", title: "Home", id: "home" },
        { icon: "fas fa-hashtag", title: "Explore", id: "explore" },
        { icon: "fas fa-bell", title: "Notifications", id: "notifications" },
        { icon: "fas fa-envelope", title: "Messages", id: "messages" },
        { icon: "fas fa-bookmark", title: "Bookmarks", id: "bookmarks" },
        { icon: "fas fa-clipboard-list", title: "Lists", id: "lists" },
        { icon: "fas fa-user", title: "Profile", id: "profile" },
        { icon: "fas fa-ellipsis-h", title: "More", id: "more" },
      ],
      id: "home",
    };
  },
};
</script>

<style></style>
