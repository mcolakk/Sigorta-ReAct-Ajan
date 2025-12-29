# 🧠 DeepSeek Otonom Yapay Zeka Ajanı (RAG + Tools)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![DeepSeek](https://img.shields.io/badge/Model-DeepSeek--V3-purple)
![LangChain](https://img.shields.io/badge/Orchestration-LangChain-green)
![Status](https://img.shields.io/badge/Status-Benchmark%20Passed-success)

Bu proje, standart Dil Modellerinin (LLM) en büyük kısıtı olan "güncel veriye erişim" ve "halüsinasyon" sorunlarını çözmek amacıyla geliştirilmiş **Otonom Bir Ajan (Autonomous Agent)** sistemidir.

**DeepSeek-V3** modelini beyin olarak kullanan sistem; borsa verilerini çekebilir, hava durumunu kontrol edebilir, internette arama yapabilir ve şirket içi PDF dokümanlarını (RAG) sorgulayabilir.

---

## 🚀 Özellikler

Bu ajan, sadece sohbet etmekle kalmaz, **karar verir ve eyleme geçer (ReAct Mimarisi):**

* 📈 **Canlı Finans Takibi:** `yfinance` API ile Borsa, Kripto ve Döviz kurlarını anlık çeker. (Örn: "THY hissesi ne kadar?", "Bitcoin kaç dolar?")
* weather **Anlık Hava Durumu:** `Open-Meteo` ile dünya genelindeki şehirlerin hava durumunu sorgular.
* 🔍 **Web Arama Yeteneği:** `DuckDuckGo` ile modelin eğitim verisinde olmayan güncel olayları araştırır.
* 📄 **Doküman Analizi (RAG):** Şirket içi PDF dosyalarını (Örn: Sigorta Poliçesi) vektör veritabanına gömerek soruları bu kaynak üzerinden cevaplar.
* 🧠 **Düşünce Zinciri (CoT):** Ajanın hangi aracı neden seçtiğini gösteren detaylı loglama sistemi.

---

## 🛠️ Sistem Mimarisi

Sistem 4 ana bileşenden oluşur:

1.  **Manager Agent (Yönetici):** Kullanıcının niyetini anlar ve hangi aracı (`tool`) kullanacağına karar verir.
2.  **Tool Belt (Araç Seti):** Python fonksiyonları (API çağrıları).
3.  **Observation (Gözlem):** API'dan dönen ham verinin işlenmesi.
4.  **Judge (Hakem):** Cevabın doğruluğunu denetleyen değerlendirme katmanı.



---

## 📊 Benchmark ve Performans

Sistemin başarısı, **40 soruluk** kapsamlı bir test seti ile ölçülmüştür. Testlerde **"Ground Truth Enjeksiyonu"** (Referans Veri) yöntemi kullanılarak, canlı verilerin doğruluğu otomatik olarak test edilmiştir.

| Kategori | Soru Tipi | Başarı Oranı | Açıklama |
| :--- | :--- | :--- | :--- |
| **Finans** | Canlı Veri | **%100 (10/10)** | API entegrasyonu kusursuz. Sembolleri (Örn: Dolar -> TRY=X) otomatik tanır. |
| **Hava Durumu**| Canlı Veri | **%100 (10/10)** | Şehir bazlı sıcaklık verilerini doğru çeker. |
| **Web Search** | Halüsinasyon | **Yüksek** | "Türkiye'nin Mars Valisi" gibi tuzak sorularda "Yoktur" cevabını verir. |
| **RAG (PDF)** | Doküman | **Orta** | PDF verisini okur ancak bazen genel bilgisini (Pre-training) tercih edebilir. |

> **Not:** Benchmark sonuçları `ground_truth_benchmark.xlsx` dosyasında, ajanın düşünce süreci ise `ajan_dusunce_gunlugu.txt` dosyasında detaylıca incelenebilir.

---

## ⚙️ Kurulum

Projeyi yerel ortamınızda çalıştırmak için:

1.  **Depoyu Klonlayın:**
    ```bash
    git clone [https://github.com/kullaniciadiniz/deepseek-agent.git](https://github.com/kullaniciadiniz/deepseek-agent.git)
    cd deepseek-agent
    ```

2.  **Gereksinimleri Yükleyin:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **API Anahtarını Tanımlayın:**
    Kod içerisindeki veya `.env` dosyasındaki API anahtarı bölümünü düzenleyin:
    ```python
    api_key = "sk-senin-deepseek-anahtarin"
    ```

---

## 🖥️ Kullanım

Ajanı iki farklı modda çalıştırabilirsiniz:

### 1. İnteraktif Sohbet Modu
Sürekli soru-cevap yapabileceğiniz terminal arayüzü:
```python
start_interactive_chat()
