# 🛡️ PoliçeGPT: Sigorta ReAct Ajanı (AI Agent)

Bu proje, **ReAct (Reasoning + Acting)** mimarisini kullanarak sigorta poliçelerini analiz eden, kullanıcı sorularını "düşünerek" ve dökümanlara başvurarak cevaplayan akıllı bir yapay zeka asistanıdır.

Standart RAG sistemlerinden farklı olarak; bu ajan cevabı ezbere vermez, önce **düşünür (Thought)**, gerekirse **arama yapar (Action)** ve bulduğu bilgiyi **yorumlar (Observation)**.

## 🚀 Özellikler
* **Orkestratör:** Qwen-2.5-7B Instruct (LLM)
* **Mimari:** ReAct (Reasoning and Acting) + Agentic RAG
* **Veritabanı:** ChromaDB (Vektör Veritabanı)
* **Yetenekler:**
    * Semantik Arama (Anlamsal Eşleştirme)
    * Sorgu Genişletme (Query Expansion)
    * Düşünce Zinciri (Chain of Thought) ile karar verme

## 📂 Proje İçeriği
* `Proje_Notebook.ipynb`: Tüm kodların bulunduğu Google Colab/Jupyter dosyası.
* `kasko_policesi.pdf`: Ajanın eğitildiği örnek veri seti.
* `requirements.txt`: Gerekli Python kütüphaneleri.

## 🛠️ Kurulum ve Çalıştırma

1. **Repoyu Klonlayın:**
   ```bash
   git clone [https://github.com/mcolakk/Sigorta-ReAct-Ajan.git](https://github.com/mcolakk/Sigorta-ReAct-Ajan.git)
   cd Sigorta-ReAct-Ajan
