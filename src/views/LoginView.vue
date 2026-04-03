<script lang="ts" setup>
import router from '@/router';
import { ref } from 'vue';

  interface User {
    email: string;
    password: string;
  }

  const email = ref<string>('');
  const password = ref<string>('');
  const error = ref<string>('');

  const user : User = {
    email: email.value,
    password: password.value,
  };
  
  const login = () => {

    if(email.value === user.email && password.value === user.password) {
        localStorage.setItem('user', JSON.stringify(user));
        router.push('/home');
        console.log('Connexion réussie');
    } else {
      error.value = 'Email ou mot de passe incorrect';
    }
  }
</script>
<template>
	<main class="auth-page">
		<section class="left-panel">
			<div class="brand-wrap">
				<div class="brand-mark">S</div>
				<div>
					<p class="brand-kicker">Stratix Workspace</p>
					<h1>Connectez-vous a votre espace projet</h1>
					<p class="brand-copy">
						Suivez les tickets, priorisez les sprint goals et gardez toute l'equipe alignee sur une seule vue.
					</p>
				</div>
			</div>

			<ul class="feature-list">
				<li>Board agile en temps reel</li>
				<li>Planification sprint simplifiee</li>
				<li>Suivi des releases et incidents</li>
			</ul>
		</section>

		<section class="right-panel">
			<form class="login-card" @submit.prevent="login">
				<header class="card-header">
					<p class="eyebrow">Bon retour</p>
					<h2>Connexion</h2>
					<p class="subtext">Entrez vos identifiants pour continuer.</p>
				</header>

				<label class="field">
					<span>Email professionnel</span>
					<input
						type="email"
						name="email"
						placeholder="ex: amine@stratix.io"
						autocomplete="email"
						required
					/>
				</label>

				<label class="field">
					<span>Mot de passe</span>
					<div class="password-wrap">
						<input
							type="password"
							name="password"
							placeholder="Minimum 6 caracteres"
							autocomplete="current-password"
							required
						/>
						<button
							type="button"
							class="toggle-btn"
							aria-label="Afficher le mot de passe"
						>
							Afficher
						</button>
					</div>
				</label>

                <span v-if="error" class="error">{{ error }}</span>
				<button class="submit-btn" type="submit">
					Se connecter
				</button>

				<p class="signup-hint">
					Nouveau sur Stratix ?
					<a href="#" class="text-link">Creer un compte</a>
				</p>
			</form>
		</section>
	</main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@500;700;800&family=Space+Grotesk:wght@600;700&display=swap');

:root {
	color-scheme: light;
}

