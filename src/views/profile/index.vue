<template>
  <div class="app-container">
    <div v-if="user">
      <el-row :gutter="20">

        <el-col :span="6" :xs="24">
          <user-card :user="user" />
        </el-col>

        <el-col :span="18" :xs="24">
          <el-card>
            <el-tabs v-model="activeTab">
              <el-tab-pane label="Contact Numbers" name="contacts">
                <contacts />
              </el-tab-pane>
              <el-tab-pane label="Address" name="address">
                <addresses />
              </el-tab-pane>
              <el-tab-pane label="Activity" name="activity">
                <!-- <account :user="user" /> -->
              </el-tab-pane>
              <el-tab-pane label="Messages" name="messages">
                <!-- <account :user="user" /> -->
              </el-tab-pane>
            </el-tabs>
          </el-card>
        </el-col>

      </el-row>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import UserCard from './components/UserCard'
import Contacts from './components/Contacts'
import Addresses from './components/Addresses'
// import Activity from './components/Activity'
// import Timeline from './components/Timeline'
// import Account from './components/Account'

export default {
  name: 'Profile',
  components: { UserCard, Contacts, Addresses },
  data() {
    return {
      user: {},
      activeTab: 'contacts'
    }
  },
  computed: {
    ...mapGetters([
      'name',
      'avatar',
      'roles'
    ])
  },
  created() {
    this.getUser()
  },
  methods: {
    getUser() {
      this.user = {
        name: this.name,
        role: this.roles.join(' | '),
        email: 'admin@test.com',
        avatar: this.avatar
      }
    }
  }
}
</script>
