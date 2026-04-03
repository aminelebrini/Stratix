<template>
	<main class="home-page">
		<header class="topbar">
			<div class="brand">
				<div class="brand-mark">S</div>
				<div>
					<p class="kicker">Stratix</p>
					<h1>Team Workspace</h1>
				</div>
			</div>
			<button class="new-ticket" type="button">+ Nouveau ticket</button>
		</header>

		<section class="stats-grid">
			<article class="stat-card">
				<p>Tickets ouverts</p>
				<strong>24</strong>
			</article>
			<article class="stat-card">
				<p>En revue</p>
				<strong>8</strong>
			</article>
			<article class="stat-card">
				<p>Bloques</p>
				<strong>3</strong>
			</article>
			<article class="stat-card">
				<p>Livres cette semaine</p>
				<strong>17</strong>
			</article>
		</section>

		<section class="board">
			<article class="column">
				<h2>A faire</h2>
				<div class="ticket">
					<h3>STR-102 Refonte page profil</h3>
					<p>Mettre a jour les composants avatar et permissions.</p>
				</div>
				<div class="ticket">
					<h3>STR-118 API commentaires</h3>
					<p>Ajouter endpoint pour reactions et tri chronologique.</p>
				</div>
			</article>

			<article class="column">
				<h2>En cours</h2>
				<div class="ticket">
					<h3>STR-099 Auth 2FA</h3>
					<p>Activation OTP et ecran de verification.</p>
				</div>
				<div class="ticket">
					<h3>STR-121 Dashboard mobile</h3>
					<p>Optimiser les cartes KPI pour ecrans < 768px.</p>
				</div>
			</article>

			<article class="column">
				<h2>Termine</h2>
				<div class="ticket done">
					<h3>STR-087 Import CSV</h3>
					<p>Validation schema et rapport d erreurs.</p>
				</div>
				<div class="ticket done">
					<h3>STR-093 Filtre priorites</h3>
					<p>Ajout du filtre P1/P2/P3 sur le backlog.</p>
				</div>
			</article>
		</section>
	</main>
</template>

<style scoped>
.home-page {
	--bg: #edf3ff;
	--panel: #ffffff;
	--text: #1a2b4d;
	--muted: #5f7193;
	--line: #d7e2f6;
	--accent: #0059d6;
	--accent-soft: #eaf1ff;

	min-height: 100vh;
	padding: clamp(1rem, 2vw, 2rem);
	color: var(--text);
	background:
		radial-gradient(circle at 15% 15%, #dae8ff 0, transparent 40%),
		radial-gradient(circle at 90% 90%, #d5f2ff 0, transparent 38%),
		linear-gradient(135deg, #f2f7ff 0%, #fbfdff 100%);
	font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.topbar {
	display: flex;
	align-items: center;
	justify-content: space-between;
	gap: 1rem;
	margin-bottom: 1rem;
}

.brand {
	display: flex;
	align-items: center;
	gap: 0.8rem;
}

.brand-mark {
	width: 2.3rem;
	height: 2.3rem;
	border-radius: 0.7rem;
	display: grid;
	place-items: center;
	color: #fff;
	font-weight: 800;
	background: linear-gradient(140deg, var(--accent), #0e85ff);
}

.kicker {
	margin: 0;
	font-size: 0.78rem;
	color: var(--muted);
	text-transform: uppercase;
	letter-spacing: 0.06em;
}

h1 {
	margin: 0.1rem 0 0;
	font-size: clamp(1.1rem, 2vw, 1.5rem);
}

.new-ticket {
	border: none;
	border-radius: 0.7rem;
	background: var(--accent);
	color: #fff;
	padding: 0.65rem 0.95rem;
	font-weight: 700;
	cursor: pointer;
}

.stats-grid {
	display: grid;
	grid-template-columns: repeat(4, minmax(0, 1fr));
	gap: 0.8rem;
	margin-bottom: 1rem;
}

.stat-card {
	background: var(--panel);
	border: 1px solid var(--line);
	border-radius: 0.9rem;
	padding: 0.9rem;
}

.stat-card p {
	margin: 0;
	color: var(--muted);
	font-size: 0.88rem;
}

.stat-card strong {
	display: block;
	margin-top: 0.35rem;
	font-size: 1.5rem;
}

.board {
	display: grid;
	grid-template-columns: repeat(3, minmax(0, 1fr));
	gap: 0.8rem;
}

.column {
	background: color-mix(in srgb, var(--panel) 90%, var(--accent-soft));
	border: 1px solid var(--line);
	border-radius: 1rem;
	padding: 0.8rem;
	display: grid;
	gap: 0.7rem;
	align-content: start;
}

h2 {
	margin: 0;
	font-size: 1rem;
}

.ticket {
	background: #fff;
	border: 1px solid var(--line);
	border-left: 4px solid var(--accent);
	border-radius: 0.7rem;
	padding: 0.7rem;
}

.ticket h3 {
	margin: 0;
	font-size: 0.92rem;
}

.ticket p {
	margin: 0.4rem 0 0;
	color: var(--muted);
	font-size: 0.84rem;
}

.ticket.done {
	border-left-color: #2f9e44;
}

@media (max-width: 980px) {
	.stats-grid {
		grid-template-columns: repeat(2, minmax(0, 1fr));
	}

	.board {
		grid-template-columns: 1fr;
	}
}

@media (max-width: 560px) {
	.topbar {
		flex-direction: column;
		align-items: flex-start;
	}
}
</style>