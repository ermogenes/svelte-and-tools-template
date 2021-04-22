<script>
	// Bulma with Svelma
	import { Button, Modal} from 'svelma';

	// FontAwesome with Fa-Svelte
	import Icon from 'fa-svelte';
	import { faClock } from '@fortawesome/free-solid-svg-icons';

	// Date-fns
	import { formatDistance, subDays } from 'date-fns';
	import { ptBR } from 'date-fns/locale';

	export let name;
  	let active = false;
	let dayBeforeYesterday = formatDistance(subDays(new Date(), 2), new Date(), { addSuffix: true, locale: ptBR });
</script>

<style global lang="scss">
	@import "main.scss";
</style>

<main>
	<h1 class="title is-1">Hello {name}!</h1>

	<p>Bulma with Svelma ▶
		<Button on:click={() => active = !active} type="is-primary is-small">Open modal</Button>
		<Modal bind:active={active}>
			<p class="image is-4by3">
				<img alt="Test" src="https://via.placeholder.com/1280x920"/>
			</p>
		</Modal>
	</p>

	<p>fa-svelte ▶ <Icon icon={faClock}></Icon></p>
	<p>date-fns ▶ Anteontem foi {dayBeforeYesterday}!</p>
</main>
