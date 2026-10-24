KT Chat — Free Starter (Android Chrome)
========================================

ဒီ starter မှာ အလုပ်လုပ်တာ
- Email/Password အကောင့်ဖွင့်၊ ဝင်၊ ထွက်
- User UID ပြသခြင်း
- UID ဖြင့် တစ်ဦးချင်း chat စခြင်း
- Firestore မှ real-time စာဖတ်ခြင်း/ပို့ခြင်း
- တစ်ဦးချင်း Voice Call နှင့် Video Call (WebRTC အခြေခံ)
- အဝင် Call လက်ခံ/ငြင်း၊ ဖုန်းချခြင်း
- Firestore Security Rules အခြေခံကာကွယ်မှု

မပါသေးတာ
- Photo/Video upload
- Group chat
- Group calls
- Background/closed-app ringing and push notifications
- Production-grade TURN relay
- Website hosting/deployment

အရေးကြီး
- Firebase Console ရှိ Project ID: kt-chat-bb6e3 ကိုသုံးပါ။
- API key, authDomain, projectId, appId သည် Web app config ထဲမှ ယူပါ။
- Service account JSON / private key များကို browser code ထဲ မထည့်ပါနှင့်၊ ဘယ်သူ့ကိုမှ မပို့ပါနှင့်။
- Firebase Authentication + Firestore သာ သုံးထားသည်။ Billing မချိတ်ဘဲ Spark plan ဖြင့် စတင်နိုင်သော်လည်း free quota limits ရှိသည်။
- Call များအတွက် browser ရှိ HTTPS context လိုအပ်သည် (localhost ကိုသာ browser က ခွင့်ပြုနိုင်သည်)။ index.html ကို file:// ဖြင့်ဖွင့်ပါက camera/microphone သုံးမရနိုင်ပါ။
- WebRTC STUN server သည် အခမဲ့ connectivity စမ်းသပ်ရန်သာ ဖြစ်သည်။ အချို့ mobile/network/NAT များတွင် Call မချိတ်နိုင်နိုင်ပါ။ TURN relay မပါသောကြောင့် အမြဲအလုပ်လုပ်မည်ဟု အာမမခံနိုင်ပါ။
- Android တစ်လုံးတည်းဖြင့် file ကို edit လုပ်ခြင်းနှင့် Firebase Console စီမံခြင်း လုပ်နိုင်သော်လည်း public website တင်ဖို့ hosting service တစ်ခုကို ထပ်ရွေးရပါမည်။
- Firestore Rules ကို Firebase Console > Build > Firestore Database > Rules ထဲမှာ အစားထိုးပြီး Publish လုပ်ပါ။
- Authentication > Sign-in method > Email/Password ကို Enable လုပ်ပါ။
- Rules ပြင်ပြီးနောက် account နှစ်ခုဖြင့် စမ်းသပ်ပါ။ User A ၏ UID ကို User B ထံ ပေးပါ။ User B က UID ထည့်ပြီး chat စပါ။ A နှင့် B နှစ်ဖက်လုံး စာပို့/လက်ခံစမ်းပါ။
- User list အားလုံးကို အများမြင်စေမည့် directory မရှိပါ။ တစ်ဖက်လူ၏ UID ကို တိုက်ရိုက်မျှဝေရမည်။

Android မှာ စတင်သုံးရန်
1. ZIP ကို ဖြည်ပါ။
2. index.html ကို HTML code ပြင်နိုင်သော Android editor app ဖြင့်ဖွင့်ပါ၊ သို့မဟုတ် HTTPS static hosting တင်ပါ။
3. Firebase Console > Project settings > General > Your apps > Web app > Config မှ apiKey, authDomain, projectId, appId ကိုယူပါ။
4. index.html ကိုဖွင့်ပြီး Config အကွက် ၄ ခုဖြည့်ကာ "Config ကို ဒီ Browser မှာ အသုံးပြုမယ်" ကိုနှိပ်ပါ။
5. Authentication > Sign-in method > Email/Password ကို Enable လုပ်ပါ။
6. Firestore Rules ထဲက firestore.rules ကို paste လုပ်ပြီး Publish လုပ်ပါ။
7. Account ၂ ခုဖွင့်ရန် email ၂ ခုလိုပါသည်. Account တစ်ခုကို ဖုန်း၏ browser profile/private session တစ်ခုတွင် စမ်းသပ်နိုင်သည်; private browsing data may disappear after closing.
8. Account A UID ကို copy လုပ်ပြီး Account B ထဲမှာ ထည့်ကာ Chat စပါ။

