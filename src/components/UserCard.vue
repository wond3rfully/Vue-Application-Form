<script>
export default {
  name: "UserCard",

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
        <span class="skillsSpan"><span
          v-for="(skill, index) in skills"
          :key="`dt-${index}}`"
          data="skill"
          >{{ skill + " -" }}</span
        ></span>

        <!-- rah mapiasa v-for ka te hi-modifier index 1 en particulier d aona -->

        
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.cardContainer {
  position: absolute;
  width: 225px;
  height: 200px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  border: 1px solid rgba(0, 0, 0, 0.3);
  padding: 18px;
}

.userName {
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  text-align: left;
}

.userEmail {
  font-size: 12px;
  font-weight: 400;
  line-height: 14px;
  letter-spacing: 0em;
  text-align: left;
  color: #9a9a9a;
}

.avatar {
  width: 45px;
  height: 45px;
  border: 1px solid rgba(0, 0, 0, 0.3);
  border-radius: 100%;
}
.userIdentity {
  display: flex;
  flex-direction: row;
  gap: 13px;
}

.identityText {
  display: flex;
  flex-direction: column;
  gap: 9px;
}

.userInfo {
  display: flex;
  flex-direction: column;
  gap: 13px;
  width: 80%;

}

.aboutUser {
  display: flex;
  gap: 4px;
  align-items: center;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  text-align: left;
}

.skillsSpan{
    top: 8px;
    position: relative;
    display: flex;
    flex-wrap: wrap;
}
</style>
