# Unity + GitHub Ortak Proje Rehberi

2 kişilik 2D platformer (Mario tarzı) projesi için adım adım rehber.
Bu dosyayı sakla, arkadaşınla paylaş, takıldığında bak.

---

## BÖLÜM 1: İlk Kurulum (Bir kere yapılır)

### 1.1 Gerekli programlar
- **Unity Hub + Unity Editor** (2D / Universal şablonu). İkiniz de **aynı sürümü** kurun.
  - Sürümü görmek için: proje klasöründe `ProjectSettings/ProjectVersion.txt` dosyasını aç.
- **Git** (git-scm.com). Kurulumda varsayılan ayarlarla ilerle.
- **Kod editörü:** Visual Studio (Unity ile birlikte kurulur) veya VS Code.
- İsteğe bağlı: **GitHub Desktop** (komut yazmak istemezsen).

### 1.2 Git kimliğini tanıt (terminalde bir kere)
```
git config --global user.name "Adın Soyadın"
git config --global user.email "github-mailin@ornek.com"
```
Kontrol: `git config --global --list`

### 1.3 Unity Learn
- Unity Learn indirilen bir program değil, **web sitesidir:** learn.unity.com
- Unity hesabınla giriş yap.
- Sırayla yap: **Unity Essentials**, sonra **Beginner Scripting**.
- Günde 1 saat yeterli.

---

## BÖLÜM 2: Projeyi Kuran Kişi (Repo sahibi)

### 2.1 Repoyu bilgisayara indir
Terminal aç ve projeyi koymak istediğin klasöre git:
```
git clone https://github.com/KULLANICI/REPO-ADI.git
```
Bu komut `REPO-ADI` adında bir klasör oluşturur.

### 2.2 Unity dosyalarını kopyala
1. Unity'yi **kapat**.
2. Eski Unity proje klasöründen sadece şunları kopyala:
   - `Assets`
   - `Packages`
   - `ProjectSettings`
3. Bunları klonlanan repo klasörünün **içine** yapıştır.
4. `Library`, `Temp`, `Obj`, `Logs`, `UserSettings` klasörlerini **kopyalama**. `.gitignore` zaten bunları yok sayar.

### 2.3 .gitignore kontrolü
Repo klasöründe `.gitignore` dosyası olmalı. Yoksa GitHub'da "Unity.gitignore" resmi şablonunu bulup ekle.

### 2.4 Terminali DOĞRU klasörde aç
Çok önemli: komutlar proje klasöründe çalışmalı.
- Dosya Gezgini'nde repo klasörünü aç.
- Üstteki **adres çubuğuna** tıkla, `powershell` yaz, Enter'a bas.
- Terminalin başında `PS C:\...\REPO-ADI>` yazmalı.
- `PS C:\Users\kullanici>` yazıyorsa **yanlış yerdesin**. Bu durumda `git add .` bütün kullanıcı klasörünü eklemeye çalışır ve "Permission denied" uyarıları verir.

Doğru yerde olduğunu kontrol et:
```
git status
```
`Assets`, `Packages`, `ProjectSettings` "Untracked files" altında görünmeli.

### 2.5 İlk yükleme
```
git add .
git commit -m "Unity projesi eklendi"
git push origin main
```
GitHub'da repo sayfasını yenile, dosyalar görünmeli. `Library` veya `Temp` görünmemeli.

### 2.6 Unity'yi doğru klasörden aç
Unity Hub > **Add > Add project from disk** > klonlanan repo klasörünü seç. Bundan sonra hep bu klasörle çalış, eski proje klasörünü kullanma.

### 2.7 Unity ayarları (Git uyumu için şart)
**Edit > Project Settings > Editor**:
- Version Control Mode: **Visible Meta Files**
- Asset Serialization Mode: **Force Text**

Değiştirdiysen commit at:
```
git add .
git commit -m "Unity editor ayarlari guncellendi"
git push origin main
```

