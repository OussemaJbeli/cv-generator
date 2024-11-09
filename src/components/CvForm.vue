<template>
    <form @submit.prevent="submitForm" class="form_first_part">
      <h2 class="text-2xl font-bold mb-4 text-white text-center w-full">CV Generate</h2>
      <div class="buttons">
        <button type="submit">
          generate
        </button>      
      </div>
      <div class="parts">
        <!-- Profile Section -->
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Name</label>
          <input v-model="formData.Username" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Stephen Colbert"  />
        </div>
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Job Title</label>
          <input v-model="formData.jobTitle" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Designer"  />
        </div>
        <div class="mb-5">
          <label for="message" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">About</label>
          <textarea v-model="formData.About" rows="15" class="input block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Description"></textarea>
        </div>
      </div>

      <div class="parts">
        <!-- Contacts Section -->
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">contacts</label>
          <div v-for="(contact, index) in formData.contacts" :key="index" class="flex space-x-2 mb-2">
            <input v-model="contact.icon" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Icon" />
            <input v-model="contact.data" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Data" />
            <button @click="removeContact(index)" class="btn-danger">Remove</button>
          </div>
          <button @click.prevent="addContact" type="button" class="buttonAdd"><span class="button__text">Add</span><span class="button__icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 24 24" stroke-width="2" stroke-linejoin="round" stroke-linecap="round" stroke="currentColor" height="24" fill="none" class="svg"><line y2="19" y1="5" x2="12" x1="12"></line><line y2="12" y1="12" x2="19" x1="5"></line></svg></span></button>
        </div>
        <!-- Skills Section -->
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Skills</label>
          <div v-for="(skill, index) in formData.skills" :key="index" class="flex space-x-2 mb-2">
            <input v-model="skill.name" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Skill" />
            <input v-model="skill.level" type="number" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Level" />
            <button @click="removeSkill(index)" class="btn-danger">Remove</button>
          </div>
          <button @click.prevent="addSkill" type="button" class="buttonAdd"><span class="button__text">Add</span><span class="button__icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 24 24" stroke-width="2" stroke-linejoin="round" stroke-linecap="round" stroke="currentColor" height="24" fill="none" class="svg"><line y2="19" y1="5" x2="12" x1="12"></line><line y2="12" y1="12" x2="19" x1="5"></line></svg></span></button>
        </div>
        <!-- Social Links Section -->
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Social Links</label>
          <div v-for="(link, index) in formData.socialLinks" :key="index">
            <input v-model="link.handle" type="text" class=" mb-2 input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Link" />
            <div  class="flex space-x-2 mb-2">
              <input v-model="link.platform" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Platform" />
              <input v-model="link.icon" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Icon" />
            </div>
            <button @click="removeSocialLink(index)" class="btn-danger mb-2">Remove</button>
          </div>
          <button @click.prevent="addSocialLink" type="button" class="buttonAdd"><span class="button__text">Add</span><span class="button__icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 24 24" stroke-width="2" stroke-linejoin="round" stroke-linecap="round" stroke="currentColor" height="24" fill="none" class="svg"><line y2="19" y1="5" x2="12" x1="12"></line><line y2="12" y1="12" x2="19" x1="5"></line></svg></span></button>
        </div>
        <!-- hobbies -->
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Hobbies</label>
          <input v-model="formData.hobbies" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Stephen Colbert"  />
        </div>
        <div class="mb-5">
          <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Hobbies</label>
          <div v-for="(hobbie, index) in formData.hobbies" :key="index" class="flex space-x-2 mb-2">
            <input v-model="hobbie.icon" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Icon" />
            <button @click="removeHobbies(index)" class="btn-danger">Remove</button>
          </div>
          <button @click.prevent="addHobbies" type="button" class="buttonAdd"><span class="button__text">Add</span><span class="button__icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 24 24" stroke-width="2" stroke-linejoin="round" stroke-linecap="round" stroke="currentColor" height="24" fill="none" class="svg"><line y2="19" y1="5" x2="12" x1="12"></line><line y2="12" y1="12" x2="19" x1="5"></line></svg></span></button>
        </div>
      </div>

      <div class="parts">
        <!-- Work Experience Section -->
        <DynamicSection
          title="Work Experience"
          :items="formData.workExperience"
          fieldName="position"
          @add-item="addWorkExperience"
          @remove-item="removeWorkExperience"
        />
        <!-- Education Section -->
        <DynamicSection
          title="Education"
          :items="formData.education"
          fieldName="degree"
          @add-item="addEducation"
          @remove-item="removeEducation"
        />
      </div>
    </form>
</template>

<script>
import DynamicSection from './DynamicSection.vue';

export default {
  components: { DynamicSection },
  data() {
    return {
      formData: {
        profilePic: '/eCijVBe.png',
        name: '',
        jobTitle: '',
        About: '',
        contacts: [
          { data: 'local' ,icon: '<i class="fa-solid fa-location-dot"></i>'},
          { data: 'phone' ,icon: '<i class="fa-solid fa-phone"></i>'},
          { data: 'email' ,icon: '<i class="fa-solid fa-envelope"></i>'},
          { data: 'www.portfoli.com' ,icon: '<i class="fa-solid fa-user"></i>'}
        ],
        skills: [{ name: '', level: 0 }],
        workExperience: [{ date: '', position: '', description: '' }],
        education: [{ date: '', degree: '', description: '' }],
        socialLinks: [{ platform: 'Linkedin', handle: 'www.linkkidin.com',icon: '<i class="fa-brands fa-linkedin-in"></i>' }],
        hobbies: [
          { icon: '<i class="fa-solid fa-book"></i>' },
          { icon: '<i class="fa-solid fa-dumbbell"></i>' },
          { icon: '<i class="fa-solid fa-clapperboard"></i>' },
          { icon: '<i class="fa-solid fa-book"></i>' }
        ],
      }
    };
  },
  methods: {
    submitForm() {
      this.$emit('form-submitted', this.formData);
    },
    addContact() {
      this.formData.contacts.push({ data: '',icon: '' });
    },
    removeContact(index) {
      this.formData.contacts.splice(index, 1);
    },
    addSkill() {
      this.formData.skills.push({ name: '', level: 0 });
    },
    removeSkill(index) {
      this.formData.skills.splice(index, 1);
    },
    addWorkExperience() {
      this.formData.workExperience.push({ date: '', position: '', description: '' });
    },
    removeWorkExperience(index) {
      this.formData.workExperience.splice(index, 1);
    },
    addEducation() {
      this.formData.education.push({ date: '', degree: '', description: '' });
    },
    removeEducation(index) {
      this.formData.education.splice(index, 1);
    },
    addSocialLink() {
      this.formData.socialLinks.push({ platform: '', handle: '',icon: '' });
    },
    removeSocialLink(index) {
      this.formData.socialLinks.splice(index, 1);
    },
    addHobbies() {
      this.formData.hobbies.push({icon: '' });
    },
    removeHobbies(index) {
      this.formData.hobbies.splice(index, 1);
    },
  }
};
</script>

<style scoped>
.input {
  width: 100%;
  padding: 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid #ddd;
}
.btn {
  background-color: #007bff;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  cursor: pointer;
}
.btn-primary {
  background-color: #0056b3;
}
.btn-danger {
  background-color: #dc3545;
  color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
}
</style>
