# BERTopic ile 20 Newsgroups Veri Seti Üzerinde Konu Modellemesi

Bu proje, **BERTopic** kütüphanesi kullanarak 20 Newsgroups veri seti üzerinde kapsamlı bir konu modellemesi çalışması gerçekleştirmektedir. Proje, modern derin öğrenme teknikleriyle geleneksel konu modellemesi yöntemlerini birleştirerek, anlamlı ve yorumlanabilir konular çıkarmayı hedeflemektedir.

## 🎯 Proje Amacı

Bu proje ile amaçlanan:
- **BERTopic** kullanarak etkili konu modellemesi yapma
- Konu kalitesini çeşitli metriklerle ölçme
- İnteraktif görselleştirmeler oluşturma
- Model performansını analiz etme
- Kararlı ve tekrarlanabilir sonuçlar elde etme

## 📊 Öne Çıkan Sonuçlar

### Konu Keşfi
- **29 adet** anlamlı konu başarıyla tespit edildi
- Hedeflenen 30 konuya oldukça yakın performans
- Spor, teknoloji, politika gibi belirgin temalar çıkarıldı

### Kalite Metrikleri
- **Konu Tutarlılığı (C_v):** 0.6757 ✅ (İyi seviye)
- **Konu Farklılığı (Jaccard):** 0.9984 ✅ (Mükemmel ayrışma)
- **Benzersiz Kelime Oranı (PUW):** 0.9621 ✅ (Yüksek çeşitlilik)

### Performans
- **Eğitim Süresi:** ~1.45 dakika
- **Çıkarım Hızı:** 6.52 doküman/saniye

## 🚀 Kullanılan Teknolojiler

### Ana Kütüphaneler
- **BERTopic 0.17.0** - Konu modellemesi
- **Sentence Transformers** - Metin gömmeleri
- **Gensim 4.3.3** - Tutarlılık metrikleri
- **scikit-learn** - Veri işleme
- **UMAP & HDBSCAN** - Boyut indirgeme ve kümeleme

### Model Konfigürasyonu
- **Gömme Modeli:** `all-MiniLM-L6-v2`
- **Temsil Modeli:** `KeyBERTInspired`
- **Vektörizasyon:** `CountVectorizer` (stop-words, n-gram(1,2))

## 📁 Proje Yapısı

```
bertopic-newsgroups-analysis/
├── BERTopic_ile_20_Newsgroups_Veri_Seti_Uzerinde_Konu_Modellemesi.ipynb
├── README.md
├── requirements.txt (önerilen)
└── images/ (görselleştirmeler için)
```

## 🔧 Kurulum ve Çalıştırma

### 1. Gereksinimler
```bash
# Python 3.7+ gereklidir
pip install bertopic==0.17.0
pip install sentence-transformers
pip install gensim==4.3.3
pip install scikit-learn
pip install matplotlib seaborn
pip install umap-learn hdbscan
pip install nltk
```

### 2. Notebook Çalıştırma
1. **Google Colab** ortamında açın (önerilen)
2. **Hücre 1'i** çalıştırarak kütüphaneleri kurun
3. **Çalışma zamanını yeniden başlatın** (kritik!)
4. **Hücre 2'den** itibaren sırasıyla çalıştırın

> ⚠️ **ÖNEMLİ:** Hücre 1'den sonra mutlaka runtime restart yapın!

## 📋 Hücre Açıklamaları

### Hücre 1: Kütüphane Kurulumu
- Kararlı BERTopic ortamı oluşturma
- NumPy uyumluluk sorunlarını çözme
- "Altın standart" versiyonları kurma

### Hücre 2: Kütüphane İmportları
- Tüm gerekli modüllerin yüklenmesi
- Versiyon kontrolü ve ortam doğrulama
- GPU desteği kontrolü

### Hücre 3: Veri Hazırlama
- 20 Newsgroups veri setini yükleme
- Meta verileri temizleme (headers, footers, quotes)
- 18,846 dokümanın işlenmesi

