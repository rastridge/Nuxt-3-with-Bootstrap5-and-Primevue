<script setup>
	const router = useRouter()

	const onSubmit = function (state) {
		handleSubmit(state)
	}

	const handleSubmit = async function (state) {
		const runtimeConfig = useRuntimeConfig()
		await useFetch('/accounts/addone', {
			method: 'post',
			body: state,
			headers: {
				firebaseapikey: runtimeConfig.apiSecret,
			},
		})
		navigateTo('/admin/accounts')
	}
</script>

<template>
	<div>
		<Head>
			<Title>Add Account</Title>
		</Head>
		<div class="text-center m-5 display-6">
			<b>Add Account</b>
		</div>

		<div class="root">
			<my-form @submitted="onSubmit" />
		</div>
	</div>
</template>

<style scoped></style>
