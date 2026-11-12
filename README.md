# SIRIUS STORE — APK (GitHub Actions orqali yig'iladi)

## v2.7
- Diagnostika: o'ng pastdagi yozuvda versiya, WebView, APK/web va plagin holati ko'rinadi. Tugma bosilganda javob bo'lmasa, qizil xabarda qaysi element bosishni to'sayotgani chiqadi.

## v2.2
- Eski Android WebView (Chrome 80 dan past) da ishlamaydigan yangi sintaksis (`?.`, `??`) olib tashlandi: bunday telefonlarda tugmalar bosilganda animatsiya bor, lekin hech narsa ochilmasdi.
- Ekranning o'ng pastida kichik `v2.2 • WebView NN` yozuvi turadi. Ilova to'liq yuklanmasa, qizil xabar chiqadi.

## v2.1 — tuzatish (MUHIM)
- **"Ilovaga kirsam hech qaysi tugma ishlamaydi" xatosi tuzatildi.** Sabab: kod Android ichida mavjud bo'lmagan `Capacitor.registerPlugin()` ni chaqirardi va shu joyda to'xtab, qulf, orqaga tugmasi, sinxronlash va boshqa hamma narsa yuklanmay qolardi. Endi `Capacitor.Plugins.Sirius` orqali ulanadi.
- Kutilmagan xato bo'lsa, ekran tepasida qizil xabar chiqadi (jim qotib qolmaydi). Shu xabarni menga yuborsangiz, sababini topaman.

