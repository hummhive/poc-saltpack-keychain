<script>
 import PSpace from '../layout/PSpace.svelte'
 import DefLink from '../text/DefLink.svelte'
</script>

<section class="section white-bg">
 <div class="container">
	 <h1 class="title">Keypairs</h1>
		<h2 class="subtitle">The need for strong keypairs.</h2>

  <p>
   Saltpack uses <DefLink url={"https://ed25519.cr.yp.to/"} text={"Ed25519"} /> cryptographic keypairs.<br />
   Both the private and public key are 32 bytes and the keypair can be generated deterministically from a seed.
  </p>

  <PSpace />

  <p>
   The saltpack encryption is only as strong as the weakest secret across all recipients.<br />
   If <strong>any</strong> recipient has their seed or secret stolen then encrypted messages can be read.<br />
   This is similar to a user having their username and password stolen in a traditional login system.<br />
   The difference here is that we are also publishing the password database alongside the login system.<br />
   The history of all passwords everywhere shows that users consistently choose <DefLink text={"terrible passwords"} url={"https://en.wikipedia.org/wiki/Password_cracking"} />.<br />
   The only good option from the sender's perspective is to require that all recipients choose a cryptographically random private key.
  </p>

  <PSpace />

 </div>
</section>
