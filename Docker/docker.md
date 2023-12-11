# Docker

- [Docker Nedir](#docker-nedir)
- [Sanallastirma ve Konteynerleme Arasindaki Farklar](#sanallastirma-ve-konteynerleme-arasindaki-farklar)
- [Docker Komut Satiri](#docker-komut-satiri)
- [Docker run stop remove](#docker-run-stop-remove)
- [Konteyneri Baglanmak](#konteyneri-baglanmak)
- [Konteyner Log](#konteyner-log)  


## Docker Nedir?

Docker, yazılım uygulamalarını geliştirmek, dağıtmak ve çalıştırmak için kullanılan bir platformdur. Bu platform, uygulamaları konteynerlara paketleyerek çalışma ortamlarını standartlaştırır. 

### Ne İşe Yarar?

- **Hızlı Dağıtım:** Konteynerler, uygulamaları hızlı bir şekilde başlatmanıza, durdurmanıza ve dağıtmanıza olanak tanır.
- **Çeviklik:** İhtiyaç duyulan yazılım ve araçların hızlıca oluşturulmasını ve çalıştırılmasını sağlar.
- **Çalışma Ortamı İzolasyonu:** Her uygulama veya hizmet için ayrı bir konteyner oluşturarak izolasyonu sağlar.
- **Taşınabilirlik:** Uygulamaları farklı ortamlarda (lokalden buluta) sorunsuzca taşımanıza imkan verir.
***
## Sanallaştırma ve Konteynerleme Arasındaki Farklar

### Sanallaştırma (Virtualization)

- **Hypervisor Kullanımı:** Sanallaştırma, bir fiziksel sunucunun üzerine bir veya birden fazla sanal makine (VM) oluşturarak çalışır. Her bir VM, kendi işletim sistemini barındıran ve bağımsız bir ortam sağlayan bir hypervisor kullanır.
- **Kaynak Yoğunluğu:** VM'ler, işletim sistemlerini ve uygulamalarını ayrı ayrı çalıştırdıkları için daha fazla kaynak gerektirirler. Her biri tam bir işletim sistemini barındırır.
- **Bağımsızlık:** Her bir sanal makine, kendine özgü bir işletim sistemine ve uygulamalarına sahiptir, bu da daha fazla depolama ve işlem gücü gerektirir.

### Konteynerleme (Containerization)

- **Ortak Çekirdek:** Konteynerleme, bir işletim sistemi çekirdeği üzerinde çalışan ve kaynakları paylaşan hafif konteynerlerden oluşur. Bu konteynerler, uygulama ve bağımlılıklarını bir araya getirir.
- **Kaynak Verimliliği:** Konteynerler, ortak bir işletim sistemi çekirdeğini paylaştıkları için daha az kaynak tüketirler. Her biri sadece uygulama ve gerekli bağımlılıkları içerir.
- **Hızlı Başlatma:** Konteynerler, hızlı bir şekilde başlatılıp durdurulabilirler. Bunlar, hızlı dağıtım ve ölçeklendirme için idealdir.

Konteynerleme, kaynak verimliliği ve hız açısından sanallaştırmaya göre daha avantajlı olabilir. Hangi teknolojiyi kullanmanız gerektiğine karar verirken ihtiyaçlarınızı ve gereksinimlerinizi göz önünde bulundurmalısınız.
***
## Docker Komut Satırı

Docker'ı kullanırken, sıkça kullanılan bazı komutlar şunlardır:

### Konteynerler

- **Konteynerleri Listeleme:** `docker ps` veya `docker container ls`
- **Tüm Konteynerleri Listeleme:** `docker ps -a` veya `docker container ls -a`
- **Konteyner Oluşturma:** `docker create <image>`
- **Konteyneri Başlatma:** `docker start <container_id>`
- **Konteyneri Duraklatma:** `docker pause <container_id>`
- **Konteyneri Kaldırma:** `docker rm <container_id>`
- **Konteyner Loglarını Görüntüleme:** `docker logs <container_id>`
- **Konteyner İçine Giriş Yapma:** `docker exec -it <container_id> <komut>`

### Görüntüler (Images)

- **Görüntüleri Listeleme:** `docker images` veya `docker image ls`
- **Görüntü İndirme:** `docker pull <image_name>`
- **Yerel Görüntü Oluşturma:** `docker build -t <image_name> <dockerfile_path>`
- **Görüntüyü Kaldırma:** `docker rmi <image_name>`

### Diğer

- **Docker Sürümünü Görüntüleme:** `docker --version` veya `docker -v`
- **Yardım ve Komut Bilgisi:** `docker help` veya `docker <komut> --help`

***

# Docker run stop remove

### Konteyneri Çalıştırmak:
```bash
docker start <konteyner_adı veya ID>
```

### Konteyneri Durdurmak:
```bash
docker stop <konteyner_adı veya ID>
```

### Konteyneri Silmek:
```bash
docker rm <konteyner_adı veya ID>
```
***
## Konteyneri Baglanmak
Konteynerlere bağlanma, Docker'da çalışan bir konteynerin içine girerek, içerideki işlemleri yönetme veya kontrol etme işlemidir. Genellikle bu, komut satırı aracılığıyla yapılır.

Bir Docker konteynerine bağlanmak için docker exec komutunu kullanabilirsiniz. Örneğin, PostgreSQL konteynerine bağlanmak istediğinizi varsayalım:

### PostgreSQL Konteynerine Bağlanma:
```bash
docker exec -it my-postgres bash
```
- `-it` parametresi, etkileşimli bir terminal oturumu başlatır.
- `my-postgres` yerine kendi PostgreSQL konteynerinizin adını veya ID'sini kullanmalısınız.
  Bu komut, PostgreSQL konteynerine bir bash oturumu başlatacaktır. Eğer PostgreSQL yerine başka bir servis veya işletim sistemi çalıştırıyorsanız, kullanmanız 
  gereken komut biraz farklılık gösterebilir. Örneğin, Ubuntu tabanlı bir konteynerde çalışıyorsanız, `bash` yerine `sh` kullanabilirsiniz.
***

## Konteyner Log
Konteyner logları, Docker konteynerlerinin çalışması sırasında oluşan çeşitli olayların kaydını tutar. Bu loglar, konteynerin çalışma durumu, hata mesajları, uygulama çıktıları ve daha fazlasını içerebilir. Loglar, konteynerin durumunu anlamak, hata ayıklama yapmak veya performans analizi gibi amaçlarla kullanılabilir.

Docker loglarını görmek için `docker logs` komutunu kullanabilirsiniz. Örneğin, belirli bir konteynerin loglarını görmek için:

### Konteyner Loglarını Görüntüleme:
```bash
docker exec -it my-postgres bash
```
Bu komut, belirtilen konteynerin loglarını terminalinizde görüntüler.
***
## Docker Volume
Docker Volume'ü, Docker konteynerleri içinde veri saklamak veya veri paylaşımı sağlamak için kullanılan bir yapıdır. Bu yapı, konteynerler arasında veri paylaşımını kolaylaştırırken veri saklama ve veri kaybını önleme konusunda da yardımcı olur.

Docker Volume'leri, konteynerlerin dosya sistemleri dışında depolama alanları olarak düşünebiliriz. Özellikle, konteynerler silinse veya yeniden oluşturulsa bile bu volume'lerin içeriği korunur.

Volume'ler, `docker volume create` komutu veya bir konteyner oluştururken `-v` veya `--volume` flag'ini kullanarak oluşturulabilir. Örneğin:

### Docker Volume Oluşturma:
```bash
docker volume create my_volume

```

### Konteyner Oluştururken Volume Kullanımı:
```bash
docker run -d --name my_container -v my_volume:/path/in/container my_image
```
Burada `my_volume` adında bir Docker Volume oluşturuyoruz. Ardından, `my_container` adında bir konteyner oluştururken bu volume'ü kullanıyoruz. `-v my_volume:/path/in/container` komutu, `my_volume` adlı Docker Volume'ün `my_container` içindeki belirli bir yol ile eşleştirilmesini sağlar.













