1. Что такое Event Loop
2. Как браузер понимает, откуда получить файлы сайта
3. Как браузер рендерит страницу
4. Задачи: https://codepen.io/anonymous-link/pen/ZEwqMzW
	1. Использование семантических элементов HTML5 (header, nav, main, section, article, form, label, input, footer, address, figure и т. д.) вместо несемантических `<div>`. 
	   https://codepen.io/anonymous-link/pen/jOdebmR?editors=1000
	   
	2. Использование псевдоэлементов (`::before`, `::after`) и псевдокласса `:hover` в CSS для изменения стиля при наведении.
	   https://codepen.io/anonymous-link/pen/XWOxmam?editors=0100
	   
	3. Фильтрация и преобразование «грязного» массива в JavaScript с помощью `filter` и `map` для получения строго типизированного результата.
	   https://codepen.io/anonymous-link/pen/zYemvEq?editors=0011
	   
	4. Разница между синхронными и асинхронными ошибками в JavaScript: работа `try/catch`, Event Loop и обработка ошибок в колбэках/Promise.
	   https://codepen.io/anonymous-link/pen/qEOwJPE?editors=0012
	   
	5. Использование метода массива `reduce` для преобразования массива строк в единый результат по заданному правилу.
	   https://codepen.io/anonymous-link/pen/ExrdeXw?editors=0011
	   
	6. Реализация функции `sleep` с использованием `Promise` и `setTimeout` в JavaScript/TypeScript.
	   https://codepen.io/anonymous-link/pen/rNPgEZG?editors=0011
	   
	7. Раскрытие (Prettify) пересечения типов (`&`) и объединений (`|`) в TypeScript для получения финальной структуры.
	   [Ссылка](https://typescript-eslint.io/play/#ts=5.6.3&fileType=.tsx&code=PQKhFgCgAIWxiEEFwggGEEGwggOEEEIghWEGoJhBoBZATwDkB7AJwFsBDAGwEsAvAUwBMAVYgB1ekAiIOkC8IMkDcIIBkQYYD4QXNMD8IIAEQbIBYQbGOzD0uTOnnJoFGgxYdufADTR50sTMCCIJgmA5EGiLk9xIsDSIHmSB5EGhHRUBhEERMEND8e2xAURBobEBmEGlrW2xAThAoWGAoKAAXXn4ABUpWPLzGADNiAB5OAD5oAF5oTmhWAA881gA7dgBnaAAlVgBjKnYa-rzKRh6AcysAVx6Aax7yAHce%2BqzoAH5oAG9oAG0AaWg56FXWYnJK1oBdAC5oErKK6rqLp8aAXz2b04AG5cpBgMBoAU%2BIYqHQmGwuIVmu9SuUqrUoJDoLiABRHbFQ3G4nq0aisN7TWYLMEQ4kk2jzSnQFbrLY9Ok4knQZl9ViUN4AI3I5HorFonKJPOgPFopR6eX2bx6S2oQoFXIZ-2gADJjtKeWSKVSZnN5lqZYx2KaaRbDSSAG4MJYs6nmy24-4ASmgAB9oO6FtL6nTwTD%2BCQjAjTMjYS0jv8gA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
	   
	8. Кортежи (Tuple Types) и остаточные элементы (`...rest`) в TypeScript для строгой типизации массивов фиксированной структуры.
	   [Ссылка](https://typescript-eslint.io/play/#ts=5.9.2&fileType=.ts&code=PQKhFgCgAIWw8EEPwggOEEBIgzBCIIVhBoeY6AEQEMAXYgFQFcAHAGwFNdAGEEC4QAGmkHEQDQPhBBGEEDSINEDsIIF4QZlyxjkgeRBogQRBevDICYQLBgVreq5oG4QZItW8sgHhBAwiC58lqLGiHWvUyj2y%2BgARBoFAJ40GAZQBjACcASxpSaDEcVUFAFhBmXT1oXnR%2BXlYALls4EGAoKFJfJhJyanomAF5oYgA7bwBuaGBgaEAkEGZUaEc4gsgAMypawNJQgHta6FJaRgoxgHkAIwArBhGAClspmYZMojJKHfYoAEpoAG8twImAZ0iAbVCAE046YkWGOk5iEdCANwYnAAdCDggw7gBdaDVaYVBp9aDQMHTYKTc7QZ6vd6fb6-AGcMF3aAAX3hkGJfVhswWKzWpE2MGg9wALAAmTgAckAhCAYZgYQAyILIOZxSMEqIDoBz4FIxPzhZK4gYxGJBIBOEHlHMVyGVao1Wp16s5%2BpVhsl2FYWg1AEIORDTg0gA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
	   
	9. Использование mapped types и шаблонных литеральных типов (Template Literal Types) в TypeScript для генерации новых строковых ключей.
	   [Ссылка](https://typescript-eslint.io/play/#ts=5.9.2&fileType=.ts&code=PQKhFgCgAIWwCEEKwggGEENwggOEEOwghhEEJwgghEEWgFsBDAB3IFMATAWn3UH4QaABQCcqAzASwA8AygFcuvPlFjRA4iD5AfCDRAjCCBpEGhNZqbFPT5AMiAAuCXABEAI24B7TgH0eAOy7mrpLgBcq7I9AA%2B0UxeukAMYuPOa2AM5Oru5GhsBQUC4AntTQANJUSeHQALzQAOR2DvneBUEhYeH5ANwJkIkpVGycYsKi-LnQpLZJ1dDAwNCASCDIgBIg0IBcILKALCB1DakASlThQgA2Lp0c3PxtYgA8GVkANAVmDtb5J-lRbuz5AHzVQA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
	   
	10. Условные типы (Conditional Types) в TypeScript с использованием `infer` для извлечения типа из `Promise`.
	    [Ссылка](https://typescript-eslint.io/play/#ts=5.9.2&fileType=.ts&code=PQKhFgCgAIWxcEEAwgh%2BEEBwghBEEYIRBAyINLqy0AqgHYDuATgIYAOACpQPYC2AlgM4Cm%2BigXCAAaaIHEQLID4QaIEYQQNIg0KLGgAiQAQgidMn5jATCDYci6IHYQQLwgiYYFYQI6jPQtRwMIgWQAIgqaI1acu8kMChQALgCetDxkVHRu7NzQALzQ1KQBANzQwMDQgEggiIASINB8YoAsIL6QqdCA%2BCDOgDwgZo4AXP5BIQCMMSQUNAzMkVwAPBEe3aQAriwARlyUAHwTySVDo%2BP1wSQATC2h7X3c3Rx%2BlGykAObTKWk7e4dQQA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
	11. Использование `never` для исчерпывающих проверок (exhaustive checks) в TypeScript при работе с union-типами.
	    [Ссылка](https://typescript-eslint.io/play/#ts=5.9.2&fileType=.ts&code=PQKhFgCgAIWwSEEMIgheEEFwggxEEBwgh5EGofhBABEE2U0B4QQBhBBWEECEQacgwZhBFTLlbrM9zoA7AVwC2AIwCmAJ2iZA3CCZoAZwAuYgJY8A5gDoosaIFwQSoD4QQIwggURADgFhAyB6MYLkjB6uWqAZEGiAmEECCIJQ8HA7CCkBoBsIMiA0iA%2B7vSY5Gyh0Hw8ygD2PAC0HFzQAKI8CuIACmJJAA5y0J74BoGAkiAugHIg8gDuygoAxgAWwK0AhnIiWjBwgAQglIASIKyYPuYGUiHWRqGu0BnGlH4GXJ5hpABc%2BETQdp6jmAQTsu5m5sgGDNYZ5NpwqFV40tjUBgTQACoAnsURABlVoqYoKDyhczkTy0AwnIyoRAAGkqqG4yB8RkQ5ho0GmRnI7ikrG4ngMjncNFh7kQdWq5FwtnsjnRAx0gCIQM7Y6m4QgWSiBZCwogEAyRJaYTx4GYudaREg%2BB68EQAN3E%2BKkuDO5BkfnIWFkUsA4iCUAh4UKRemYEz7cVmgyoaAAChEAA92t0%2BIplOroB0RK0ANZyACU7JAwCgUAUAJE2VyBSKpWgAF5oABGABMAGZoAAfaAAciE3R4Ze6RYLxe6xWKABsRFXC0WeCJGv9AUWANzRyAAMwSrQUyR40FLYldibEhRKYb2qqSygAJtAAN7aJotDoukTT2elUPrzfQf29eNF5ciRt5AD6AhEt%2B6-byYlv7WUanaCnrn%2B-t-EIoxCLHYT1PccxBEbog17GBwJ6PpM1zUC4PAiCoJgsCEIvUty3LECwNPIRIOg2C0Owms60bAjUPA4iMLItDoDA4BgD0RAglYaAr37L16wUVI23VMQAEJNwAXygSTICgVjoEAfBAiBYAhQigCdnRLCt8NDbtwLk6Y8EQWEyFCQBOEA8KIYmoNTuknTS8O6AB%2BIsdNPOT4UwBxjTCUzUWmWYuKkcVMFcTxcHcbiRF4vh%2BJsuzawbJtXL0tiDKMjhSDMiyiCsuLnQSHjVBEZdkvchEDG8sy-JmTjkGgIL3BClwwo8SLotiyB1OzHNkqY6B9I2dKTPMyIcrYPsgA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
		[Ссылка](https://www.typescriptlang.org/play/?target=6&jsx=0#code/PQKhAIBUEMGcGtwEYBc4CqsCWA7A5uAC4AWApuDqQG6kBORAngA7kjABQ7ww4AMloTrQANoxbtCzcgGVC0QgFdY4ALzgA5AAVSOACa4868AB8NAdQD2teAaOn1AYQsBbJsNKDd6gNycAZgo4AMaEWBY44Cx6BgAUcggAkrposIS0BgA04EG0pPKkyeAAIvkAlOAA3uwAvuwBwaHh4ADuVjb4cXDwSSlpmdm5+YUlguVVtfUhYRFBLm4eBZ2Jhanp+GM1-oFTTUy0FkGksLBL3St9+Fk5eZ5oI6RZqfJKaLLPsBvg4NzggEgggNIggHYQQBMIIAGEEAQiCAGRBwIAREEAwiCAXhBAGIggA4QQByIOBAIIggD4QbHg4Fw8GY-FwtGASRBSVjwRC4Zi4QA6P7gQCMIHDACwgcLJgFYQQA8IFSaTjgeAedjAGwgXPB-KhLOxgG4QSGACRAueAUeBAKIg2MA4iASzGAeRBwIB+EDlcM1KOlPNBgC4QTEonlwvkG2VowXgPFSlHazGW7GAThBwN6eQaUbLdaiUfTNkA)
		
	12. Строгая типизация объектов в TypeScript с ограничением значений ключей через **mapped types и `Record` с union-типами**.
	    [Ссылка](https://typescript-eslint.io/play/#ts=5.6.3&fileType=.tsx&code=PQKhFgCgAIWw8EEPwggOEEIIggGEEEIggZEGoPhBBGEECkQQVhBAuEE2gAMB7AIwCsrpN0yAaaQcRBNDBpEGiB2EEC8IOi4lhyQPIg0QEwgqEoFEQaCUDMIHmhlA3CCA5EHGBOEGiAeEDyqtyaAT44WeLdjIbMyROmgBnAC4AnAJYA7AHNoZHNoOhoaABsAUwBDfwA6KFhoQHwQQAEQC0BZEF4jTkQs-AIM9EBJEAlkCzJoXQI8I0BhEGhUWTx9VExZZsJSCnROQBYQO0A2EAkWvEVS4SkcVBlHYTIMkkxhPkNnRCFRcUkpFLhAFAJoUULkIxIMzhJUMO09ZtQ8PC7Vzu7VlswMvDIB2wsFyWRqDL5ePxBG53CwERpaEhtHZiSokaAnCLReJJQ6HaCAIhAXMhBOhAGIg0mgwy0I1ElmsuE6v3U%2BgAXNBEHhENZ-pTCOhZMgbA8uC1TiRhohGp0LnwjECOXKRCj9tAABRnLKXa7QfwAVwAtnQYt4AJR4qk0tznNqDQW4Gp4QASIMgCGQ0Y4jCgtFJyRYACoATwADjEAMoAYz8Qc8yRgIGAUETkHDNH8Xmg9AY0AAvNAAN4paAACxiUSiNDZAHIAO40bxRAAmlfYhZi-jidFibJ8upiLZg0GrRbingAghFdZ4AHIGo3eNkABn7AF8kym01jEuXAqrK5nmxnGIkS2WaIlPDQADI0cNxWIAVSDIe8AGE4u4YqqTSaANxQdfuJu267vunCZokbYdrEv5AA&eslintrc=N4KABGBEBOCuA2BTAzpAXGYBfEWg&tsconfig=N4KABGBEDGD2C2AHAlgGwKYCcDyiAuysAdgM6QBcYoEEkJemy0eAcgK6qoDCAFutAGsylBm3TgwAXxCSgA&tokens=false)
	    
	13. Перегрузка функций (Function Overloads) в TypeScript: определение нескольких сигнатур и одна универсальная реализация.
	    [Ссылка](https://www.typescriptlang.org/play/?#code/FAehAkHsHcAIBNIFMDOsBmBXAdgYwC4CWk2skAbkgE4A2kAhvGtJFQNayGkAqAngA5IAyriqF++APzBgWPERKx+Y7PgAUAW1Qp6AcyQAuWCnwrdASiPlIheLJwFipZV3VaUO-UZNmA2gF1LWGtbYCA)
	    
	14. Разница между `extends` и `implements` в TypeScript: наследование реализации класса (`extends`) и соблюдение контракта интерфейса или типа (`implements`).