# 🛡️ AI Sigorta Asistanı (AI Insurance Assistant)

Bu proje, **Doğal Dil İşleme (NLP)** ve **Generative AI** teknolojilerini kullanarak sigorta sektörü için geliştirilmiş akıllı bir asistandır.

Proje, **LangChain** ve **Groq (Llama 3)** altyapısını kullanarak kullanıcıların sigorta poliçeleri, araç yedek parça fiyatları, finansal veriler ve risk analizleri hakkındaki sorularını yanıtlar. Sistem, **RAG (Retrieval-Augmented Generation)** mimarisi ile PDF dokümanlarını okuyabilir ve **Agent (Ajan)** yapısı ile internetten canlı veri toplayabilir.

## 🚀 Özellikler

Bu asistan aşağıdaki yeteneklere sahip otonom araçlar (tools) kullanır:

* **📄 RAG (Doküman Analizi):** Kasko poliçesi gibi PDF dosyalarını vektör veritabanına (ChromaDB) dönüştürerek poliçe kapsamı hakkında soruları yanıtlar.
* **🌍 Canlı Web Araması (DuckDuckGo):** Yedek parça fiyatları, kronik araç arızaları veya güncel sigorta haberleri için interneti tarar.
* **📈 Finansal Analiz (Yahoo Finance):** Döviz kurları (Dolar/Euro) ve Altın fiyatlarını canlı takip ederek maliyet hesabı yapar.
* **☁️ Risk Analizi (Hava Durumu API):** Anlık hava durumu verisi çekerek (Dolu, Sel riski vb.) sigorta risk uyarısı yapar.
* **🚗 Tramer/Hasar Sorgusu (Simülasyon):** Plaka üzerinden hasar kaydı kontrolü yapar.

## 🛠️ Kullanılan Teknolojiler

* **Python 3.10+**
* **LLM:** Llama-3.3-70b-versatile (via Groq API)
* **Orchestration:** LangChain & LangChain Community
* **Vector Store:** ChromaDB
* **Embeddings:** HuggingFace (`sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2`)
* **Tools:** `yfinance`, `duckduckgo-search`, `requests`
* **Platform:** Google Colab

## ⚙️ Kurulum ve Çalıştırma

Bu proje Google Colab üzerinde çalıştırılmak üzere tasarlanmıştır.

1. **Repoyu Klonlayın veya İndirin:**
   Proje dosyasını (`.ipynb`) bilgisayarınıza indirin.

2. **Google Colab'de Açın:**
   Dosyayı Google Colab'e yükleyin.

3. **API Anahtarını Ayarlayın:**
   * [Groq Console](https://console.groq.com/) adresinden ücretsiz bir API Key alın.
   * Colab sol menüsündeki **Anahtar (Secrets)** simgesine tıklayın.
   * `groq1` adıyla bir anahtar oluşturun ve değerini girin.

4. **PDF Yükleyin (Opsiyonel):**
   * Sistemin kendi dokümanlarınızla konuşması için `kasko_policesi.pdf` adında bir dosyayı Colab dosya yöneticisine yükleyin.
   * *Not: Dosya yüklemezseniz sistem sanal verilerle çalışmaya devam eder.*

5. **Hücreleri Çalıştırın:**
   Tüm hücreleri sırasıyla çalıştırın ve `👉 Soru:` kısmına sorunuzu yazın.

## 📝 Örnek Senaryolar

Sisteme sorabileceğiniz bazı örnek sorular:

* **Poliçe Sorusu:** *"Poliçemde sel hasarı karşılanıyor mu?"* (PDF'ten okur)
* **Parça Fiyatı:** *"Fiat Egea 2023 ön tampon fiyatı ne kadar?"* (İnternetten arar)
* **Finans:** *"Dolar kuru şu an ne kadar? Hasar maliyetim artar mı?"* (Borsadan çeker)
* **Risk:** *"İstanbul'da şu an dolu riski var mı?"* (Hava durumuna bakar)

## 🧠 Mimari Yapı

Proje, **ReAct (Reasoning and Acting)** benzeri bir döngü kullanır:

1.  **Kullanıcı Sorusu:** Sisteme girilir.
2.  **Karar Mekanizması (LLM):** Model, soruyu analiz eder ve hangi aracı (Tool) kullanması gerektiğini seçer (Örn: `Action: web_search`).
3.  **Eylem (Action):** Python fonksiyonu çalışır ve veriyi getirir.
4.  **Gözlem (Observation):** Gelen veri modele geri beslenir.
5.  **Cevap (Answer):** Model, veriyi yorumlayarak son kullanıcıya Türkçe cevap verir.

## 🤝 Katkıda Bulunma

Bu bir üniversite projesidir. Geliştirmek için Pull Request atabilir veya fikirlerinizi belirtebilirsiniz.

## 📄 Lisans

Bu proje MIT Lisansı ile lisanslanmıştır.
