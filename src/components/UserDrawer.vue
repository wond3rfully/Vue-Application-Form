<script>
export default {
  name: "UserDrawer",

  props: {
    firstName: {
      type: String,
      //required: true
    },

    lastName: {
      type: String,
      //required: true
    },

    email: {
      type: String,
      //required: true
    },

    role: {
      type: String,
      //required: true
    },

    age: {
      type: String,
      //required: true
    },

    skills: {
      type: Object,
      //required: true
    },

    experiences: {
      type: Object,
    },
    /* 
        experienceDate : {
            type: String,
        },

        experienceTitle : {
            type: String,
        },

        experienceDescription : {
            type: String,
        }, */
  },
};
</script>

<template>
  <div class="cardContainer">
    <div class="userIdentity">
      <div class="avatar"></div>
      <div class="identityText">
        <span class="userName">{{ firstName + " " + lastName }}</span>
        <span class="userEmail">{{ email }}</span>
      </div>
    </div>
    <div class="userInfo">
      <div class="aboutUser userRole">
        <div class="icon">
          <img src="../../public/user.png" alt="" />
        </div>
        <span>{{ role }}</span>
      </div>
      <div class="aboutUser userAge">
        <div class="icon">
          <img src="../../public/age.png" alt="" />
        </div>
        <span>{{ age }}</span>
      </div>
      <div class="aboutUser userSkills">
        <div class="icon">
          <img src="../../public/exp.png" alt="" />
        </div>

        <!-- rah mapiasa v-for ka te hi-modifier index 1 en particulier d aona -->

        <span
          v-for="(skill, index) in skills"
          :key="`dt-${index}}`"
          data="skill"
          >{{ skill + " -" }}</span
        >
      </div>

      <div
        class="experienceSection"
        v-for="(exp, index) in experiences"
        :key="`dt-${index}}`"
        data="exp"
      >
        <div class="drawerDate">
          <div class="cardio"></div>
          <span>{{ experiences[index].experienceDate }}</span>
        </div>

        <div class="drawerDesc">
          <div class="line"></div>
          <div class="desc">
            <span>{{ experiences[index].experienceTitle }}</span>
            <span class="description">{{
              experiences[index].experienceDescription
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.experienceSection {
  display: flex;
  flex-direction: column;
  margin-top: 30px;

  .drawerDate {
    display: flex;
    gap: 20px;

    .cardio {
      width: 15px;
      height: 15px;
      border-radius: 100%;
      background-color: rgba(0, 0, 0, 0.4);
    }
  }


  .drawerDesc{
    margin-left: 6px;
    display: flex;
    gap: 28px;
    height: fit-content;


    .line{
    height: auto;
    width: 2px;
    background-color: rgba(0, 0, 0, 0.4);

  }

  .desc{
    display: flex;
    flex-direction: column;
  }
  }
  
  .description {
    margin-top: 20px;
  }
}

.identityText {
  display: flex;
  flex-direction: column;
}

.aboutUser {
  display: flex;
  gap: 10px;
  align-items: center;
}
</style>
