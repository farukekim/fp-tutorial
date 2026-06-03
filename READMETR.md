# Filament Painting Kullanım Tutoriali

Bu tutorial, Filament Painting uygulamasını ilk açılıştan STL dışa aktarmaya kadar baştan sona anlatır. Uygulama; fotoğrafları katmanlı 3D filament sanatına dönüştürmek, filament geçişlerini planlamak, 3D mesh önizlemesi almak, proje kaydetmek ve STL dışa aktarmak için tasarlanmıştır.

## 1. Uygulamayı Tanıma

Ana ekranda çalışma alanı birkaç panelden oluşur:

- **Mesh Preview**: Oluşturulan 3D modeli canlı olarak gösterir. Buradan mesh modu seçilir, kaynak proje içe aktarılır, proje kaydedilir ve STL dışa aktarılır.
- **Image Preview**: Fotoğraf yükleme, görüntüyü inceleme, görselden katman seçme ve Color Match için renk örnekleme alanıdır.
- **Palette Engine**: Baskıda kullanılacak filament renk sırasını ve katman aralıklarını yönetir.
- **Geometry Engine**: Color Match modunda renk eşleşmesine göre geometriyi ve aktif/pasif katmanları yönetir.
- **Filament Library**: Hazır ve özel filamentlerin bulunduğu kütüphanedir. Filamentleri işaretleyebilir, filtreleyebilir, sürükleyip core panellerine bırakabilirsiniz.
- **Project Controls**: Model yüksekliği, katman yüksekliği, taban yüksekliği, taban kalınlığı, genişlik ve yükseklik ayarlarını içerir.

Geniş ekranlarda paneller yan yana görünür. Küçük ekranlarda bazı paneller **Show / Hide** düğmeleriyle açılıp kapanır.

## 2. İlk Fotoğrafı Yükleme

1. **Image Preview** paneline gidin.
2. **Load Image** düğmesine dokunun.
3. Fotoğraflar seçicisinden bir görsel seçin.
4. Görsel yüklendiğinde **Change Image** düğmesiyle daha sonra başka bir görsele geçebilirsiniz.

Uygulama JPG, PNG, WEBP ve SVG kaynaklarını kullanıcı arayüzünde desteklenen görsel akışına göre kabul eder. Görsel yüklendiğinde uygulama modelin en uzun kenarını mevcut ölçüye göre koruyarak **Width** ve **Height** değerlerini otomatik oranlar.

İyi sonuç için yüksek kontrastlı, net silüetli ve fazla bulanık olmayan görseller seçin. Transparan alanlar STL mesh üretiminde boş alan gibi davranabilir.

![Load Image](<loadimage.gif>)

## 3. Model Ölçülerini Ayarlama

**Project Controls** panelinde baskı geometrisini belirleyen temel alanlar bulunur:

- **Mesh Height**: Modelin toplam hedef kalınlığıdır. Varsayılan değer `2.24 mm`.
- **Layer Height**: Dilimleyicide kullanacağınız katman yüksekliğidir. Varsayılan değer `0.08 mm`.
- **Base Layer Height**: İlk taban katmanının yüksekliğidir. Varsayılan değer `0.16 mm`.
- **Base Thickness**: STL geometrisinin minimum taban kalınlığıdır. Varsayılan değer `0.48 mm`.
- **Width**: Model genişliğidir. Varsayılan değer `200 mm`.
- **Height**: Model yüksekliğidir. Varsayılan değer `200 mm`.

Katman sayısı hesaplama:

Örnek: `2.24 mm` mesh yüksekliği, `0.16 mm` base layer ve `0.08 mm` layer height ile yaklaşık 27 katmanlık bir çalışma oluşur.

Sayısal alanlara yalnızca sayı ve nokta girilebilir. Alan boş bırakılırsa uygulama varsayılan değeri geri koyar.
![3D Mesh Model Sizes](<3dmeshmodelsizes.gif>)

## 4. Mesh Preview ile 3D Modeli İnceleme

Fotoğraf yüklendiğinde **Mesh Preview** paneli 3D önizlemeyi üretir.

Önizleme kontrolleri:

- **Drag to rotate**: Tek parmakla veya mouse ile modeli döndürün.
- **Two fingers to pan**: İki parmakla modeli kaydırın.
- **Pinch to zoom**: Yakınlaştırıp uzaklaştırın.
- **Reset**: Kamera görünümünü sıfırlar.
- Tam ekran simgesi: Mesh önizlemesini daha büyük görüntüler.

