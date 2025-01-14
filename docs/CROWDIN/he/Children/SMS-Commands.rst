פקודות SMS
**************************************************
בטיחות לפני הכל
==================================================
* AndroidAPS מאפשר שליטה בלופ שבטלפון של ילד מרחוק באמצעות הודעת טקסט.  אם תאפשרו את תקשורת SMS, זכרו שהטלפון ששולח את הפקודות יכול להיגנב. לכן זכרו להגן עליו עם סיסמא לכל הפחות. מומלץ להגדיר סיסמא חזקה או זיהוי ביומטרי.
* בנוסף, מומלץ לאשר `מספר טלפון נוסף <#authorized-phone-numbers>`_ לפקודות SMS. כך תוכלו להשתמש במספר הנוסף כדי `להשבית זמנית <#other>`_ את תקשורת ה-SMS במקרה של אובדן או גניבת מכשיר הטלפון העיקרי.
* AndroidAPS יודיע בהודעת טקסט אם בוצעו הפקודות שנשלחו, כגון בולוס או שינוי פרופיל. רצוי להגדיר זאת כך שתשלחנה הודעות SMS לאישור לשני מספרי טלפון שונים לפחות, במקרה שאחד הטלפונים המקבלים ייגנב.
* **במידה ומתן הבולוסים מתבצע באמצעות פקודות SMS, יש להזין את כמות הפחמימות לנייטסקאוט (NSClient, האתר...)!** אם לא תעשה זאת, הIOB (אינסולין בגוף) יהיה נכון, אך הCOB (פחמימות בגוף) יירשם כנמוך מידי, וכתוצאה מכך יתכן שלא יתבצע בולוס תיקון מכיון שהAAPS יעריך כי רמת האינסולין הפעיל בגוף גבוהה מידי.
החל מגירסת AndroidAPS 2.7, יש להשתמש באפליקציית אימות עם סיסמה חד פעמית מבוססת-זמן להגברת בטיחות השימוש בפקודות SMS.

הגדרת פקודות SMS
==================================================

.. image:: ../images/SMSCommandsSetup.png
  :alt: הגדרת פקודות SMS
      
* ניתן לבצע את רוב התאמות ערכי המטרה הזמניים, מעקב AAPS, וכו'. באפליקציית `NSClient <../Children/Children.html>`_ בטלפון אנדרואיד עם חיבור לאינטרנט.
* לא ניתן לתת בולוסים דרך הנייטסקאוט, אבל ניתן להשתמש בפקודות SMS.
במידה ומכשיר הטלפון למעקב שלך הוא אייפון, ולכן אין באפשרותכם להשתמש באפליקציית ה-NSClient, קיימות פקודות SMS נוספות לשם כך.

* בהגדרות מכשיר האנדרואיד, עבור ליישומים > AndroidAPS > הרשאות ואפשרו הרשאת SMS.

מספרי טלפון מורשים
-------------------------------------------------
ב-AndroidAPS, עברו ל**העדפות > תקשורת SMS** והזינו את מספר(י) הטלפון מהם אפשר יהיה לקבל פקודות SMS (הפרידו באמצעות ";" - לדוגמא, +972598765432;+972541234567) 
* הפעילו את 'אפשר פקודות SMS מרחוק'.
* במידה וברצונכם להשתמש ביותר ממספר אחד:

  * הזינו מספר אחד בלבד.
  * וודאו כי המספר היחיד הזה עובד באמצעות שליחת ואישור פקודת SMS.
  * הזינו מספר(י) נוספ(ים), המופרדים ביניהם באמצעות ";", ללא רווחים.
  
    .. image:: ../images/SMSCommandsSetupSpace2.png
      :alt: SMS Commands Setup multiple numbers

מספר הדקות בין פקודות בולוס
-------------------------------------------------
* ניתן להגדיר את זמן העיכוב המינימלי בין שני בולוסים הניתנים באמצעות פקודות SMS.
מטעמי בטיחות, עליכם להוסיף לפחות שני מספרי טלפון מאושרים על מנת לערוך נתון זה.

תוספת PIN קבוע לקוד האסימון
-------------------------------------------------
מטעמי בטיחות, על קוד PIN להופיע בסוף קוד התגובה.
* כללי ה-PIN:

  * 3 עד 6 ספרות
  * ללא ספרות זהות (כגון 1111)
  * ללא מספרים עוקבים (כגון 1234)

הגדרת מאמת
-------------------------------------------------
מטרת השימוש באימות דו-גורמי היא לשיפור הבטיחות.
* תוכלו להשתמש בכל אפליקציית אותנטיקציה שתומכת באסימוני RFC 6238 TOTP. מספר אפליקציות חינמיות פופולאריות:

  * `Authy <https://authy.com/download/>`_
  * Google Authenticator - `Android <https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2>`_ / `iOS <https://apps.apple.com/de/app/google-authenticator/id388497605>`_
  * `LastPass Authenticator <https://lastpass.com/auth/>`_
  * `FreeOTP Authenticator <https://freeotp.github.io/>`_

