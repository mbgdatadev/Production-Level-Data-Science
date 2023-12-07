# Docker

- [Docker Nedir](#docker-nedir)
- [Sanallastirma ve Konteynerleme Arasindaki Farklar](#sanallastirma-ve-konteynerleme-arasindaki-farklar)
- [Docker Komut Satiri](#docker-komut-satiri)


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
