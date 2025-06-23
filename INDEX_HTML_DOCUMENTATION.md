# Chrome DevTools Eğitim Sayfası - Buton Metodları Rehberi

Bu rehber, Chrome DevTools eğitim sayfasındaki tüm butonların açıklamalarını ve tetikledikleri JavaScript metodlarını içermektedir.

## 🔴 Console Sekmesi

### JavaScript Hataları

#### `triggerReferenceError()`
- **Amaç**: ReferenceError hatası oluşturur
- **Çalışma**: Tanımlanmamış bir değişkene erişmeye çalışır (`undefinedVariable`)
- **Öğrenme**: Değişken tanımlama hatalarını gösterir
- **Console'da**: "🔴 ReferenceError: undefinedVariable is not defined"

#### `triggerTypeError()`
- **Amaç**: TypeError hatası oluşturur
- **Çalışma**: `null` değer üzerinde olmayan bir metodu çağırır
- **Öğrenme**: Veri tipi uyumsuzluğu hatalarını gösterir
- **Console'da**: "🔴 TypeError: Cannot read properties of null"

#### `triggerSyntaxError()`
- **Amaç**: SyntaxError hatası oluşturur
- **Çalışma**: `eval()` ile bozuk JavaScript kodu çalıştırır
- **Öğrenme**: Sözdizimi hatalarını gösterir
- **Console'da**: "🔴 SyntaxError: Unexpected token"

#### `triggerRangeError()`
- **Amaç**: RangeError hatası oluşturur
- **Çalışma**: Negatif boyutta array oluşturmaya çalışır
- **Öğrenme**: Geçersiz aralık değerlerini gösterir
- **Console'da**: "🔴 RangeError: Invalid array length"

#### `triggerURIError()`
- **Amaç**: URIError hatası oluşturur
- **Çalışma**: Geçersiz URI decode işlemi yapar
- **Öğrenme**: URL kodlama/çözme hatalarını gösterir
- **Console'da**: "🔴 URIError: URI malformed"

### Console Metodları

#### `showAllConsoleMethods()`
- **Amaç**: Tüm console metodlarını gösterir
- **İçerik**: 
  - `console.log()` - Normal mesaj
  - `console.info()` - Bilgi mesajı
  - `console.warn()` - Uyarı mesajı
  - `console.error()` - Hata mesajı
  - `console.debug()` - Debug mesajı
  - `console.assert()` - Koşul kontrolü
  - `console.count()` - Sayaç
  - `console.dir()` - Obje detayları
  - `console.dirxml()` - DOM element detayları

#### `showConsoleTable()`
- **Amaç**: `console.table()` metodunu gösterir
- **Çalışma**: Kullanıcı verilerini tablo formatında görüntüler
- **Öğrenme**: Veri görselleştirme teknikleri

#### `showConsoleGroup()`
- **Amaç**: Console gruplarını gösterir
- **Çalışma**: İç içe console grupları oluşturur
- **Öğrenme**: Log organizasyonu teknikleri

#### `showConsoleTime()`
- **Amaç**: Zaman ölçümü gösterir
- **Çalışma**: `console.time()` ve `console.timeEnd()` kullanır
- **Öğrenme**: Performance ölçüm teknikleri

#### `showConsoleTrace()`
- **Amaç**: Stack trace gösterir
- **Çalışma**: İç içe fonksiyonlar çağırarak call stack'i görüntüler
- **Öğrenme**: Debug teknikleri

### Asenkron Hatalar

#### `triggerPromiseRejection()`
- **Amaç**: Promise rejection hatalarını gösterir
- **Çalışma**: Hem handled hem unhandled promise rejection'ları oluşturur
- **Öğrenme**: Asenkron hata yönetimi

#### `triggerAsyncError()`
- **Amaç**: Async/await hatalarını gösterir
- **Çalışma**: Async fonksiyon içinde hata fırlatır
- **Öğrenme**: Modern JavaScript hata yönetimi

#### `triggerTimeoutError()`
- **Amaç**: Timeout içinde hata gösterir
- **Çalışma**: `setTimeout` içinde hata fırlatır
- **Öğrenme**: Asenkron hata yakalama zorlukları

## 🌐 Network Sekmesi

### HTTP Status Codes

#### `fetch404Error()`
- **Amaç**: 404 Not Found hatası oluşturur
- **Çalışma**: Var olmayan endpoint'e istek gönderir
- **Network'te**: Kırmızı status, 404 kodu
- **Öğrenme**: Client-side hata kodları

#### `fetch500Error()`
- **Amaç**: 500 Server Error oluşturur
- **Çalışma**: httpbin.org/status/500 endpoint'ini çağırır
- **Network'te**: Kırmızı status, 500 kodu
- **Öğrenme**: Server-side hata kodları

#### `fetch403Error()`
- **Amaç**: 403 Forbidden hatası oluşturur
- **Çalışma**: httpbin.org/status/403 endpoint'ini çağırır
- **Network'te**: Kırmızı status, 403 kodu
- **Öğrenme**: Yetkilendirme hataları

