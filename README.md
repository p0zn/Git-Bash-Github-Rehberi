![N|Background](https://i.ibb.co/Q9Hqc6X/background.png)



Makale içeriği,


- Git bash ve kullanımı.
- Github repository oluşturma, dosya yükleme, branch oluşturma ve genel bilgiler.


## 1- Git Nedir? Neden Kullanılır?

- Git genel tanımıyla versiyon kontrol sistemidir. Oluşturduğumuz projeleri internet ortamında(uzak bilgisayar) tutmamızı sağlayan bir sistemdir. Tanımdan anlaşıldığı üzere **git ve github aynı şey değildir.** 

## 2- Git İş Akışı :

![N|Mimari](https://i.im.ge/2022/08/31/OElMv6.git-mimarisi.png)

- Working Directory : Kendimize ait olan çalışma dizinidir (Dosya dizinimiz). 
- Staging Area(Index Area) : Geçiş bölgesi, çalışma dizinimizden repositoriye aktaracağımız dosyalar için bir ara kontrol katmanıdır. Bu katman üzerinden belirli kontroller sağlanarak dosya bütünlüğü ve doğruluğu sağlanır. 
- Git Repository : Git üzerindeki depolama alanıdır. 

## 3- Git Bash Yararlı Komutlar : 
- **pwd** : Mevcut dizini gösterir.
- **ls** : Mevcut dizindeki dosyaları listeler
- **ls -a** : Mevcut dizindeki gizli dosyaları listeler.
- **cd** : Dizin değiştirmeyi sağlar.
- **cd ..** : Bir önceki dizine dönmeyi sağlar.
- **clear** : Bash terminalini temizlemeyi sağlar.

## 4- Git Rehberi : 
#### 4.1 - Git'e Kullanıcı Bilgileri Girmek :
Bir proje üzerinde alınan sürümlerin kim tarafından alındığını bilmek için gerekli önemli bir adımdır.

##### git'e isim girmek :
Git'e isim girmek için aşağıdaki komut kullanılır.
```sh
git config --global user.name "Furkan Özkan"
```

##### git'e mail girmek :
Git'e mail girmek için aşağıdaki komut kullanılır.
```sh
git config --global user.email "p0zn@protonmail.com"
```

Komutları sayesinde git üzerinde kullanıcı bilgilerimizi tanımlayabiliriz. Daha sonrasında bilgilerimizi görmek ve kontrol etmek için : 
```sh
git config --global user.name
git config --global user.email
```
komutlarını kullanabiliriz.

![N|user_info](https://i.im.ge/2022/08/31/OEd52y.git-user-info.png)

#### 4.2 - Git Projesi Oluşturma :

**cd** komutu ile proje dosyamızın konumuna giderek, projenin bir git projesi olmasını belirtmemiz için :

```sh
git init
```
komutunu yazıyoruz. Bu sayede proje dosyamızın içerisine git dosyaları yüklendi. 
Dosya içeriğini **ls** komutu ile kontrol ettiğinizde boş olduğunu göreceksiniz. Fakat bu dosyanın boş olduğu anlamına gelmez. 
Git dosyaları klasör içerisinde gizli olarak tutulur. Gizli dosyaları görmek için **ls -a** komutunu kullanabilirsiniz. 
Bu komutu girdikten sonra klasör içerisindeki .git dosyalarını görebilirsiniz. 
".git" klasörü içerisinde git ile alakalı dosyalar bulunur.

![N|project_create](https://i.im.ge/2022/08/31/OEdZDP.git-proje-olusturma.png)

#### 4.3 - Projeyi Git Deposuna Ekleme :

Working directory deki dosyalarımızı verilen git iş şeması akışında git deposuna eklemek için öncellikle : 

```sh
git add .
```
komutunu kullanıyoruz. "." şuanki dizin içerisindeki tüm dosyaları belirtir. 
add komutu sonrasında artık dosyalarımız "Staging Area" dediğimiz geçiş bölgesine geçer. 
Dosyalarımızı git deposuna eklemek için commit etmemiz gerekir : 

```sh
git commit -m "eyyo my first commit"
```

"-m" mesajı belirtir. Girilen mesaj versiyonun niteliğini ve bilgisini içerecek şekilde olmalıdır.
Şuan dosyalarımızın git tarafından bir versiyon kopyası oluşturuldu.

Alınan versiyonları listelemek için : 

```sh
git log
```

komutunu kullanırız. Komut çıktısında ekleme tarihi, mesaj, kim tarafından eklendiği ve hash gibi bilgiler mevcuttur. 

![N|project_inf](https://i.im.ge/2022/08/31/OEqmdf.git-repoya-ekleme.png)

#### 4.4 - Proje Üzerindeki Değişiklikleri Gösterme :

```sh
git status
```
komutu ile projede değişiklik olup olmadığı kontrolü yapılır. 
**"nothing to commit,working tree clean"** çıktısı commit edilecek dosyamızın olmadığını bize belirtir.

![N|project_clr](https://i.ibb.co/k2KkC1C/temiz-proje.png)

Proje dosyamıza yeni dosyalar eklendiğinde **git status** komutu çıktı olarak commit edilmemiş dosyaları gösterir. 
Projeye eklediğimiz yeni dosyaları **add** komutu ile ilk önce geçiş bölgesine daha sonra **commit** komutu ile git deposuna aktarıyoruz. Tekrar **git status** komutunu çalıştırınca commit edilecek dosya olmadığını görüyoruz. 
**add** komutu "." ile kullanıldığında proje içindeki tüm dosyaları, spesifik olarak dosya adı verilince sadece verilen dosyayı geçiş bölgesine geçirir.

![N|project_afternew](https://i.im.ge/2022/08/31/OEsLzJ.dosya-sonrasi-commit.png)

#### 4.5 - Proje Üzerinde Değişiklik Yapma :

Proje geliştirme sürecinde dosyalarımız üzerinde değişiklik yapmamız gerekebilir. Örneğin projeye eklediğimiz hello.py dosyası içerisinde bir kaç değişiklik yapalım ve git status ile tekrar kontrol edelim. 

![N|project_mdf1](https://i.im.ge/2022/08/31/OEaalD.proje-degisiklik-1.png)

**git status** komutunu çalıştırdıktan sonra hello.py nin kırmızı bir şekilde modified olarak işaretlendiğini görüyoruz. Bu bize hello.py nin en son commit edildikten sonra içeriğinin değiştirildiği anlamına gelmektedir. 

#### 4.6 - Proje Üzerinde Değişiklikleri Görme (Working Directory) :

Proje dosyalarımızdaki değişiklikleri satır satır listelemek için :

```sh
git diff
```

komutunu kullanırız. Dosya üzerinde ekleme yapılan kısımlar yeşil renkli ve + işareti ile satır satır gösterilir. Komut çıktısında da görüldüğü gibi sum_method() adlı yeni bir fonksiyon hello.py içerisine eklenmiş. 
Değişiklerin tekrar git deposuna göndermek için : 

```sh
git add .
git commit -m "sum_method() added to hello.py"
```
komutlarını giriyoruz. Daha sonra **git status** ve **git log** komutlarını çalıştırarak her şeyin doğru olduğuna emin oluyoruz.

> Not: Dosya içerisinde silme işlemi yapıldığında terminalde çıktı olarak silinen alanlar **kırmızı** ve **"-"** işareti ile gösterilecektir. 

![N|project_diff1](https://i.ibb.co/C0bqsLV/git-dif-1.png) 

#### 4.7 - Proje Üzerinde Değişiklikleri Görme (Staging Area) :

**git diff** komutu parametresiz olarak çalıştırıldığında "Working Directory" ve "Staging Area" arasındaki değişiklikleri gösterir. Commit işlemi sonrasındaki değişiklikleri (Staging Area ve Git Repo arasındaki) görmek için komutumuza yeni bir parametre daha ekliyoruz. 

```sh
git diff --staged 
```

#### 4.8 - Git Dosya Silme İşlemi :

git üzerinde dosyaları silmek için 2 method bulunur. 

##### 4.8.1 - Manuel Silme :

Dosyalarınızı manuel olarak "Working Directory" üzerinde elle silebilirsiniz. Dosya silme işleminden sonra **git status** komutunu çalıştıralım. Silinen dosya kırmızı renkli ve deleted tagi ile işaretlenmiş bir şekilde gözüküyor. 
Sildiğimiz dosyayı geçiş bölgesine göndermek için : 

```sh
git rm hello.py
```
komutunu kullanıyoruz. Daha sonra git deposuna silme işlemini bildirmek için tekrar **commit** işlemi uyguluyoruz. İşlemleri gerçekleştirdikten sonra **git status** komutunu yazarak her şeyin yolunda olduğunu kontrol ediyoruz. 

![N|project_dell1](https://i.ibb.co/gRJKxn8/dell1.png)

##### 4.8.2 - Komut İle Silme (Önerilen Yöntem) :

Dosyalarımızı komut ile silmek daha basit ve önerilen yoldur. 
Komut satırına silmek istediğimiz dosyayı : 

```sh
git rm hello.py
```

**rm** komutu ile giriyoruz. Ardından commit ederek işlemimizi tamamlıyoruz. 

![N|project_dell2](https://i.ibb.co/K9z3Yjz/dell2.png)


##### 4.8.3 - BONUS - Klasör Silme :

Proje üzerinde klasör silmek için **rm** komutuna ekstra olarak yeni bir parametre ekliyoruz ve klasör adını giriyoruz : 

```sh
git rm -r will_delete/
```

> Not: **-r** : recursive yani özyinelemeli anlamına gelir. Klasör içindeki dosyaları ve klasörü siler. 


#### 4.9 - Dosya İsimlendirme ve Taşıma İşlemleri :

Proje içerisinde dosyalarımızı isimlendirmek ve taşımak için **mv** komutunu kullanıyoruz. 

##### 4.9.1 - Dosya İsimlendirme :

Dosyanın adını değiştirmek için : 

```sh
git mv hello.py new_name.py
```

komutunu kullanıyoruz. **mv** den sonra ismi değiştirilecek dosya ardından dosyanın yeni adı olacak şekilde komutumuzu yazıyoruz. Daha sonra commit işlemimizi yaparak git deposuna değişikliliği bildiriyoruz. 

![N|project_change-name](https://i.ibb.co/xfjxcrm/isim-de-i-tirme.png)


##### 4.9.2 - Dosya Taşıma :

Proje dosyalarını dizin içerisindeki başka bir klasöre taşımak için : 

```sh
git mv hello.py functions/
```
komutunu kullanıyoruz. Taşınacak dosya --> Taşınacak Klasör


#### 4.10 - Dosyaları Geri Alma İşlemi (Working Directory) :
Proje geliştirme aşamasında hata yapma olasılığı yüksektir. Kazara yapılan hata sonucu dosyaları geri almak, kurtarmak mümkündür. Öncelikle hello.py içerisindeki sum_method() fonksiyonunu silelim (Kaza senaryomuz). Daha sonra **git status** komutunu kullanarak değişiklikleri görelim.
hello.py modified tag i ile kırmızı bir şekilde gösteriliyor. **git status** çıktısında yer alan yardımcı komutlardan:

```sh
git restore hello.py
```
komutunu kullanarak dosyayı geri alalım. 

![N|project_restore_workingarea](https://i.ibb.co/G97Ysgm/restore-work.png)

Dosyayı geri aldık ve silinen sum_method() fonksiyonumuz da geri geldi. Böylelikle "Working Directory" üzerinde dosya kurtarma işlemini gerçekleştirdik. 

##### 4.10.1 - Dosyaları Geri Alma İşlemi (Staging Area) :
Bir önceki aşamada "Working Directory" üzerinden dosya kurtarma işlemini gerçekleştirmiştik. Şimdi geçiş bölgesinde olan dosyalarımız üzerinde dosya kurtarma işlemini görelim (**add** komutu ile geçiş bölgesine eklenmiş henüz commit edilmemiş dosyalar). Bu işlemde komutumuza aşina olduğumuz bir parametre ekliyoruz:

```sh
git restore --staged hello.py
```

**--staged** ile "Staging Area" dan kurtardığımız dosyayı daha sonrasında "Working Directory" e bildirmek için bir önceki adımda ki **restore** işlemimizi tekrar uyguluyoruz. 

```sh
git restore hello.py
```

Bu şekilde "Staging Area" ya gönderilmiş dosyamızı "Working Directory" e bildirmiş olup, dosyamızı kurtarmış oluyoruz. 

![N|project_restore_stagingarea](https://i.im.ge/2022/08/31/OEi2LS.sttaged-restore.png)

#### 4.11 - Versiyon Değiştirme :

Projemiz üzerinde birçok versiyon bulunabilir ve ihtiyaca göre versiyonlar arasında geçiş yapmamız gerekebilir. Örneğin versiyon yapımız şu şekilde olsun : 

version 1.0 --> version 2.0 --> version 3.0 

version 3.0 dan version 2.0 a geçerken version 2.0 ın kopyasını oluşturmuş olup projemizi o kopya üzerinden geliştirmeye devam ediyoruz. Böylelikle yeni versiyon yapımız şu şekilde olmuş oluyor : 

version 1.0 --> version 2.0 --> version 3.0 --> version 2.0-copy

Öncelikle yeni bir git projesi oluşturalım ve içerisine 3 tane dosya açalım. 
İlk versiyonumuza ait dosya içerisine bilgiler girelim. 

![N|project_ver1](https://i.im.ge/2022/08/31/OE0Moh.ver1.png)

Daha sonra değişikleri commit edelim ve **git log** ile versiyonlarımızı kontrol edelim. 

![N|project_ver2](https://i.im.ge/2022/08/31/OE0OOp.ver2.png)


**git log** komutu ile version 1.0 ı görmüş olduk. Şimdi 2 version daha alalım ve senaryomuzu gerçekleştirelim. 

![N|project_ver3](https://i.im.ge/2022/08/31/OE0wGS.ver-3.png)

**git log** komutunu kullanarak versiyonlarımızı kontrol edelim. 

![N|project_ver4](https://i.im.ge/2022/08/31/OE0Naz.ver-4.png)

Görüldüğü gibi artık 3 adet versiyonumuz var. Güncel versiyon en üstte ilk versiyon ise en altta yazmakta(yukarıda belirtilen versiyon hiyerarşisindeki gibi). 

Şimdi version 3.0 dan version 2.0 a geçelim. 

Versiyonlar arasında geçiş yapmak için **hash** bilgisini kullanıyoruz. **Sarı renkle yazılan commit yazısının yanındaki hash in ilk 7 hanesini** veya **hash in tamamını kullanarak** versiyonlar arası geçiş yapabiliriz : 

```sh
git checkout 02c603d7938e4256692f8f7b480e839dce1e31ea -- .
```

komutu ile version 2.0 a dönüyoruz ("." işareti versiyondaki tüm dosyaları getirmek için kullanılır).

Şimdi dosya içeriklerimizi tekrar kontrol edelim : 

![N|project_ver5](https://i.im.ge/2022/08/31/OE0pcm.ver-5.png)

Version 2.0 a geçiş yaptık : 

![N|project_ver5](https://i.im.ge/2022/08/31/OE0n7W.ver-6.png)

Görüldüğü gibi dosya içeriğimiz artık version 2.0 a dönmüş oldu. Bu şekilde projedeki versiyonlar arasında geçiş yapabiliriz.

#### 4.12 - Github'a Dosya Gönderme :
Sıra oluşturduğumuz projeleri github repositorymize göndermede. İlk önce github üzerinden yeni bir repository oluşturuyoruz. 

![N|project_gitrepo](https://i.im.ge/2022/08/31/OE5SSF.repo-olusturma.png)

Daha sonra repository bağlantı linkimizi alıyoruz : 

![N|project_gitrepolink](https://i.im.ge/2022/08/31/OE5708.githubrepolink.png)

Şimdi git ile github repository arasındaki bağlantıyı oluşturalım :

```sh
git remote add "gitlessRepo" https://github.com/p0zn/git-guide-repository.git
```
komutu ile bağlantıyı oluşturuyoruz. **remote add** dan sonra bağlantımızı isimlendiriyoruz. Ben burada "gitlessRepo" şeklinde isimlendirdim. Siz nasıl isterseniz o şekilde isimlendirebilirsiniz. 
> Not: Bu aşamada sizden github kullanıcı adı ve şifrenizi isteyebilir(daha önce yetkilendirme yapmadıysanız).

Bağlantının doğru kurulduğunu kontrol etmek için :

```sh
git remote 
```
komutunu yazıyoruz. Eğer bağlantıya verdiğimiz isim karşımıza çıkıyorsa bağlantı doğru kurulmuş demektir :) 

Şimdi sıra dosyalarımızı github repository e yüklemede : 

```sh
git push -u gitlessRepo master 
```

komutunu kullanarak dosyalarımızı github repository imize yüklüyoruz. "-u" parametresi tüm dosyalar anlamına gelmektedir. "-u" parametresinden sonra bağlantı ismimizi ve proje dalımızı yazıyoruz(**master anadaldır.** Dallara ileride değineceğiz).

![N|project_gitrepopush](https://i.im.ge/2022/08/31/OEtpgq.github-push-step.png)

Bu şekilde dosyalarımızı github repository imize yüklemiş oluyoruz. Dosya üzerinde herhangi bir değişiklik yapınca yeniden push etmeyi unutmuyoruz. 

#### 4.13 - .gitignore nedir? nasıl oluşturulur? :
##### 4.13.1 - .gitignore nedir? :
.gitignore git tarafından göz ardı edilmesi istenilen dosyalar için kullanılır. Örneğin projenize ait API Token bilgisi bulunan bir dosyayı herkese açık bir şekilde commit etmemek için .gitignore kullanılır. 

##### 4.13.2 - .gitignore nasıl oluşturulur? :
.gitignore dosyaları gizli dosyadır. .gitignore dosyası oluşturulurken başına "." koyulur. Nokta(.) koyulması sayesinde gizli dosya olur. 

bash terminal ile .gitignore dosyası oluşturalım : 

![N|project_gitig1](https://i.im.ge/2022/08/31/OEA0Uc.git-ignore2.png)

**ls** ile dosyalarımızı listelediğimiz zaman token.txt adlı bir dosyayı görüyoruz. Bu dosyanın git tarafından göz ardı edilmesini istiyorum. Öncelikle .gitignore dosyamızı oluşturuyoruz

```sh
cat >> .gitignore 
```
dosya içerisine girince **git tarafından göz ardı edilmesi istenilen dosyanın adı yazılır.** 

```sh
cat >> .gitignore 
token.txt
```

**CTRL + C** tuşuna basılarak dosya içerisinden çıkılır. 

daha sonra commit işlemleri gerçekleştirilir. 
Dosya üzerinde değişikilik yaptığımız için proje tekrar repository e push edilir. 

Şimdi github repository imizde token.txt dosyası gözüküyor mu kontrol edelim : 

![N|project_gitig2](https://i.im.ge/2022/08/31/OEAR1M.gitignore1.png)

Görüldüğü gibi diğer dosyalarımız gösterilirken token.txt dosyası gösterilmiyor. 

##### 4.13.3 - BONUS - .gitignore a nasıl klasör eklenir? :
Proje dosyaları içerisinde git tarafından göz ardı edilmesini istediğiniz dosyalarınızı bir klasörde topladınız. Ve bu klasörün gözükmesini istemiyorsunuz. .gitignore içerisine : 

```sh
klasör_adı/* 
```
şeklinde ekliyoruz. "*" parametresi bütün dosyalar anlamına gelmektedir. Böylelikle klasör içindeki tüm dosyalar git tarafından göz ardı edilecektir.
Eğer klasör içerisindeki bir veya birkaç dosyayı istisna tutmak istiyorsanız : 

```sh
!klasör_adı/dosya_adı 
```
şeklinde belirterek dosya veya dosyalarınızı istisna edebilirsiniz. 

#### 4.14 - Branchler :

Bir projede birden çok geliştirici bulunuyorsa ve her birinin kendine ait görevleri varsa kişilere veya görevlere göre branchler oluşturulur. 

Master anadaldır. Sonrasında alt dallar yapıya eklenir. Daha sonra alt dallar birleştirilerek proje son haliyle master da toplanır. 

##### 4.14.1 - Branch oluşturma :

Github repository veya bash shell üzerinden branch oluşturulur : 

![N|project_branchcreate](https://i.im.ge/2022/08/31/OECweq.branch-olusturma.png)

branch adı verilir ve "Create branch" butonuna basılarak branch oluşturulur. 

"Branches" sekmesinden branchler arasında geçiş yapılabilir. Dikkat ederseniz branchlerin her birinde dosyalar aynı olarak gözükecektir. 

Şimdi oluşturduğumuz subbranch in içerisine github üzerinden bir dosya ekleyelim ve commit edelim : 

![N|project_branchfilecreate](https://i.im.ge/2022/08/31/OEEqfm.sub-dosya-olusturma.png)

Şimdi subbranch üzerinde dosyamızı kontrol edelim : 

![N|project_branchfilecheck](https://i.im.ge/2022/08/31/OEEK3q.sub-uzerinde-dosya.png)

Gördüğünüz gibi oluşturduğumuz "file_4.txt" dosyası subbranch e eklenmiş. Peki bu dosya master dalında bulunuyor mu kontrol edelim : 

![N|project_branchfilecheckmaster](https://i.im.ge/2022/08/31/OEEkqP.masterda-sub-dosyasi-yok.png)

Gördüğünüz gibi master dalında dosyamız **yok**. Çünkü biz dosyamızı subbranch üzerinde oluşturduk. 

Şimdi branch leri birleştirelim : 

github repository > branches > All branches yoluna gidelim. 

![N|project_branchfilemerge1](https://i.im.ge/2022/08/31/OExTqG.branch-birlestirme.png)

subbranch imizin yanında bulunan "New pull request" butonuna tıklıyoruz. 

Ardından açılan sayfada branchlerimizin birleştirmeye uygun olduğunu gösteren "Able to merge" ifadesi ile karşılaşıyoruz. 

![N|project_branchfilemerge2](https://i.im.ge/2022/08/31/OExujy.merge1.png)

Yorum kısmına isterseniz açıklama yapabilirsiniz. 

Sayfanın en altında branchler arasındaki dosya farklılıklarını gösteren kısım bulunuyor. Bu kısımdan branchlerin birbiri üzerindeki dosya farklılığını görebilirsiniz : 

![N|project_branchfilemerge3](https://i.im.ge/2022/08/31/OEx1Tz.merge2.png)

Daha sonra **"Create pull request"** butonuna tıklıyoruz. 

Tartışma sayfasına yönlendiriliyoruz. Bu sayfa üzerinden kendi geliştirici ekibinizle veya diğer geliştiricler ile proje hakkında soru cevap , tartışma öneri vb. faaliyetleri gerçekleştirebilirsiniz. 

Branchleri birleştirmek için artık son adıma geldik : 
**"Merge pull request"** butonuna tıklıyoruz : 

![N|project_branchfilemerge4](https://i.im.ge/2022/08/31/OExLmM.issue-page-marge.png)

Ve artık dallarımız master dalında birleştirilmiş oldu. 

Şimdi "Working Directory" üzerindeki dosyalarımıza bakalım : 

![N|project_branchfilemerge5](https://i.im.ge/2022/08/31/OExtmm.workmer1.png)

Subbranch üzerindeki dosyamız bu dizinde yok. 

Yapmamız gereken tek şey : 

```sh
git pull
```

komutunu yazarak github üzerindeki dosyaları çekmek. Şimdi tekrar kontrol edelim : 

![N|project_branchfilemerge6](https://i.im.ge/2022/08/31/OExyZr.pulll.png)

Dosyalarımızı çektik. Şimdi "Working Directory" i kontrol edelim : 

![N|project_branchfilemerge7](https://i.im.ge/2022/08/31/OExxbT.workiing-merge-pulled.png)

Ve subbranch üzerindeki dosyamızda "Working Directory" üzerine eklendi. Böylelikle branchleri birleştirmeyi görmüş olduk. 

##### 4.14.2 - BONUS - Komut İle Branch Birleştirme :

Oluşturduğumuz branchleri komut ile birleştirmek için öncelikle : 

```sh
git branch --all
```
komutu ile repository üzerindeki branchleri listeliyoruz. 

Bu örnek için yeni bir subbranch oluşturuyorum : 

```sh
git branch subbranch_2
```

tekrar branchleri listelemek için 

```sh
git branch 
```
komutunu yazıyoruz. 

Şimdi master dalından oluşturduğumuz alt dala geçiş yapalım : 

```sh
git checkout subbranch_2
```
komutu ile oluşturduğumuz subbranch e geçiş yapıyoruz. 

Proje dizini içersinde yeni bir dosya oluşturuyoruz.
Daha sonra değişiklikleri commit ediyoruz. 

Branchleri birleştirmek için öncelike master dalına geçiş yapıyoruz : 

```sh
git checkout master
```

Daha sonra branchleri birleştirmek için : 

```sh
 git merge subbranch_2
```

komutunu yazıyoruz ve branchleri birleştiriyoruz. 

Son adımda github a tekrar push ederek birleştirme işlemini tamamlıyoruz. 

Hazırlayan : **Furkan ÖZKAN**






