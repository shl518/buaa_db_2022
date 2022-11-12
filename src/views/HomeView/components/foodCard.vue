<template>
  <div>
      <v-card
        max-width="344"
        class="mx-auto"
      >
        <v-list-item>
          <v-list-item-avatar color="grey">
            <v-img src="favicon.ico">
            </v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="headline">{{dish_name}}</v-list-item-title>
            <v-list-item-subtitle>{{canteen}}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-img
          :src="dish_picture"
          height="194"
        ></v-img>

        <v-card-text>
          {{info}}
        </v-card-text>

        <v-card-actions>
          <v-btn
            text
            color="deep-purple accent-4"
            @click = "showFoodDetails()"
          >
            Read
          </v-btn>
          <v-btn
            text
            color="deep-purple accent-4"
            @click = "bookmark()"
          >
            Bookmark
          </v-btn>
          <v-spacer></v-spacer>
          <v-btn icon>
            <v-icon>mdi-heart</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-message-minus</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>

    <v-row justify="center">
      <v-dialog v-model="dialog" width="600px">

        <v-card
          max-width="600px"
          class="mx-auto"
        >
          <v-toolbar
            color="pink"
            dark
          >
            <v-app-bar-nav-icon></v-app-bar-nav-icon>

            <v-toolbar-title>Inbox</v-toolbar-title>

            <v-spacer></v-spacer>

            <v-btn icon>
              <v-icon>mdi-magnify</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-checkbox-marked-circle</v-icon>
            </v-btn>
          </v-toolbar>
          <br/>
          <v-list-item>
            <v-img
              :src="dish_picture"
              height="194"
              width="50"
            ></v-img>
            <v-list-item-content>
              <v-list-item-title class="headline">{{dish_name}}</v-list-item-title>
              <v-list-item-subtitle>{{canteen}}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-card-text class="text--primary">{{info}}</v-card-text>

          <v-list two-line>
            <v-list-item-group
              v-model="selected"
              multiple
              active-class="pink--text"
            >
              <template v-for="(item, index) in items">
                <v-list-item :key="item.title">
                  <template v-slot:default="{ active, toggle }">
                    <v-list-item-content>
                      <v-list-item-title v-text="item.title"></v-list-item-title>
                      <v-list-item-subtitle class="text--primary" v-text="item.headline"></v-list-item-subtitle>
                      <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>
                    </v-list-item-content>

                    <v-list-item-action>
                      <v-list-item-action-text v-text="item.action"></v-list-item-action-text>
                      <v-icon
                        v-if="!active"
                        color="grey lighten-1"
                      >
                        mdi-star_border
                      </v-icon>

                      <v-icon
                        v-else
                        color="pink"
                      >
                        mdi-star
                      </v-icon>
                    </v-list-item-action>
                  </template>
                </v-list-item>

                <v-divider
                  v-if="index + 1 < items.length"
                  :key="index"
                ></v-divider>
              </template>
            </v-list-item-group>
          </v-list>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog = false">返回</v-btn>
            <v-btn color="green darken-1" text @click="dialog = false">返回</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>

export default {
  name: "foodCard",
  props: ['dish_id','dish_name','canteen','dish_price','info','dish_star','dish_tag'],
  data() {
    return {
      dialog:false,
      selected: [2],
      items: [
        {
          action: '15 min',
          headline: 'Brunch this weekend?',
          title: 'Ali Connors',
          subtitle: "I'll be in your neighborhood doing errands this weekend. Do you want to hang out?",
        },
        {
          action: '2 hr',
          headline: 'Summer BBQ',
          title: 'me, Scrott, Jennifer',
          subtitle: "Wish I could come, but I'm out of town this weekend.",
        },
        {
          action: '6 hr',
          headline: 'Oui oui',
          title: 'Sandra Adams',
          subtitle: 'Do you have Paris recommendations? Have you ever been?',
        },
        {
          action: '12 hr',
          headline: 'Birthday gift',
          title: 'Trevor Hansen',
          subtitle: 'Have any ideas about what we should get Heidi for her birthday?',
        },
        {
          action: '18hr',
          headline: 'Recipe to try',
          title: 'Britta Holt',
          subtitle: 'We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
        {
          action: '18hr',
          headline: 'Recipe to try',
          title: 'Britta Holt',
          subtitle: 'We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
        {
          action: '18hr',
          headline: 'Recipe to try',
          title: 'Britta Holt',
          subtitle: 'We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
        {
          action: '18hr',
          headline: 'Recipe to try',
          title: 'Britta Holt',
          subtitle: 'We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
      ],
    }
  },
  methods:{
    showFoodDetails(){
      this.dialog = true
    },
    bookmark(){

    }
  },
  computed: {
    dish_picture(){
      //console.log(this.dish_name)
      return "foodimage/"+this.dish_name+".png"
    },
    star_str(){
      return "👍︎".repeat(this.dish_star)
    }
  }
}
</script>

<style scoped>

</style>