.auth-page {
	--bg-soft: #f4f7ff;
	--surface: #ffffff;
	--text-main: #1f2a44;
	--text-muted: #60708f;
	--accent: #0057d8;
	--accent-strong: #003e9f;
	--line: #d7e1f2;
	--danger: #c0392b;

	min-height: 100vh;
	display: grid;
	grid-template-columns: 1.1fr 1fr;
	background:
		radial-gradient(circle at 10% 20%, #dbe8ff 0%, transparent 45%),
		radial-gradient(circle at 90% 80%, #d6f3ff 0%, transparent 40%),
		linear-gradient(135deg, #eff4ff 0%, #f9fcff 100%);
	color: var(--text-main);
	font-family: 'Manrope', 'Segoe UI', Tahoma, sans-serif;
}

.left-panel {
	padding: clamp(2rem, 4vw, 4rem);
	display: flex;
	flex-direction: column;
	justify-content: center;
	gap: 2rem;
}

.brand-wrap {
	display: grid;
	grid-template-columns: auto 1fr;
	gap: 1.25rem;
	align-items: start;
}

.brand-mark {
	width: 3rem;
	height: 3rem;
	border-radius: 0.9rem;
	display: grid;
	place-items: center;
	background: linear-gradient(145deg, var(--accent), #00a3bf);
	color: #fff;
	font-weight: 800;
	font-family: 'Space Grotesk', 'Manrope', sans-serif;
	box-shadow: 0 12px 20px rgb(0 87 216 / 30%);
}

.brand-kicker {
	margin: 0;
	color: var(--accent);
	font-size: 0.86rem;
	letter-spacing: 0.07em;
	text-transform: uppercase;
}

h1 {
	margin: 0.65rem 0;
	max-width: 18ch;
	font-size: clamp(1.6rem, 3vw, 2.4rem);
	line-height: 1.1;
	font-family: 'Space Grotesk', 'Manrope', sans-serif;
}

.brand-copy {
	margin: 0;
	color: var(--text-muted);
	max-width: 50ch;
}

.feature-list {
	margin: 0;
	padding: 0;
	list-style: none;
	display: grid;
	gap: 0.9rem;
}

.feature-list li {
	position: relative;
	padding-left: 1.3rem;
	color: #304364;
}

.feature-list li::before {
	content: '';
	position: absolute;
	left: 0;
	top: 0.55rem;
	width: 0.5rem;
	height: 0.5rem;
	border-radius: 999px;
	background: var(--accent);
	box-shadow: 0 0 0 0.3rem rgb(0 87 216 / 12%);
}

.right-panel {
	display: grid;
	place-items: center;
	padding: 1.6rem;
}

.login-card {
	width: min(100%, 440px);
	border-radius: 1.2rem;
	padding: clamp(1.4rem, 3vw, 2rem);
	background: color-mix(in srgb, var(--surface) 88%, #eaf2ff);
	border: 1px solid var(--line);
	box-shadow: 0 20px 38px rgb(29 58 102 / 13%);
	display: grid;
	gap: 1rem;
}

.card-header h2 {
	margin: 0.15rem 0 0;
	font-size: 1.8rem;
	font-family: 'Space Grotesk', 'Manrope', sans-serif;
}

.eyebrow {
	margin: 0;
	text-transform: uppercase;
	font-size: 0.78rem;
	letter-spacing: 0.06em;
	color: #4f6d9f;
}

.subtext {
	margin: 0.5rem 0 0;
	color: var(--text-muted);
}

.field {
	display: grid;
	gap: 0.45rem;
}

.field span {
	font-size: 0.92rem;
	color: #3c4e71;
}

input[type='email'],
input[type='password'],
input[type='text'] {
	width: 100%;
	border-radius: 0.72rem;
	border: 1px solid var(--line);
	background: #fff;
	color: #11213f;
	padding: 0.75rem 0.85rem;
	font: inherit;
	transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

input:focus {
	outline: none;
	border-color: var(--accent);
	box-shadow: 0 0 0 0.2rem rgb(0 87 216 / 14%);
}

.password-wrap {
	display: grid;
	grid-template-columns: 1fr auto;
	gap: 0.45rem;
}

.toggle-btn {
	border: 1px solid var(--line);
	border-radius: 0.72rem;
	background: #fff;
	color: #33538a;
	padding: 0 0.8rem;
	font: inherit;
	font-size: 0.88rem;
	cursor: pointer;
}

.actions-row {
	display: flex;
	justify-content: space-between;
	align-items: center;
	gap: 0.7rem;
	flex-wrap: wrap;
}

.check-label {
	display: inline-flex;
	align-items: center;
	gap: 0.45rem;
	color: #395173;
	font-size: 0.9rem;
}

.text-link {
	color: var(--accent);
	font-weight: 700;
	text-decoration: none;
}

.text-link:hover {
	color: var(--accent-strong);
	text-decoration: underline;
}

.error-text {
	margin: 0;
	color: var(--danger);
	font-size: 0.9rem;
}

.submit-btn {
	border: none;
	border-radius: 0.8rem;
	background: linear-gradient(130deg, var(--accent), #0077ff);
	color: #fff;
	font: inherit;
	font-weight: 700;
	padding: 0.85rem 1rem;
	cursor: pointer;
	transition: transform 0.15s ease, box-shadow 0.2s ease;
	box-shadow: 0 12px 22px rgb(0 87 216 / 26%);
}

.submit-btn:hover:enabled {
	transform: translateY(-1px);
}

.submit-btn:disabled {
	opacity: 0.65;
	cursor: not-allowed;
	box-shadow: none;
}

.signup-hint {
	margin: 0.1rem 0 0;
	color: #53678d;
	font-size: 0.9rem;
}

@media (max-width: 900px) {
	.auth-page {
		grid-template-columns: 1fr;
	}

	.left-panel {
		padding-bottom: 0.4rem;
	}
}

@media (max-width: 520px) {
	.left-panel {
		padding: 1.4rem 1rem 0;
	}

	.right-panel {
		padding: 1rem;
	}
}
</style>
