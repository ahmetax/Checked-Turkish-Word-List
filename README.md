# Denetlenmiş Türkçe Sözcük Dağarcığı
Bu projede, güncel Türkçede geçerli olan ve genellikle hala kullanılan sözcüklerin bir listesini oluşturuyoruz.
Bu projeye örnek veri sağlamak için elimdeki 2 milyonluk listeden yaklaşık 50 bin adedini kullanacağım. 
Bu sayının hem github açısından sorun teşkil etmeyeceğini, hem de kodların çalışması açısından yeterli
olacağını umuyorum. Gerekirse sayılarda değişiklikler yapabilirim. 

Belki de başlangıç kodu olarak bir "kelime toplayıcı" hazırlamak daha iyi olacak.

Kod çalışmalarını hızlandırmak amacıyla Claude, Gemini ve Grok'u kodlama danışmanı olarak kullanacağım.
Ana kodlama dilimiz Python olacak.
Veritabanı yöneticisi olarak SQLite kullanacağız.
Kelime analizlerimizin çekirdeğinde Zemberek kütüphanesinin son sürümü (zemberek-full-0.17.1.jar) bulunacak.

## YAPILACAKLAR LİSTESİ

1. Kelime Toplayıcı (Tamamlandı)
2. Wikipedia'dan kelime toplamak
3. Veritabanı ve tabloları oluşturmak
4. Güncel zemberek-full.jar dosyasının indirilmesi
5. Kelime Analizleri

## Kelime Toplayıcı Kullanımı

1. Bu repoyu klonla:
   ```bash
   git clone https://github.com/ahmetax/Checked-Turkish-Word-List.git
   cd Checked-Turkish-Word-List
   ```
   Sanal ortam kullanmanızı öneririm: (Aşağıdaki kodlar Ubuntu 24.04 içindir. Kendi sisteminize göre uyarlayın.)
   ```bash
   python3.12 -m venv e312
   source e312/bin/activate
   pip install -r requirements.txt
   ```
2. Gerekli kütüphaneleri kurun:
   ```bash
   pip install python-docx ebooklib beautifulsoup4 PyPDF2 tqdm
   ```
   veya
   ```bash
   pip install -r requirements.txt
   ``` 
3. Kaynak metinleri içerecek bir klasör açın:
   ```bash
   mkdir kaynak_metnler
   ```
4. kaynak_metnler klasörünün içine Türkçe metin dosyalarını kopyalayın.

5. Kelime toplayıcıyı çalıştırın:
   ```bash
   python kelime_toplayici.py
   ```
   Her çalıştırmada yeni bulunan kelimeler alfabetik olarak kelimeler.txt dosyasına eklenir.
   

   
