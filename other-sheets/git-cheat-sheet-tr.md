# Git Cheat Sheet Türkçe

![Git Logo](../Img/git-logo.png)

En çok kullanılan Git komutları için hızlı referans rehberi, kolay kullanım için kategorilere göre düzenlenmiştir.

## 📖 Bu Rehber Hakkında

Bu kapsamlı Git referans rehberi, Git iş akışlarını iyileştirmek isteyen herkes için eksiksiz bir kaynaktır. Git yolculuğuna başlayan yeni başlayanlardan deneyimli geliştiricilere kadar, bu rehber geliştirme sürecinizi hızlandırmak için sistematik olarak düzenlenmiş ve kategorize edilmiş komutlar sağlar.

### Temel Özellikler:
- **Sistematik kategoriler**: Komutlar açık ve mantıklı gruplara düzenlenmiştir
- **Pratik örnekler**: Gerçek kullanım durumlarıyla birlikte verilmiştir
- **Yeni başlayanlar için uygun**: Net açıklamalar ve ipuçları içerir
- **Hızlı referans**: Temel komutlara anında erişim

---

## 📑 İçindekiler

- [📖 Bu Rehber Hakkında](#bu-rehber-hakkında)
- [🔧 İlk Kurulum](#i̇lk-kurulum)
- [⚙️ Yapılandırma Dosyaları](#yapılandırma-dosyaları)
- [📁 Depo Kurulumu](#depo-kurulumu)
- [📊 Durum Komutları](#durum-komutları)
- [📝 Dosya Yönetimi](#dosya-yönetimi)
- [💾 Commit'ler](#commitler)
- [🌿 Dal'lar (Branches)](#dallar-branches)
- [🔀 Birleştirme (Merge)](#birleştirme-merge)
- [🌐 Uzak Depolar](#uzak-depolar)
- [📚 Geçmiş ve Loglar](#geçmiş-ve-loglar)
- [🔍 Arama](#arama)
- [📁 Taşıma/Yeniden Adlandırma](#taşımayeniden-adlandırma)
- [🏷️ Etiketler (Tags)](#etiketler-tags)
- [↩️ Değişiklikleri Geri Alma](#değişiklikleri-geri-alma)
- [📦 Saklama (Stash)](#saklama-stash)
- [🌊 Git Flow](#git-flow)
- [💡 Faydalı İpuçları](#faydalı-i̇puçları)
- [📚 Ek Kaynaklar](#ek-kaynaklar)
- [🌍 Diğer Diller](#diğer-diller)
- [🤝 Katkıda Bulunma](#katkıda-bulunma)
- [📄 Lisans](#lisans)

---

## 🔧 İlk Kurulum

Git'i kişisel bilgilerinizle yapılandırın:

```bash
# Kullanıcı adını ayarlama
git config --global user.name "Adınız"

# E-posta adresini ayarlama
git config --global user.email "email@example.com"

# Mevcut yapılandırmayı görme
git config --list

# Varsayılan editörü ayarlama
git config --global core.editor "nano"

# Birleştirme aracını ayarlama
git config --global merge.tool vimdiff
```

---

## ⚙️ Yapılandırma Dosyaları

Git, yapılandırmayı çeşitli seviyelerde yönetir:

### Global yapılandırma dosyası
```bash
# Global yapılandırma dosyası yolu
~/.gitconfig

# Global yapılandırmayı düzenleme
git config --global --edit
```

### Depo yapılandırma dosyası
```bash
# Depo yapılandırma dosyası yolu
.git/config

# Depo yapılandırmasını düzenleme
git config --edit
```

### Sistem yapılandırması
```bash
# Sistem yapılandırma dosyası (yönetici izinleri gerekli)
/etc/gitconfig

# Sistem yapılandırmasını düzenleme
git config --system --edit
```

### Yararlı yapılandırma ayarları
```bash
# Renkli çıktıyı etkinleştirme
git config --global color.ui true

# Varsayılan dal adını ayarlama
git config --global init.defaultBranch main

# Satır sonu işleme (macOS/Linux)
git config --global core.autocrlf input

# Satır sonu işleme (Windows)
git config --global core.autocrlf true
```

---

## 📁 Depo Kurulumu

### Yeni depo oluşturma:

```bash
# Yeni Git deposu oluşturma
git init

# Mevcut depoyu klonlama
git clone <depo-url>

# Belirli dizine klonlama
git clone <depo-url> <dizin-adı>
```

---

## 📊 Durum Komutları

### Deponuzun durumunu kontrol etme:

```bash
# Deponun mevcut durumunu gösterme
git status

# Kısa formatta durum gösterme
git status -s

# İzlenmeyen dosyaları yok sayarak durum gösterme
git status --ignored

# Değiştirilmiş dosyalardaki farkları gösterme
git diff

# Hazırlama alanındaki farkları gösterme
git diff --staged

# Dallar arasındaki farkları gösterme
git diff <dal1> <dal2>
```

---

## 📝 Dosya Yönetimi

### Dosya ekleme ve kaldırma:

```bash
# Belirli dosyayı hazırlama alanına ekleme
git add <dosya>

# Tüm değiştirilmiş dosyaları ekleme
git add .

# Belirli türdeki tüm dosyaları ekleme
git add *.txt

# Etkileşimli ekleme
git add -i

# Dosyayı depo ve çalışma dizininden kaldırma
git rm <dosya>

# Dosyayı sadece depodan kaldırma (dizinde tutma)
git rm --cached <dosya>

# Dosya taşıma/yeniden adlandırma
git mv <kaynak-dosya> <hedef-dosya>
```

---

## 💾 Commit'ler

### Depoda değişiklikleri kaydetme:

```bash
# Mesajla commit yapma
git commit -m "Commit mesajı"

# Tüm değiştirilmiş dosyaları ekleyerek commit yapma
git commit -am "Commit mesajı"

# Son commit'i değiştirme
git commit --amend

# Boş commit yapma (CI/CD tetikleyicileri için yararlı)
git commit --allow-empty -m "CI Tetikleyici"

# Ayrıntılı mesajla commit yapma (editör açılır)
git commit
```

---

## 🌿 Dal'lar (Branches)

### Dallarla çalışma:

```bash
# Tüm dalları gösterme
git branch

# Uzak dalları gösterme
git branch -r

# Tüm dalları gösterme (yerel ve uzak)
git branch -a

# Yeni dal oluşturma
git branch <dal-adı>

# Dala geçiş yapma
git checkout <dal-adı>

# Yeni dal oluşturup geçiş yapma
git checkout -b <dal-adı>

# Belirli commit'ten dal oluşturma
git checkout -b <dal-adı> <commit-hash>

# Dal silme
git branch -d <dal-adı>

# Zorla dal silme
git branch -D <dal-adı>

# Mevcut dalı yeniden adlandırma
git branch -m <yeni-ad>

# Belirli dalı yeniden adlandırma
git branch -m <eski-ad> <yeni-ad>
```

---

## 🔀 Birleştirme (Merge)

### Dallar arasında değişiklikleri birleştirme:

```bash
# Mevcut dala başka dalı birleştirme
git merge <dal-adı>

# Fast-forward olmadan birleştirme (merge commit oluşturma)
git merge --no-ff <dal-adı>

# Sadece fast-forward olduğunda birleştirme
git merge --ff-only <dal-adı>

# Devam eden birleştirmeyi iptal etme
git merge --abort

# Çakışma çözümünden sonra birleştirmeye devam etme
git merge --continue
```

---

## 🌐 Uzak Depolar

### Uzak depo yönetimi:

```bash
# Uzak depoları gösterme
git remote

# URL'lerle uzak depoları gösterme
git remote -v

# Uzak depo ekleme
git remote add <ad> <url>

# Uzak depo URL'ini değiştirme
git remote set-url <ad> <yeni-url>

# Uzak depo kaldırma
git remote remove <ad>

# Uzak depoya değişiklikleri gönderme
git push <uzak> <dal>

# Dal göndererek takibi ayarlama
git push -u <uzak> <dal>

# Tüm dalları gönderme
git push --all

# Etiketleri gönderme
git push --tags

# Uzak depodan değişiklikleri indirme
git pull <uzak> <dal>

# Birleştirme olmadan değişiklikleri indirme
git fetch <uzak>

# Tüm uzak dalları indirme
git fetch --all
```

---

## 📚 Geçmiş ve Loglar

### Commit geçmişini keşfetme:

```bash
# Commit geçmişini gösterme
git log

# Commit başına bir satırda geçmiş gösterme
git log --oneline

# Grafik ile geçmiş gösterme
git log --graph

# Belirli dosyanın geçmişini gösterme
git log <dosya>

# Commit istatistiklerini gösterme
git log --stat

# Her commit'teki değişiklikleri gösterme
git log -p

# Son N commit'i gösterme
git log -n <sayı>

# Tarihler arasındaki commit'leri gösterme
git log --since="2023-01-01" --until="2023-12-31"

# Yazara göre commit'leri gösterme
git log --author="Yazar Adı"

# Commit mesajlarında arama yapma
git log --grep="anahtar kelime"
```

---

## 🔍 Arama

### İçerik ve geçmişte arama:

```bash
# İzlenen dosyalarda metin arama
git grep "aranacak metin"

# Büyük/küçük harf duyarsız arama
git grep -i "metin"

# Tam kelime arama
git grep -w "kelime"

# Satır numaralarını gösterme
git grep -n "metin"

# Sadece dosya adlarını gösterme
git grep -l "metin"

# Belirli dosyalarda arama
git grep "metin" -- "*.js"

# Commit geçmişinde arama
git log -S "metin" --source --all

# Geçmişte ekleme/silme araması
git log -G "regex_pattern" --patch

# Dosya adına göre arama
git log --all --full-history -- "**/dosya_adi.*"

# Belirli commit'te arama
git grep "metin" <commit-hash>
```

---

## 🏷️ Etiketler (Tags)

### Sürüm etiketleri yönetimi:

```bash
# Tüm etiketleri gösterme
git tag

# Hafif etiket oluşturma
git tag <etiket-adı>

# Açıklamalı etiket oluşturma
git tag -a <etiket-adı> -m "Etiket mesajı"

# Belirli commit'e etiket oluşturma
git tag -a <etiket-adı> <commit-hash>

# Etiket bilgilerini gösterme
git show <etiket-adı>

# Yerel etiket silme
git tag -d <etiket-adı>

# Uzak etiket silme
git push --delete <uzak> <etiket-adı>

# Belirli etiket gönderme
git push <uzak> <etiket-adı>

# Tüm etiketleri gönderme
git push <uzak> --tags
```

---

## 📁 Taşıma/Yeniden Adlandırma

### Dosya ve dizin yönetimi:

```bash
# Dosya taşıma/yeniden adlandırma
git mv <eski-dosya> <yeni-dosya>

# Dizin yeniden adlandırma
git mv <eski-dizin> <yeni-dizin>

# Birden fazla dosyayı dizine taşıma
git mv dosya1.txt dosya2.txt dizin/

# Büyük/küçük harf değişikliği (büyük/küçük harf duyarlı dosya sistemleri)
git mv dosyaadi.txt temp.txt
git mv temp.txt DosyaAdi.txt

# Taşınan dosyanın geçmişini takip etme
git log --follow <dosya>

# Taşınan dosyaları izleme
git log --stat -M

# Yeniden adlandırma algılama eşiğini ayarlama
git log --follow -M90% <dosya>
```

---

## ↩️ Değişiklikleri Geri Alma

### Değişiklikleri geri almak:

```bash
# Belirli dosyadaki değişiklikleri iptal etme
git checkout <dosya>

# Tüm commit edilmemiş değişiklikleri iptal etme
git checkout .

# Dosyayı belirli sürüme geri getirme
git checkout <commit-hash> <dosya>

# Dosyayı hazırlama alanından kaldırma
git reset <dosya>

# Tüm dosyaları hazırlama alanından kaldırma
git reset

# Önceki commit'e dönme (değişiklikleri koruma)
git reset --soft HEAD~1

# Önceki commit'e dönme (değişiklikleri iptal etme)
git reset --hard HEAD~1

# Belirli commit'e dönme
git reset --hard <commit-hash>

# Başka commit'i iptal eden yeni commit oluşturma
git revert <commit-hash>

# Birden fazla commit'i geri alma
git revert <hash-başlangıç>..<hash-bitiş>
```

---

## 📦 Saklama (Stash)

### Geçici olarak çalışmayı saklama:

```bash
# Mevcut değişiklikleri stash'e saklama
git stash

# Açıklayıcı mesajla saklama
git stash save "Açıklayıcı mesaj"

# Tüm stash'leri gösterme
git stash list

# Son stash'i uygulama
git stash apply

# Belirli stash'i uygulama
git stash apply stash@{0}

# Son stash'i uygulayıp silme
git stash pop

# Belirli stash'i silme
git stash drop stash@{0}

# Tüm stash'leri silme
git stash clear

# Stash'teki değişiklikleri gösterme
git stash show stash@{0}

# Stash'ten dal oluşturma
git stash branch <dal-adı> stash@{0}
```

---

## 🌊 Git Flow

Git Flow, proje yayınları etrafında tasarlanmış katı bir iş akışı tanımlayan dallanma modelidir.

### Ana dallar:
- **master/main**: Üretim kodu
- **develop**: Ana geliştirme dalı

### Destek dalları:
- **feature**: Yeni özellikler için
- **release**: Yeni sürüm hazırlığı için
- **hotfix**: Üretimde acil düzeltmeler için

### Git Flow komutları:

```bash
# git flow başlatma
git flow init

# Yeni özellik başlatma
git flow feature start <özellik-adı>

# Özelliği bitirme
git flow feature finish <özellik-adı>

# Özelliği yayınlama
git flow feature publish <özellik-adı>

# Sürüm başlatma
git flow release start <sürüm>

# Sürümü bitirme
git flow release finish <sürüm>

# Hotfix başlatma
git flow hotfix start <sürüm>

# Hotfix'i bitirme
git flow hotfix finish <sürüm>
```

### Git Flow olmadan iş akışı:

![Git Flow Commands](../Img/git-flow-commands-without-flow.png)

```bash
# Özellik dalı oluşturma
git checkout develop
git checkout -b feature/yeni-özellik

# Özellik üzerinde çalışma
git add .
git commit -m "Yeni özellik ekle"

# Develop'a özellik birleştirme
git checkout develop
git merge --no-ff feature/yeni-özellik
git branch -d feature/yeni-özellik

# Sürüm dalı oluşturma
git checkout develop
git checkout -b release/1.0.0

# Sürümü tamamlama
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "Sürüm 1.0.0"
git checkout develop
git merge --no-ff release/1.0.0
git branch -d release/1.0.0
```

---

## 💡 Faydalı İpuçları

### Faydalı kısayollar:

```bash
# Faydalı kısayolları ayarlama
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

### .gitignore dosyaları:

```bash
# .gitignore dosyası oluşturma
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore

# Zaten izlenen dosyaları yok sayma
git rm --cached <dosya>
echo "<dosya>" >> .gitignore
git add .gitignore
git commit -m ".gitignore'a dosya ekle"
```

---

## 📚 Ek Kaynaklar

### Resmi Dokümantasyon ve Rehberler
- [Git Resmi Dokümantasyonu](https://git-scm.com/doc)
- [Pro Git Kitabı (ücretsiz)](https://git-scm.com/book)
- [Git Referans Kılavuzu](https://git-scm.com/docs)
- [Git Eğitimi](https://git-scm.com/docs/gittutorial)

### Çevrimiçi Öğrenme Materyalleri
- [GitHub Git El Kitabı](https://guides.github.com/introduction/git-handbook/)
- [Atlassian Git Eğitimleri](https://www.atlassian.com/git/tutorials)
- [Learn Git Branching (etkileşimli)](https://learngitbranching.js.org/)
- [Git Immersion](http://gitimmersion.com/)

### GUI Araçları
- [GitHub Desktop](https://desktop.github.com/)
- [GitKraken](https://www.gitkraken.com/)
- [SourceTree](https://www.sourcetreeapp.com/)
- [Tower](https://www.git-tower.com/)

### İleri Düzey Konular
- [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- [Git İş Akışları](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Git İç Yapısı](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

---

## 🌍 Diğer Diller

Bu Git Cheat Sheet aşağıdaki dillerde mevcuttur:

- 🇺🇸 [English](../README.md)
- 🇸🇦 [العربية](git-cheat-sheet-ar.md)
- 🇧🇩 [বাংলা](git-cheat-sheet-bn.md)
- 🇩🇪 [Deutsch](git-cheat-sheet-de.md)
- 🇬🇷 [Ελληνικά](git-cheat-sheet-el.md)
- 🇪🇸 [Español](git-cheat-sheet-es.md)
- 🇮🇳 [हिन्दी](git-cheat-sheet-hi.md)
- 🇰🇷 [한국어](git-cheat-sheet-ko.md)
- 🇵🇱 [Polski](git-cheat-sheet-pl.md)
- 🇧🇷 [Português](git-cheat-sheet-pt_BR.md)
- 🇹🇷 **Türkçe** (mevcut)
- 🇨🇳 [中文](git-cheat-sheet-zh.md)

---

## 🤝 Katkıda Bulunma

Katkıları memnuniyetle karşılıyoruz! Bu projeyi iyileştirmeye yardımcı olmak için:

1. **Sorunları bildirin**: Hataları veya iyileştirme önerilerini paylaşın
2. **Yeni diller ekleyin**: Çeviriler oluşturun veya mevcut olanları geliştirin
3. **İçeriği iyileştirin**: Yeni komutlar, örnekler veya açıklamalar ekleyin
4. **Geri bildirim verin**: Deneyimlerinizi ve önerilerinizi paylaşın

### Nasıl katkıda bulunulur:
- [GitHub'da sorun açın](https://github.com/arslanbilal/git-cheat-sheet/issues)
- Pull request gönderin
- Dokümantasyon iyileştirmeleri önerin

---

## 📄 Lisans

Bu proje MIT Lisansı altında lisanslanmıştır. Ayrıntılar için [LICENSE](../LICENSE) dosyasına bakın.

---

<div align="center">
  <strong>⭐ Bu cheat sheet yararlı olduğunda yıldızlayın!</strong><br>
  <em>Git ile mutlu kodlamalar! 🚀</em>
</div>
