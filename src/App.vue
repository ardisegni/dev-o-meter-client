<template>
  <v-app>
     <div id="app">
     <div style="display:flex;justify-content: space-around;">
         <div style="display: flex; justify-content: center; align-items: center;">
            <img src="./assets/graph.png" style="width: 500px;"/>
         </div>
           <div>
     <v-card-title>
           <v-text-field
             v-model="search"
             append-icon="mdi-magnify"
             label="Search"
             single-line
             hide-details
           ></v-text-field>
         </v-card-title>
         <v-data-table
             :headers="headers"
             :items="employees"
             :single-expand="singleExpand"
             :expanded.sync="expanded"
             item-key="author"
             show-expand
             class="elevation-1"
      :search="search"
           >
            <template v-slot:item.author="{ item }">
                          <td>
                          <div style="display: flex; justify-content:center; align-items: center;">
                            <img style="width: 50px;" :src="item.avatar"/>

                            <div style="margin: 0 10px;">{{item.author}}</div>
                          </div>
                          </td>
                        </template>
             <template v-slot:expanded-item="{ headers, item }">
               <td :colspan="headers.length" style="padding: 15px;">
                <div>
                 Start of employment date: {{item.date}}
                 </div>
                 <div>
    Department: {{item.dept}}
    </div>
                 <div>
    Working on {{item.projectsNumber}} active projects
    </div>
                 <div>
    Department: {{item.dept}}
    </div>
                 <div>
    Role: {{item.role}}
    </div>
                 <div>
    Supervisor: {{employees[randomInteger(0,employees.length-1)].author}}
    </div>
                 <div>
    Team members: {{teamMembers()}}
    </div>
               </td>
             </template>
           </v-data-table>
       </div>
               <div><img style="width:200px;" src="./assets/emp.png"/></div>
       </div>
       </div>

  </v-app>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
  expanded: [],
  singleExpand: false,
  search: '',
    headers:[{
                         text: 'Name',
                         align: 'start',
                         sortable: false,
                         value: 'author',
                       },
                       { text: 'Seniority', value: 'seniority' },
                       { text: 'Languages', value: 'language' },],
"employees": [
		{
			"author": "Moshe Yamini",
			"seniority": "Middle",
			"language": "Angular, VueJS",
			"avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
			"date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
			"dept": "R&D",
            "projectsNumber": randomInteger(1,20),
            "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Ariel Markus",
			"seniority": "Middle",
			"language": "Java",
			"avatar": "https://cdn1.iconfinder.com/data/icons/people-job/100/Emotion-plus-39-512.png",
            "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
            "dept": "R&D",
            "projectsNumber": randomInteger(1,20),
            "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Efrat Eichenstein",
			"seniority": "Junior",
			"language": "Java",
            "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
       "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
       "dept": "R&D",
       "projectsNumber": randomInteger(1,20),
       "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Ariel Di Segni",
			"seniority": "Junior",
			"language": "Java",
            "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
       "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
       "dept": "R&D",
       "projectsNumber": randomInteger(1,20),
       "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Hanan Uzana",
			"seniority": "Senior",
			"language": "SQL",
           "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
      "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
      "dept": "R&D",
      "projectsNumber": randomInteger(1,20),
      "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Michael Cohen",
			"seniority": "Junior",
			"language": "Java",
            "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
       "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
       "dept": "R&D",
       "projectsNumber": randomInteger(1,20),
       "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Itamar",
			"seniority": "Middle",
			"language": "VueJS, Angular",
             "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
        "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
        "dept": "R&D",
        "projectsNumber": randomInteger(1,20),
        "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		},
		{
			"author": "Eran Cohen",
			"seniority": "Middle",
			"language": "Angular, VueJS",
             "avatar": "https://th.bing.com/th/id/OIP.IF102FHNWBg-bvssc_tR_wHaHa?pid=ImgDet&rs=1",
        "date": randomInteger(1,30) +"/" + randomInteger(1,12)  + "/20" +randomInteger(15,21) ,
        "dept": "R&D",
        "projectsNumber": randomInteger(1,20),
        "role": randomInteger(0,1) ? "Front-end developer" : "Back-end developer"
		}
	]

  }),
  methods: {
    randomInteger: function(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
    teamMembers: function() {
        return this.employees.map(e=>e.author).join(', ');
        }
  }
};

function randomInteger(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
</script>
