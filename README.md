# Post It! challenge
A feladat megoldásához szükséges kritériumok:
- Lehessen egy posztot elküldeni a form-on keresztül (nem kell validáció)
- A posztokat lehessen listázni ugyanezen az oldalon (nem kell lapozás)
- Amikor egy poszt hozzáadásra kerül, akkor vagy legyen "optimistic update" vagy pedig kerüljön a lista újból lekérésre a végponttól

A feladat megoldásához létrehoztam két végpontot, amik Serverless Edge Function-ként futnak
és [Turso](Turso.tech) adatbázishoz kapcsolódnak.
- POST végpont:
    POST https://edge-post.vercel.app/api/posts
    Példa request:
    {
        "name": "Teszt Név",
        "text": "Teszt szöveg."
    }
    Példa response:
    {
        "id": 7, 
        "text": "Teszt szöveg.",
        "createdAt": "2023-11-05 20:49:11",
        "userId": 7
    }

- GET végpont:
  GET https://edge-post.vercel.app/api/posts
  [
    {
      "posts": {
         "id": 7,
         "text": "Teszt szöveg.",
          "createdAt": "2023-11-05 20:49:11",
          "userId": 7
       },
       "users": {
          "id": 7,
          "name": "Teszt Név"
       }
    },
    {
       "posts": {
         "id": 7,
         "text": "Teszt szöveg.",
         "createdAt": "2023-11-05 20:49:11",
         "userId": 7
       },
         "users": {
         "id": 7,
         "name": "Teszt Név"
       }
    },
  ]

A kész alkalmazás megtalálható ezen a linken:
https://edge-post.vercel.app/

To start this project you need to run:

```npm install```

and then

```npm run dev```