Önizleme, uygulama aktif değilken GPU işini durdurabilir. Uygulamaya geri dönüldüğünde preview tekrar hazırlanır.
![Mesh Preview](<meshpreview.gif>)

## 5. Mesh Mode Seçimi

**Mesh Preview > Mesh Mode** bölümünde iki mod vardır:

### Standard Mesh

Standard Mesh ücretsizdir. Görselin parlaklık/luminance bilgisinden katmanlı bir yükseklik modeli üretir. Kendi filament paletinizi **Palette Engine** üzerinden yönetirsiniz.

Bu mod şu işler için uygundur:

- Basit resimler.
- Kişisel projeleriniz, yani satış yapmak için değil kendi kullanımınız için projelerinizde bu modu kullanabilirsiniz.

### Color Match

Color Match aylık abonelik gerektirir. Görseldeki renkleri analiz eder, filament kütüphanesindeki renklerle eşleştirir, palette ve geometry core atamalarını otomatik hazırlamaya yardımcı olur.

Color Match ile:

- Otomatik dominant renk analizi yapabilirsiniz. Bu özellik geliştirme aşamasında olduğundan bazı resimlerde iyi sonuç vermeyebilir. En iyi sonuç için manuel renk seçimi yapmalısınız.
- Filament dizilimini görsele göre optimize edebilirsiniz.
- Geometry Engine üzerinden bazı katmanları devre dışı bırakabilirsiniz.
- Renk eşleştirme metodu seçebilirsiniz.
- Aktif abonelik süresince ticari kullanım lisansına erişirsiniz.

Color Match seçildiğinde abonelik aktif değilse abonelik ekranı açılır.

## Not:

Dominant colors experimental özelliktir, bazı resimlerde çok iyi sonuç verirken bazı resimlerde iyi sonuç vermeyebilir. Bu durumda color match algoritmalarında manuel geometry engine üzerinde renk atamaları ile en iyi sonucu alabilirsiniz. Dominant Colors algoritması color match algoritmasına doğrudan etki etmez. Unutmayın Color Match algoritmalarında en iyi sonucu kendiniz geometry engine ve palette engine üzerinde ayarlamalar yaparak alabilirsiniz.

![Mesh Modes](<meshmodes.gif>)

## 6. Color Match Aboneliği ve Restore

Color Match ekranında şu seçenekler bulunur:

- **Subscribe for ... / month**: Aylık aboneliği Apple üzerinden başlatır.
- **Restore Purchases**: Daha önce aynı Apple ID ile alınmış aboneliği geri yükler.
- **License Terms**: Ticari kullanım koşullarını gösterir.
- **Privacy**: Gizlilik bilgisini gösterir.
- **Tutorials**: Tutorial bağlantısını açar.
- **Apple EULA**: Apple standart EULA sayfasını açar.

Standard Mesh kişisel projeler için ücretsiz kalır. Uygulamanın lisans metnine göre satış amaçlı 3D baskılar veya dijital dosyalar için aktif aylık abonelik gerekir.

## 7. Color Match Otomatik Pipeline

Color Match aktifken **Mesh Preview** panelinde **Dominant Colors** kontrolü çalışır.

1. **Color Match** modunu açın.
2. **Dominant Colors** değerini seçin. Aralık `2` ile `8` arasındadır, varsayılan `6`.
3. Play düğmesine dokunun.
4. İşlem sırasında progress bar ve durum mesajları görünür.
5. Pipeline tamamlandığında Palette Engine ve Geometry Engine otomatik güncellenir.

Pipeline görüntüyü analiz eder, baskıda anlamlı hedef renkler çıkarır, uygun filamentleri seçer, katman aralıklarını kurar ve bazı geometry katmanlarını devre dışı bırakabilir.

![Dominant Colors Experimental](<dominantcolors.gif>)

## 8. Color Match Modları

Color Match aktifken **Modes** bölümünde eşleştirme yöntemi seçilir:

- **0 RGB**: RGB mesafesine dayalı daha doğrudan renk eşleştirme.
- **2 Lab+**: Lab tabanlı, geliştirilmiş algısal eşleştirme.
- **3 Lab**: Lab renk uzayına dayalı algısal eşleştirme.

En iyi mod görsele ve filament setine göre değişebilir. Çok doygun görsellerde veya ten/ara ton içeren fotoğraflarda modları değiştirip preview sonucunu karşılaştırın.

