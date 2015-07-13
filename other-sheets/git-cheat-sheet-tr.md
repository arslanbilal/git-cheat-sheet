Git Cheat Sheet Turkish
===============


###Index
* [Oluşturma](#oluşturma)
* [Yerel Değişiklikler](#yerel-değişiklikler)
* [Arama](#arama)
* [Commit Geçmişi](#commit-geçmişi)
* [Branches & Tags(Etiketler)](#branches--tags)
* [Güncelleştirme & Yayınlama](#güncelleştirme--yayınlama)
* [Merge(Birleştirme) & Rebase](#merge--rebase)
* [Geri Alma](#geri-alma)
* [Git Flow](#git-flow)

<hr>
##Oluşturma

#####Var olan bir repositoryi(depoyu) klonlama:
```
$ git clone ssh://user@domain.com/repo.git
```

#####Yeni bir yerel repository(depo) oluşturma:
```
$ git init
```

<hr>


##Yerel Değişiklikler

#####Çalışılan dizindeki dosyaların değişimi:
```
$ git status
```

#####İzlenen dosyalardaki değişiklikler:
```
$ git diff
```

#####Tüm güncel değişiklikleri sonraki commite ekleme:
```
$ git add
```

#####Sonraki commite &lt;dosyasındaki&gt; bazı değişikleri ekleme:
```
$ git add -p <file>
```

#####Tüm izlenen dosyalardaki yerel değişiklikleri Commitleme:
```
$ git commit -a
```

#####Önceden hazırlanan değişiklikleri commitleme:
```
$ git commit
```

#####Mesaj ile commitleme:
```
$ git commit -m 'message here'
```

#####Önceki belli bir tarihe commitleme:
```
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

#####Son commiti değiştirme:<br>
######Yayınlanan commite değişiklik yapmayın!
```
$ git commit --amend
```

#####Mevcut branchteki kaydedilmemiş commitleri diğer bazı branchlere taşıma:
```
git stash
git checkout branch2
git stash pop
```

<hr>
##Arama

#####Bir metni dizindeki bütün dosyalarda aramak:
```
$ git grep "Merhaba"
```

#####Bir metni herhangi bir sürüm içinde aramak:
```
$ git grep "Merhaba" v2.5
```

<hr>
##Commit Geçmişi

#####Tüm commitleri en yenisinden başlayarak listeler:
```
$ git log
```

#####Tüm commitleri görüntüler(Sadece commit hash ve commit mesajı görüntülenir.):
```
$ git log --oneline
```

#####Belli kullanıcıya ait commitleri görüntüler:
```
$ git log --author="username"
```

#####Belirli bir dosya üzerinde zaman içinde meydana gelen değişiklikleri göstermektedir:
```
$ git log -p <file>
```

#####&lt;Dosyayı&gt; kim , ne ve ne zaman değiştirdiğini gösterir.:
```
$ git blame <file>
```

<hr>


##Branches & Tags

#####Tüm var olan branchleri listeler:
```
$ git branch
```

#####Ana branchi değiştirir:
```
$ git checkout <branch>
```

#####Mevcut ana branchte yeni bir branch oluşturur:
```
$ git branch <new-branch>
```

#####Remote branchte yeni bir izlenen branch oluşturur:
```
$ git branch --track <new-branch> <remote-branch>
```

#####Yerel branchi siler:
```
$ git branch -d <branch>
```

#####Güncel commiti etiket ile işaretler:
```
$ git tag <tag-name>
```

<hr>


##Güncelleştirme & Yayınlama

#####Yapılandırılmış tüm güncel remoteları listeler:
```
$ git remote -v
```

#####Belirli bir &lt;remote&gt; hakkında bilgileri gösterir.:
```
$ git remote show <remote>
```

#####Yeni remote repository oluşturur, &lt;remote&gt; diye isimlendirir:
```
$ git remote add <remote> <url>
```

#####&lt;Remote&gt; da bulunan tüm değişiklikleri indirir, ama ana brachle birleştirmez:
```
$ git fetch <remote>
```

#####Değişiklikleri indirir ve doğrudan ana brache merge/integrate eder:
```
$ git remote pull <remote> <url>
```

#####Tüm ana Branchteki değişiklikleri yerel repositorye ekler:
```
$ git pull origin master
```

#####Remote da bulunan repositorye(depoya), yerel değişiklikleri yayınlar:
```
$ git push remote <remote> <branch>
```

#####Remote da bulunan bir branchi siler:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
or
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

#####Etiketleri yayınlar:
```
$ git push --tags
```

<hr>


##Merge & Rebase

#####Merge <branch> into your current HEAD:
```
$ git merge <branch>
```

#####Rebase your current HEAD onto &lt;branch&gt;:<br>
######Don't rebase published commit!
```
$ git rebase <branch>
```

#####Rabase iptal etmek:
```
$ git rebase --abort
```

#####Çakışmaları çözümledikten sonra rebase devam etmek:
```
$ git rebase --continue
```

#####Çatışmaları çözmek için yapılandırılmış birleştirme aracını kullanmak:
```
$ git mergetool
```

#####Use your editor to manully solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```
```
$ git rm <resolved-file>
```

<hr>


##Geri Alma

#####Çalışılan dosyadaki tüm yerel değişiklikleri kaldırır:
```
$ git reset --hard HEAD
```

#####Evreleme alanı dışındaki tüm dosyaları alır(örnek: son git add'i geri alır):
```
$ git reset HEAD
```

#####Belli bir dosyadaki yerel değişiklikleri kaldırır:
```
$ git checkout HEAD <file>
```

#####Silinen dosyayı geri döndürme dosyanın commit loglarının tutuluyor olması ile mümkündür:
```
$ git revert <commit>
```

#####Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

#####Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

#####Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

<hr>


##Git-Flow

###Index
* [Ayarlar](#ayarlar)
* [Başlarken](#başlarken)
* [Özellikler (Features)](#features)
* [Bir Yayın Çıkarırken (Release)](#release)
* [Hata Giderimleri (Hotfixes)](#hata-giderimleri)
* [Komutlar (Commands)](#komutlar)
<hr>


###Ayarlar
######Git flow'u kullanabilmek için öncelikli olarak git kurulumunun yapılması gerekmektedir. Git flow OSX, Linux ve Windows üzerinde çalıştırılabilir.

#####OSX Homebrew:
```
$ git clone ssh://user@domain.com/repo.git
```

#####OSX Macports:
```
$ port install git-flow
```

#####Linux:
```
$ apt-get install git-flow
```

#####Windows (Cygwin):
######Git flow kurulumu için wget ve util-linux gerekmektedir.
```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```
<hr>


###Başlarken
######Git flow, kullanmak istediğiniz projede ayarlarınızı özelleştirmek amacıyla başlatılır (initialize).

#####Başlangıç (Initialize):
######Bu noktada kafanızda dallarınızı (branches) isimlendirme konusuna ilişkin birçok soru işareti oluşacaktır. Bu bağlamda varsayılan (default) değerleri kullanmanız önerilir.
######git flow'u kullanmak istediğiniz reponuzdayken:
```
git flow init
```
<hr>


###Özellikler (Features)
######Git flow ile yayınlamak üzere olduğunuz projenize ekleyeceğiniz özellikler için yeni dallarda (feature) kodlama yaparsınız. Genel olarak sadece geliştirici repolarında bulunurlar.

#####Yeni bir özellik eklemesi başlatmak (feature start):
######Yeni özelliklerin eklenmesi öncelikle develop dalından (branch) başlar.
```
git flow feature start MYFEATURE
```
###### Bu komut bize develop dalını (branch) temel alan bir özellik dalı (feature) oluşturur. Ve bulunduğumuz dalı develop/MYFEATURE olarak değiştirir.

#####Bir özellik eklemesi bitirilirken (feature finish):
######Bir özelliğin eklenme işlemi bitirilirken şunları yapılır: 
######1)Kendi çalıştığımız özellik dalı (burada MYFEATURE) develop ana dalı ile birleştirilir.
######2)Bu birleşmeden sonra kendi özellik dalımız (MYFEATURE) silinir.
######3)Bulunduğumuz dal tekrar develop olarak değiştirilir.
```
git flow feature finish MYFEATURE
```

#####Bir özelliği yayınlamak (Publish a feature):
######Bir ekip içerisinde geliştirme mi yapıyorsunuz? O zaman geliştirdiğiniz özelliği bir uzak sunucuya gönderin, böylelikle geliştirdiğiniz özellik diğer kullanıcılar tarafından kullanılabilir.
```
git flow feature publish MYFEATURE
```

#####Yayınlanmış bir özelliği almak (Getting a published feature):
######Uzak sunucu üzerinde yayınlanmış bir özelliği kendi yerel (local) çalışma ortamınıza aktarırken:
```
git flow feature pull origin MYFEATURE
```
<hr>


###Bir Yayın Çıkarırken (Release)
######Yeni bir ürünün yayınlanmasına yardımcı olur. Küçük hata giderimleri ve meta-data hazırlığı için kullanılabilir.

#####Bir sürüm yayınlamak (Start a release):
######Bu komut ile develop dalını temel kabul eden bir release dalı (branch) yaratılır.
######Opsiyonel olarak yayınınızın [BASE] noktasından başlamasını sağlayabilirsiniz. Bu commit develop dalında (branch) iken yapılmalıdır.
```
git flow release start RELEASE [BASE]
```
######Yayınlama dalınız (release branch) oluştuktan sonra bu yöntem ile diğer yazılımcılar tarafından yapılan release commitlerinin de kabul edilmesini sağlayabilirsiniz. Bunu özellik yayınlama (feature publishing) ile kolaylıkla yapabilirsiniz.
```
git flow release publish RELEASE
```
######(Uzak sunucu üzerindeki yayınları ```git flow release track RELEASE``` ile izleyebilirsiniz. )

#####Bir sürüm yayınını tamamlamak(Finish up a release):
######Bir sürüm yayınını tamamlarken git dallanmasının (branching) en büyük adımını atarız. Yayınlanma tamamlanırken:
######1)Yayınlama yaptığımız dal olan release dalı (branch) master ana dalı ile birleştirilir.
######2)Etiketler (tags) isimleri ile birlikte yayınlanır.
######3)Arkaplandaki birleştirmeler (back-merges) develop dalında yayınlanır.
######4)Yayınlama için açmış olduğumuz dal (branch) silinir.
```
git flow release finish RELEASE
```
######Ancak etiketlerinizi de eklemeyi unutmayın! ```git push --tags``` bu sorununuzu da halledecektir.
<hr>


###Hata giderimleri (Hotfixes)
######Yayına çıkarılmış bir versiyonda istenmeyen durumlar ortaya çıktığında ani hata giderimi için kullanılır. Hotfixler, master ana dalı (branch)ındaki versiyon numarasını belirten etiketten dallanır (branching).

#####Bir hata giderimini başlatmak(git flow hotfix start):
######iğer git flow komutlarında olduğu gibi bir hotfix başlatılırken:
```
$ git flow hotfix start VERSION [BASENAME]
```
######Versiyon argümanları yeni hotfix yayınının adını alır. Opsiyonel olarak başlangıç noktası için bir isim özelleştirmesi yapabilirsiniz (basename).

#####Hata giderimi bitirme (Finish a hotfix):
######Bir hata giderimi tamamlanırken, develop ve master dalları ile birleştirilir. Ayrıca master dalına (branch) hotfix versiyonunun etiketi eklenir.
```
git flow hotfix finish VERSION
```
<hr>


###Komutlar (Commands)
<p align="center">
	<img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>