## APK ni yig'ish (bir marta sozlanadi)
1. github.com da **YANGI PRIVATE repo** oching (Private bo'lishi shart — ichida imzo kaliti va Telegram token bor).
2. Shu zip ichidagi hamma narsani repoga yuklang. `.github` papkasi yashirin bo'lgani uchun web orqali yuklashda ko'rinmasligi mumkin.
   Shunda: repoda **Add file → Create new file** → nom maydoniga `.github/workflows/build-apk.yml` yozing va zipdagi `build-apk.yml` mazmunini qo'ying.
   Yoki kompyuterda:
   ```
   git init && git add -A && git commit -m "SIRIUS STORE"
   git branch -M main
   git remote add origin https://github.com/<login>/<repo>.git
   git push -u origin main
   ```
3. Repo → **Actions** → "Build APK" → bajarilishini kuting (5–10 daqiqa).
4. Tugagach shu yugurish sahifasi pastida **Artifacts → SIRIUS-STORE-apk** ni yuklab oling, zipdan `app-debug.apk` chiqadi.
5. Telefonga o'rnating ("noma'lum manbalardan o'rnatish"ga ruxsat bering).

Keyin kodni o'zgartirsangiz (`www/index.html`), repoga push qiling — APK qayta yig'iladi.
Imzo kaliti doimiy (`signing/debug.keystore`), shuning uchun yangi APK eskisi ustiga ma'lumot yo'qolmasdan o'rnatiladi.

## Birinchi ishga tushirish (telefonda)
1. Ilovani oching → SMS ruxsatini bering (so'rasa).
2. **Sozlamalar → "Fon rejimi"** kartasini bosing va chiqqan savollarga "Ha" deng: SMS ruxsati, "Signal va eslatmalar", batareya cheklovi.
3. **Android 13+ da SMS ruxsati o'chiq/kulrang bo'lsa** (APK Play Market'dan emas, shuning uchun): Telefon sozlamalari → Ilovalar → SIRIUS STORE → yuqori o'ngdagi **⋮ → "Cheklangan sozlamalarga ruxsat berish"**, so'ng Ruxsatlar → SMS ni yoqing. Ilova "Sozlamalarni ochaymi?" deb o'zi ham taklif qiladi.
4. **Sozlamalar → "Fon tekshiruvini hozir sinash"** — o'z raqamingiz bilan test qarzdor qo'shib sinab ko'ring.

Xiaomi / Redmi / Oppo / Vivo / Huawei / Samsung: ilovaga **Avtostart** ruxsatini bering va batareya tejashda **Cheklovsiz** qiling.

## v2.0 da nima o'zgardi
- **Qarz berishda muddat majburiy** (bo'sh qoldirib bo'lmaydi).
- **Barcha qarzdorlarga SMS** — telefon SIM-kartasidan, ilovadan chiqmasdan, har biriga natija (yuborildi/xato sababi) bilan. Mijoz ichidagi SMS tugmalari ham ilovadan chiqmaydi.
- **Orqaga tugmasi / imo-ishora** to'g'ri ishlaydi (oyna → sahifa → bosh sahifa → chiqish).
- **Qo'ng'iroq tugmasi** to'g'ridan-to'g'ri mijozga qo'ng'iroq qiladi (birinchi marta ruxsat so'raydi).
- **Telegram tugmasi** (bosh sahifa) — botingizni Telegramda ochadi. **Mijozdagi Telegram tugmasi** — shu mijoz raqami bilan Telegramdan izlaydi.
- **Bazani yuklash** tugmasi — botdagi yangi operatsiyalarni darhol yuklaydi (faylga saqlash: Sozlamalar → "Bazani faylga saqlash").
- **PIN-kod + barmoq izi** (Sozlamalar → Maxfiylik). Ilova 30 soniyadan ko'p fonda tursa qayta qulflanadi.
- **Til: O'zbekcha / Русский** (Sozlamalar → Ilova tili). SMS matni tili alohida (SMS sozlash sahifasida).
- **Avto-eslatma vaqti** sozlanadi (Sozlamalar → Avto-eslatma vaqti). Muddat — belgilangan vaqtdan keyingi 12 soat ichida (telefon o'chiq bo'lsa yoqilgach yuboriladi).
- **Murojat telefoni**: +998 90 661 04 99.
- **Ovozli xabar**: mijoz sahifasida "Ovozli xabar (WhatsApp/Telegram)" — matn telefon ovoz dvigatelida audio faylga aylantirilib yuboriladi.
- **Logotip** (yulduz) — ikonka, splash va bildirishnoma belgisi.
- **Bildirishnomalar**: har kuni ertalab "Muddati o'tgan qarzdorlar" ro'yxati + SMS yuborilgach "kimlarga ketdi" ro'yxati.
- Boshqa tuzatishlar: muddat hisobi endi to'lovlarni eng eski qarzdan yopadi (FIFO); sana UTC emas, mahalliy vaqt bo'yicha; Telegram sozlamalari fon hisobotida ham ishlatiladi (avval kod ichidagi token olinardi); do'kon nomi/telefon saqlanadi; operatsiyani o'chirish (mijoz sahifasida 🗑); PDF/chop etish APK da ishlaydi; mijozlar korzinadan tiklash va import to'g'rilandi.

## Telefonlarni sinxronlash (2 ta telefonda bir xil baza)
1. **Ikkala telefonda ham**: Sozlamalar → *Telegram sozlamalari* — **bir xil bot tokeni va bir xil birinchi chat ID** kiriting (masalan o'zingizning shaxsiy chat ID yoki umumiy guruh).
2. **Ikkala telefonda**: Sozlamalar → *Telefonlarni sinxronlash* → yoqing, telefonga nom bering (Telefon-1, Telefon-2).
3. Har bir amal (qarz, to'lov, kassa, sotuv, mijoz...) bot orqali o'tadi: Telegramga qisqa xabar boradi, baza fayli yangilanadi va ikkinchi telefonga **bildirishnoma** keladi.
4. Ilova ochiq bo'lsa ~12 soniyada yangilanadi; yopiq bo'lsa fonda ~5–15 daqiqada tekshiriladi. "Bazani yuklash" tugmasi darhol yangilaydi.
Qanday ishlaydi: baza JSON fayl sifatida botga yuboriladi, oxirgi fayl ko'rsatkichi botning tavsifida (description) saqlanadi. Ikkala telefon bir vaqtda o'zgartirsa, ma'lumotlar yozuvlar bo'yicha birlashtiriladi (hech narsa yo'qolmaydi).

## Cheklovlar
- Qarz to'langanini ilova faqat siz "To'lov" yozganingizdan keyin biladi.
- "SMS yuborildi" = telefon SMS ni operatorga topshirdi; yetib borganini kafolatlamaydi (hisobda mablag' bo'lishi kerak).
- Android bir vaqtda ~30 tadan ortiq SMS ni cheklaydi — so'rov chiqsa "Ruxsat" bosing.
- O'zbekcha ovoz telefonda o'rnatilmagan bo'lsa, ovozli xabar ruscha ovozda yaratiladi (Google "Speech Services" ni yangilang). WhatsApp audio faylni "ovozli xabar" emas, audio fayl sifatida jo'natadi.
- Bot tavsifi (description) sinxron ko'rsatkichi uchun ishlatiladi — botni boshqa maqsadda tavsifini o'zgartirmang.
- Telegram token kod ichida (`www/index.html`) — repo faqat Private bo'lsin. Xohlasangiz @BotFather'da tokenni yangilab, ilovada Sozlamalar → Telegram sozlamalariga kiriting (ikkala telefonda).
- Ilovani "Force stop" qilsangiz yoki o'chirib qayta o'rnatsangiz, ilovani bir marta ochish kerak.

## Telegram sozlamalari (Sozlamalar → "Telegram sozlamalari")
- Bot tokenini almashtirish mumkin (@BotFather). Bir nechta chat ID vergul bilan: shaxsiy chat, guruh (`-100...`), kanal.
- Guruh: botni guruhga qo'shing. Kanal: botni kanalga **administrator** qiling.
- "ID topish" tugmasi guruh/kanal ID sini o'zi topadi (avval o'sha yerga xabar yozing).
- Sinxronlash fayli **birinchi** chat ID ga yuboriladi.


## v2.7 o'zgarishlari
1. Mijoz sahifasida (va ro'yxatda) qalamcha: ism va telefonni keyin kiritish/tahrirlash.
2. Bosh sahifadan "Sotuvlar" bo'limi olib tashlandi, Kassa qoldi.
3. Kassa yangi ko'rinishda: balans kartasi, davr filtri, Hammasi/Kirim/Chiqim, qidiruv, kategoriya, kunlar bo'yicha guruh. Kirim/Chiqim — pastdan chiqadigan forma.
4. SMS yuborishda ilovaning "Davom etasizmi?" savoli yo'q — tugma bosilishi bilan yuboriladi.
5. Do'kon qarzlari, yetkazib beruvchilar, kirimlar, mening qarzlarim, xarajatlar, kassa, qarz/to'lov operatsiyalarida tahrirlash (qalamcha).
6. Barcha sodda prompt/confirm oynalari o'rniga zamonaviy forma va dialog oynalari.
7. Hisobotlar: Qarzlar / Sotuvlar / Kassa / Xarajatlar / Top qarzdorlar kartalari, 7 kun / Oy / Yil.
8. Ro'yxatlarda xulosa kartalari, qidiruv, filtrlar, qisman to'lov (−) tugmasi, bo'sh holat ekranlari.
9. Ikonka: qulupnay (fonsiz). Ilova nomi launcherda ikki qatorda: SIRIUS / STORE.
10. Kirim/Chiqim, xarajat, sotuv, do'kon qarzi, mening qarzlarim, kirimlar va yetkazib beruvchi formalarida: ovozli yozish (mikrofonni bosib turing, 2 daqiqagacha, 5 tagacha) va rasm qo'shish (kamera/galereya, 10 tagacha). Fayllar telefon xotirasida (IndexedDB) saqlanadi, ro'yxatda 📎 belgisi bilan ochiladi. Ruxsatlar: RECORD_AUDIO, CAMERA.

## v2.8 yangiliklari
- **Savdo (POS):** mahsulotlar bazasi (Ombor), savat, chegirma (so'm/%), qisman to'lov, qolgani mijoz qarziga; shtrix-kod skaneri (kamera, qo'lda, Bluetooth/USB skaner); kam qolgan mahsulot ogohlantirishi; qaytarish; chek (rasm, PDF, WhatsApp, Telegram, SMS, RawBT orqali termoprinter).
- **Mijozlar:** qarz/to'lov formasi rasm va ovoz bilan, bo'lib to'lash (2-12 oy), mijoz reytingi, akt sverka (PDF/rasm), to'lov cheki (SMS/Telegram/WhatsApp, avtomatik SMS), muddati o'tganlar uchun bosqichli eslatma, kontaktlar (.vcf) va Excel/CSV import.
- **Hisobotlar 2.0:** oraliq sana, grafiklar, foyda va sof foyda, top mahsulotlar, Excel (.xlsx, 8 varaq) va PDF eksport, Telegram'ga yuborish.
- **Xavfsizlik:** egasi/sotuvchi rollari (alohida PIN), faoliyat jurnali, o'chirilgan yozuvlar savati (hammasini tiklash), rasm/ovozni Telegram orqali boshqa telefonlarga o'tkazish, zaxira nusxani ulashish.
- **Qulaylik:** kunduzgi/tungi mavzu, shrift o'lchami, umumiy qidiruv, bosh sahifa xulosasi.
- **Native o'zgarish:** SiriusPlugin.java ga `shareData` (fayl ulashish) va `saveFile` ga binar (b64) qo'llab-quvvatlash qo'shildi.

## v2.9 yangiliklari
- **Ovozli xabar (TTS'siz):** "Ovozli o'qish" — mikrofonni bosib turib ovoz yozish va mijozga saqlash; "Ovozli xabar (Telegram/WhatsApp)" eng yangi ovozni (yangi yoki qarz berilgan vaqtdagi) yuboradi. Telegram: bot orqali matn + ovoz (mijoz botga bir marta Start bosadi), WhatsApp: mijoz chatiga.
- **Avto-SMS takrorlanishi:** muddati o'tganlarga har 24 soat / 2 kun / 3 kunda (orqa fonda, DailyCore.java).
- Mijozni ro'yxatdan o'chirish (savat tugmasi, o'chirilganlardan qaytariladi).
- Yangi qarzdor qo'shishda telefon va qaytarish muddati majburiy (qarz berishda ham telefon so'raladi).
- Imlo: "Murojat".
- **Ilovani Telegram orqali yangilash:** yangi versiya chiqqanda ekran bloklanadi, APK ilova ichida yuklanadi va o'rnatiladi; yangilangandan keyin bir martalik "nima yangi" xabari.

### Yangi versiyani chiqarish (yangilanish tizimi)
1. `package.json` dagi `version` ni oshiring (masalan `2.9.0` -> `3.0.0`). versionCode avtomatik: major*10000 + minor*100 + patch (3.0.0 -> 30000).
2. GitHub Actions'da APK yig'iladi (SIRIUS-STORE-apk artifact).
3. APK ni yangilanish kanaliga (bot admin) FAYL sifatida yuboring. Izoh (caption):
   ```
   #SIRIUS 3.0.0
   build=30000
   • nima yangi 1
   • nima yangi 2
   ```
   Majburiy bo'lmasa izohga `force=0` qo'shing.
4. Xabarni **qadang (Pin)**. Ilova qadalgan xabarni tekshiradi.
5. Cheklov: Telegram bot orqali 20 MB gacha fayl yuklanadi.

## v2.9.2 tuzatishlari
- Yangilanish ekranida har doim "Telegram kanalida ochish va yuklash" tugmasi bor.
- APK imzosi telefondagi ilova bilan mos kelmasa, tizim xato bermasdan oldin ilova buni aniqlaydi va qadamma-qadam qayta o'rnatish yo'riqnomasini ko'rsatadi (zaxira, kanaldan yuklash, eskisini o'chirish).
- GitHub Actions yig'ish natijasida "Imzo (signing)" bo'limi chiqadi: kutilgan SHA-256 `B05C3696E1E95DF119E90F9A3F638AC2E29FB36F8AE6EE46F01AA4F14A105431`. Boshqacha chiqsa, bu APK eski ilova ustiga o'rnatilmaydi.
- Yangi o'rnatilgan ilovada Telegram bot va chat maydonlari bo'sh (hamma o'rnatishlar bitta bazaga ulanib qolmaydi). Eski egalarda mavjud ulanish saqlanadi.

## v2.9.3
- Bosh sahifa: "Savdo" va "Ombor" plitkalari eng oxirida.
- Istalgan plitkani bosib turib (0,5 soniya) surish orqali tartibni o'zgartirish mumkin; tartib saqlanadi. "Bosh sahifa sozlamalari" oynasida tartibni boshlang'ich holatga qaytarish tugmasi bor.

## v2.9.4 — imzo muammosi butunlay yopildi
- `scripts/patch_android.py` endi `signing/debug.keystore` ni to'g'ridan-to'g'ri `android/app/build.gradle` ga ulaydi (signingConfigs). Yig'ish fayli (workflow) eski bo'lsa ham kalit doim bir xil: SHA-256 `B05C3696E1E95DF119E90F9A3F638AC2E29FB36F8AE6EE46F01AA4F14A105431`.
- `signing/debug.keystore` topilmasa yig'ish ataylab XATO bilan to'xtaydi (kalitsiz APK chiqmaydi).
- Yig'ish oxirida imzo tekshiriladi; kalit boshqacha bo'lsa yig'ish qizil bo'ladi.
- Ilova: Sozlamalar -> "Ilovani yangilash" kartasi o'rnatilgan ilovaning imzosini ko'rsatadi (barqaror yoki boshqa kalit).

## v2.9.5
- Kassadan "Kirim" (mijoz tanlangan) endi mijoz qarzidan AYRILMAYDI: u mijozning *xaridi* sifatida yoziladi. Qarz faqat mijoz profilidagi "To'lov" orqali kamayadi.
- Mijoz profili: xaridlar, qarzlar va to'lovlar bitta ro'yxatda (filtr: Hammasi / Qarzlar / To'lovlar / Xaridlar), jami xarid/to'langan/qarz xulosasi, reyting.
- Ortiqcha to'lov (minus) bo'lgan mijozlar uchun avtomatik tuzatish: ilova birinchi ochilganda taklif qiladi, profil ichida ham tugma bor. Kassadagi pul o'zgarmaydi.
- "Eng zo'r mijozlar" sahifasi (xarid bo'yicha, medallar, davr filtri), bosh sahifada plitka va Mijozlar ro'yxatida saralash (Qarz / Eng zo'r / Reyting / Yangi).

## v2.9.6
- **Tarix** endi hamma bo'limlarning umumiy jurnali: qarz/to'lov, kassa kirim/chiqim (mijozsiz ham), mijoz xaridlari, xarajat, savdo (POS), qaytarish, ombor kirimi, do'kon qarzi, mening qarzlarim. Filtr (Hammasi / Qarz va to'lov / Kassa / Savdo / Xarajat / Boshqa) va qidiruv. Boshqa yozuvga bog'langan kassa yozuvlari ikki marta ko'rsatilmaydi.
- **Statistika**: tanlangan davr uchun kassa kirim/chiqim, savdo va xarajat kartalari qo'shildi.
- **Bosh sahifa va Hisobotlar**: "Savdo tushumi" toifasidagi kassa kirimlari ham savdoga hisoblanadi.
- Sozlamalardan boshqa hamma ma'lumot telefonlar orasida sinxronlanishi tekshirildi (kassa, xarajat, savdo, ombor, mijozlar).

## v2.9.7
- Kassa (Kirim/Chiqim) va Xarajat formalarida «Kategoriyasiz» olib tashlandi. Chiqim: Ovqatlanish, Taksi, Pochta, Uy xarajati, Tovar xaridi, Ish haqi, Ijara, Kommunal, Transport, Soliq, Reklama, Boshqa. Kirim: Savdo tushumi (1-o'rinda), Qarz qaytarish, Boshqa.
- Kategoriyani qo'shish (+ Kategoriya) va o'chirish (qalamcha tugmasi, so'ng kategoriyani bosish). Qo'shilgan/o'chirilgan kategoriyalar telefonlar orasida sinxronlanadi. Eski yozuvlar o'zgarmaydi.
- Kassa kirimida mijoz tanlashda «Yangi mijoz qo'shish» (ism + telefon). Takroriy mijoz telefon raqami bo'yicha aniqlanadi: raqam bor bo'lsa yangisi yaratilmaydi, mavjud mijoz tanlanadi. Ismi bir xil, raqami boshqa mijozlar alohida mijoz bo'ladi. Yangi mijoz oynasi va mijozni tahrirlashda ham shu tekshiruv bor.
