# Chrome DevTools Eğitim Dokümanı

## 🎯 Amaç
Bu döküman, test mühendislerinin **Chrome DevTools**'u etkin bir şekilde kullanabilmeleri için hazırlanmıştır. Manuel ve otomasyon testlerinde hata ayıklamak, performans analizi yapmak ve element incelemek için temel ve ileri düzey bilgileri içerir.

---

## 🧭 DevTools'a Giriş

### DevTools Nasıl Açılır?
- Sağ tık → "İncele" (Inspect)
- `F12`
- `Ctrl + Shift + I` (Windows/Linux)
- `Cmd + Option + I` (Mac)
- `Ctrl + Shift + C` (Element seçici modunda açar)

### Dock Pozisyonu Değiştirme
- DevTools'u alt, sağ, sol ya da ayrı pencerede açabilirsiniz
- Ayarlar simgesi → Dock side seçenekleri

---

## 🧱 1. Elements Paneli

### Ne İşe Yarar?
- Sayfadaki HTML ve CSS'i canlı olarak inceleyip düzenlemenizi sağlar
- DOM manipülasyonu ve CSS değişiklikleri anlık görünür

### Öne Çıkan Özellikler
- **Element Seçici**: Sol üstteki ok ikonu ile sayfadan element seçme
- **Copy Selector**: Element üzerine sağ tık → "Copy" → "Copy selector/XPath/Full XPath"
- **Force State**: `:hover`, `:active`, `:focus`, `:visited` durumlarını simüle etme
- **Layout Bölümü**: Box model (margin, padding, border) görüntüsü
- **Event Listeners**: Elemente bağlı JavaScript eventlerini görme
- **Accessibility**: ARIA özellikleri ve erişilebilirlik bilgileri

### Test İçin Pratik Kullanım
```html
<!-- Elementin görünüp görünmediğini kontrol -->
<!-- Elementin doğru class/id'ye sahip olup olmadığını doğrulama -->
<!-- CSS stillerinin doğru uygulanıp uygulanmadığını test etme -->
```

---

## 🎨 2. Styles & Computed

### Styles Sekmesi
- Seçilen elementin tüm CSS kurallarını gösterir
- **Canlı düzenleme**: Değerleri tıklayıp değiştirebilirsiniz
- **CSS kuralı ekleme**: `+` simgesi ile yeni kural ekleme
- **Renk seçici**: Renk değerlerinin yanındaki kare ile renk paleti açma

### Computed Sekmesi
- Tarayıcının gerçekte uyguladığı stilleri listeler
- **Box Model**: Margin, border, padding, content boyutları
- **Filter**: Sadece belirli CSS özelliklerini görme

---

## 🧪 3. Console Paneli

### Kullanım Alanları
- JavaScript hatalarını görme ve debug etme
- Manuel olarak kod çalıştırma ve test etme
- Log mesajlarını (`console.log`, `console.error`, `console.warn`) takip etme
- Network hatalarını ve güvenlik uyarılarını görme

### Pratik Komutlar
```js
// Element seçimi ve manipülasyon
$0                    // Son seçilen element (Elements panelinden)
$1, $2, $3, $4       // Önceki seçilen elementler
$$('div')            // querySelectorAll('div') kısayolu
$x("//div[@class='test']") // XPath sorgusu

// Utility fonksiyonlar
copy($0)             // Elementi veya değişkeni panoya kopyalar
inspect($0)          // Elementi Elements panelinde gösterir
monitor(functionName) // Fonksiyon çağrılarını izler
clear()              // Console'u temizler

// Test senaryolarında kullanışlı
document.querySelector('#loginButton').click() // Element tıklama
localStorage.getItem('userToken')              // Local storage kontrol
sessionStorage.clear()                         // Session temizleme
```

### Console Ayarları
- **Preserve log**: Sayfa yenilendiğinde logları koruma
- **Show timestamps**: Zaman damgası gösterme
- **Filter**: Error, Warning, Info, Debug seviyelerine göre filtreleme

---

## 🌐 4. Network Paneli

### Ne İşe Yarar?
- Sayfa yüklenirken yapılan tüm HTTP(S) isteklerini izler
- API testleri için kritik öneme sahiptir

