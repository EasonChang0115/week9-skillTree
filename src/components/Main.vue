<template>
  <div class="main">
    <left :nowLevel="nowlevel"></left>
    <mid :skills="skills" :nowFocus="now_selected" @changeNowSelected="changeSelected"></mid>
    <right :nowSkill="now_skill"></right>
  </div>
</template>

<script>
import Left from './Left';
import Mid from './Mid';
import Right from './Right';
let skills = [
  {
    title: "BASIC",
    img: "./static/images/img-planet-basics.png",
    all_completed: false,
    skill: [
      {
        name: "BASIC SKILLS",
        icon: "category",
        recommened : [
          {
            rc_skill:'Learn HTML',
            selected: false,
          },
          {
            rc_skill:'Basics of CSS',
            selected: false,
          },
          {
            rc_skill:'Basics of JavaScript',
            selected: false,
          }
        ],
        optional: []
      },
      {
        name: "BASIC TOOLS",
        icon: "build",
        recommened : [
          {
            rc_skill:'Git - Version Control',
            selected: false,
          },
          {
            rc_skill:'Basic Terminal Usage',
            selected: false,
          },
          {
            rc_skill:'Text Editor',
            selected: false,
          },
          {
            rc_skill:'A Heart of Reserching',
            selected: false,
          }
        ],
        optional: []
      }
    ]
  },
  {
    title: "CSS",
    img: "./static/images/img-planet-css.png",
    all_completed: false,
    skill: [
      {
        name: "CSS FRAMEWORK",
        icon: "flip_to_front",
        recommened : [
          {
            rc_skill:'Bootstrap',
            selected: false,
          }
        ],
        optional : [
          {
            op_skill:'UIKit',
            selected: false,
          },
          {
            op_skill:'Foundation',
            selected: false,
          },
          {
            op_skill:'Semantic UI',
            selected: false,
          }
        ]
      },
      {
        name: "CSS PREPROCESSORS",
        icon: "view_quilt",
        recommened : [
          {
            rc_skill:'Sass',
            selected: false,
          },
          {
            rc_skill:'PostCSS',
            selected: false,
          },
        ],
        optional : [
          {
            op_skill:'Less',
            selected: false,
          },
          {
            op_skill:'Stylus',
            selected: false,
          }
        ]
      },
      {
        name: "CSS ARCHITECHTURE",
        icon: "developer_board",
        recommened : [
          {
            rc_skill:'OOCSS',
            selected: false,
          }
        ],
        optional : [
          {
            op_skill:'SMACSS',
            selected: false,
          },
          {
            op_skill:'BEM',
            selected: false,
          }
        ]
      },
      {
        name: "CSS SKILLS",
        icon: "devices",
        recommened : [
          {
            rc_skill:'Responsive Web',
            selected: false,
          },
          {
            rc_skill:'Flexbox',
            selected: false,
          }
        ],
        optional: []
      },
      {
        name: "CSS MASTERY",
        icon: "widgets",
        recommened: [],
        optional : [
          {
            op_skill:'Grid Layout',
            selected: false,
          },
          {
            op_skill:'Animation',
            selected: false,
          },
          {
            op_skill:'Transform 2D, 3D',
            selected: false,
          }
        ]
      }
    ]
  },
  {
    title: "JAVASCRIPT",
    img: "./static/images/img-planet-js.png",
    all_completed: false,
    skill: [
      {
        name: "BASIC DOM",
        icon: "hdr_strong",
        recommened: [],
        optional : [
          {
            op_skill:'jQuery',
            selected: false,
          }
        ]
      },
      {
        name: "WEB DRAWING",
        icon: "gradient",
        recommened: [],
        optional : [
          {
            op_skill:'SVG',
            selected: false,
          },
          {
            op_skill:'Canvas',
            selected: false,
          },
          {
            op_skill:'D3.js',
            selected: false,
          }
        ]
      },
      {
        name: "JAVASCRIPT SKILLS",
        icon: "format_quote",
        recommened : [
          {
            rc_skill:'ES6',
            selected: false,
          }
        ],
        optional: []
      },
      {
        name: "JAVASCRIPT FRAMEWORK",
        icon: "developer_mode",
        recommened : [
          {
            rc_skill:'Vus.js',
            selected: false,
          },
          {
            rc_skill:'Angular',
            selected: false,
          },
          {
            rc_skill:'React.js',
            selected: false,
          }
        ],
        optional: []
      },
      {
        name: "JAVASCRIPT PREPROCESSORS",
        icon: "nfc",
        recommened: [],
        optional : [
          {
            op_skill:'TypeScript',
            selected: false,
          },
          {
            op_skill:'Babel',
            selected: false,
          },
          {
            op_skill:'CoffeeScript',
            selected: false,
          }
        ]
      }
    ]
  },
  {
    title: "MANAGERS",
    img: "./static/images/img-planet-managers.png",
    all_completed: false,
    skill: [
      {
        name: "PACKAGE MANAGERS",
        icon: "device_hub",
        recommened : [
          {
            rc_skill:'NPM',
            selected: false,
          },
          {
            rc_skill:'YARN',
            selected: false,
          }
        ],
        optional : [
          {
            op_skill:'Bower',
            selected: false,
          }
        ]
      },
      {
        name: "TASK RUNNERS",
        icon: "import_contacts",
        recommened : [
          {
            rc_skill:'npm scripts',
            selected: false,
          },
          {
            rc_skill:'gulp',
            selected: false,
          }
        ],
        optional : [
          {
            op_skill:'grunt',
            selected: false,
          }
        ]
      },
      {
        name: "BUILD TOOLS",
        icon: "table_chart",
        recommened : [
          {
            rc_skill:'Webpack',
            selected: false,
          }
        ],
        optional : [
          {
            op_skill:'Parcel',
            selected: false,
          }
        ]
      }
    ]
  }
];
export default {
  name: 'Main',
  data () {
    return {
      skills: skills,
      now_selected: 'BASIC SKILLS',
    }
  },
  components: {
    Left,
    Mid,
    Right
  },
  methods: {
    changeSelected(val) {
      this.now_selected = val;
    }
  },
  computed: {
    now_skill() {
      let nowData = null;
      this.skills.forEach(data => {
        if(!nowData) {
          nowData = data.skill.find(item => item.name === this.now_selected);
        }
      });
      return nowData;
    },
    nowlevel () {
      let completed_count = 0;
      this.skills.forEach(skill => {
        if (skill.all_completed) {
          completed_count++;
        }
      });
      return completed_count;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss'>
@import '../style/components/main.scss';
</style>
