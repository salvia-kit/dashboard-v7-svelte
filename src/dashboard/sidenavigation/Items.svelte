<script>
	import data from './data';
	import { page } from '$app/stores';

	const style = {
		title: `mx-4 text-sm`,
		section: `font-thin pl-5 text-white mb-6 uppercase lg:pl-6`,
		active: `border-l-4 border-white lg:border-l-0 lg:border-r-4`,
		link: `flex items-center text-gray-200 justify-start my-2 p-3 w-full hover:text-white`
	};
</script>

<ul class="md:pl-6">
	<li>
		{#each data as section, i (section.section)}
			<div class="mb-12">
				<div class={style.section}>{section.section}</div>

				{#each section.content as item, i (item.title)}
					<a
						href={item.link}
						class={`${style.link} ${item.link === $page.url.pathname ? style.active : ''}`}
					>
						<span><svelte:component this={item.icon} /></span>
						<span class={style.title}>{item.title}</span>
					</a>
				{/each}
			</div>
		{/each}
	</li>
</ul>