* התקינו אפליקציית אימות לבחירתכם על הטלפון העוקב, וסרקו את הברקוד (QR) המופיע ב-AAPS.
* נסו את הקוד החד-פעמי ע"י הקלדת האסימון שמופיע באפליקציית האימות ואת ה-PIN שהגדרתם קודם לדוגמה:

  * PIN החובה שהגדרתם הוא 2020
  הקוד שאפליקציית האימות רושם הוא 457051
  * הזינו 4570512020
   
* במידה והקוד שהזנתם נכון, ההודעה "PIN שגוי" באדום תשתנה **אוטומטית** ל"OK" ירוק. **אין לחצן עליו עליכם ללחוץ!**
* על השעונים בשני מכשירי הטלפון להיות מסונכרנים. מומלץ להגדיר עדכון זמן אוטומטי מהרשת. הפרשים בזמנים עלולים לגרום לשגיאות אימות.
* השתמשו בלחצן "איפוס מאמתים" אם ברצונכם למחוק מאמתים קיימים.  (איפוס המאמתים הופך את כל המאמתים שהוגדרו כלא חוקיים. תצטרכו להגדירם מחדש)

השתמשו בפקודות SMS
==================================================
* שלחו הודעת SMS לטלפון בו מופעל ה-AndroidAPS ממספר(י) הטלפונ(ים) המאושר(ים), באמצעות אחת מה`פקודות <../Children/SMS-Commands.html#commands>`__ למטה. 
* מכשיר הטלפון עם ה-AAPS ישלח תגובה על הצלחת הפקודה או הסטטוס המבוקש. 
* אשרו את הפקודה באמצעות שליחת הקוד, במידת הצורך. לדוגמה:

  * PIN החובה שהגדרתם הוא 2020
  הקוד שאפליקציית האימות רושם הוא 457051
  * הזינו 4570512020

**טיפ**: תוכנית SMS ללא הגבלה (בכל מכשיר טלפון בו תשתמש) תהיה שימושית מאד במידה והינכם צפויים לשלוח מספר רב של פקודות SMS.

פקודות
==================================================
את הפקודות יש לשלוח באנגלית. התגובה תהיה בשפה המקומית שלך, במידה ומחרוזת התגובה כבר `תורגמה <../translations.html#translate-strings-for-androidaps-app>`_.

.. image:: ../images/SMSCommands.png
  :alt: דוגמא לפקודות SMS

לולאה
--------------------------------------------------
* LOOP STOP/DISABLE (עצור/הפסק לולאה)
  * תגובה: הלולאה הופסקה
* LOOP START/ENABLE (התחל/הפעל לולאה)
  * תגובה: הלולאה הופעלה
* LOOP STATUS (סטטוס לולאה)

  * התגובה תהיה תלויה בסטטוס הלולאה באותו זמן

    * הלולאה כבויה
    * הלולאה פעילה
    * מושהת (10 דקות)
* LOOP SUSPEND 20 (השהיית לולאה 20)
  * תגובה: הלולאה הושהתה למשך 20 דקות
* LOOP RESUME (הפעל לולאה מחדש)
  * תגובה: הלולאה הופעלה מחדש

נתוני החיישן (ניטור סוכר רציף)
--------------------------------------------------
* BG (סוכר בדם)
  * תגובה: רמת גלוקוז אחרונה: 5.6 לפני 4 דקות, דלתא: -0,2 mmol, IOB: 0.20U (בולוס: 0.10U בזאל: 0.10U)
* CAL 5.6 (כיול)
  * תגובה: על מנת לשלוח כיול 5.6, השיבו באמצעות הקוד מאפליקציית האימות למשתמש, ולאחריה קוד ה-PIN
  * תגובה לאחר קבלת הקוד הנכון: הכיול נשלח (**במידה והותקן xDrip. על קבלת כיולים להיות מופעלת בxDrip+**)

אינסולין בזאלי
--------------------------------------------------
* BASAL STOP/CANCEL (עצור/בטל אינסולין בזאלי)
  * תגובה: על מנת לעצור את המינון הבזאלי הזמני, השיבו באמצעות הקוד מאפליקציית האימות למשתמש, ולאחריו קוד ה-PIN
* BASAL 0.3 (בזאלי 0.30)
  * תגובה: על מנת להתחיל בזאלי 0.30U/h למשך 30 דקות, השיבו עם הקוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* BASAL 0.3 20 (בזאל 0.3 למשך 20 דקות)
  * תגובה: על מנת להתחיל בזאל 0.30U/h למשך 20 דקות, השיבו עם הקוד מאפליקציית האימות למשתמש, ולאחריו קוד ה-PIN
* BASAL 30% (בזאל 30%)
  * תגובה: על מנת להתחיל מינון בזאלי 30% למשך 30 דקות, השיבו עם הקוד מאליקציית האימות למשתמש, ואחריו קוד ה-PIN
* BASAL 30% 50 (בזאלי 30% למשך 50 דקות)
  * תגובה: על מנת להתחיל מינון בזאלי 30% למשך 50 דקות, השיבו עם הקוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN

