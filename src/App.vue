<template>
  <div id="app" class="flex container h-screen w-full">
    <!-- side nav -->
    <div class="w-1/5 border-r border-lighter px-2 lg:px-6 py-2 flex flex-col justify-between">
      <div>
        <button class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue">
          <i class="fab fa-twitter"></i>
        </button>
        <div>
          <button v-for="tab in tabs" v-bind:key="tab.id" @click="id = tab.id" :class="`hover:text-blue focus:outline-none flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${ id === tab.id ? 'text-blue' : ''}`">
              <i :class="`${ tab.icon } text-2xl mr-4`"></i>
              <p class="text-lg font-semibold text-left">{{ tab.title }}</p>
          </button>  
        </div> 
        <button class="text-white bg-blue w-12 h-12 lg:h-auto lg:w-full p-3 rounded-full font-semibold focus:outline-none hover:bg-darkblue">
          <p class="hidden lg:block">Tweet</p>
          <i class="fas fa-plus lg:hidden"></i>
        </button >
      </div>
      <div class="lg:w-full relative">
        <button @click="dropdown = true" class="flex items-center w-full hover:bg-lightblue focus:outline-none rounded-full p-2">
          <img src="profile.jpeg" class="w-10 h-10 rounded-full border border-lighter" alt="">
          <div class="ml-4 hidden lg:block">
            <p class="text-sm font-bold leading-tight">Nuno Pereira</p>
            <p class="text-sm leading-tight">@nunocgp</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg hidden lg:block"></i>
        </button>
        <div v-if="dropdown === true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-16">
          <button @click="dropdown = false" class="flex items-center w-full hover:bg-lightest focus:outline-none p-2">
            <img src="profile.jpeg" class="w-10 h-10 rounded-full border border-lighter" alt="">
            <div class="ml-4">
              <p class="text-sm font-bold leading-tight">{{ name }}</p>
              <p class="text-sm leading-tight">@ {{ handler }}</p>
            </div>
            <i class="fas fa-check ml-auto text-blue"></i>
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter p-3 test-sm focus:outline-none">
            Add en existing account
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter p-3 test-sm focus:outline-none">
            Log out @ {{ handler }}
          </button>
        </div>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      name: 'Nuno Pereira',
      handler: 'nunocgp',
      tabs: [
        {icon: 'fas fa-home', title: 'Home', id:'home'},
        {icon: 'fas fa-hashtag', title: 'Explore', id: 'explore'},
        {icon: 'far fa-bell', title: 'Notifications', id: 'notifications'},
        {icon: 'far fa-envelope', title: 'Messages', id: 'messages'},
        {icon: 'far fa-bookmark', title: 'Bookmarks', id: 'bookmarks'},
        {icon: 'fas fa-clipboard-list', title: 'Lists', id: 'lists'},
        {icon: 'far fa-user', title: 'Profile', id: 'profile'},
        {icon: 'fas fa-ellipsis-h', title: 'More', id: 'more'}
      ],
      id: 'home',
      dropdown: false,
    }
  }
}
</script>
