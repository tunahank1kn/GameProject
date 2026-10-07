# Mario Tarzı Platformer: GitHub Issues Görev Listesi

Her başlık ayrı bir Issue olarak açılabilir. Etiket önerileri: `kurulum`, `oyuncu`, `seviye`, `düşman`, `arayüz`, `ses`, `hata`.
Pano sütunları: Yapılacak / Yapılıyor / Bitti

---

## Hafta 1-2: Kurulum (İkisi birlikte)

- [ ] **Unity Learn: Essentials yolunu tamamla** (A ve B)
- [ ] **Unity Learn: Beginner Scripting yolunu tamamla** (A ve B)
- [ ] **Repo kurulumu:** Unity `.gitignore`, README, collaborator ekleme
- [ ] **Unity ayarları:** Visible Meta Files + Force Text, aynı Unity sürümü
- [ ] **Klasör yapısı:** `Assets/Scripts`, `Prefabs`, `Scenes`, `Sprites`, `Audio`
- [ ] **İlk test:** kare karakter hareket etsin, commit at, diğer kişi pull yapsın

---

## Hafta 3-4

### Kişi A
- [ ] **Oyuncu hareketi** (sağ/sol, `Rigidbody2D`)
- [ ] **Zıplama** (yerde mi kontrolü, zıplama yüksekliği ayarı)
- [ ] **Oyuncu prefab'ı oluştur**
- [ ] **Test scene'i:** `TestScene_A`

### Kişi B
- [ ] **Tilemap kurulumu** (Grid, Tilemap, Tile Palette)
- [ ] **Zemin ve platform tile'ları** (Tilemap Collider 2D)
- [ ] **Boş test seviyesi:** `Level_Test`

---

## Hafta 5-6

### Kişi A
- [ ] **Kamera takibi** (Cinemachine veya basit script)
- [ ] **Can sistemi** (can sayısı, hasar alma)
- [ ] **Ölüm ve yeniden başlama**
- [ ] **Checkpoint**

### Kişi B
- [ ] **Yürüyen düşman** (kenara gelince dönsün)
- [ ] **Üstüne basınca ölme** mantığı
- [ ] **Coin prefab'ı** ve toplama
- [ ] **Düşman prefab'ı**

---

## Hafta 7-8: Birleştirme

- [ ] **Branch'leri birleştir**, çakışmaları çöz (İkisi birlikte)
- [ ] **Bitiş bayrağı** ve seviye geçişi (A)
- [ ] **Oyun yöneticisi:** skor, coin sayacı (A)
- [ ] **İlk gerçek seviyeyi çiz** (B)
- [ ] **Oyuncu hissini ince ayarla** (zıplama, hız, yerçekimi) (A)

---

## Hafta 9-10

### Kişi A
- [ ] **Ana menü ve duraklatma menüsü** mantığı
- [ ] **Game Over ekranı**
- [ ] **Hata düzeltmeleri** (Issues'taki `hata` etiketli kayıtlar)

### Kişi B
- [ ] **Arayüz:** can, skor, coin göstergesi (UI Canvas)
- [ ] **Ses efektleri:** zıplama, coin, ölüm
- [ ] **Arka plan müziği**
- [ ] **İkinci seviye**

---

## Hafta 11-12: Cila ve Yayın

- [ ] **Animasyonlar:** yürüme, zıplama, düşman (Animator)
- [ ] **Oyun testi:** en az 3 kişiye oynat, geri bildirim topla (İkisi birlikte)
- [ ] **Son hata düzeltmeleri**
- [ ] **Build al** (WebGL veya Windows)
- [ ] **itch.io sayfası:** ekran görüntüleri, açıklama, yükleme
- [ ] **README'yi güncelle:** nasıl oynanır, kontroller, ekran görüntüleri

---

## Çalışma Kuralları (README'ye eklenebilir)

- `main` branch'e doğrudan commit atılmaz.
- Branch isimleri: `feature/oyuncu-hareketi`, `fix/zipalama-hatasi`
- Her iş için Pull Request açılır, diğer kişi inceler.
- Aynı scene'de aynı anda çalışılmaz.
- Her sabah `git pull`, her akşam commit.
- Haftada bir 15-20 dakikalık görüşme.
