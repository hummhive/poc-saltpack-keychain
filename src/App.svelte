<script>
	// @see https://github.com/c0bra/svelma
	import 'bulma/css/bulma.css'
	import '@fortawesome/fontawesome-free/css/all.css'

 import Background from './Background.svelte'
	import SectionSpace from './SectionSpace.svelte'
</script>

<Background/>

<section class="hero is-primary">
 <div class="hero-body">
	 <div class="container">
		 <h1 class="title">
			 POC saltpack keypairs
			</h1>
	</div>
</section>

<SectionSpace/>

<section class="section white-bg">
 <div class="container">
	 <h1 class="title">Overview</h1>
		<h2 class="subtitle">Saltpack encryption for SPAs.</h2>

	 <p>
		 <DefLink url="https://saltpack.org/" text="Saltpack"/> is an encryption format pioneered by <DefLink url="https://keybase.io/" text="Keybase" />.
		</p>

		<p>
		 Saltpack is a messaging protocol that composes the primitives of <DefLink url="https://nacl.cr.yp.to/" text="NaCL" /> and <DefLink url="https://msgpack.org/index.html" text="Messagepack" />.
		</p>

 </div>
</section>