### İncelenecek Noktalar
- **Status Code**: 200 (başarılı), 404 (bulunamadı), 500 (sunucu hatası) vb.
- **Request Headers/Response Headers**: Kimlik doğrulama, content-type vb.
- **Request Payload/Response Body**: Gönderilen ve alınan veri
- **Timing**: DNS, SSL, TTFB (Time to First Byte) süreleri
- **Waterfall Chart**: İsteklerin zaman çizelgesi

### Filtreleme ve Arama
- **Filtreler**: All, XHR, JS, CSS, Img, Media, Font, Doc, WS, Other
- **Arama**: URL, response body, header içeriğinde arama
- **Preserve log**: Sayfa navigasyonunda logları koruma
- **Disable cache**: Cache'i devre dışı bırakma

### Test Senaryoları
```js
// API response'ları kontrol etme
// Form submit işlemlerini izleme
// Third-party servislerin çalışıp çalışmadığını görme
// Slow network simülasyonu (Throttling)
```

---

## ⏱️ 5. Performance Paneli

### Kullanım Amacı
- Sayfa yüklenme performansını analiz etme
- JavaScript execution süresini ölçme
- Rendering problemlerini tespit etme

### Kayıt Alma ve Analiz
1. **Record** butonuna basın
2. Sayfayı yeniden yükleyin veya test senaryonuzu çalıştırın
3. **Stop** ile kaydı durdurun
4. **Timeline** üzerinden analiz yapın

### Önemli Metrikleri
- **FCP (First Contentful Paint)**: İlk içerik görünme süresi
- **LCP (Largest Contentful Paint)**: En büyük içerik görünme süresi
- **CLS (Cumulative Layout Shift)**: Layout kayması
- **FID (First Input Delay)**: İlk etkileşim gecikmesi

---

## 🐞 6. Sources Paneli

### Özellikler
- JavaScript dosyalarını görüntüleme ve düzenleme
- **Breakpoint** koyarak kod execution'ı durdurma
- **Call Stack**: Fonksiyon çağırma hiyerarşisi
- **Scope Variables**: Local ve global değişkenleri görme
- **Watch**: Belirli değişkenleri sürekli izleme

### Debug İşlemleri
```js
// Breakpoint türleri:
// Line breakpoints: Satır numarasına tıklayarak
// Conditional breakpoints: Sağ tık → Add conditional breakpoint
// Logpoints: Console.log eklemeden log alma
```

### Kod Durdurma ve İlerletme
- **Pause/Resume** (F8): Execution'ı durdur/devam ettir
- **Step Over** (F10): Bir sonraki satıra geç
- **Step Into** (F11): Fonksiyon içine gir
- **Step Out** (Shift+F11): Fonksiyondan çık
- **Continue to Here**: İmlecin bulunduğu satıra kadar çalıştır

### Local Overrides
- Sunucudaki dosyaları local olarak override etme
- Canlı sitede geçici değişiklik yapabilme

---

## 🕵️ 7. Application Paneli

### Storage Bölümleri
- **Local Storage**: Kalıcı browser storage
- **Session Storage**: Oturum süresince saklanan veri
- **Cookies**: HTTP cookie'leri görüntüleme ve düzenleme
- **IndexedDB**: Karmaşık client-side database
- **Web SQL**: (Deprecated) SQL database

### Diğer Özellikler
- **Service Workers**: PWA ve offline functionality
- **Cache Storage**: Application cache
- **Background Services**: Push messages, background sync
- **Frames**: iframe yapıları

### Test Senaryoları
```js
// Login token kontrolü
localStorage.getItem('authToken')

// Cookie manipülasyonu
document.cookie = "testMode=true"

// Session storage temizleme
sessionStorage.clear()
```

---

## 🧰 8. Diğer Yararlı Paneller

### Lighthouse
- **Performance**: Sayfa hızı analizi
- **Accessibility**: Erişilebilirlik skorları
- **Best Practices**: Web standartları uygunluğu
- **SEO**: Arama motoru optimizasyonu
- **PWA**: Progressive Web App kriterleri

### Coverage
- Kullanılan/kullanılmayan CSS ve JavaScript kodlarını gösterir
- Kod temizleme için kritik bilgiler sağlar

### Recorder (Chrome 89+)
- UI test adımlarını kaydetme
- Puppeteer formatında export etme
- Test otomasyonu için kod üretme

### Security
- HTTPS sertifika bilgileri
- Mixed content uyarıları
- Güvenlik açıkları

