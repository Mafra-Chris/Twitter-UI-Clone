<template>
	<div id="app" class="flex container h-screen w-full">
		<!-- Left Navbar -->
		<div class="lg:w-1/5 border-r border-lighter lpx-2 lg:px-6 py-2 flex flex-col justify-between">
			<div>
				<button class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue">
					<i class="fab fa-twitter"></i>
				</button>
				<div>
					<button
						v-for="tab in tabs"
						v-bind:key="tab"
						@click="id = tab.id"
						:class="
							`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 
						${id === tab.id ? 'text-blue' : ''}`
						"
					>
						<i :class="`${tab.icon} text-2xl mr-4 text-left`"></i>
						<p class="hidden lg:block text-lg font-semibold text-left">
							{{ tab.title }}
						</p>
					</button>
				</div>
				<button class="text-white bg-blue rounded-full font-semibold focus:outline-none w-12 h-12 lg:h-auto lg:w-full p-3 hover:bg-darkblue">
					<p class="hidden lg:block">Tweet</p>
					<i class="fas fa-plus lg:hidden"></i>
				</button>
			</div>
			<div class="lg:w-full relative">
				<button @click="dropdown = true" class="flex items-center w-full hover:bg-lighblue rounded-full p-2 focus:outline-none">
					<img src="profile.jpg" class="w-12 h-12 rounded-full" />
					<div class="hidden lg:block ml-4">
						<p class="text-sm font-bold leading-tight">
							Chris Mafra
						</p>
						<p class="text-sm leading-tight">@chris</p>
					</div>
					<i class="hidden lg:block fas fa-angle-down ml-auto text-lg"></i>
				</button>
				<div v-if="dropdown === true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-16">
					<button @click="dropdown = false" class="flex items-center w-full hover:bg-lightest p-4 focus:outline-none">
						<img src="profile.jpg" class="w-12 h-12 rounded-full" />
						<div class="ml-4">
							<p class="text-sm font-bold leading-tight">
								Chris Mafra
							</p>
							<p class="text-sm leading-tight">@chris</p>
						</div>
						<i class="fas fa-check ml-auto text-blue"></i>
					</button>
					<button
						@click="dropdown = false"
						class="w-full text-left hover:bg-lightest border-t border-lighter p4 text-sm focus:outline-none"
					>
						<p class="p-3">Add an existing account</p>
					</button>
					<button
						@click="dropdown = false"
						class="w-full text-left hover:bg-lightest border-t border-lighter p4 text-sm focus:outline-none"
					>
						<p class="p-3">Log out @chris</p>
					</button>
				</div>
			</div>
		</div>
		<!-- Tweets -->
		<div class="w-1/2 h-full">

		</div>
		<!-- Trends -->
		<div class="w-1/3 h-full border-l border-lighter py-2 px-6 overfloe-y-scroll relative">
			<input class="pl-12 rounded-full w-full p-2 bg-lighter text-sm mb-4 focus:outline-none" placeholder="Search Twitter ">
			<i class="fas fa-search absolute left-0 top-0 mt-5 ml-12 text-sm text-light"></i>
			<div class="w-full rounded-lg bg-lightest">
				<div class="flex items-center justify-between p-3">
					<p class="text-lg font-bold">Trends for You</p>
					<i class="fas fa-cog text-lg text-blue"></i>
				</div>
				<button v-for="trend in trending" v-bind:key="trend" class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter focus:outline-none">
					<div>
						<p class="text-sm text-left leading-tight text-dark">{{ trend.top }}</p>
						<p class="font-bold text-left leading-tight">{{ trend.title }}</p>
						<p class="text-left leading-tight text-dark">{{ trend.bottom }}</p>
					</div>
					<i class="fas fa-angle-down text-lg text-dark"></i>
				</button>
				<button class="p-3 w-full hover:bg-lighter text-left text-blue border-t border-lighter">
					Show More
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
				{
					icon: "fas fa-bell",
					title: "Notifications",
					id: "notifications",
				},
				{ icon: "fas fa-envelope", title: "Messages", id: "messages" },
				{
					icon: "fas fa-bookmark",
					title: "Bookmarks",
					id: "bookmarks",
				},
				{ icon: "fas fa-clipboard-list", title: "Lists", id: "lists" },
				{ icon: "fas fa-user", title: "Profile", id: "profile" },
				{ icon: "fas fa-ellipsis-h", title: "More", id: "more" },
			],
			id: "home",
			dropdown: false,
			trending: [
				{top: 'Trending in TX', title: 'Gigi', bottom: 'Trending with: Rip Gigi'},
				{top: 'Music', title: 'We Won', bottom: '135k Tweets'},
				{top: 'Pop', title: 'Blue Ivy', bottom: '40k Tweets'},
				{top: 'Trending in US', title: 'Denim Day', bottom: '40k Tweets'},
				{top: 'Trending', title: 'When Beyonce', bottom: '25.4k Tweets'},
			],
		};
	},
};
</script>

<style></style>
