# Denetlenmiş Türkçe Sözcük Dağarcığı
Bu projede, güncel Türkçede geçerli olan ve genellikle hala kullanılan sözcüklerin bir listesini oluşturuyoruz.
Elimdeki 2 milyonluk listeyi burada paylaşmayacağım. 
Github, dosya boyutu konusunda katı kısıtlamalara sahip.
Bunu aşmak da mümkün elbette, ama, pek kullanıcı dostu değil bana göre.
O yüzden size hazır bir liste sunmak yerine, sizinle, benim elimdeki gibi bir Türkçe Sözcük Dağarcığını elde etmenizi sağlayacak araçlar paylaşacağım. 

Bbaşlangıç kodu olarak basit bir "kelime toplayıcı" hazırlamak iyi olacak.

Kod çalışmalarını hızlandırmak amacıyla Claude, Gemini ve Grok'u kodlama danışmanı olarak kullanıyorum.
Ana kodlama dilimiz Python olacak.
Veritabanı yöneticisi olarak SQLite kullanacağız.
Kelime analizlerimizin çekirdeğinde Zemberek kütüphanesinin son sürümü (zemberek-full-0.17.1.jar) bulunacak.

## YAPILACAKLAR LİSTESİ

1. Kelime Toplayıcı (Tamamlandı)
2. Wikipedia'dan kelime toplayıcı (Tamamlandı)
3. Veritabanı ve tabloları oluşturma
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
3. Kaynak metinleri içine koyacağınız bir klasör açın:
   ```bash
   mkdir kaynak_metnler
   ```
4. kaynak_metnler klasörünün içine Türkçe metin dosyalarını kopyalayın.

5. Kelime toplayıcıyı çalıştırın:
   ```bash
   python kelime_toplayici.py
   ```
   Her çalıştırmada yeni bulunan kelimeler alfabetik olarak kelimeler.txt dosyasına eklenir.
   

## Wikipedia'dan veri aktarımı ve kelimelere ayrıştırma

https://dumps.wikimedia.org/trwiki/latest/trwiki-latest-pages-articles.xml.bz2
dosyasını indirin.

Bu dosyayı çalışma klasörünüze kopyalayın veya wiki_xml2txt.py dosyasında tam adresini verin.

wiki_xml2txt.py betiğini çalıştırın. (Bu işlem biraz uzun sürebilir. Yaklaşık 1,580,000 makale işlenecek.)

   ```bash
   python wiki_xml2txt.py
   ```
Şimdi elinizde tr_corpus_wiki.txt isimli bir dosya olmalı. Boyutu 2GB civarındadır. 
Bu dosyanın içindeki bilgiler doğrudan işimize yaramaz. 
O yüzden yeni_kelime_tara.py betiği aracılığıyla corpus dosyasından kelime adaylarını çıkaracağız.
Bu betik, zemberek-full.jar dosyasına ihtiyaç duyar.

### Zemberek jar dosyasının indirilmesi

Zemberek projesi  https://github.com/ahmetaa/zemberek-nlp adresinde bulunur.
Dağıtım dosyaları içinse bir Google-drive adresi verilmiştir:
https://drive.google.com/#folders/0B9TrB39LQKZWSjNKdVcwWUxxUm8
Bağlandığınız drive ana sayfasından distributions klasörüne geçin ve 0.17.1 sürümünü indirin.
İnecek dosyanın adı 0.17.1-20251119T073639Z-1-001.zip benzeri olmalıdır.
Bu zip dosyasını açın. 
Elde edeceğiniz klasörün altındaki 0.17.1 isimli klasöre girin.
Buradaki zemberek-full.jar dosyasını çalışma klasörünüze kopyalayın.

### Yeni kelimelerin çıkarılması

   ```bash
   python yeni_kelime_tara.py
   ```
kesin_turkce_adaylari.txt dosyasındaki kelimeleri listenize ekleyebilirsiniz.

Not: trigram_model.txt dosyasını yeniden oluşturmak isterseniz:

   ```bash
   python build_trigram_model.py
   ```
betiğini kullanabilirsiniz.


   
   