### Hücre 4: BERTopic Model Eğitimi
- Model konfigürasyonu ve parametreleri
- `fit_transform` ile eğitim
- `KeyBERTInspired` ile temsil güncelleme

### Hücre 5: Kalite Metrikleri
- Konu tutarlılığı hesaplama (C_v, C_UCI, C_NPMI, U_MASS)
- Konu farklılığı analizi (Jaccard, PUW)
- Gensim entegrasyonu

### Hücre 6: Görselleştirmeler
- İnteraktif çubuk grafikler
- Konu benzerlik haritaları
- Hiyerarşik analiz (dendrogram)
- Doküman dağılım haritaları

### Hücre 7: Performans Analizi
- Eğitim ve çıkarım süreleri
- Model verimliliği hesaplama

## 📈 Analiz Sonuçları

### Keşfedilen Konu Örnekleri
- **Konu 0 (Spor):** nhl, hockey, season, league, players...
- **Konu 1 (Teknoloji):** modem, mhz, ram, vga, monitor...
- **Konu 3 (Güvenlik):** militia, firearms, guns, amendment...
- **Konu 8 (Kriptografi):** encryption, crypto, cryptography...

### Konu Kalitesi Değerlendirmesi
| Metrik | Değer | Durum |
|--------|--------|--------|
| C_v Tutarlılık | 0.6757 | 🟢 İyi |
| Jaccard Uzaklığı | 0.9984 | 🟢 Mükemmel |
| PUW Çeşitliliği | 0.9621 | 🟢 Çok İyi |

## 🎨 Görselleştirme Özellikleri

Proje, BERTopic'in güçlü görselleştirme araçlarını kullanır:
- **Çubuk Grafikler:** Konu anahtar kelimeleri
- **Isı Haritaları:** Konu benzerlik matrisleri
- **Dendrogramlar:** Hiyerarşik konu yapısı
- **Dağılım Grafikleri:** Doküman-konu ilişkileri
- **Mesafe Haritaları:** Konular arası mesafeler

## 🔬 Teknik Detaylar

### Ön İşleme Stratejisi
- Stop-words filtreleme
- Minimum doküman frekansı: 5
- N-gram aralığı: (1,2)
- Bigram desteği

### Model Parametreleri
```python
BERTopic(
    embedding_model="all-MiniLM-L6-v2",
    vectorizer_model=CountVectorizer(...),
    nr_topics=30,
    min_topic_size=20,
    calculate_probabilities=True
)
```

### Değerlendirme Yaklaşımı
- **Nicel Metrikler:** Gensim CoherenceModel
- **Nitel Analiz:** Anahtar kelime incelemesi
- **Performans:** Süre ve verimlilik ölçümü

## 🚧 Bilinen Sorunlar ve Çözümler

### NumPy Uyumluluk Sorunu
- **Sorun:** `numpy.dtype size changed` hatası
- **Çözüm:** Belirli numpy versiyonu (1.26.4) kullanımı

### Dependency Conflicts
- **Sorun:** Kütüphane versiyon çakışmaları
- **Çözüm:** Temiz environment ve runtime restart

## 🤝 Katkıda Bulunma

Bu proje açık kaynak ruhuyla geliştirilmiştir. Katkılarınızı bekliyoruz:

1. Fork edin
2. Feature branch oluşturun
3. Değişikliklerinizi commit edin
4. Pull request gönderin

## 📝 Lisans

Bu proje MIT lisansı altında yayınlanmıştır.

## 👨‍💻 Yazar

**[Adınız]**
- Email: [email@example.com]
- LinkedIn: [linkedin.com/in/profiliniz]
- GitHub: [github.com/kullaniciadiniz]

## 🙏 Teşekkürler

- **BERTopic** geliştiricilerine
- **Scikit-learn** topluluğuna
- **20 Newsgroups** veri seti sağlayıcılarına
- **Google Colab** platformuna

---

⭐ **Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!**