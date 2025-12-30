# Bursa Şehir İçi Rota Optimizasyonu: TSP-with-Neighborhoods

Bu proje, Bursa ili Osmangazi merkezli gerçek yol ağı verilerini kullanarak **Gezgin Satıcı Problemi (Traveling Salesman Problem - TSP)** için farklı algoritmaların performans karşılaştırmasını sunar. Çalışma kapsamında **Greedy Insertion**, **Google OR-Tools** ve **Genetik Algoritma** yaklaşımları hem rota uzunluğu hem de işlem süresi açısından analiz edilmiştir.

## 🚀 Proje Özeti

Proje, Bursa'da **7 km yarıçaplı** bir yol ağında rastgele üretilen noktaların kümelenmesiyle oluşturulan **10 ana merkez** arasındaki en kısa rotayı bulmayı hedefler.

- **Veri Kaynağı:** OSMnx kütüphanesi ile çekilen gerçek yol ağı verisi  
- **Modelleme:** K-Means kümeleme ve Dijkstra algoritması ile mesafe matrisi oluşturulması  
- **Deney Tasarımı:** İstatistiksel güvenilirlik için **30 bağımsız deney** gerçekleştirilmiştir  

## 🛠 Kullanılan Teknolojiler

- **OSMnx & NetworkX:** Yol ağı analizi ve snapping işlemleri  
- **Google OR-Tools:** Gelişmiş rota optimizasyonu çözümleri  
- **Scikit-learn:** K-Means kümeleme algoritması  
- **Folium:** İnteraktif harita görselleştirme  
- **Matplotlib:** Performans ve karşılaştırma grafiklerinin oluşturulması  

## 📊 Karşılaştırılan Algoritmalar

1. **Greedy Insertion**  
   Her adımda toplam mesafeyi en az artıran düğümü tura ekler.  
   Çok hızlıdır ancak yerel optimumda takılma riski yüksektir.

2. **OR-Tools (Routing Library)**  
   Dallandır-sınırla ve yerel arama yöntemlerini kullanır.  
   Yüksek doğruluk oranıyla en etkili çözücüdür.

3. **Genetik Algoritma (GA)**  
   OX1 crossover ve swap mutasyonu kullanarak **200 nesil** boyunca evrimsel arama yapar.  
   Karmaşık ve esnek kısıtlar altında avantajlıdır.

## 📈 Performans Sonuçları (30 Deney Ortalaması)

| Algoritma | Ortalama Uzunluk (km) | Ortalama Süre (s) | Başarı Oranı |
|----------|----------------------|------------------|--------------|
| **OR-Tools** | 43.17 | 0.00448 | %90.0 |
| **Genetik Algoritma** | 43.82 | 2.07000 | %6.7 |
| **Greedy Insertion** | 44.39 | 0.00026 | %3.3 |

### 🔍 Önemli Çıkarımlar

- **OR-Tools**, hem hız hem de doğruluk açısından endüstriyel uygulamalar için en ideal yöntemdir.  
- **Greedy Insertion**, milisaniyeler içinde çalışmasına rağmen ortalama %2.8–5 daha uzun rotalar üretmektedir.  
- **Genetik Algoritma**, bazı deneylerde (örn. Deney 5 ve 20) OR-Tools’tan daha kısa rotalar bulabilmiştir.

## 🖥️ Kurulum ve Kullanım

Gerekli kütüphaneleri yükleyin:

```bash
pip install osmnx folium ortools networkx scikit-learn