![Color Match Preview](<colormatchpreview.gif>)
![Color Match Manual for Better Match](<colormatchmanual.gif>)

## 9. Brightness Settings

Tam ekran mesh preview içinde **Brightness Settings** düğmesi bulunur.

Ayarlar:

- **Target > Edit Image**: Açık olduğunda parlaklık düzenlemesi giriş görseline uygulanır. Kapalı olduğunda mesh preview tarafına uygulanır.
- **Method**: Parlaklık eğrisi yöntemini seçer. Örnekler: Standard, Clean Lift, Soft Lift, Filmic Balance, Shadow Recovery, Highlight Guard, Soft Contrast.
- **Power**: Eğrinin gücünü ayarlar. Aralık `1.00` ile `10.00`.
- **Alternate Edit**: Alternatif düzenleme yolunu açıp kapatır.
- **Bright Adjust**: Genel parlaklık ayarıdır. Aralık `-1.00` ile `1.00`.
- **Reset Settings**: Tüm parlaklık ayarlarını varsayılana döndürür.

Görsel çok karanlıksa Shadow Recovery veya Clean Lift deneyin. Açık alanlar patlıyorsa Highlight Guard veya Soft Contrast daha dengeli sonuç verebilir.

![Brightness Settings](<brightnessSettings.gif>)

![Edit Image Brightness Settings](<editimageBS.gif>)


## 10. Filament Library Kullanımı

**Filament Library** paneli uygulamanın filament veritabanını yönetir.

### Filamentleri filtreleme

- Üstteki material sekmelerinden PLA, PETG, ABS, TPU gibi tipleri seçebilirsiniz.
- **Filter** alanına marka veya filament adı yazabilirsiniz.
- **Type Filters** ile birden fazla filament tipini aynı anda filtreleyebilirsiniz.
- Filamentler **Owned** ve **Unowned** olarak ayrılır.

### Owned işaretleme

Bir filament satırına dokunduğunuzda o filament owned/unowned olarak değişir. Bu bilgi cihazda yerel olarak saklanır.

### Filament ekleme

1. **Add Filament** düğmesine dokunun.
2. **Brand** alanına marka adını yazın.
3. **Name** alanına filament adını yazın.
4. **Material / Type** seçin veya **Custom Type** alanına özel tip yazın.
5. **Color Hex** alanına `#RRGGBB` formatında renk girin.
6. **Transmissivity** değerini girin.
7. İsterseniz **Mark as Owned** seçeneğini açın.
8. **Save** ile kaydedin.

Aynı marka, ad, tip, renk ve transmissivity kombinasyonunda ikinci bir filament eklenemez.

### Filament silme

Satırdaki üç nokta menüsünden **Delete Filament** seçin.

- Özel filamentler cihazdan kalıcı olarak silinir.
- Uygulamayla gelen bundled filamentler uygulama paketinden kaldırılmaz, sadece bu cihazda gizlenir.

![Add Filament](<addfilament.gif>)
![Delete Filament](<deletefilament.gif>)

## 11. Palette Engine ile Filament Sırası Kurma

**Palette Engine**, baskıda kullanılacak filament renklerini ve hangi katman aralıklarında etkin olacaklarını gösterir.

Temel kavramlar:

- Dikey renk çubuğu katmanları gösterir.
- Sağdaki küçük tutamaçlar slicer sınırlarıdır.
- Sol taraftaki sayılar sınır katmanlarını gösterir.
- Her renk bloğu bir filament segmentidir.

Kullanım:

1. Filament Library içinden bir filament satırını sürükleyin.
2. Palette Engine üzerindeki tek bir katmana bırakırsanız yalnızca o katman değişir.
3. Slicer çizgisine yakın bırakırsanız ilgili katman aralığının tamamına uygulanır.
4. Tutamaçları yukarı/aşağı sürükleyerek filament geçiş katmanlarını değiştirin.
5. İlk tutamacı en alta çekmek ilk filament segmentini kaldırır ve sonraki segmenti öne alır.

Palette Engine, filamentlerin transmissivity ve renk değerleriyle katman katman karışım görünümünü hesaplar.

### Undo, Redo ve aktarım

Palette Engine üstünde:

- Geri ok: Son değişikliği geri alır.
- İleri ok: Geri alınan değişikliği tekrar uygular.
- Sağa ok: Palette Engine atamalarını Geometry Engine tarafına kopyalar.

