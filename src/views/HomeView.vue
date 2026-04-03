<template>
	<main class="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-cyan-50 px-4 py-4 text-slate-800 sm:px-6 lg:px-8">
		<div class="mx-auto flex max-w-7xl flex-col gap-4">
			<header class="flex flex-col gap-3 rounded-3xl border border-slate-200/80 bg-white/80 p-4 shadow-lg shadow-slate-200/60 backdrop-blur md:flex-row md:items-center md:justify-between">
				<div class="flex items-center gap-3">
					<div class="grid h-11 w-11 place-items-center rounded-2xl bg-gradient-to-br from-blue-600 to-cyan-500 text-base font-extrabold text-white shadow-lg shadow-blue-500/25">
						S
					</div>
					<div>
						<p class="text-xs font-semibold uppercase tracking-[0.22em] text-slate-500">Stratix</p>
						<h1 class="mt-1 text-xl font-bold tracking-tight text-slate-900 sm:text-2xl">Team Workspace</h1>
					</div>
				</div>
				<button
					class="inline-flex items-center justify-center rounded-2xl bg-blue-600 px-4 py-2.5 text-sm font-semibold text-white shadow-lg shadow-blue-600/20 transition hover:-translate-y-0.5 hover:bg-blue-700 active:translate-y-0"
					type="button"
					@click="toggle('createticketmodal')"
				>
					+ Nouveau ticket
				</button>
			</header>

			<section
				id="createticketmodal"
				class="hidden overflow-hidden rounded-3xl border border-slate-200/80 bg-white/90 shadow-2xl shadow-slate-200/70 backdrop-blur"
			>
				<div class="relative overflow-hidden p-5 sm:p-6">
					<div class="pointer-events-none absolute inset-0 bg-[radial-gradient(circle_at_top_right,rgba(59,130,246,0.12),transparent_38%)]"></div>
					<header class="relative z-10 mb-5 flex flex-col gap-3 md:flex-row md:items-end md:justify-between">
						<div>
							<p class="text-xs font-semibold uppercase tracking-[0.22em] text-slate-500">Creation rapide</p>
							<h2 class="mt-1 text-2xl font-bold tracking-tight text-slate-900">Ajouter un nouveau ticket</h2>
						</div>
						<p class="max-w-md text-sm leading-6 text-slate-500">
							Formulaire statique pour structurer un ticket avant integration.
						</p>
					</header>

					<form class="relative z-10 grid gap-5" @submit.prevent="handleSubmit">
						<label class="grid gap-2">
							<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Titre du ticket</span>
							<input
								type="text"
								name="title"
								placeholder="Ex: Corriger le bug de login"
								class="w-full rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition placeholder:text-slate-400 focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
							/>
						</label>

						<label class="grid gap-2">
							<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Description</span>
							<textarea
								name="description"
								rows="4"
								placeholder="Decrire le besoin, le contexte et les criteres de validation"
								class="min-h-32 w-full resize-y rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition placeholder:text-slate-400 focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
							></textarea>
						</label>

						<div class="grid gap-4 md:grid-cols-2">
							<label class="grid gap-2">
								<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Priorite</span>
								<select
									name="priority"
									class="w-full rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
								>
									<option value="">Choisir une priorite</option>
									<option value="p1">P1 - Critique</option>
									<option value="p2">P2 - Haute</option>
									<option value="p3">P3 - Moyenne</option>
									<option value="p4">P4 - Basse</option>
								</select>
							</label>

							<label class="grid gap-2">
								<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Statut</span>
								<select
									name="status"
									class="w-full rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
								>
									<option value="todo">A faire</option>
									<option value="progress">En cours</option>
									<option value="review">En revue</option>
								</select>
							</label>

							<label class="grid gap-2">
								<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Responsable</span>
								<input
									type="text"
									name="assignee"
									placeholder="Ex: Amine"
									class="w-full rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition placeholder:text-slate-400 focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
								/>
							</label>

							<label class="grid gap-2">
								<span class="text-xs font-semibold uppercase tracking-[0.18em] text-slate-500">Date limite</span>
								<input
									type="date"
									name="dueDate"
									class="w-full rounded-2xl border border-slate-200 bg-white px-4 py-3 text-slate-900 outline-none transition focus:border-blue-500 focus:ring-4 focus:ring-blue-500/15"
								/>
							</label>
						</div>

						<div class="flex flex-col gap-3 border-t border-slate-200 pt-4 md:flex-row md:items-center md:justify-between">
							<label class="inline-flex items-center gap-2 text-sm text-slate-600">
								<input name="notifyTeam" type="checkbox" checked class="h-4 w-4 rounded border-slate-300 text-blue-600 focus:ring-blue-500" />
								<span>Notifier l'equipe</span>
							</label>
							<div class="flex flex-col gap-3 sm:flex-row sm:items-center">
								<button
									class="inline-flex items-center justify-center rounded-2xl border border-slate-200 bg-white px-4 py-3 text-sm font-semibold text-slate-700 transition hover:border-slate-300 hover:bg-slate-50"
									type="button"
									@click="toggle('createticketmodal')"
								>
									Annuler
								</button>
								<button
									class="inline-flex items-center justify-center rounded-2xl bg-blue-600 px-5 py-3 text-sm font-semibold text-white shadow-lg shadow-blue-600/20 transition hover:-translate-y-0.5 hover:bg-blue-700 active:translate-y-0"
									type="submit"
								>
									Creer le ticket
								</button>
							</div>
						</div>
					</form>
				</div>
			</section>

			<section class="grid gap-4 md:grid-cols-2 xl:grid-cols-4">
				<article class="rounded-2xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<p class="text-sm text-slate-500">Tickets ouverts</p>
					<strong class="mt-2 block text-3xl font-bold text-slate-900">{{ count({ status: 'todo' } as Task) }}</strong>
				</article>
				<article class="rounded-2xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<p class="text-sm text-slate-500">En cours</p>
					<strong class="mt-2 block text-3xl font-bold text-slate-900">{{ count({ status: 'progress' } as Task) }}</strong>
				</article>
				<article class="rounded-2xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<p class="text-sm text-slate-500">En revue</p>
					<strong class="mt-2 block text-3xl font-bold text-slate-900">{{ count({ status: 'review' } as Task) }}</strong>
				</article>
			</section>

			<section class="grid gap-4 lg:grid-cols-3">
				<article class="grid gap-3 rounded-3xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<h2 class="text-base font-bold text-slate-900">A faire</h2>
					<div v-for="task in tasks.filter(t => t.status === 'todo')" :key="task.title" class="rounded-2xl border border-slate-200 border-l-4 border-l-blue-600 bg-slate-50 p-4">
						<h3 class="text-sm font-semibold text-slate-900">{{ task.title }}</h3>
						<p class="mt-2 text-sm leading-6 text-slate-500">{{ task.description }}</p>
					</div>
                    <div v-if="!tasks.some(t => t.status === 'todo')" class="flex h-full items-center justify-center rounded-2xl border border-slate-200 border-dashed bg-slate-50 p-4">
                        <p class="text-sm italic text-slate-400">Aucun ticket a faire</p>
                    </div>
				</article>

                <article  class="grid gap-3 rounded-3xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<h2 class="text-base font-bold text-slate-900">En cours</h2>
					<div v-for="task in tasks.filter(t => t.status === 'progress')" :key="task.title" class="rounded-2xl border border-slate-200 border-l-4 border-l-emerald-500 bg-slate-50 p-4">
						<h3 class="text-sm font-semibold text-slate-900">{{ task.title }}</h3>
						<p class="mt-2 text-sm leading-6 text-slate-500">{{ task.description }}</p>
					</div>
                    <div v-if="!tasks.some(t => t.status === 'progress')" class="flex h-full items-center justify-center rounded-2xl border border-slate-200 border-dashed bg-slate-50 p-4">
                        <p class="text-sm italic text-slate-400">Aucun ticket en cours</p>
                    </div>
				</article>

				<article  class="grid gap-3 rounded-3xl border border-slate-200 bg-white/90 p-4 shadow-lg shadow-slate-200/60">
					<h2 class="text-base font-bold text-slate-900">Termine</h2>
					<div v-for="task in tasks.filter(t => t.status === 'review')" :key="task.title" class="rounded-2xl border border-slate-200 border-l-4 border-l-emerald-500 bg-slate-50 p-4">
						<h3 class="text-sm font-semibold text-slate-900">{{ task.title }}</h3>
						<p class="mt-2 text-sm leading-6 text-slate-500">{{ task.description }}</p>
					</div>
                    <div v-if="!tasks.some(t => t.status === 'review')" class="flex h-full items-center justify-center rounded-2xl border border-slate-200 border-dashed bg-slate-50 p-4">
                        <p class="text-sm italic text-slate-400">Aucun ticket termine</p>
                    </div>
				</article>
			</section>
		</div>
	</main>
