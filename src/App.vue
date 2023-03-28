<script>
import UserCard from "./components/UserCard.vue";
import AddButton from "./components/AddButton.vue";
import GreyBox from "./components/GreyBox.vue";
import UserDrawer from "./components/UserDrawer.vue";

export default {
  name: "App",
  components: {
    UserCard,
    AddButton,
    GreyBox,
    UserDrawer,
  },

  data() {
    return {
      userInfo: {
        firstName: "",
        lastName: "",
        email: "",
        age: "",
        role: "",

        skills: "",
        skillsData: [],

        experiences: {
          experienceTitle: "",
          experienceDescription: "",
          experienceDate: "",
        },
        expData: [],
      },
      infoList: [],
      drawerInfo: null,
    };
  },

  methods: {
    showData() {
      
      console.log(this.userInfo);
      this.infoList = [
        ...this.infoList,
        JSON.parse(JSON.stringify(this.userInfo)),
      ];
      this.userInfo = {
        firstName: "",
        lastName: "",
        email: "",
        age: "",
        role: "",

        skills: "",
        skillsData: [],

        experiences: {
          experienceTitle: "",
          experienceDescription: "",
          experienceDate: "",
        },
        expData: [],
      };
      /* 
      this.infoList = [...this.infoList, this.userInfo]
      this.userInfo = [] */

      /* this.infoList.push(this.userInfo);
      console.log(this.infoList);

      this.userInfo.firstName = "",
      this.userInfo.lastName= "",
      this.userInfo.email= "",
      this.userInfo.age= "",
      this.userInfo.role= "",

      this.userInfo.skills= "",
      this.userInfo.skillsData= [],

      this.userInfo.experiences= {
          experienceTitle: "",
          experienceDescription: "",
          experienceDate: "",
        },
      this.userInfo.expData= []
 */
    },

    deleteSkill() {
      console.log("delete this");
      // this.skillsData = this.skillsData.filter((_, index) => index !== indexBox);
    },

    handleDeleteSkill(indexDeleted) {
      this.userInfo.skillsData = this.userInfo.skillsData.filter(
        (_, index) => index !== indexDeleted
      );
    },

    handleDeleteExp(indexDeleted) {
      this.userInfo.expData = this.userInfo.expData.filter(
        (_, index) => index !== indexDeleted
      );
    },

    showDrawer() {
      this.infoList = this.infoList.filter(
        (_, index) => (this.drawerInfo = this.infoList[index])
      );
    },

    pushSkills() {
      this.userInfo.skillsData = [
        ...this.userInfo.skillsData,
        this.userInfo.skills,
      ];
      this.userInfo.skills = "";
      console.log(this.userInfo.skillsData);
    },

    pushExperiences() {
      this.userInfo.expData = [
        ...this.userInfo.expData,
        this.userInfo.experiences,
      ];
      this.userInfo.experiences = {};
      console.log(this.userInfo.expData);
    },

    closeDrawer() {
      this.drawerInfo = null
    }
  },
};
</script>

