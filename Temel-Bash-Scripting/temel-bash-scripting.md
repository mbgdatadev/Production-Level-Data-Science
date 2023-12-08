# Temel Bash Scrippting
# İçindekiler
- [Temel Bash Scrippting](#temel-bash-scrippting)
- [Kullanici Girdi Alma](#kullanici-girdi-alma)
- [if else Kullanimi](#if-else-kullanimi)
- [Koşul Operatorleri](#koşul-operatorleri)
- [Argumanlar](#argumanlar)
- [Fonksiyonlar](#fonksiyonlar)


***
  
## Temel Bash Scrippting
Linux'ta Bash Scripting, Bash adlı kabuk (shell) programlama dilini kullanarak otomatik görevler oluşturmayı sağlar. Bir betik (script) dosyası oluşturarak komutları bir araya getirebilir ve ardışık işlemler gerçekleştirebilirsin.

Örneğin, bir dizindeki belirli türdeki dosyaların listesini almak için basit bir Bash scripti şöyle olabilir:
```bash
#!/bin/bash

# Scriptin çalıştığı dizini belirtelim
working_dir="/home/kullanici/misal_dizin"

# Belirli türdeki dosyaların listesini alalım
echo "Belirli türdeki dosyalar:"
ls ${working_dir}/*.txt
```
Bu script, `misal_dizin` adlı dizindeki `.txt` uzantılı dosyaların listesini terminalde gösterir. Betik dosyası `.sh` uzantılı olarak kaydedilip çalıştırılabilir hale getirilmelidir (`chmod +x script_adi.sh ile çalıştırılabilir izin verilebilir`).

Tabii ki, bu sadece basit bir örnek. Bash, dosya işleme, döngüler, koşullar, fonksiyonlar gibi birçok yapıyı destekler ve karmaşık görevleri gerçekleştirmek için kullanılabilir. Bu sayede sistem yönetimi, dosya işleme ve otomatikleştirme gibi birçok alanda kullanılabilir.
***
## Kullanici Girdi Alma

Kullanıcıdan girdi alma işlemi Bash scriptleriyle oldukça kolay. read komutu kullanıcıdan girdi almayı sağlar. 
İşte basit bir örnek:
```bash
#!/bin/bash

# Kullanıcıdan ismini alma
echo "İsminizi girin: "
read isim

# Alınan ismi ekrana yazdırma
echo "Merhaba, $isim! Hoş geldiniz."
```
Bu script, kullanıcıya ismini girmesi için bir istekte bulunur ve girilen ismi ekrana yazdırır.

`read` komutu kullanıcının girdisini bir değişkene atar.
***
## if else Kullanimi
if, programlama dillerinde kullanılan bir kontrol yapısal ifadedir. Genellikle belirli bir koşulun doğrulanıp doğrulanmadığını kontrol etmek ve buna göre farklı işlemleri yapmak için kullanılır.

Bir programın akışını yönlendirmek için kullanılır: Eğer belirtilen koşul doğruysa (true), belirli bir kod bloğu çalıştırılır; aksi halde (false), farklı bir kod bloğu veya alternatif bir işlem çalıştırılır.
Eğer birden fazla girdi almak istiyorsanız, `read` komutunu sırasıyla kullanabilirsiniz.

Girdileri kontrol etmek ve doğrulamak için koşullar kullanılabilir. 
Örneğin:
```bash
#!/bin/bash

# Kullanıcıdan yaş bilgisini alma
echo "Yaşınızı girin: "
read yas

# Yaşın kontrolü
if [ $yas -ge 65 ]; then
    echo "Emekli yaşınızı geçmişsiniz."
elif [ $yas -ge 18 ]; then
    echo "Ehliyet alma yaşınızı geçmişsiniz."
else
    echo "Ehliyet alma yaşınıza gelmediniz."
fi

```
- `#!/bin/bash`: Betiğin kullanılacak kabuğu (shell) belirtir. Burada, bu betiğin Bash kabuğunda çalışacağını gösterir.

- `echo "Yaşınızı girin: "`: Kullanıcıya yaşını girmesi için bir metin mesajı gösterir.

- `read yas`: Kullanıcının girdiği yaş bilgisini `yas` adlı bir değişkene atar. `read` komutuyla kullanıcı girdisi alınır ve bu değer belirtilen değişkene atanır.
- `if [ $yas -ge 65 ]; then`: Bu satırda, girilen yaşın 65 veya daha büyük olup olmadığını kontrol etmek için bir koşul başlatılır. `-ge`, "greater than or equal to" anlamına gelir.

- `elif [ $yas -ge 18 ]; then`: Bu satırda, girilen yaşın 18 veya daha büyük olup olmadığını kontrol etmek için bir koşul başlatılır. `-ge`, "greater than or equal to" anlamına gelir.

- `echo "Ehliyet alma yaşınızı geçmişsiniz."`: Eğer kullanıcının girdiği yaş 18 veya daha büyükse, bu mesajı ekrana yazdırır.

- `else`: Eğer koşul sağlanmazsa, yani yaş 18'den küçükse, bu bloğa geçilir.

- `echo "Ehliyet alma yaşınıza gelmediniz."`: Yaşın 18'den küçük olduğu durumda bu mesajı ekrana yazdırır.

- `fi`: Koşulun sonunu belirtir. `if` yapısının sona erdiğini ifade eder.

Bu script, kullanıcının yaşını girmesini bekler, ardından bu yaşa göre bir mesaj görüntüler: Eğer yaş 18 veya daha büyükse "Ehliyet alma yaşınızı geçmişsiniz." mesajını, değilse "Ehliyet alma yaşınıza gelmediniz." mesajını gösterir. Markdown içinde bu şekilde daha anlaşılır olabilir.

***

## Koşul Operatorleri

Elsif yapısı ile koşul operatörleri && ve || çok kullanışlıdır. Bunlar, belirli koşulları birleştirmek ve birden fazla koşulun sağlanıp sağlanmadığını kontrol etmek için kullanılır.

- `&&` (ve operatörü): Bu operatör, sol ve sağ tarafındaki koşulların her ikisinin de doğru olduğu durumda ifadeyi doğru yapar. Eğer sol tarafın koşulu yanlışsa, sağ tarafı kontrol etmeye gerek duymaz çünkü her ikisinin de doğru olması gerekir. 

  Örnek:
   ```bash
   if [ $yas -ge 18 ] && [ $cinsiyet == "erkek" ]; then
       echo "Ehliyet alabilirsiniz ve erkeksiniz."
   else
     echo "Ehliyet alamazsınız veya cinsiyet belirsiz."
    fi
   ```
- `||` (veya operatörü): Bu operatör, sol veya sağ tarafındaki koşullardan en az birinin doğru olduğu durumda ifadeyi doğru yapar. Sol taraf doğruysa, sağ tarafı kontrol etmeye gerek yoktur çünkü en az birinin doğru olması yeterlidir.

  
  Örnek:
   ```bash
   if [ $renk == "mavi" ] || [ $renk == "yeşil" ]; then
    echo "Renk mavi veya yeşil."
   else
     echo "Başka bir renk."
   fi

   ```
   Bu örnekte, renk "mavi" veya "yeşil"se bir mesaj yazdırılır.

   Bu operatörler, koşulların birleştirilmesiyle birlikte daha karmaşık kontroller sağlar ve çeşitli durumların kontrol edilmesini mümkün kılar.

Linux terminalinde bu operatörleri kullanabilirsiniz. Bash veya başka bir kabuk (shell) kullanıyorsanız, koşulları kontrol etmek için bu operatörleri kullanabilirsiniz.

Örnek olarak, terminalde şu şekilde kullanabilirsiniz:  

  ```bash
# && operatörü kullanımı
[ 10 -gt 5 ] && echo "10, 5'ten büyük."
# Bu ifade, 10 sayısının 5'ten büyük olduğunu kontrol eder ve doğruysa "10, 5'ten büyük." mesajını gösterir.

# || operatörü kullanımı
[ 10 -lt 5 ] || echo "10, 5'ten küçük değil."
# Bu ifade, 10 sayısının 5'ten küçük olmadığını kontrol eder ve yanlışsa "10, 5'ten küçük değil." mesajını gösterir.
   ```
***

## Argumanlar

Bash scriptlerinde argümanlar, betiğin çalıştırıldığı komut satırından alınan değerlerdir. 
Bu argümanlar, scriptin çalıştırılması sırasında sağlanır ve betiğin farklı davranışlar sergilemesini veya dinamik olarak işlem yapmasını sağlar.
Argümanlar, scriptin adından sonra boşluklarla ayrılarak yazılır ve scriptin içinde kullanılabilir. 
Örnek olarak, bir betik dosyasını çalıştırırken argümanları şu şekilde verebilirsiniz:
```bash
./script_adi.sh arguman1 arguman2 arguman3
```
Script içinde, argümanlar şu şekilde kullanılabilir:

```bash
#!/bin/bash

echo "Birinci argüman: $1" # $1, ilk argümanı temsil eder
echo "İkinci argüman: $2" # $2, ikinci argümanı temsil eder
echo "Üçüncü argüman: $3" # $3, üçüncü argümanı temsil eder
# ...

echo "Toplam argüman sayısı: $#" # $# ile toplam argüman sayısını alabilirsiniz
echo "Tüm argümanlar: $@" # $@ ile tüm argümanları bir dizi olarak alabilirsiniz
```

Bu örnekte, `$1`, `$2`, `$3` gibi özel değişkenlerle argümanlara erişebilirsiniz. Ayrıca `$#` ile toplam argüman sayısını ve `$@` ile tüm argümanları dizi olarak alabilirsiniz.

Örneğin, `./script_adi.sh 10 20 30` şeklinde bir komut çalıştırırsanız, script bu argümanları kullanarak çalışacaktır. `echo "Birinci argüman: $1"` ifadesi, `10` değerini, `echo "İkinci argüman: $2"` ifadesi `20` 
değerini ve `echo "Üçüncü argüman: $3"` ifadesi `30` değerini yazdıracaktır.


## Donguler

- `for` ve `while` döngüleri, Bash scriptlerinde tekrarlayan işlemler yapmak için kullanılan yapısal ifadelerdir.
  `for` döngüsü, belirli bir listedeki her öğe için işlem yapmak için kullanılır. 
   Örneğin:
   ```bash
    #!/bin/bash

    # Bir dizi içinde dolaşarak her elemanı yazdıralım
    for item in 1 2 3 4 5
    do
        echo "Eleman: $item"
    done
    ```
- `while`  döngüsü, belirli bir koşul doğru olduğu sürece işlem yapmaya devam eder. 
   Örneğin:
   ```bash
     #!/bin/bash

     # 1'den 5'e kadar olan sayıları yazdıralım
     counter=1
     while [ $counter -le 5 ]
     do
        echo "Sayı: $counter"
        ((counter++))  # counter değişkenini artırma
     done
    ```
   Bu örnek, 1'den 5'e kadar olan sayıları ekrana yazdırmak için bir while döngüsü kullanır. counter değişkeni 1'den başlar ve her döngüde 1 artar. Döngü, counter değeri 5 olduğunda sona erer çünkü -le (less than or equal to) koşulunu kontrol eder.

***
## Fonksiyonlar
Fonksiyonlar, belirli bir görevi yerine getirmek için gruplanmış kod bloklarıdır. Bash'te fonksiyonlar, tekrar eden işlemleri gruplamak ve daha düzenli, modüler bir kod oluşturmak için kullanılır.

Örnek bir fonksiyon:
   ```bash
    #!/bin/bash

    # Fonksiyon tanımlama
    hello() {
      echo "Merhaba! Bu bir fonksiyon."
    }

    # Fonksiyonu çağırma
    hello
   ```

Bu basit örnekte, hello adında bir fonksiyon tanımlıyoruz. hello() ifadesi fonksiyonun başlangıcını belirtir. İçinde sadece echo komutu var, bu yüzden çalıştırıldığında "Merhaba! Bu bir fonksiyon." metnini yazdıracaktır.

Fonksiyonlar, aynı kodu birden fazla kez kullanmanız gerektiğinde veya kodu daha modüler hale getirmek istediğinizde özellikle kullanışlıdır. Örneğin, belirli bir işlemi farklı parametrelerle tekrar tekrar gerçekleştirmek istediğinizde fonksiyonlar oldukça kullanışlı olabilir. Bu sayede kodunuz daha okunabilir, daha az tekrar eden ve daha yönetilebilir olur.

Örnek:
   ```bash
#!/bin/bash

# Virgül ile ayrılmış parametreleri alan bir fonksiyon
hello_comma() {
    local param1=$1
    local param2=$2

    echo "Hello, $param1 and $param2!"
}

# Fonksiyonu çağırma ve parametreleri verme
hello_comma "Alice" "Bob"

   ```

















