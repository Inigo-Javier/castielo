markdown open preview:

AUTH /api/auth/

|Method      |	URL        |	Description     |
|------------|:------------|:----------------:|
|POST        |	/signup	   |Signup            |
|POST        |	/login	   |Register Form POST|
|POST	       |  /logout    |Logout            |
| GET        |	/verify	   |Authenticateds    |

USER /api/user

| Method   |  URL       | Description       |
|----------|:-----------|:-----------------:|
|   GET    | /          | Users             |
|   PUT    | /:id/edit  | User Profile Page |
|          |            |                   |

PLACES /api/places

| Method |  URL          | Description       |
|--------|:--------------|:-----------------:|
|  GET   | /             |Places             |
|  POST  | /create       |Create Places      |
|  PUT   | /:id/edit     |Delete profile POST|
|  DELETE| /:id/delete   |Matches List       |
|  PUT   | /:id/like ?   |Create Match       |
|  PUT   | /:id/dislike ?| Create Match Form |


especificación MODELOS:
```javascript
const placesSchema = new Schema(
    {
        title: {
            type: String,
            required: [true, 'El nombre es obligatorio']
        },
        imageUrl: {
              type: String,
              required: [true, 'La imagen es obligatoria'],
              default: 'https://i.imgur.com/Itw5P5a.jpeg',

        },
        description: {

            type: String,
            required: [true, 'La descripción es obligatoria'],
            minlength: [20, 'La descripción debe tener min. 20 caracteres']
            enum: ['vineyard', 'historic building','landscapes']
        },
        address: {
            city: String,
            country: String,
            address: String,
            location: {
            type: {
                    type: String
                },
                coordinates: [Number],
            }
        },
        owner: {
            type: Schema.Types.ObjectId,
            ref: 'User'
        },
        opinion: {
            type: Schema.Types.ObjectId,
            ref: 'Comments'
        }
      },     
    {
        timestamps: true
    }
);

```

```javascript
const commentSchema = new Schema(
    {
        description: {
            type: String,
            maxlength: [300, 'Cannot exceed 300 characters'],

        },
        owner: {
            type: Schema.Types.ObjectId,
            ref: 'User'
        }
    },
    {
        timestamps: true
    }
)

```


```javascript
const userSchema = new Schema(
  {
    username: {
      type: String,
      trim: true,
      unique: true,
      required: [true, 'Name is required']
    },
    image: {
      type: String,
      default: 'https://i.stack.imgur.com/l60Hf.png'
      },
    email: {
      type: String,
      required: [true, 'Email is required'],
      unique: true,
      lowercase: true,
      trim: true
    },
    password: {
      type: String,
      required: [true, 'Password is required']
    },
    role: {
      type: String,
      enum: ['ADMIN', 'USER'],
      default: 'USER'
    },
  },
  {
    
    timestamps: true,
  }
);





express-generator/-->server
├── app.js
├── package.json
├── .gitignore
├── routes
│   │── index.js
│   └── base.routes.js
├── models
│   └── user.model.js
├── utils
│   └── index.js
├── middlewares
│   └── index.js
├── views
│   │── layout.hbs
│   │── errors
│   │   │── not-found.hbs
│   │   └── server-error.hbs
│   │── pages
│   │   └── index.hbs
│   └── partials
├── public
│   ├── img
│   ├── js
│   │   └── script.js
│   └── css
│       └── styles.sass
├── config
│   │── db.config.js
│   │── debug.config.js
│   │── hbs.config.js
│   │── locals.config.js
│   │── middleware.config.js
│   │── sass.config.js
│   └── views.config.js
└── bin
    ├── seeds.js
    └── www

npx create-react-app
├──PUBLIC
│   │── img
│   └──index.html
├──SRC
│  ├──index.js(import react and reactDOM--> .render(<div>hola mundo</div>, document.getElementById('root')))
│  ├──App.jsx(import react and create App function,  )
│  ├──COMPONENTS
│  │   ├──Navbar.js
│  │   ├──
│  └──
│   
│
