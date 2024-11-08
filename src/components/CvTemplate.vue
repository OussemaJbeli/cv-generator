<template>
  <div id="page">
    <!-- Photo and Name Section -->
    <div class="photo-and-name">
      <img :src="profilePicture" class="photo" alt="Profile Picture" />
      <div class="contact-info-box">
        <h1 class="name">{{ name }}</h1>
        <br />
        <h3 class="job-title">{{ jobTitle }}</h3>
        <p class="contact-details">
          Phone: {{ phone }} &nbsp; - &nbsp; Email: {{ email }}
        </p>
      </div>
    </div>

    <!-- Objective Section -->
    <div id="objective">
      <h3>Objective</h3>
      <p>{{ objective }}</p>
    </div>

    <!-- Education Section -->
    <div id="education">
      <h3>Education</h3>
      <table>
        <tr v-for="(edu, index) in education" :key="index">
          <td>{{ edu.year }}</td>
          <td><b>{{ edu.institution }}</b>: {{ edu.degree }}</td>
        </tr>
      </table>
    </div>

    <!-- Work Experience Section -->
    <div id="work">
      <h3>Experience</h3>
      <table>
        <tr v-for="(work, index) in workExperience" :key="index">
          <td>{{ work.year }}</td>
          <td><b>{{ work.company }}</b>: {{ work.position }}</td>
        </tr>
      </table>
    </div>

    <!-- Bio-Data Section -->
    <div id="bio-data">
      <h3>Bio-Data</h3>
      <table>
        <tr>
          <td>F'Name:</td>
          <td><b>{{ fatherName }}</b></td>
        </tr>
        <tr>
          <td>Date of Birth:</td>
          <td><b>{{ dob }}</b></td>
        </tr>
        <tr>
          <td>CNIC:</td>
          <td><b>{{ cnic }}</b></td>
        </tr>
        <tr>
          <td>Religion:</td>
          <td><b>{{ religion }}</b></td>
        </tr>
        <tr>
          <td>Nationality:</td>
          <td><b>{{ nationality }}</b></td>
        </tr>
        <tr>
          <td>Marital Status:</td>
          <td><b>{{ maritalStatus }}</b></td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    formData: Object,
  },
  data() {
    return {
      profilePicture: '/user.png', // Default profile picture path
      name: 'Muhammad Owais',
      jobTitle: 'IT Manager',
      phone: '+92-344-4XX3-1XX',
      email: 'contact@muhammadovi.com',
      objective:
        'To take a challenging and managerial role in the field of Computer programming and implement the expertise and experience gained in this field to develop complex project with efficiency and quality.',
      education: [
        { year: '2002 - 2015', institution: 'ABC School', degree: 'Standard KG-VIII' },
        { year: '2012 - 2014', institution: 'XYZ School', degree: 'Standard IX-X' },
        { year: '2012 - 2014', institution: 'ACCESS', degree: 'English Micro Scholarship Program by US Consulate' },
        { year: '2015 - 2017', institution: 'The Professional\'s Academy', degree: 'Web Designing (HTML, CSS, JS, Bootstrap)' },
        { year: '2015 - 2017', institution: 'Board of Intermediate Karachi', degree: 'Intermediate - Private' },
      ],
      workExperience: [
        { year: '2014 - 2015', company: 'ABC Corp', position: 'IT Manager and Call Service Representative' },
        { year: '2015 - Present', company: 'Reliable Punching', position: 'IT Manager and Customer Service Representative' },
      ],
      fatherName: 'Naseem Akhter',
      dob: '25th November 1996',
      cnic: '42401-XXXXXXX-7',
      religion: 'Islam',
      nationality: 'Pakistani',
      maritalStatus: 'Unmarried',
    };
  },
};
</script>

<style scoped>
* {margin: 0;padding: 0;}

body{font-family: 'Montserrat', sans-serif;}

#page {
    min-height: 200px;
    width: 60%;
    min-width: 600px;
    background: whitesmoke;
    margin: 50px auto;
    padding: 30px;
    color: #27aae1;
}

.photo-and-name {
    /* NO STYLE NEEDED YET */
}

.photo {
    width: 15%;
    min-width: 130px;
    float: left;
    margin-right: 20px;
}

.contact-info-box {
    width: 70.9%;
    display: inline-block;
}

.name {
    margin-bottom: -5px;
}
.job-title {
    display: inline-block;
}

.contact-details {
    background: #27aae1;
    color: white;
    text-align: center;
    margin: auto;
    margin-top: 25px;
    padding: 5px;
    font-size: 15px;
}

#objective {
    
}

#objective h3 {
    border: 1px solid #d3d3d3;
    text-transform: uppercase;
    padding: 5px;
    border-radius: 5px;
    margin: 30px 0 10px;
}

#objective p {
    padding: 0 5px;
    line-height: 25px;
    font-size: 14px;
    color: #000;
}

#education h3 {
    border: 1px solid #d3d3d3;
    text-transform: uppercase;
    padding: 5px;
    border-radius: 5px;
    margin: 30px 0 10px;
}

#education table td {
    padding: 5px;
    font-size: 14px;
    color: #000;
}

#education table tr.school-1 td:first-child {
    width: 120px;
    color: gray;
    padding-bottom: 25px;
}

#education table tr.school-2 td:first-child {
    padding-bottom: 25px;
}

#work h3 {
    border: 1px solid #d3d3d3;
    text-transform: uppercase;
    padding: 5px;
    border-radius: 5px;
    margin: 30px 0 10px;
}

#work table td {
    padding: 5px;
    font-size: 14px;
    color: #000;
}

#work table tr.work-1 td:first-child {
    width: 120px;
    color: gray;
    padding-bottom: 25px;
}

#work table tr.work-1 td {
    padding-bottom: 25px;
}

#work table tr.work-2 td:first-child {
    width: 120px;
    color: gray;
}

#bio-data h3 {
    border: 1px solid #d3d3d3;
    text-transform: uppercase;
    padding: 5px;
    border-radius: 5px;
    margin: 30px 0 10px;
}

#bio-data table td {
    padding: 8px;
    font-size: 15px;
    color: #000;
}

#bio-data table tr td:first-child {
    width: 200px;
}

#bio-data table tr td:nth-child(2) {
    width: 300px;
}
</style>