Undo/redo geçmişi panel bazlı tutulur.

## 12. Geometry Engine Kullanımı

**Geometry Engine**, Color Match modunda aktif hale gelir. Abonelik yoksa veya Color Match kapalıysa panel kilitli görünür.

Geometry Engine, görseldeki renk eşleşmesine göre mesh geometrisinin hangi katmanları kullanacağını yönetir.

Kullanım:

- Filamentleri Palette Engine ile aynı şekilde sürükleyip bırakabilirsiniz.
- Tutamaçlarla geometry slicer sınırlarını değiştirebilirsiniz.
- Bir katmana tek dokunuş, o katmanı aktif/pasif yapar.
- Devre dışı katmanlar üzerinde **OFF** veya X işareti görünür.
- Bir katmana çift dokunuş, o katmanı preview üzerinde vurgular.

Üstteki sola ok, Geometry Engine atamalarını Palette Engine tarafına kopyalar. Geometry tarafındaki devre dışı katman bilgisi Palette Engine'e kopyalanmaz.

## 13. Görsel Üzerinden Katman Bulma

**Image Preview** panelinde görselin üzerine dokunarak veya basılı tutarak ilgili mesh katmanını bulabilirsiniz.

- Kısa dokunuş: Dokunulan noktaya karşılık gelen katmanı preview ve core panellerinde vurgular.
- Sürükleme veya uzun basış benzeri hareket: Büyüteç açar, renk örnekler ve en yakın filamentleri listeler.

Bu özellik, bir detayın hangi katmana denk geldiğini görmek ve filament geçişlerini hassas ayarlamak için kullanışlıdır.

![Hightlight Layer](<hightlightLayer.gif>)

## 14. Görselden Renk Örnekleme ve Manuel Color Match

Color Match aktifken Image Preview üzerinde renk seçimi yapabilirsiniz.

1. Görsel üzerinde istediğiniz renge basılı tutun veya hafif sürükleyin.
2. Büyüteç ve seçilen renk göstergesi açılır.
3. **Find Closest Filament** popup'ında örneklenen HEX rengi ve en yakın filamentler listelenir.
4. **Add** ile bu rengi manuel dominant renk listesine ekleyin.
5. En az 2 renk seçtikten sonra **Process** düğmesine dokunun.

Seçili renkler yatay küçük renk etiketleri olarak görünür. Bir etikete dokunarak listeden çıkarabilirsiniz. Manuel renk sayısı en fazla `8` olabilir.

![Pick Colors and Use Auto Color Match](<dominantcolorspickcolors.gif>)

## 15. Describe Ekranı

**Project Controls** veya alt kontrol barından **Describe** düğmesine dokunun.

Describe ekranı şunları özetler:

- Baskı özeti: infill, layer height ve base layer bilgisi.
- **Project**: Model boyutu, base thickness ve gerçek toplam kalınlık.
- **Filaments**: Kullanılan benzersiz filamentler, material, HEX ve transmission bilgisi.
- **Swap Instructions**: Hangi katmanda hangi filamente geçileceği.

Bu ekranı baskı öncesi kontrol listesi gibi kullanabilirsiniz. Dilimleyicide filament değişimlerini girerken özellikle **Layer #** ve yükseklik değerlerini takip edin.

- **![Describe & Print Instructions](<describe.gif>)**

## 16. STL Dışa Aktarma

1. Fotoğraf veya proje kaynağı yüklü olmalı.
2. Mesh preview başarıyla oluşmalı.
3. **Mesh Preview > Actions** bölümünü açın.
4. **Export STL** düğmesine dokunun.
5. Dosya konumunu seçin ve kaydedin.

STL binary formatta üretilir. Export adı mümkünse kaynak görsel veya proje adına göre oluşturulur; aksi halde `selected_image_preview.stl` gibi varsayılan ad kullanılır.

STL export sırasında görsel çok küçükse, tamamen transparansa veya mesh index verisi üretilemediyse uygulama hata mesajı gösterir.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)


## 17. Proje Kaydetme

1. Bir görsel yükleyin ve ayarlarınızı yapın.
2. **Mesh Preview > Actions** bölümünü açın.
3. **Save Project** düğmesine dokunun.
4. `.fpproj` dosyasını istediğiniz konuma kaydedin.

Kaydedilen proje şunları içerir:

