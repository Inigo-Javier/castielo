markdown open preview:

| Endpoints     | modelos       | URLs de cliente 
| ------------- |:-------------:| -------------:        |
| /             |    user       | /inicio               |
| / website     |    places     | /lugares              |
| /api/places   |    castillo   | /localización         |
| /api/maps     |               | /proyecto             |
|               |               | /un poco de historia  |
|               |               | /registro             |
|               |               |                       |







especificación MODELOS:
```javascript
const castilloSchema = new Schema(
    {
        title: {
            type: String,
            required: [true, 'El nombre es obligatorio']
        },
        description: {
            type: String,
            required: [true, 'La descripción es obligatoria'],
            minlength: [20, 'La descripción debe tener min. 20 caracteres']
        },
              
        imageUrl: {
            type: String,
            required: [true, 'La imagen es obligatoria'],
        },
        author: [{                                  
        type: Schema.Types.ObjectId,
        ref: 'User'                             
    }],
    },
    {
        timestamps: true
    }
);

```

```javascript
const placeSchema = new Schema(
  {
    name: {
      type: String,
    },
    type: { 
      type: String, 
      enum: ['coffee-shop', 'bookstore']
    },
    location:{
      lat: Number,
      lng: Number
    }
  },
  {    
    timestamps: true,
  }
);
```

```javascript
const userSchema = new Schema(
  {
    username: {
      type: String,
      unique:true
    },
    password: String,
  },
  {
    
    timestamps: true,
  }
);
```
```

npx create-react-app---> client
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
---


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

```