# Crontab

`crontab`,linux benzeri işletim sistemlerinde belirli aralıklarla tekrarlanan görevlerin zamanlanmasını sağlayan bir komuttur. `cron` adı verilen zamanlanmış görevlerin listesini tutar.

Bir kullanıcının cron görevlerini oluşturmasına, düzenlemesine veya silebilmesine izin veren crontab komutu, kullanıcının belirli aralıklarla çalıştırmak istediği komutları, betikleri veya programları belirlemesine olanak tanır.

crontab komutu genellikle bir metin düzenleyicisiyle çağrılır ve bu dosyada zamanlanmış görevler belirtilir. Her satırda, görevin çalışma zamanı, komut veya betik dosyasının adı gibi bilgiler yer alır.

Örneğin, `crontab -e` komutuyla bir kullanıcının cron görevlerini düzenleyebilir ve yeni görevler ekleyebilirsiniz. Bu görevler, belirli bir zamanda veya belirli aralıklarla çalıştırılmak üzere zamanlanabilir. Bu şekilde, tekrar eden işlemler otomatik olarak ve zamanında gerçekleştirilebilir.

crontab dosyası, bir metin düzenleyicisi kullanılarak veya terminalde doğrudan komutlarla oluşturulabilir. Bu dosya, kullanıcıya özeldir ve kullanıcının zamanlanmış görevlerini içerir.

Yeni bir crontab dosyası oluşturmak için terminale şu komutu yazabilirsiniz:

Örnek:
```bash
crontab -e
```
Bu komut vi editörü açar ve içine istediğiniz görevi koyabililrsiniz
Örnek:
```bash
30 18 * * * /bin/bash /home/kullanici/backup.sh

```
Bu satırın anlamı şudur:
- `30 18`: Betiğin saat 18:30'da çalıştırılacağını belirtir.
- `* * *`: Her gün, her ay ve her günün herhangi bir saatinde çalıştırılacağını belirtir.
- `/bin/bash /home/kullanici/backup.sh`: Çalıştırılacak komut veya betiği ifade eder.
Bu örnek, her günün saat 18:30'unda backup.sh adlı betiği /home/kullanici/ dizininde çalıştıracaktır. cron görevleri, bu şekilde belirtilen zamanlamalara göre otomatik olarak çalıştırılacaktır.

