#### `fetchTimeoutError()`
- **Amaç**: Request timeout gösterir
- **Çalışma**: AbortController ile 1 saniye timeout ayarlar, 5 saniye geciken API'yi çağırır
- **Network'te**: Canceled request
- **Öğrenme**: Timeout yönetimi

### Slow Loading Resources

#### `loadSlowImage()`
- **Amaç**: Yavaş yüklenen resim gösterir
- **Çalışma**: Yüksek çözünürlüklü NASA resmi yükler
- **Network'te**: Uzun loading time, waterfall chart'ta görünür
- **Öğrenme**: Resim optimizasyonu ihtiyacı

#### `loadSlowAPI()`
- **Amaç**: Yavaş API çağrısı gösterir
- **Çalışma**: 4 saniye geciken API endpoint'ini çağırır
- **Network'te**: Uzun response time
- **Öğrenme**: API performance analizi

#### `loadLargeFile()`
- **Amaç**: Büyük dosya indirme gösterir
- **Çalışma**: 100MB'lık dosya indirir
- **Network'te**: Büyük dosya boyutu, uzun transfer süresi
- **Öğrenme**: Dosya boyutu optimizasyonu

### CORS ve Security

#### `triggerCORSError()`
- **Amaç**: CORS hatası oluşturur
- **Çalışma**: Cross-origin request yapar
- **Network'te**: CORS policy error
- **Öğrenme**: Cross-origin güvenlik politikaları

#### `triggerMixedContent()`
- **Amaç**: Mixed content uyarısı oluşturur
- **Çalışma**: HTTPS sayfasında HTTP resim yüklemeye çalışır
- **Network'te**: Mixed content warning
- **Öğrenme**: HTTPS güvenlik gereksinimleri

## 🎨 Elements Sekmesi

### DOM Manipülasyonu

#### `addElement()`
- **Amaç**: Dinamik element ekleme gösterir
- **Çalışma**: Yeni div elementi oluşturur ve sayfaya ekler
- **Elements'te**: DOM tree'de yeni element görünür
- **Öğrenme**: DOM manipülasyon teknikleri

#### `removeElement()`
- **Amaç**: Element silme gösterir
- **Çalışma**: Son eklenen elementi siler
- **Elements'te**: Element DOM'dan kaybolur
- **Öğrenme**: DOM element yönetimi

#### `modifyStyles()`
- **Amaç**: CSS stillerini dinamik olarak değiştirir
- **Çalışma**: Test elementine gradient, transform ve shadow ekler
- **Elements'te**: Computed styles değişir
- **Öğrenme**: Runtime CSS manipülasyonu

#### `breakLayout()`
- **Amaç**: Layout bozma gösterir
- **Çalışma**: Body elementine scale ve overflow özellikleri ekler
- **Elements'te**: Layout problemleri görünür
- **Öğrenme**: CSS layout problemleri

## 📝 Sources Sekmesi

### Breakpoint Testleri

#### `debugFunction()`
- **Amaç**: Debug işlemini gösterir
- **Çalışma**: `debugger` statement ile kodda durur
- **Sources'te**: Execution durur, variables görünür
- **Öğrenme**: Debug teknikleri

#### `complexCalculation()`
- **Amaç**: Karmaşık hesaplama gösterir
- **Çalışma**: İç içe döngülerle CPU-intensive işlem yapar
- **Sources'te**: Performance profiling
- **Öğrenme**: Code optimization

#### `recursiveFunction(n)`
- **Amaç**: Recursive fonksiyon gösterir
- **Çalışma**: Faktöriyel hesaplaması yapar
- **Sources'te**: Call stack'te recursive çağrılar
- **Öğrenme**: Recursion debugging

#### `minifiedCode()`
- **Amaç**: Minified kod gösterir
- **Çalışma**: `eval()` ile sıkıştırılmış kod çalıştırır
- **Sources'te**: Okunması zor kod
- **Öğrenme**: Source maps ihtiyacı

## ⚡ Performance Sekmesi

### Performans Testleri

#### `heavyCalculation()`
- **Amaç**: CPU-intensive işlem gösterir
- **Çalışma**: 10 milyon iterasyonlu matematiksel hesaplama
- **Performance'te**: CPU usage spike
- **Öğrenme**: JavaScript performance analizi

#### `memoryLeakTest()`
- **Amaç**: Memory leak oluşturur
- **Çalışma**: Global array'e 100.000 büyük obje ekler
- **Performance'te**: Memory usage artışı
- **Öğrenme**: Memory management

#### `domManipulationTest()`
- **Amaç**: DOM performance testi
- **Çalışma**: 1000 element oluşturur ve siler
- **Performance'te**: DOM operations
- **Öğrenme**: DOM performance optimization