---

## 🔧 9. İleri Düzey Özellikler

### Device Simulation
- **Responsive Design Mode**: Farklı cihaz boyutları test etme
- **User Agent**: Farklı browser/device simülasyonu
- **Network Throttling**: Yavaş internet simülasyonu
- **Geolocation**: Konum simülasyonu

### Console Utilities
```js
// Performance ölçümü
console.time('myTimer')
// ... kod
console.timeEnd('myTimer')

// Obje/array güzel görüntüleme
console.table(myArray)

// Stack trace
console.trace('Debug point')

// Gruplama
console.group('Test Group')
console.log('Test 1')
console.log('Test 2')
console.groupEnd()
```

### Keyboard Shortcuts
- `Ctrl + Shift + P`: Command palette
- `Ctrl + F`: Panel içinde arama
- `Ctrl + G`: Satır numarasına gitme (Sources'da)
- `Esc`: Console drawer açma/kapatma

---

## 🔎 Test Mühendisleri İçin Pratik Senaryolar

### Manuel Test
- ✅ Element locator (XPath/CSS selector) doğrulama
- ✅ Form validation davranışlarını test etme
- ✅ JavaScript error'larını yakalama
- ✅ API response'larını doğrulama
- ✅ Cookie/session management test etme
- ✅ Mobile responsive test yapma
- ✅ Performance bottleneck bulma

### Otomasyon Test Desteği
- ✅ Dynamic selector oluşturma
- ✅ Wait condition'ları belirleme
- ✅ Test data'sını browser storage'dan okuma
- ✅ Network intercept için pattern belirleme
- ✅ Screenshot comparison için element koordinatları

### Debugging
- ✅ Selenium WebDriver hatalarını debug etme
- ✅ JavaScript execution sorunlarını çözme
- ✅ Timing issue'larını tespit etme
- ✅ Element interaction problemlerini analiz etme

---

## 🚨 10. Yaygın Hata Senaryoları ve Çözümleri

### JavaScript Hatası Analizi
```js
// Uncaught ReferenceError: $ is not defined
// Çözüm: jQuery library yüklü mü kontrol et

// Cannot read property 'click' of null
// Çözüm: Element DOM'da var mı kontrol et
if (document.getElementById('myButton')) {
    document.getElementById('myButton').click();
}
```

### Network Hatası Analizi
- **CORS Error**: Cross-origin policy ihlali
- **404 Not Found**: Resource bulunamıyor
- **500 Internal Server Error**: Sunucu hatası
- **Timeout**: İstek zaman aşımı

### Performance Sorunları
- **Long Task**: 50ms'den uzun JavaScript execution
- **Layout Thrashing**: Sürekli DOM reflow
- **Memory Leak**: Garbage collection sorunları

---

## 📚 Kaynaklar ve İleri Öğrenim

### Resmi Dökümentasyon
- [Chrome DevTools Resmi Dokümantasyonu](https://developer.chrome.com/docs/devtools/)
- [What's New in DevTools](https://developer.chrome.com/docs/devtools/whats-new/)
- [DevTools Tips](https://devtoolstips.org/)

### Pratik Kaynaklar
- [Chrome Dev Tools](https://developer.chrome.com/docs/devtools)

### Video Eğitimler
- [Chrome for Developers YouTube Kanalı] (https://www.youtube.com/@ChromeDevs)

---

## 🎓 Eğitim Sonrası Alıştırmalar

1. **Element Inspector**: Farklı web sitelerinde element selector'ları bulma
2. **Network Analysis**: API çağrılarını izleyip response'ları analiz etme
3. **Performance Testing**: Yavaş yüklenen sayfaları analiz etme
4. **Console Mastery**: JavaScript komutlarıyla sayfa manipülasyonu
5. **Debug Practice**: Kasıtlı bug'lar oluşturup çözme

---

> 💡 **Pro Tip:** DevTools'u günlük test rutininizin bir parçası haline getirin. Her test senaryosunda Network ve Console panellerini açık tutmak, proaktif hata tespiti yapmanızı sağlar.

> 🧠 **Hatırlatma:** DevTools, test mühendislerinin sadece hata yakalamak değil, test öncesi analiz yapmalarını da sağlar. Düzenli kullanımı, hata çözüm süresini ciddi oranda azaltır ve test kalitesini artırır.