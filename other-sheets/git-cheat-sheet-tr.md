# Git ve Git Flow Kopya Kağıdı
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

---

## 📖 Hakkında

Bu kapsamlı Git kopya kağıdı, her şeyi ezberlemenize gerek kalmadan Git komutlarında ustalaşmanıza yardımcı olur. İster yeni başlayan ister deneyimli bir geliştirici olun, bu rehber temel Git işlemleri için hızlı bir referans sağlar.

**Katkılarınızı Bekliyoruz!** Yapabilecekleriniz:
- Dilbilgisi hatalarını düzeltme
- Yeni komutlar ekleme
- Kendi dilinize çevirme
- Açıklamaları iyileştirme

---
## 📋 İçindekiler

- [🔧 Kurulum](#-kurulum)
- [⚙️ Yapılandırma Dosyaları](#️-yapılandırma-dosyaları)
- [🆕 Depo Oluşturma](#-depo-oluşturma)
- [📝 Yerel Değişiklikler](#-yerel-değişiklikler)
- [🔍 Arama](#-arama)
- [📖 Commit Geçmişi](#-commit-geçmişi)
- [📁 Taşıma / Yeniden Adlandırma](#-taşıma--yeniden-adlandırma)
- [🌿 Dallar ve Etiketler](#-dallar-ve-etiketler)
- [🔄 Güncelleme ve Yayınlama](#-güncelleme-ve-yayınlama)
- [🔀 Birleştirme ve Rebase](#-birleştirme-ve-rebase)
- [↩️ Geri Alma](#️-geri-alma)
- [🌊 Git Flow](#-git-flow)
- [🌍 Diğer Diller](#-diğer-diller)

---

## 🔧 Kurulum

### Yapılandırmayı Görüntüleme

**Mevcut yapılandırmayı göster:**
```bash
git config --list
```

**Depo yapılandırmasını göster:**
```bash
git config --local --list
```

**Global yapılandırmayı göster:**
```bash
git config --global --list
```

**Sistem yapılandırmasını göster:**
```bash
git config --system --list
```

### Kullanıcı Yapılandırması

**Sürüm geçmişi için adınızı ayarlayın:**
```bash
git config --global user.name "[firstname lastname]"
```

**E-posta adresinizi ayarlayın:**
```bash
git config --global user.email "[valid-email]"
```

### Görüntüleme ve Editör Ayarları

**Otomatik komut satırı renklendirmesini etkinleştirin:**
```bash
git config --global color.ui auto
```

**Commit'ler için global editörü ayarlayın:**
```bash
git config --global core.editor vi
```

---

## ⚙️ Yapılandırma Dosyaları

| Kapsam | Konum | Komut Bayrağı |
|--------|-------|---------------|
| **Depo** | `<repo>/.git/config` | `--local` |
| **Kullanıcı** | `~/.gitconfig` | `--global` |
| **Sistem** | `/etc/gitconfig` | `--system` |

---

## 🆕 Depo Oluşturma

### Mevcut Depoyu Klonlama

**SSH ile:**
```bash
git clone ssh://user@domain.com/repo.git
```

**HTTPS ile:**
```bash
git clone https://domain.com/user/repo.git
```

### Yeni Depo Başlatma

**Mevcut dizinde depo oluştur:**
```bash
git init
```

**Belirli dizinde depo oluştur:**
```bash
git init <directory>
```

---

## 📝 Yerel Değişiklikler

### Durum ve Farkları Kontrol Etme

**Çalışma dizini durumunu görüntüle:**
```bash
git status
```

**İzlenen dosyalardaki değişiklikleri göster:**
```bash
git diff
```

**Belirli dosyadaki değişiklikleri göster:**
```bash
git diff <file>
```

### Değişiklikleri Hazırlama

**Tüm mevcut değişiklikleri ekle:**
```bash
git add .
```

**Belirli dosyaları ekle:**
```bash
git add <filename1> <filename2>
```

**Bir dosyanın parçalarını etkileşimli olarak ekle:**
```bash
git add -p <file>
```

### Değişiklikleri Kaydetme

**Tüm izlenen dosya değişikliklerini kaydet:**
```bash
git commit -a
```

**Hazırlanmış değişiklikleri kaydet:**
```bash
git commit
```

**Mesajla kaydet:**
```bash
git commit -m 'message here'
```

**Hazırlama adımını atlayarak mesajla kaydet:**
```bash
git commit -am 'message here'
```

**Belirli tarihle kaydet:**
```bash
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### Son Commit'i Değiştirme

> ⚠️ **Uyarı:** Yayınlanmış commit'leri değiştirmeyin!

**Son commit'i düzelt:**
```bash
git commit -a --amend
```

**Commit mesajını değiştirmeden düzelt:**
```bash
git commit --amend --no-edit
```

**Committer tarihini değiştir:**
```bash
GIT_COMMITTER_DATE="date" git commit --amend
```

**Yazar tarihini değiştir:**
```bash
git commit --amend --date="date"
```

### Değişiklikleri Saklama

**Mevcut değişiklikleri geçici olarak sakla:**
```bash
git stash
```

**Son saklanan değişiklikleri uygula:**
```bash
git stash apply
```

**Belirli bir stash'i uygula:**
```bash
git stash apply stash@{stash_number}
```
> Mevcut stash'leri görmek için `git stash list` kullanın

**Son stash'i kaldır:**
```bash
git stash drop
```

**Kaydedilmemiş değişiklikleri başka bir dala taşı:**
```bash
git stash
git checkout branch2
git stash pop
```

---

## 🔍 Arama

### Metin Arama

**Tüm dosyalarda metin ara:**
```bash
git grep "Hello"
```

**Belirli sürümde ara:**
```bash
git grep "Hello" v2.5
```

### Commit Arama

**Belirli anahtar kelimeyi ekleyen commit'leri bul:**
```bash
git log -S 'keyword'
```

**Düzenli ifade ile ara:**
```bash
git log -S 'keyword' --pickaxe-regex
```

---

## 📖 Commit Geçmişi

### Temel Geçmiş

**Tüm commit'leri göster (ayrıntılı):**
```bash
git log
```

**Commit'leri göster (her biri tek satır):**
```bash
git log --oneline
```

**Belirli yazarın commit'lerini göster:**
```bash
git log --author="username"
```

**Belirli dosyadaki değişiklikleri göster:**
```bash
git log -p <file>
```

### Gelişmiş Geçmiş

**Dalları karşılaştır:**
```bash
git log --oneline <origin/master>..<remote/master> --left-right
```

**Kim neyi ne zaman değiştirdi göster:**
```bash
git blame <file>
```

### Referans Günlükleri

**Referans günlüğünü göster:**
```bash
git reflog show
```

**Referans günlüğünü sil:**
```bash
git reflog delete
```

---

## 📁 Taşıma / Yeniden Adlandırma

**Bir dosyayı yeniden adlandır:**
```bash
git mv Index.txt Index.html
```

---

## 🌿 Dallar ve Etiketler

### Dalları Listeleme

**Yerel dalları listele:**
```bash
git branch
```

**Tüm dalları listele (yerel + uzak):**
```bash
git branch -a
```

**Uzak dalları listele:**
```bash
git branch -r
```

**Birleştirilmiş dalları listele:**
```bash
git branch --merged
```

### Dal Değiştirme ve Oluşturma

**Mevcut dala geç:**
```bash
git checkout <branch>
```

**Yeni dal oluştur ve geç:**
```bash
git checkout -b <branch>
```

**Önceki dala geç:**
```bash
git checkout -
```

**Mevcut daldan yeni dal oluştur:**
```bash
git checkout -b <new_branch> <existing_branch>
```

**Belirli commit'ten dal oluştur:**
```bash
git checkout <commit-hash> -b <new_branch_name>
```

**Geçiş yapmadan dal oluştur:**
```bash
git branch <new-branch>
```

**İzleme dalı oluştur:**
```bash
git branch --track <new-branch> <remote-branch>
```

### Dal İşlemleri

**Farklı daldan tek dosya al:**
```bash
git checkout <branch> -- <filename>
```

**Başka daldan belirli commit'i uygula:**
```bash
git cherry-pick <commit hash>
```

**Mevcut dalı yeniden adlandır:**
```bash
git branch -m <new_branch_name>
```

**Yerel dalı sil:**
```bash
git branch -d <branch>
```

**Yerel dalı zorla sil:**
```bash
git branch -D <branch>
```
> ⚠️ **Uyarı:** Birleştirilmemiş değişiklikleri kaybedersiniz!

### Etiketler

**HEAD'de etiket oluştur:**
```bash
git tag <tag-name>
```

**Açıklamalı etiket oluştur:**
```bash
git tag -a <tag-name>
```

**Mesajlı etiket oluştur:**
```bash
git tag <tag-name> -am 'message here'
```

**Tüm etiketleri listele:**
```bash
git tag
```

**Etiketleri mesajlarıyla listele:**
```bash
git tag -n
```

---

## 🔄 Güncelleme ve Yayınlama

### Uzak Depo Yönetimi

**Yapılandırılmış uzak depoları listele:**
```bash
git remote -v
```

**Uzak depo bilgisini göster:**
```bash
git remote show <remote>
```

**Yeni uzak depo ekle:**
```bash
git remote add <remote> <url>
```

**Uzak depoyu yeniden adlandır:**
```bash
git remote rename <remote> <new_remote>
```

**Uzak depoyu kaldır:**
```bash
git remote rm <remote>
```
> ℹ️ **Not:** Bu yalnızca yerel uzak referansı kaldırır, uzak deponun kendisini silmez.

### Fetch ve Pull

**Değişiklikleri birleştirmeden indir:**
```bash
git fetch <remote>
```

**Değişiklikleri indir ve birleştir:**
```bash
git pull <remote> <branch>
```

**Ana daldan değişiklikleri al:**
```bash
git pull origin master
```

**Rebase ile pull yap:**
```bash
git pull --rebase <remote> <branch>
```

### Push ve Yayınlama

**Yerel değişiklikleri yayınla:**
```bash
git push <remote> <branch>
```

**Uzak dalı sil:**
```bash
# Git v1.7.0+
git push <remote> --delete <branch>

# Git v1.5.0+
git push <remote> :<branch>
```

**Etiketleri yayınla:**
```bash
git push --tags
```

---

## 🔀 Birleştirme ve Rebase

### Birleştirme İşlemleri

**Dalı mevcut HEAD'e birleştir:**
```bash
git merge <branch>
```

**Birleştirme aracını global olarak yapılandır:**
```bash
git config --global merge.tool meld
```

**Yapılandırılmış birleştirme aracını kullan:**
```bash
git mergetool
```

### Rebase İşlemleri

> ⚠️ **Uyarı:** Yayınlanmış commit'leri rebase etmeyin!

**Mevcut HEAD'i dal üzerine rebase et:**
```bash
git rebase <branch>
```

**Rebase'i iptal et:**
```bash
git rebase --abort
```

**Çakışmaları çözdükten sonra rebase'e devam et:**
```bash
git rebase --continue
```

### Çakışma Çözümü

**Dosyayı çözüldü olarak işaretle:**
```bash
git add <resolved-file>
```

**Çözülen dosyayı kaldır:**
```bash
git rm <resolved-file>
```

### Commit'leri Birleştirme (Squash)

**Squash için etkileşimli rebase:**
```bash
git rebase -i <commit-just-before-first>
```

**Örnek squash yapılandırması:**
```
# Önce
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

# Sonra (commit_id2 ve commit_id3'ü commit_id ile birleştir)
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---

## ↩️ Geri Alma

### Değişiklikleri İptal Etme

**Tüm yerel değişiklikleri iptal et:**
```bash
git reset --hard HEAD
```

**Tüm dosyaları hazırlama alanından çıkar:**
```bash
git reset HEAD
```

**Belirli dosyadaki değişiklikleri iptal et:**
```bash
git checkout HEAD <file>
```

### Sıfırlama İşlemleri

**Önceki commit'e sıfırla (tüm değişiklikleri sil):**
```bash
git reset --hard <commit>
```

**Uzak dal durumuna sıfırla:**
```bash
git reset --hard <remote/branch>
# Örnek: git reset --hard upstream/master
```

**Değişiklikleri hazırlanmamış olarak koruyarak sıfırla:**
```bash
git reset <commit>
```

**Kaydedilmemiş yerel değişiklikleri koruyarak sıfırla:**
```bash
git reset --keep <commit>
```

### Commit'leri Geri Alma

**Commit'i geri al (ters değişikliklerle yeni commit oluştur):**
```bash
git revert <commit>
```

### Yok Sayılan Dosyaları Temizleme

**Yanlışlıkla kaydedilmiş, yok sayılması gereken dosyaları kaldır:**
```bash
git rm -r --cached .
git add .
git commit -m "remove ignored files"
```

---

## 🌊 Git Flow

**Geliştirilmiş Git-flow:** [git-flow-avh](https://github.com/petervanderdoes/gitflow-avh)

### 📋 İçindekiler
- [🔧 Kurulum](#setup-1)
- [🚀 Başlangıç](#getting-started)
- [✨ Özellikler](#features)
- [🎁 Sürüm Yayınlama](#make-a-release)
- [🔥 Acil Düzeltmeler](#hotfixes)
- [📊 Komutlara Genel Bakış](#commands-overview)

---

### 🔧 Kurulum {#setup-1}

> **Ön Koşul:** Çalışan bir Git kurulumu gereklidir. Git-flow macOS, Linux ve Windows'ta çalışır.

**macOS (Homebrew):**
```bash
brew install git-flow-avh
```

**macOS (MacPorts):**
```bash
port install git-flow
```

**Linux (Debian tabanlı):**
```bash
sudo apt-get install git-flow
```

**Windows (Cygwin):**
> wget ve util-linux gerektirir
```bash
wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```

---

### 🚀 Başlangıç

Git-flow, projenizi özelleştirmek için başlatma gerektirir.

**Başlatma (etkileşimli):**
```bash
git flow init
```
> Dal adlandırma kuralları hakkında sorular yanıtlayacaksınız. Varsayılan değerler önerilir.

**Başlatma (varsayılanları kullan):**
```bash
git flow init -d
```

---

### ✨ Özellikler

Özellikler, gelecek sürümler için yeni işlevsellik geliştirmek içindir. Genellikle yalnızca geliştirici depolarında bulunurlar.

**Yeni özellik başlat:**
```bash
git flow feature start MYFEATURE
```
> 'develop' dalını temel alan özellik dalı oluşturur ve ona geçiş yapar

**Özelliği tamamla:**
```bash
git flow feature finish MYFEATURE
```
> Bu işlem:
> 1. MYFEATURE'ı 'develop' dalına birleştirir
> 2. Özellik dalını siler
> 3. 'develop' dalına geri geçer

**Özelliği yayınla (iş birliği için):**
```bash
git flow feature publish MYFEATURE
```

**Yayınlanan özelliği al:**
```bash
git flow feature pull origin MYFEATURE
```

**Origin özelliğini izle:**
```bash
git flow feature track MYFEATURE
```

---

### 🎁 Sürüm Yayınlama

Sürümler, yeni üretim sürümlerinin hazırlanmasını destekler, küçük hata düzeltmeleri ve meta-veri hazırlığına olanak tanır.

**Sürüm başlat:**
```bash
git flow release start RELEASE [BASE]
```
> 'develop' dalından sürüm dalı oluşturur. İsteğe bağlı olarak [BASE] commit SHA-1 belirtin.

**Sürümü yayınla:**
```bash
git flow release publish RELEASE
```

**Uzak sürümü izle:**
```bash
git flow release track RELEASE
```

**Sürümü tamamla:**
```bash
git flow release finish RELEASE
```
> Bu işlem:
> 1. Sürüm dalını 'master'a birleştirir
> 2. Sürümü etiketler
> 3. Sürümü 'develop'a geri birleştirir
> 4. Sürüm dalını siler

> 💡 **Unutmayın:** Etiketlerinizi `git push --tags` ile gönderin

---

### 🔥 Acil Düzeltmeler

Acil düzeltmeler, canlı üretim sürümlerindeki kritik sorunları giderir. Master üzerindeki ilgili etiketten dallanırlar.

**Acil düzeltme başlat:**
```bash
git flow hotfix start VERSION [BASENAME]
```

**Acil düzeltmeyi tamamla:**
```bash
git flow hotfix finish VERSION
```
> Hem 'develop' hem de 'master'a geri birleştirir ve master birleştirmesini etiketler

---

### 📊 Komutlara Genel Bakış

<p align="center">
    <img alt="Git Flow Komutları" src="../Img/git-flow-commands.png" height="270" width="460">
</p>

### 🌊 Git Flow Şeması

<p align="center">
    <img alt="Git Flow Şeması" src="../Img/git-flow-commands-without-flow.png">
</p>

---


## 🌍 Diğer Diller

Bu kopya kağıdı birçok dilde mevcuttur:

| Dil | Bağlantı |
|-----|----------|
| 🇸🇦 Arapça | [git-cheat-sheet-ar.md](git-cheat-sheet-ar.md) |
| 🇧🇩 Bengalce | [git-cheat-sheet-bn.md](git-cheat-sheet-bn.md) |
| 🇧🇷 Brezilya Portekizcesi | [git-cheat-sheet-pt_BR.md](git-cheat-sheet-pt_BR.md) |
| 🇨🇳 Çince | [git-cheat-sheet-zh.md](git-cheat-sheet-zh.md) |
| 🇩🇪 Almanca | [git-cheat-sheet-de.md](git-cheat-sheet-de.md) |
| 🇬🇷 Yunanca | [git-cheat-sheet-el.md](git-cheat-sheet-el.md) |
| 🇮🇳 Hintçe | [git-cheat-sheet-hi.md](git-cheat-sheet-hi.md) |
| 🇰🇷 Korece | [git-cheat-sheet-ko.md](git-cheat-sheet-ko.md) |
| 🇵🇱 Lehçe | [git-cheat-sheet-pl.md](git-cheat-sheet-pl.md) |
| 🇪🇸 İspanyolca | [git-cheat-sheet-es.md](git-cheat-sheet-es.md) |
| 🇹🇷 **Türkçe** | **(mevcut)** |

---

## 🤝 Katkıda Bulunma

Katkılarınızı bekliyoruz! Yapabilecekleriniz:

- 🐛 Hataları veya yazım yanlışlarını bildirme
- ✨ Yeni Git komutları ekleme
- 🌍 Yeni dillere çevirme
- 💡 Açıklamaları iyileştirme
- 📝 Biçimlendirmeyi geliştirme

**Nasıl katkıda bulunulur:**
1. Bu depoyu fork edin
2. Özellik dalınızı oluşturun (`git checkout -b feature/HarikaOzellik`)
3. Değişikliklerinizi kaydedin (`git commit -m 'HarikaOzellik ekle'`)
4. Dalınızı gönderin (`git push origin feature/HarikaOzellik`)
5. Bir Pull Request açın

---

## 📄 Lisans

Bu proje açık kaynaklıdır ve [MIT Lisansı](../LICENSE) altında kullanılabilir.

---

<p align="center">
    <b>⭐ Bu depoyu faydalı bulduysanız yıldızlayın!</b>
</p>
