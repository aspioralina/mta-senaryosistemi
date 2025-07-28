# mta-senaryosistemi
 MTA'da /senaryo komutuyla yazıların dünya üzerinde belirli bir mesafeye kadar görülebileceği, rol yapımına katkı sağlayan qb-core benzeri bir senaryo sistemi. Şimdi sistemin kullanımından, optimizasyonundan ve yapısından detaylıca bahsedeyim.
Kullanım Formatı
/senaryo [metin] [boyut] [font] [renk] [uzaklık]

[boyut] → dxDrawText font boyutu. (örn: 1, 1.5)

[font] → Yazı tipi (default, clear, bankgothic, arial, vb.)

[renk] → RGBA formatında renk değeri ya da r,g,b,a olarak. (örn: 255,255,255,200)

[uzaklık] → Yazının kaç metreye kadar görülebileceği. (örn: 10)Kullanım Formatı
css
Kopyala
Düzenle
/senaryo [metin] [boyut] [font] [renk] [uzaklık]
Parametre Açıklamaları:
[metin] → Yazmak istediğin senaryo metni. (örn: "Kıyafetini düzeltir.")

[boyut] → dxDrawText font boyutu. (örn: 1, 1.5)

[font] → Yazı tipi (default, clear, bankgothic, arial, vb.)

[renk] → RGBA formatında renk değeri ya da r,g,b,a olarak. (örn: 255,255,255,200)

[uzaklık] → Yazının kaç metreye kadar görülebileceği. (örn: 10)


Sistem temel olarak şunları içerir:

Komut girişi: addCommandHandler("senaryo", ...)

Yazının oyuncunun konumunda oluşturulması (örneğin createSenaryoText(...))

onClientRender ile sürekli olarak dxDrawText’in oyuncu kamerasına göre konumlandırılması

Mesafe kontrolü (getDistanceBetweenPoints3D) ile sadece belirli bir uzaklıktaki oyuncuların görebilmesi

Opsiyonel olarak getScreenFromWorldPosition ile ekran koordinatına çevrilerek 3D yerleştirme



Optimizasyon
Uzaklık kontrolü sadece ekranda görünmesi gereken yazılar için yapılır. Her karede tüm yazıları çizmek yerine mesafeye göre filtreleme yapılmalıdır.

Yazılar bir table içinde tutulur ve sadece gerekli olanlar çizilir.

Fazla senaryo yığılmasını engellemek için yazılar zamanla silinebilir (örneğin 60 saniye sonra otomatik kaldırma).

onClientRender içinde sadece ekrandaki yazılar dxDrawText ile çizilir (örneğin isLineOfSightClear ile duvar arkasında gizleme bile yapılabilir).




/senaryo komutunun bir bindKey versiyonu eklenebilir (örn: SHIFT+T tuşuna basıldığında yazı penceresi açılır).

Rol kaydı için log dosyasına veya MySQL'e kayıt yapılabilir.

Sadece belirli job’lara özel senaryolar (örn: polis / EMS gibi) yapılabilir.

Yazılar için fade-in ve fade-out efektleri dxDrawText alpha kanalı ile sağlanabilir.

<img width="641" height="297" alt="image" src="https://github.com/user-attachments/assets/7b152661-62b0-4aba-9b62-b123285a0f00" />
