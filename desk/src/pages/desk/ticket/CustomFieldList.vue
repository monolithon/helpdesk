<template>
	<div v-if="!isEmpty(customFields)" class="flex flex-col gap-5 border-b py-4">
		<div
			v-for="field in customFields"
			:key="field.label"
			class="flex flex-col gap-2.5"
		>
			<div class="text-base text-gray-600">{{ field.label }}</div>
			<a :href="field.route || null" target="_blank">
				<div class="flex items-center gap-2">
					<div class="flex h-5 w-5 items-center justify-center">
						<IconWebLink v-if="field.route" class="h-5 w-5 text-gray-600" />
						<IconTeams v-else class="h-5 w-5 text-gray-600" />
					</div>
					<div class="text-base text-gray-800">{{ field.value }}</div>
				</div>
			</a>
		</div>
	</div>
</template>

<script setup lang="ts">
import { isEmpty } from "lodash";
import { computed } from "vue";
import { ticket } from "./data";
import IconTeams from "~icons/espresso/teams";
import IconWebLink from "~icons/espresso/web-link";

const customFields = computed(() => ticket.value?.doc?.custom_fields);
</script>
