# temiz-kod-mimarisi-swiftui-master

 Ana Amaç: Uygulamanın temel amacı, restcountries.com REST API kullanarak ülkelerin listesini ve bu ülkeler hakkında detayları göstermektir. 🏳️ 🏴 🏴‍☠️

Mimari Yapı: Bu proje, "Clean Architecture" prensiplerini takip eder. Bu prensipler, uygulamanın farklı katmanları arasında iyi bir ayrım sağlar ve kodun daha okunaklı ve sürdürülebilir olmasına yardımcı olur.

Anahtar Özellikler:

Vanilla SwiftUI + Combine Uygulama: Temelde SwiftUI ve Combine kullanılarak uygulama geliştiriliyor. SwiftUI, kullanıcı arayüzünü oluşturmak için kullanılırken, Combine, veri akışlarını ve olayları işlemek için kullanılır.

Katmanların Ayrımı: Uygulama, sunum katmanı (Presentation Layer), iş mantığı katmanı (Business Logic Layer) ve veri erişim katmanı (Data Access Layer) olmak üzere üç ana katmana sahiptir.

Test Kapsamı: Uygulamanın farklı kısımları için kapsamlı bir test ağı bulunur. Bu, uygulamanın istikrarını ve güvenilirliğini artırır.

Merkezi AppState Kullanımı: Redux benzeri bir yapı kullanılarak, uygulamadaki durum (state) merkezi bir şekilde yönetilir. Bu, uygulamanın durumunu tek bir kaynaktan takip etmeyi sağlar.

CoreData ile Veri Saklama: Veri kalıcılığı için CoreData kullanılır. Bu, uygulamanın verilerini yerel olarak saklamak için kullanılır.

SOLID, DRY, KISS, YAGNI Prensipleri: Yazılım tasarımı açısından iyi prensiplere uygunluk vurgulanır. Bu prensipler, kodun daha okunaklı ve bakımı daha kolay hale gelmesine yardımcı olur.

Büyüme İçin Tasarlandı: Uygulama büyüdükçe ölçeklenebilir olabilmesi için tasarlanmıştır. Büyük üretim uygulamaları inşa etmek için referans olabilir.

Mimari Genel Bakış:

Sunum Katmanı (Presentation Layer): SwiftUI görünümleri içerir ve iş mantığına sahip değildir. Kullanıcı eylemleri (örneğin, bir düğmeye dokunma) veya görünüm yaşam döngüsü olayları (örneğin, onAppear) tarafından tetiklenen yan etkiler, Interactors'e iletilir. İş mantığı katmanı ve durum (AppState) görünüm hiyerarşisine @Environment ile enjekte edilir.

İş Mantığı Katmanı (Business Logic Layer): İş mantığı katmanı, Interactors adı verilen bileşenler tarafından temsil edilir. Interactors, verileri harici bir kaynaktan almak veya hesaplamalar yapmak gibi işleri gerçekleştirmek için istekleri alırlar, ancak veriyi doğrudan döndürmezler. Sonuçları, AppState'e veya Binding'e iletebilirler. Binding, işin sonucunun (veri) yalnızca bir Görünüm tarafından yerel olarak kullanıldığı ve AppState'e ait olmadığı durumlarda kullanılır.

Veri Erişim Katmanı (Data Access Layer): Veri Erişim Katmanı, Repositories adı verilen bileşenler tarafından temsil edilir. Repositories, backend veya yerel veritabanı üzerinde CRUD işlemleri gerçekleştirmek için asenkron bir API (Combine ile Publisher) sağlar. Repositories, iş mantığı içermezler ve AppState'i değiştirmezler. Repositories, sadece Interactors tarafından erişilebilir ve kullanılır.