---

## BÖLÜM 3: Arkadaşın İçin Kurulum

1. GitHub'dan gelen **collaborator davetini kabul et** (e-posta veya github.com/notifications).
2. Git, Unity Hub ve **aynı Unity sürümünü** kur.
3. Git kimliğini tanıt (1.2).
4. Repoyu indir:
   ```
   git clone https://github.com/KULLANICI/REPO-ADI.git
   ```
5. Unity Hub > **Add > Add project from disk** > klonlanan klasörü seç.
6. İlk açılış birkaç dakika sürer (Library klasörünü kendisi oluşturur). Normal.
7. İlk push sırasında tarayıcı açılıp GitHub girişi isteyebilir, onayla.

---

## BÖLÜM 4: Günlük Çalışma Düzeni

### Sabah, çalışmaya başlamadan önce
```
git checkout main
git pull
```

### Yeni iş için branch aç
```
git checkout -b feature/is-adi
```
Örnekler: `feature/oyuncu-hareketi`, `feature/dusman`, `fix/zipalama-hatasi`

### Çalış, sık commit at
```
git add .
git commit -m "Ne yaptığını kısaca yaz"
```

### Akşam push et
İlk push (yeni branch):
```
git push -u origin feature/is-adi
```
Sonraki push'lar:
```
git push
```

### İş bitince Pull Request (PR)
1. GitHub'da repo sayfasına git, **Compare & pull request** butonuna tıkla.
2. Başlık ve kısa açıklama yaz, **Create pull request**.
3. Arkadaşın PR'ı inceler (Files changed sekmesi), sorun yoksa **Approve** ve **Merge** eder.
4. Birleştikten sonra **herkes** şunu yapar:
   ```
   git checkout main
   git pull
   ```
5. Eski branch'i silebilirsin (GitHub'da "Delete branch" butonu çıkar).

### Altın kurallar
- `main` branch'e doğrudan commit atma.
- Aynı **scene** dosyasında aynı anda çalışmayın. Herkes kendi scene'inde çalışsın.
- Oyuncu, düşman, coin gibi nesneleri **prefab** yapın.
- Commit mesajlarını anlamlı yaz ("düzeltme" yerine "Zıplama yüksekliği ayarlandı").
- Unity açıkken `git pull` veya branch değiştirme yapma. Önce Unity'yi kapat, sonra yap, sonra aç.
- Büyük dosyaları (ses, büyük doku) repoya atmadan önce konuşun. Gerekirse **Git LFS** kullanılır.

---

## BÖLÜM 5: GitHub Düzeni

### Issues (görevler)
- Repo sayfasında **Issues > New issue**.
- `gorevler.md` içindeki görevleri tek tek ekle, **Assignees** kısmından kişiye ata.
- Etiket (label) öner: `oyuncu`, `seviye`, `düşman`, `arayüz`, `ses`, `hata`.

### Projects (pano)
- **Projects > New project > Board** seç.
- Sütunlar: **Yapılacak / Yapılıyor / Bitti**.
- Issue'ları panoya ekle, iş ilerledikçe sütunlar arasında taşı.

### Haftalık görüşme
Haftada bir 15-20 dakika: ne bitti, ne takıldı, gelecek hafta ne yapılacak.

---

## BÖLÜM 6: İş Bölümü

**Kişi A: Oyuncu ve oyun mantığı**
- Oyuncu hareketi, zıplama, animasyon
- Kamera takibi
- Can, ölüm, yeniden başlama, checkpoint
- Oyun yöneticisi (skor, seviye geçişi), bitiş bayrağı

**Kişi B: Dünya ve içerik**
- Tilemap ile seviye tasarımı
- Düşman (yürüyen, üstüne basınca ölen)
- Coin ve toplanabilir objeler
- Arayüz (skor, can, menü), ses ve müzik

