<script setup>
      import { RouterLink } from "vue-router";
      import useSkills from "../../composables/skill";
      import { onMounted } from "vue";

      const { skills, getSkills , destroySkill } = useSkills();
      onMounted(() =>getSkills());

</script>

<template>
      <div class="mt-12">
            <div class="flex justify-end m-2 p-2">
                  <RouterLink :to="{name: 'SkillCreate'}"
                  class="px-4 py-2 bg-indigo-500 hover:bg-indigo-700 rounded text-white">
                        + New Skill
                  </RouterLink>
            </div>
            
            <div class="relative overflow-x-auto">
                  <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                  <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                        <tr>
                              <th scope="col" class="px-6 py-3">
                              Name
                              </th>
                              <th scope="col" class="px-6 py-3">
                              Slug
                              </th>
                              <th scope="col" class="px-6 py-3">
                              Others
                              </th>
                        </tr>
                  </thead>
                  <tbody>
                        <tr v-for="skill in skills" :key="skill.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                              <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                              {{ skill.name }}
                              </th>
                              <td class="px-6 py-4">
                              {{ skill.slug }}
                              </td>
                              <td class="px-6 py-4">
                                    <RouterLink :to="{name: 'SkillEdit', params: { id: skill.id }}"
                                    class="px-4 py-2 mr-4 bg-green-600 hover:bg-green-800 rounded text-white">
                                          Edit
                                    </RouterLink>
                                    <button @click="destroySkill(skill.id)"
                                    class="px-4 py-2 mr-4 bg-red-600 hover:bg-red-800 rounded text-white">
                                          Delete
                                    </button>
                              </td>
                        </tr>
                  </tbody>
                  </table>
            </div>
  
      </div>
</template>