- Görsel verisi.
- Mesh mode.
- Mesh height, layer height, base layer, base thickness, width ve height.
- Palette Engine slicer ve filament segmentleri.
- Geometry Engine slicer ve filament segmentleri.
- Devre dışı Geometry Engine katmanları.
- Color Match match method.
- Brightness settings.

`.fpproj` dosyaları cihaz keychain'inde saklanan anahtarla şifrelenir. Bu nedenle güvenli proje dosyaları, onları oluşturan uygulama kurulumu tarafından açılmak üzere tasarlanmıştır.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)

## 18. Proje İçe Aktarma

**Mesh Preview > Source** bölümünde iki kaynak bulunur:

- **Use Image**: Şu anda yüklenmiş görseli kullanır.
- **Project**: Bir proje dosyası içe aktarır.

Project seçildiğinde dosya seçici açılır. Uygulama `.fpproj` ve uyumlu JSON proje dosyalarını okuyabilir.

İçe aktarılan dosya Filament Painting projesiyse uygulama ayarları ve görseli ana çalışma alanına uygular. Uyumlu preview project formatında image veya STL referansı varsa preview kaynağı olarak kullanılabilir.

### Use Project STL

Project kaynağı seçili ve proje içinde STL referansı varsa **Use Project STL** toggle'ı görünür. Bu seçenek açıldığında preview, proje içindeki STL yolunu kullanmayı dener.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)

## 19. Privacy ve Yerel İşleme

Uygulama akışında seçilen görseller, proje dosyaları, özel filament kayıtları ve STL export işlemleri cihazda yerel olarak işlenir.

Mevcut kod tabanında:

- Hesap girişi yoktur.
- Reklam yoktur.
- Üçüncü taraf analytics yoktur.
- Cross-app tracking yoktur.
- Fotoğraflar, STL dosyaları, proje dosyaları veya özel filamentler geliştirici sunucusuna yüklenmez.
- Satın alma ve restore işlemleri Apple StoreKit üzerinden yürür.

**Privacy** düğmesi bu bilgileri uygulama içinde de gösterir.

## 20. License Terms

**License Terms** ekranında ticari kullanım koşulları özetlenir:

- Standard Mode ile aktif abonelik olmadan kişisel projeler oluşturabilirsiniz.
- Aktif aylık abonelik varken uygulama ile oluşturduğunuz 3D baskıları ve dijital dosyaları satma hakkınız olur.
- Abonelik biter veya iptal edilirse ticari satış hakkı abonelik tekrar aktif olana kadar duraklar.
- Başkasına ait fikri mülkiyet, logo, karakter, marka veya görseller için gerekli hakları almak kullanıcı sorumluluğundadır.

## 21. Baştan Sona Önerilen İş Akışı

1. **Load Image** ile görsel yükleyin.
2. **Project Controls** içinden Width, Height, Mesh Height, Layer Height ve Base ayarlarını kontrol edin.
3. Ücretsiz akış için **Standard Mesh** modunda kalın.
4. Daha otomatik renk eşleşmesi istiyorsanız **Color Match** modunu açın ve aboneliği etkinleştirin.
5. Filament Library'de sahip olduğunuz filamentleri **Owned** olarak işaretleyin.
6. Gerekirse **Add Filament** ile kendi filamentlerinizi ekleyin.
7. Palette Engine'e filamentleri sürükleyip bırakın.
8. Slicer tutamaçlarını hareket ettirerek filament geçiş katmanlarını ayarlayın.
9. Color Match kullanıyorsanız Dominant Colors sayısını seçip otomatik pipeline çalıştırın.
10. Geometry Engine'de gereksiz katmanları kapatın veya geometry filament dizilimini düzenleyin.
11. Image Preview üzerinde detaylara dokunarak ilgili katmanları vurgulayın.
12. Mesh Preview'da modeli döndürüp yakınlaştırarak kontrol edin.
13. **Brightness Settings** ile karanlık/açık alanları gerekiyorsa dengeleyin.
14. **Describe** ekranından filament ve swap talimatlarını kontrol edin.
15. **Save Project** ile `.fpproj` kaydedin.
16. **Export STL** ile baskıya hazır STL dosyasını dışa aktarın.
17. STL dosyasını slicer'a alın, %100 infill ve uygulamadaki layer height değerleriyle dilimleyin.
18. Describe ekranındaki swap talimatlarına göre filament değişimlerini ayarlayın.

