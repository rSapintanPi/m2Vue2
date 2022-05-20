# m2Vue2
magento 2 vue2 setup - magento 2.4.4 with vue storefront 2 setup

extended mark shust docker setup (https://github.com/markshust/docker-magento)
to add vue storefront 2

FE - https://magento.test:3000/

BE - https://magento.test/

## setup steps

`git clone git@github.com:rSapintanPi/m2Vue2.git && cd magento2`

`bin/download 2.4.4`

`bin/setup magento.test`

`bin/magento sampledata:deploy`

`bin/magento setup:upgrade`

##  extra info

1. in bin/download I added 2 extra modules:

`caravelx/module-graphql-config` -> This module allow to configure the GraphQL complexity and depth inside the Magento administration

`graycore/magento2-cors` -> This package allows you to securely add the necessary CORS headers to the Magento 2 GraphQL or REST APIs

after the "src" directory is visible on your host add in app/etc/env.php following info:

```
'system' => [
    'default' => [
        'web' => [
            'graphql' => [
                'cors_max_age' => 86400,
                'cors_allowed_methods' => 'GET, POST, OPTIONS, DELETE, PUT',
                'cors_allowed_headers' => 'Content-Type, Access-Control-Allow-Headers, Authorization, X-Requested-With, Content-Currency, Store, X-Magento-Cache-Id, X-Captcha',
                'cors_allowed_origins' => 'https://magento.test:3000'
            ]
        ]
    ]
]
```
`bin/magento setup:upgrade` - if you want to avoid this command than add the above info after the sample data import

2. on FE I used the same SSL certificate as we have for BE (we have same domain)

## current status

I didn't fixed the CORS policy from BE to FE :(

<img width="1310" alt="Screenshot 2022-05-20 at 01 19 10" src="https://user-images.githubusercontent.com/98535917/169416641-79427742-6acb-4bd9-be51-08a83327578a.png">

<img width="1198" alt="Screenshot 2022-05-20 at 01 19 22" src="https://user-images.githubusercontent.com/98535917/169416676-ab38c45b-5ef4-4a6d-9105-f3565a577092.png">

<img width="1003" alt="Screenshot 2022-05-20 at 01 27 07" src="https://user-images.githubusercontent.com/98535917/169416727-646fd3ce-f19b-454b-9c4f-9a248f1d0745.png">
