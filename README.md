# 🎯 Rastgele Sınav Değerlendirici

Bu proje, belirlenen soru sayısına ve öğrenci sayısına göre **rastgele bir sınav cevap anahtarı** oluşturur ve **öğrencilerin rastgele cevaplarını** değerlendirerek sınav sonuçlarını hesaplar.

## 🚀 Özellikler

- 📌 **Rastgele Cevap Anahtarı Üretme**  
  Belirlenen soru sayısı kadar rastgele cevap seçenekleri üretilir.  
- 📌 **Öğrenci Cevaplarını Oluşturma**  
  Her öğrenci için rastgele cevaplar atanır.  
- 📌 **Sınav Sonuçlarını Hesaplama**  
  Öğrenci cevapları ile cevap anahtarı karşılaştırılarak **doğru, yanlış ve net sayıları** hesaplanır.  
- 📌 **Kolay Kullanım**  
  Terminal üzerinden basit komutlarla çalıştırılabilir.  
- 📌 **Modüler Kod Yapısı**  
  Kod, anlaşılır ve düzenli bir yapıya sahiptir, geliştirilmeye açıktır.  

---

## 🛠️ Kurulum & Kullanım

### 1️⃣ Projeyi Klonlayın
```sh
git clone https://github.com/enesmalikyilmaz/RastgeleSinavDegerlendirici.git
cd RastgeleSinavDegerlendirici 
```

### 2️⃣ Projeyi Klonlayın

C programını çalıştırmak için GCC kullanabilirsiniz:

```sh
gcc main.c -o sinav_degerlendirici
```

### 3️⃣ Programı Çalıştırın
```sh
./sinav_degerlendirici
```

## 📜 Kod Açıklamaları
- 📌 **Cevap Anahtarı Oluşturma**
  
rastgele_cevap_anahtari_olustur() fonksiyonu, belirlenen soru sayısına göre rastgele cevap anahtarı oluşturur.
```c
void rastgele_cevap_anahtari_olustur(char *cevapAnahtari, int soruSayisi) {
    char secenekler[] = {'A', 'B', 'C', 'D', 'E'};
    for (int i = 0; i < soruSayisi; i++) {
        cevapAnahtari[i] = secenekler[rand() % 5];
    }
}
```
- 📌 **Öğrenci Cevaplarını Oluşturma**
  
ogrenci_cevaplarini_olustur() fonksiyonu, her öğrenci için rastgele cevaplar üretir.

```c
void ogrenci_cevaplarini_olustur(char ogrenciCevaplari[][MAX_SORU], int ogrenciSayisi, int soruSayisi) {
    char secenekler[] = {'A', 'B', 'C', 'D', 'E'};
    for (int i = 0; i < ogrenciSayisi; i++) {
        for (int j = 0; j < soruSayisi; j++) {
            ogrenciCevaplari[i][j] = secenekler[rand() % 5];
        }
    }
}
```
- 📌 **Sınav Sonuçlarını Değerlendirme**
  
Öğrenci cevapları cevap anahtarıyla karşılaştırılarak doğru ve yanlış sayıları hesaplanır.

```c
void sinav_sonucu_hesapla(char *cevapAnahtari, char ogrenciCevaplari[][MAX_SORU], int ogrenciSayisi, int soruSayisi) {
    for (int i = 0; i < ogrenciSayisi; i++) {
        int dogru = 0, yanlis = 0;
        for (int j = 0; j < soruSayisi; j++) {
            if (ogrenciCevaplari[i][j] == cevapAnahtari[j]) {
                dogru++;
            } else {
                yanlis++;
            }
        }
        printf("Öğrenci %d → Doğru: %d, Yanlış: %d, Net: %.2f\n", i + 1, dogru, yanlis, dogru - (yanlis / 4.0));
    }
}
```