<template>
  <div class="applicationForm">
    <span class="userInfoTitle">User Info</span>

    <input type="text" placeholder="Firstname" v-model="userInfo.firstName" />
    <input type="text" placeholder="Lastname" v-model="userInfo.lastName" />
    <input type="text" placeholder="Email" v-model="userInfo.email" />
    <input type="text" placeholder="Age" v-model="userInfo.age" />
    <input type="text" placeholder="Role" v-model="userInfo.role" />
    <div class="skillsContainer">
      <input
        class="skills"
        type="text"
        placeholder="Skills"
        v-model="userInfo.skills"
      />
      <AddButton @click="pushSkills()" />
    </div>
    <GreyBox
      v-for="(skill, index) in userInfo.skillsData"
      :key="`dt-${index}}`"
      :title="userInfo.skillsData[index]"
      :handleDelete="deleteSkill()"
      :data="skill"
      class="greyBoxSkill"
      @delete="handleDeleteSkill(index)"
    />
    <input
      type="text"
      class="experienceTitle"
      placeholder="Experience"
      v-model="userInfo.experiences.experienceTitle"
    />
    <input
      type="text"
      class="experienceDescription"
      placeholder="Experience Description"
      v-model="userInfo.experiences.experienceDescription"
    />

    <div class="experienceDateContainer">
      <input
        type="text"
        class="experienceDate"
        placeholder="Experience date"
        v-model="userInfo.experiences.experienceDate"
      />
      <AddButton @click="pushExperiences()" class="btnPushExp" />
    </div>

    <GreyBox
      v-for="(exp, index) in userInfo.expData"
      :key="`dt-${index}}`"
      :title="userInfo.expData[index].experienceTitle"
      :date="userInfo.expData[index].experienceDate"
      :data="exp"
      @delete="handleDeleteExp(index)"
      class="greyBoxExp"
    />
    <button class="addUserButton" @click="showData()">Add User Info</button>
  </div>

  <div class="cardSection">
    <UserCard
      v-for="(object, index) in infoList"
      :key="`dt-${index}}`"
      :firstName="infoList[index].firstName"
      :lastName="infoList[index].lastName"
      :email="infoList[index].email"
      :age="infoList[index].age"
      :role="infoList[index].role"
      :skills="infoList[index].skillsData"
      @click="showDrawer(index)"
      data="object"
    />
  </div>

  <div>
    <UserDrawer
      v-if="drawerInfo !== null"
      :firstName="drawerInfo.firstName"
      :lastName="drawerInfo.lastName"
      :email="drawerInfo.email"
      :age="drawerInfo.age"
      :role="drawerInfo.role"
      :skills="drawerInfo.skillsData"
      :experiences="drawerInfo.expData"
      @close="closeDrawer()"
      class="drawerSection"
    />
  </div>
</template>

<style lang="scss">
input {
  border: 1px solid #9a9a9a;
  width: 274px;
  height: 42px;
  padding-left: 10px;
  padding-top: -5px;
  padding-bottom: 0;
  padding-right: 0;

  font-weight: 400;
  font-size: 14px;
  line-height: 16px;
}

#app {
  display: flex;
  gap: 16px;
}

.applicationForm {
  height: 1428px;
  width: 348px;
  margin-left: 29px;
  display: flex;
  text-align: start;
  flex-direction: column;
  gap: 25px;
  margin-top: 40px;

  .userInfoTitle {
    font-weight: 600;
    font-size: 20px;
    line-height: 23px;
  }

  .skillsContainer {
    display: flex;

    .skills {
      width: 227px;
    }
  }

  .btnPushExp {
    margin-left: 241px;
  }

  .experienceDescription {
    height: 102px;
  }

  .experienceDateContainer {
    display: flex;
    flex-direction: column;
    gap: 25px;
  }
}

.addUserButton {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #2444b5;
  border: 0px;
  height: 45px;
  width: 183px;
  border-radius: 0;
  align-self: center;
  color: white;
  font-size: 14px;
  font-weight: 400;
}

.cardSection {
  height: fit-content;
  width: 470px;
  margin-top: 25px;
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}


.drawerSection {
  padding-top: 44px;
  width: 492px;
  height: 100%;
  position: fixed;
  padding-left: 40px;
  right: 0px;
  box-shadow: -2px 0px 20px 20px rgba(0, 0, 0, 0.16);
}

.greyBoxExp {
  display: flex;
  margin-left: 0;
  height: 73px;
  width: 268px !important;
  padding-left: 18px;
  align-items: none !important;
  padding-top: 28px;
  background-color: #dde3eb;
  gap: 16px;

  .textContainer {
    display: flex;
    flex-direction: column;
    background-color: none;
    gap: 7px;
    width: 220px;
  margin-left: 0;

  }
}

.greyBoxSkill {
  display: flex;
  align-items: center;
  gap: 16px;
  width: 100%;
  margin-left: 17px;

  .textContainer {
    padding-left: 9px;
    height: 25px;
    width: 234px;
    display: flex;
    justify-content: center;
    flex-direction: column;
    background-color: #dde3eb;
  }
}
</style>