Troubleshooting
- auth/operation-not-allowed: Email/Password provider ကို Enable လုပ်ပါ။
- Missing or insufficient permissions: Firestore Rules ကို Publish လုပ်ပြီး UID မှန်ကြောင်းစစ်ပါ။
- Firebase initialization error: apiKey/authDomain/projectId/appId ပြန်စစ်ပါ။
- Module/CORS error when opening file: local file:// mode မသုံးဘဲ HTTPS hosting တင်ပါ။
- Network error: internet, browser JavaScript support, and SDK CDN access စစ်ပါ။

Firebase official docs:
https://firebase.google.com/docs/auth/web/start
https://firebase.google.com/docs/firestore
https://firebase.google.com/docs/rules
https://firebase.google.com/pricing


Phone number sign-in (SMS OTP)
------------------------------
- Email/Password and Phone/SMS are two available sign-in methods in this starter.
- Firebase Console > Authentication > Sign-in method > Phone ကို Enable လုပ်ပါ။
- Authentication > Settings > Authorized domains ထဲမှာ hosting domain ကို ထည့်ပါ။
- Authentication > Settings > SMS region policy ထဲမှာ လိုအပ်တဲ့နိုင်ငံကို ခွင့်ပြုပါ။
- Phone sign-in ကို HTTPS hosting ကနေသာ စမ်းပါ။ Firebase reCAPTCHA ပေါ်လာရင် ဖြေပါ။
- ဖုန်းနံပါတ်ကို international format ဖြင့်ထည့်ပါ (ဥပမာ Myanmar +95, နံပါတ်အစက 0 ကိုဖြုတ်ပါ)။
- SMS ကုဒ်ရောက်လာမှ OTP ထည့်ပြီး Verify လုပ်ပါ။
- အရေးကြီး: Firebase ရဲ့ လက်ရှိ pricing/limits အရ phone verification SMS သည် Blaze/pay-as-you-go plan လိုအပ်နိုင်ပြီး SMS တစ်စောင်ချင်း ကုန်ကျနိုင်သည်။ Billing မချိတ်လိုလျှင် Gmail Email/Password နည်းလမ်းကိုသာ သုံးပါ။ Test phone numbers ကို Firebase Console မှာ configure လုပ်နိုင်ပါက SMS မပို့ဘဲ test လုပ်နိုင်သည်။
- Gmail နဲ့ဖွင့်ထားတဲ့ account နဲ့ phone နဲ့ဖွင့်ထားတဲ့ account အလိုအလျောက် မချိတ်ဆက်ပါ။ Account linking သည် သီးခြား feature ဖြစ်ပြီး ဒီ starter မှာ မထည့်ရသေးပါ။

Official docs:
https://firebase.google.com/docs/auth/web/phone-auth
https://firebase.google.com/pricing
https://firebase.google.com/docs/auth/limits


Install KT Chat on Android home screen (PWA)
--------------------------------------------
1. Upload all files/folders in this ZIP to an HTTPS hosting website, keeping these together:
   - index.html
   - manifest.webmanifest
   - sw.js
   - icons/icon-192.png and icons/icon-512.png
   - firestore.rules is published separately in Firebase Console.
2. Open the deployed HTTPS URL in Google Chrome on Android.
3. Finish Firebase Config and sign in once.
4. Chrome menu ⋮ > "Install app" or "Add to Home screen" > Install/Add.
5. An icon named KT Chat should appear on the home screen. Tap it to open the app-like view.
6. If Install app does not appear, make sure the website uses HTTPS and the manifest/icon/service worker files are uploaded in the correct paths; refresh Chrome.
Important: installing to home screen does not turn it into a native APK. It is an installable web app (PWA), and chat/calls require internet and Firebase setup. Voice/video calls require HTTPS and microphone/camera permissions. The app shell may load offline, but messaging and calls need internet.