בולוס
--------------------------------------------------
לא ניתן לבצע בולוס מרחוק בתוך 15 דקות (ניתן לשנות ערך זה רק לאחר הוספת 2 מספרי טלפונים) לאחר הפקודה מרחוק או פקודת הבולוס האחרונה! לכן, התגובה תהיה תלויה בשעה בה ניתן הבולוס האחרון.

* BOLUS 1.2
  * תגובה א': על מנת לתת בולוס 1.2U, השיבו עם קוד מאפליקציית האימות למשתמש, ולאחריו קוד ה-PIN
  * תגובה ב': בולוס מרחוק אינו זמין. נסו שוב מאוחר יותר.
* BOLUS 0.60 MEAL (בולוס 0.60 - ארוחה)
  * בציון הפרמטר האופציונלי MEAL (ארוחה), ערך המטרה הזמני ישתנה לערך המתאים לאוכלים בקרוב (ערך ברירת המחדל: 90 mg/dL למשך 45 דקות).
  * תגובה א': על מנת להזריק בולוס ארוחה 0.60U, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
  * תגובה ב': בולוס מרחוק אינו זמין. 
* CARBS 5
  * תגובה: על מנת להזין 5 גר' בשעה 12:45, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* CARBS 5 17:35/5:35PM
  * תגובה: על מנת להזין 5 גר' בשעה 17:35, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* EXTENDED STOP/CANCEL (ביטול/עצירה מושהת)
  * תגובה: על מנת לעצור את הבולוס הממושך, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* EXTENDED 2 120 (בולוס מושהה 2U למשך 120 דקות)
  * תגובה: על מנת להתחיל בולוס מושהה 2U למשך 120 דקות, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN

פרופיל
--------------------------------------------------
* PROFILE STATUS (סטטוס פרופיל)
  * תגובה: פרופיל1
* PROFILE LIST (רשימת פרופילים)
  * תגובה: 1. 'פרופיל1' 2. 'פרופיל2'
* PROFILE 1 (פרופיל 1)
  * תגובה: על מנת להחליף פרופיל לפרופיל1 של 100%, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* PROFILE 2 30 (פרופיל 2, 30%)
  * תגובה: על מנת להחליף את הפרופיל לפרופיל2 30%, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN

אחר
--------------------------------------------------
* TREATMENTS REFRESH (רענן טיפולים)
  * תגובה: רענן טיפולים מהנייטסקאוט
* NSCLIENT RESTART (התחל NSClient מחדש)
  * תגובה: מתחיל NSCLIENT
* משאבה
  * תגובה: חיבור אחרון: לפני דקה. זמני: 0.00U/h בשעה 11:38 5/30דקות IOB: 0.5U נותר: 34U סוללה: 100
* PUMP CONNECT (חיבור משאבה)
  * תגובה: המשאבה חוברה מחדש
* PUMP DISCONNECT *30* (ניתוק המשאבה למשך 30 דקות)
  * תגובה: על מנת לנתק את המשאבה למשך *30* דקות, השיבו עם הקוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* SMS DISABLE/STOP (השבת/עצור SMS)
  * על מנת להשבית את שירות ה-SMS מרחוק, השיבו עם קוד Any. שימו לב: תוכלו להפעיל אותו ישירות מחדש אך ורק מתוך הטלפון החכם העיקרי עם אפליקציית ה-AAPS.
* TARGET MEAL/ACTIVITY/HYPO (ערך מטרה אוכלים בקרוב/פעילות/היפו)   
  * תגובה: על מנת להגדיר את ערך המטרה הזמני לארוחה/פעילות/היפו, השיבו עם הקוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* TARGET STOP/CANCEL (עצור/בטל ערך מטרה)   
  * על מנת לבטל את ערך המטרה הזמני, השיבו עם קוד מאפליקציית האימות למשתמש, ואחריו קוד ה-PIN
* HELP (עזרה)
  * תגובה: רמת גלוקוז, לולאה, טיפולים, .....
* HELP BOLUS (עזרה - בולוס)
  * תגובה: בולוס 1.2 בולוס 1.2 ארוחה

פתרון בעיות
==================================================
פקודות SMS מרובות
--------------------------------------------------
אם אתם מקבלים את אותה ההודעה שוב ושוב (לדוגמה החלפת פרופיל) כנראה שהגדרתם הגדרה מעגלית עם אפליקציות אחרות. לדוגמה עם xDrip+. אם כך הדבר, וודאו ש-xDrip+ (או אפליקציות אחרות) לא מעלות טיפולים לנייטסקאוט. 

אם האפליקציות האחרות מותקנות על טלפונים אחרים, בטלו העלאת טיפולים גם בהם.

כאשר פקודות ה-SMS אינן פועלות בטלפון של סמסונג
--------------------------------------------------
התקבל דיווח על כך שפעולות SMS נעצרו לאחר עדכון תוכנה בטלפונים מדגם Galaxy S10. ניתן לפתור זאת על ידי ביטול האפשרות 'שלח כהודעת צ'אט' או ע"י התקנת אפליקציית SMS אחרת.

.. image:: ../images/SMSdisableChat.png
  :alt: Disable SMS as chat message