### Hafta planı
| Hafta | İş |
|---|---|
| 1-2 | Unity Learn, repo kurulumu |
| 3-4 | A: oyuncu hareketi, B: tilemap ve test seviyesi |
| 5-6 | A: kamera, ölüm; B: düşman, coin |
| 7-8 | Birleştirme, ilk gerçek seviye |
| 9-10 | Menü, ses, ikinci seviye, hata düzeltme |
| 11-12 | Cila, test, itch.io'ya yükleme |

---

## BÖLÜM 7: İlk Görev (Git akışını öğrenmek için)

1. `git checkout -b feature/oyuncu-hareketi`
2. Unity'de: **GameObject > 2D Object > Sprites > Square**
3. Kareye **Rigidbody2D** ve **BoxCollider2D** ekle.
4. Zemin için bir Square daha ekle, **BoxCollider2D** ver, genişlet.
5. **Assets/Scripts** klasöründe `PlayerController.cs` oluştur, sağa sola hareket ve zıplama yaz.
6. Scripti kareye sürükle, test et.
7. Commit, push, PR aç, arkadaşın onaylasın, merge et.

---

## BÖLÜM 8: Sık Karşılaşılan Hatalar

| Hata | Çözüm |
|---|---|
| `git is not recognized` | Git kurulu değil veya terminal yenilenmedi. Kur, terminali kapat-aç. |
| `not a git repository` | Yanlış klasördesin. Repo klasörüne `cd` ile gir veya adres çubuğundan terminal aç. |
| `Permission denied` uyarıları yağıyor | Kullanıcı klasöründe `git add .` yaptın. Yanlış yer. 2.4'e bak. Yanlışlıkla oluşan `.git` klasörünü sil. |
| `Please tell me who you are` | Git kimliğini tanıt (1.2). |
| `Authentication failed` | Şifre kabul edilmiyor. Tarayıcı girişini kullan (Git Credential Manager) veya GitHub Desktop. |
| `rejected` / `failed to push` | Önce `git pull`, sonra tekrar `git push`. |
| `src refspec main does not match any` | Henüz commit atılmamış veya branch adı `master`. `git branch -M main` yaz. |
| Merge conflict | Dosyayı aç, `<<<<<<<` ve `>>>>>>>` işaretlerini bul, doğru versiyonu bırak, işaretleri sil, sonra `git add .` ve `git commit`. Scene dosyalarında çakışma çıkarsa birbirinize sorun. |
| Unity'de "pembe" sprite/materyal | Render pipeline uyumsuzluğu. 2D (Universal) şablonuyla açıldığından emin ol. |
| Arkadaşta proje açılmıyor | Unity sürümleri farklı olabilir. `ProjectVersion.txt`'e bak. |

---

## BÖLÜM 9: Komut Kopya Kâğıdı

```
git status                         # Durum ne?
git pull                           # Güncellemeleri çek
git checkout main                  # main'e geç
git checkout -b feature/isim       # Yeni branch aç
git checkout feature/isim          # Var olan branch'e geç
git add .                          # Tüm değişiklikleri hazırla
git commit -m "mesaj"              # Kaydet
git push                           # GitHub'a gönder
git push -u origin feature/isim    # Yeni branch'i ilk kez gönder
git branch                         # Branch'leri listele
git log --oneline                  # Commit geçmişi
```

---

## BÖLÜM 10: Kaynaklar

- **Öğrenme:** learn.unity.com, YouTube: Brackeys (2D platformer)
- **Ücretsiz grafik/ses:** kenney.nl, itch.io (Assets > Free), opengameart.org
- **Pixel art araçları:** Piskel (piskelapp.com), LibreSprite, Aseprite
- **Oyun yayınlama:** itch.io
- **Game jam:** itch.io/jams, Global Game Jam

**Telif notu:** Nintendo'nun karakter ve grafiklerini kullanma. Mekanikleri al, karakteri ve grafikleri kendin yap veya lisansı uygun ücretsiz asset kullan.
