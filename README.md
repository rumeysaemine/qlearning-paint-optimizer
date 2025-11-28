## Q-Learning ile Grid Tabanlı Boyama Optimizasyonu

Bu proje, endüstriyel boya robotlarında görülen minimum kaynak kullanımı ve minimum zaman optimizasyonu probleminden esinlenerek oluşturulmuş bir pekiştirmeli öğrenme simülasyonudur.

Amaç, 5×5 bir grid üzerinde sınırlı boya stoğuyla hedef bölgeyi (3×3) en verimli şekilde boyayabilen bir ajan eğitmektir.


### Teknik Detaylar ve Algoritma

**1. Ortam (GridEnvironment)**
- Boyut: 5x5 grid.    
- Ajan Durumu (State):
	-  Ajan Konumu ($\text{R}, \text{C}$): Ajanın mevcut satır/sütun koordinatları    
	-  Kalan Boya Miktarı ($\text{P}$): $0$ ile $9$ arasında   
	-  Grid boyalı/boyasız durumu ($\text{G}$): $2^{25}$ olası durum

**2. Eylem Uzayı (Actions)**
- Hareket: Yukarı, Aşağı, Sol, Sağ (0-3)
- Boyama: Bulunduğu hücreyi boyar ve boya stoğunu azaltır

**3. Ödül Sistemi (Reward Function)**
- Hedef bölgenin tamamını boyamak: $\mathbf{+100}$
- Her geçerli hareket (zaman maliyeti): $\mathbf{-1}$ 
- Hedef dışını boyama (atık): $\mathbf{-10}$
- Boyasızken boya basmak / duvara çarpma: $\mathbf{-3}$ ila $\mathbf{-5}$

**4. Öğrenme Algoritması:** Temel Q-Learning algoritması kullanılmıştır.


###  Sonuçlar Ve Performans
Eğitim tamamlandıktan sonra, projenin çalıştığı dizinde aşağıdaki dosyalar oluşturulacaktır:
**1. `training_performance.png`**:  Ajanın öğrenme sürecini gösteren Episode 
başına ortalama ödül grafiği.

![training_performance.png](./training_performance.png)
    
**2. `test_agent.gif`**: Eğitilmiş ajanın (farklı rastgele başlangıçlardan) optimal politikayı uygularken grid üzerindeki hareketini ve boyama sırasını gösteren animasyonlu GIF.

![test_agent.gif](/test_agent.gif)