</template>
<script lang="ts">
interface Task {
	title: string;
	description: string;
	priority: string;
	status: string;
	assignee: string;
	dueDate: string;
	notifyTeam: boolean;
}

export default {
	name: 'HomeView',

	data() {
		return {
			tasks: [] as Task[],
			form: {
				title: '',
				description: '',
				priority: '',
				status: 'todo',
				assignee: '',
				dueDate: '',
				notifyTeam: true,
			} as Task,
		};
	},

	methods: {
		toggle(id: string) {
			const el = document.getElementById(id);
			if (el) {
				el.classList.toggle('hidden');
			}
		},
		handleSubmit(event: Event) {
			const formEl = event.target as HTMLFormElement | null;
			if (!formEl) return;

			const values = new FormData(formEl);

			this.form.title = String(values.get('title') ?? '');
			this.form.description = String(values.get('description') ?? '');
			this.form.priority = String(values.get('priority') ?? '');
			this.form.status = String(values.get('status') ?? 'todo');
			this.form.assignee = String(values.get('assignee') ?? '');
			this.form.dueDate = String(values.get('dueDate') ?? '');
			this.form.notifyTeam = values.get('notifyTeam') !== null;

			this.tasks.push({ ...this.form });
			formEl.reset();
			this.toggle('createticketmodal');
		},
		count(task: Task) {
			return this.tasks.filter((item) => item.status === task.status).length;
		}
	}
};
</script>