## 22. Baskı İçin Pratik Notlar

- Uygulama Describe ekranında %100 infill önerir.
- Layer height değerini slicer'da uygulamadaki değerle aynı girin.
- Base layer ve base thickness değerleri modelin dayanıklılığını etkiler.
- Çok ince detaylarda Width/Height değerini büyütmek daha iyi sonuç verebilir.
- Çok fazla filament segmenti baskı süresini ve swap sayısını artırır.
- Transmissivity değeri renk karışımını etkilediği için özel filament eklerken gerçekçi değer girin.
- Color Match sonucu mükemmel görünmüyorsa Dominant Colors sayısını, match method'u ve brightness ayarlarını deneyerek karşılaştırın.

## 23. Sık Karşılaşılan Durumlar

### Mesh preview görünmüyor

- Önce görsel yüklediğinizden emin olun.
- Mesh Height, Layer Height, Width ve Height değerlerinin sıfır olmadığını kontrol edin.
- Uygulama arka plandan yeni döndüyse preview'in yeniden oluşması için kısa süre bekleyin.

### Export STL pasif

STL export yalnızca mesh payload üretildikten sonra aktif olur. Önce preview'in başarıyla oluşmasını bekleyin.

### Save Project pasif

Proje kaydetmek için önce görsel yüklenmiş olmalıdır.

### Color Match kilitli

Color Match aylık abonelik gerektirir. Aboneliğiniz varsa **Restore Purchases** kullanın.

### Project dosyası açılmıyor

Güvenli `.fpproj` dosyaları oluşturan kurulumun keychain anahtarına bağlıdır. Başka cihaz veya kurulumda açılmıyorsa görsel yükleme akışını veya uyumlu proje import formatını kullanın.

### Filament yanlış görünüyor

Filament kütüphanesinde renk HEX ve Transmissivity değerlerini kontrol edin. Özel filament hatalı girildiyse silip doğru değerlerle tekrar ekleyin.

## 24. Panel Kısayolları

- **Hide / Show Filament Library**: Geniş ekranda filament panelini daraltır veya geri getirir.
- **Core Panels Show / Hide**: Kompakt ekranda Palette Engine ve Geometry Engine alanını açar/kapatır.
- **Project Controls Show / Hide**: Kompakt ekranda ölçü alanlarını açar/kapatır.
- **Done**: Klavye açıkken girişi kapatır.
- **Reset**: Mesh kamerasını sıfırlar.
- **Fullscreen**: Mesh preview'i tam ekran açar.

## 25. Kısa Terimler

- **Layer**: Baskıdaki katman.
- **Slicer boundary**: Filament değişiminin gerçekleştiği katman sınırı.
- **Palette Engine**: Renk/filament karışım planı.
- **Geometry Engine**: Color Match için geometri katmanı planı.
- **Transmissivity / TD**: Filamentin ışık geçirgenliği veya renk karışım davranışını etkileyen değer.
- **Dominant Colors**: Görselden çıkarılan ana hedef renk sayısı.
- **Match Method**: Color Match'in renk eşleştirme algoritması.
- **Base Thickness**: Modelin minimum taban kalınlığı.
- **Mesh Height**: Modelin toplam hedef kalınlığı.
- **STL**: Dilimleyiciye aktarılacak 3D model dosyası.
- **FPPROJ / .fpproj**: Filament Painting proje dosyası.

## Showcase

### Color Match Mode Örnek Proje
- **Filament Painting Bookmark 2 CM.stl dosyasını indirin**
- **Baskı talimatlarını takip edin**
- **![Describe & Print Instructions](<describe.gif>)**

### Videolar

[Standart Mode Önizleme](https://www.youtube.com/watch?v=deloUQGVre4)
[Color Match Mode Önizleme](https://www.youtube.com/watch?v=9kdz2RvdSu0)

1. [Bookmark 1 Color Match](https://www.youtube.com/watch?v=x3OFoDtGYiQ)
2. [Bookmark 2 Color Match](https://www.youtube.com/watch?v=zj7FIFvfqYU)
3. [Bookmark 3 Color Match](https://www.youtube.com/watch?v=sfgcbiDYI00)

### Resimler

![Bookmark 1 Color Match](<bookmark1.jpeg>)
![Bookmark 2 Color Match](<bookmark2.jpeg>)
![Bookmark 3 Color Match](<bookmark3.jpeg>)
