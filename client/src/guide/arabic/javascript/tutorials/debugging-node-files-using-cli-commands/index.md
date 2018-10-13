---
title: Debugging Node files using CLI commands
localeTitle: تصحيح ملفات عقدة باستخدام أوامر CLI
---
## تصحيح ملفات عقدة باستخدام أوامر CLI

ستتعرف في هذا البرنامج التعليمي على كيفية تصحيح رمز Node.js الخاص بك في سطر الأوامر. يمكن تصحيح أخطاء شفرة JavaScript البسيطة بسهولة باستخدام DevTools الخاص بالمتصفح. بالنسبة للعقدة ، يمكنك تصحيح التعليمات البرمجية بدون ترك واجهة سطر الأوامر (CLI).

لنفترض أن لديك ملفًا باسم `contents.js` . يمكنك تشغيل الملف باستخدام أمر `node` .

 `node contents.js 
` 

يجب أن يكون هذا معروفًا لك منذ كتابة رمز Node.js. والآن يجب تصحيح أي أخطاء تنبثق. لتشغيل الملف في وضع التصحيح إلحاق الكلمة `inspect` أثناء تشغيل الملف.

 `node inspect contents.js 
` 

الآن سيفتح هذا الأمر ملفك في وضع التصحيح. من الآن فصاعدًا ، يمكنك التنقل خلال سطر واحد من الكود في كل مرة بالضغط على المفتاح **N** في لوحة المفاتيح.

سيبدأ مصحح الأخطاء في السطر الأول. بالضغط على **N** ، يمكنك نقل المصحح إلى السطر التالي. إذا كان هناك خطأ في السطر الأول ، فسيظهر خطأ بدلاً من الانتقال إلى السطر الثاني. هذا مفيد جدا. على سبيل المثال ، إذا حدث خطأ في السطر السابع عشر ، فسوف يظهر لك الخطأ قبل الانتقال إلى الأمام.

يمكن أن يكون هناك خطأ في المنطق الخاص بك ، بمعنى أنك تريد عرض قيمة معينة ولكن بدلاً من ذلك تعرض قيمة مختلفة. في هذه الحالة ، قد تساعدك إضافة `console.log()` s ومع وضع التصحيح ، يصبح من الأسهل التعرف على سبب الخطأ.

* * *

الآن في بعض الأحيان ، يحدث أن شفرة المصدر الخاصة بك ضخمة. تذهب إلى وضع التصحيح لتصحيح الأخطاء الخاصة بك وأنت على يقين من أن الخطأ هو من وظيفة على السطر 52. ولكن منذ وضع التصحيح يبدأ في السطر 1 ، هل لديك أي خيار سوى زيارة السطر 52 واحدا تلو الآخر؟ بالطبع لا!

ما عليك سوى إضافة `debugger` الكلمات الرئيسية قبل الوظيفة.

 `console.log("Outside the function....everything's going smoothly"); 
 
 debugger; 
 
 function doesSomething() { 
    //some logic 
    console.log("Something went wrong inside here!"); 
 } 
` 

الآن افتح الملف مرةً أخرى في وضع التصحيح ، ثم اضغط **C** على لوحة المفاتيح هذه المرة.

نقل **N** ينقل المصحح إلى السطر التالي ثم الضغط على **C** بإعلام المصحح للانتقال خلال التعليمات البرمجية بالكامل دفعة واحدة. هذا هو نفس تشغيل دون وضع التصحيح. _ولكن_ ، يحتوي كودك على إضافة هذه المرة. كنت تفكر في ذلك - الكلمة الأساسية `debugger` . ضغط **C** عادةً تشغيل التعليمات البرمجية حتى النهاية ولكن بسبب إضافة `debugger` ، فإنه سيتم إيقاف اليمين قبل بدء تشغيل الدالة.

لذلك بعد تشغيل الملف في وضع التصحيح ، سيؤدي الضغط على **C** إلى تخطي التعليمة البرمجية والتوقف تمامًا قبل الوظيفة في الكلمة الرئيسية `debugger` . بعد ذلك ، يمكنك البدء من خلال خطوة واحدة في سطر واحد في كل مرة حتى يتم تحديد الخطأ الخاص بك.