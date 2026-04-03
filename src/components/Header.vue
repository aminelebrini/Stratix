<template>
	<header class="flex flex-col gap-3 md:w-[calc(100%-1rem)] md:flex-row md:items-center md:justify-between">
		<div class="flex items-center gap-3">
			<div class="grid h-11 w-11 place-items-center rounded-2xl bg-gradient-to-br from-blue-600 to-cyan-500 text-base font-extrabold text-white shadow-lg shadow-blue-500/25">
				S
			</div>
			<div>
				<p class="text-xs font-semibold uppercase tracking-[0.22em] text-slate-500">Stratix</p>
				<h1 class="mt-1 text-xl font-bold tracking-tight text-slate-900 sm:text-2xl">Team Workspace</h1>
			</div>
		</div>
		<div v-if="email" class="text-sm font-semibold text-slate-600">
			{{ email }}
		</div>
        <button @click="handlogout" class="inline-flex items-center justify-center rounded-2xl bg-blue-600 px-4 py-2.5 text-sm font-semibold text-white shadow-lg shadow-blue-600/20 transition hover:-translate-y-0.5 hover:bg-blue-700 active:translate-y-0">
            Déconnexion
        </button>
	</header>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'Header',
    props: {
        email: {
            type: String,
            required: true
        },
    },
    methods:{
        handlogout()
        {
                localStorage.removeItem('user');
                this.$router.push('/');
        }
    }
});
</script>