#### `animationTest()`
- **Amaç**: Animation performance testi
- **Çalışma**: requestAnimationFrame ile karmaşık animasyon
- **Performance'te**: Frame rate analizi
- **Öğrenme**: Animation optimization

## 💾 Application Sekmesi

### Local Storage

#### `setLocalStorage()`
- **Amaç**: LocalStorage'a veri kaydetme
- **Çalışma**: JSON obje ve string değer kayıt eder
- **Application'da**: Local Storage'da veriler görünür
- **Öğrenme**: Client-side storage

#### `getLocalStorage()`
- **Amaç**: LocalStorage'dan veri okuma
- **Çalışma**: Kaydedilen verileri console'a yazdırır
- **Application'da**: Storage içeriği görünür
- **Öğrenme**: Data persistence

#### `clearLocalStorage()`
- **Amaç**: LocalStorage'ı temizleme
- **Çalışma**: Tüm LocalStorage verilerini siler
- **Application'da**: Storage boşalır
- **Öğrenme**: Storage management

### Session Storage

#### `setSessionStorage()`
- **Amaç**: SessionStorage'a veri kaydetme
- **Çalışma**: Session bilgilerini kayıt eder
- **Application'da**: Session Storage'da veriler görünür
- **Öğrenme**: Session management

#### `clearSessionStorage()`
- **Amaç**: SessionStorage'ı temizleme
- **Çalışma**: Tüm SessionStorage verilerini siler
- **Application'da**: Session storage boşalır
- **Öğrenme**: Session cleanup

### Cookies

#### `setCookie()`
- **Amaç**: Çeşitli cookie türleri oluşturur
- **Çalışma**: Normal, SameSite, HttpOnly cookie'ler ekler
- **Application'da**: Cookies sekmesinde görünür
- **Öğrenme**: Cookie security flags

#### `getCookie()`
- **Amaç**: Cookie'leri okuma
- **Çalışma**: Tüm cookie'leri console'a yazdırır
- **Application'da**: Cookie değerleri görünür
- **Öğrenme**: Cookie access

#### `clearCookies()`
- **Amaç**: Cookie'leri temizleme
- **Çalışma**: Tüm cookie'leri expire eder
- **Application'da**: Cookies silinir
- **Öğrenme**: Cookie management

### IndexedDB

#### `testIndexedDB()`
- **Amaç**: IndexedDB veritabanı oluşturur
- **Çalışma**: Test veritabanı ve object store oluşturur
- **Application'da**: IndexedDB sekmesinde database görünür
- **Öğrenme**: Client-side database

## 🔒 Security Sekmesi

### Güvenlik Testleri

#### `testMixedContent()`
- **Amaç**: Mixed content uyarısı oluşturur
- **Çalışma**: HTTPS sayfasında HTTP kaynakları yüklemeye çalışır
- **Security'de**: Mixed content warnings
- **Öğrenme**: HTTPS güvenlik gereksinimleri

#### `testInsecureRequest()`
- **Amaç**: Güvenli olmayan istek gösterir
- **Çalışma**: HTTP endpoint'lere istek gönderir
- **Security'de**: Insecure requests
- **Öğrenme**: Protocol security

#### `testCSP()`
- **Amaç**: CSP ihlali oluşturur
- **Çalışma**: `eval()` ve inline script çalıştırır
- **Security'de**: CSP violation warnings
- **Öğrenme**: Content Security Policy

## 📋 Form Metodları

### Form Handling

#### `handleFormSubmit(event)`
- **Amaç**: Form validation ve submission gösterir
- **Çalışma**: Form verilerini validate eder ve API'ye gönderir
- **Console'da**: Validation errors
- **Network'te**: POST request (404 error)
- **Öğrenme**: Form handling best practices

## 🔧 Otomatik Hatalar

Sayfa yüklendiğinde otomatik olarak çalışan metodlar:

- **Delayed Warning**: 5 saniye sonra uyarı mesajı
- **Unhandled Promise Rejection**: 3 saniye sonra işlenmemiş promise hatası
- **Performance Metrics**: Sayfa yükleme performans ölçümleri
- **Global Error Handlers**: Tüm JavaScript hatalarını yakalar
- **Memory Monitoring**: 10 saniyede bir memory kullanımını kontrol eder

## 🎯 Öğrenme Hedefleri

Her buton ve metod, Chrome DevTools'un farklı bir özelliğini öğretmek için tasarlanmıştır:

1. **Console**: Hata ayıklama ve logging teknikleri
2. **Network**: Ağ trafiği analizi ve optimization
3. **Elements**: DOM yapısı ve CSS debugging
4. **Sources**: Kod debugging ve profiling
5. **Performance**: Performance analysis ve optimization
6. **Application**: Client-side storage management
7. **Security**: Güvenlik analizi ve best practices
8. **Lighthouse**: Web site auditing ve optimization

Bu rehber, her butonun ne yaptığını ve Chrome DevTools'da hangi sekmelerde neleri gözlemlemeniz gerektiğini açıklamaktadır.