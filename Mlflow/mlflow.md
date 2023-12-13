# Mlflow
MLflow, makine öğrenimi projelerini kolayca yönetmeyi amaçlayan açık kaynaklı bir platformdur. Üç ana bileşeni vardır:

- **MLflow Tracking:** Makine öğrenimi deneylerini, parametreleri, kodu ve sonuçları izlemenize olanak sağlar. Bu sayede deneyleri karşılaştırabilir ve tekrar üretebilirsiniz.

- **MLflow Projects:** Proje bazlı bir çalışma ortamı sunar. Kod, bağımlılıklar ve çevrelerin kolayca paketlenmesini, paylaşılmasını ve yeniden kullanılmasını sağlar.

- **MLflow Models:** Modellerin yönetimi, takibi ve yeniden kullanılabilirliğini sağlar. Modelleri standart bir formatta paketleyip kataloglayabilir, birçok çerçevede (framework) veya platformda çalıştırabilirsiniz.
***

MLflow Tracking Sunucusunu başlatmak için aşağıdaki komutu kullanabilirsiniz:

```bash
mlflow server --backend-store-uri postgresql+psycopg2://train:sifre@localhost:5432/mlflow --default-artifact-root hdfs://localhost:9000/user/train/mlflow --host 0.0.0.0
```
Bu komut, MLflow sunucusunu belirli yapılandırmalarla başlatmayı amaçlar:

- **--backend-store-uri**: MLflow sunucusunun kullanacağı depolama sisteminin URI'sini belirtir. Bu örnekte PostgreSQL veritabanı kullanılmıştır (`postgresql+psycopg2://train:sifre@localhost:5432/mlflow`).

- **--default-artifact-root**: MLflow tarafından oluşturulan sanal ortamın (artifact) yerini belirtir. Bu durumda `hdfs://localhost:9000/user/train/mlflow` HDFS üzerindeki yoludur.

- **--host**: MLflow sunucusunun hangi IP adresi üzerinden dinleme yapacağını belirtir. `0.0.0.0` herhangi bir gelen bağlantıyı kabul etmek için tüm ağ arayüzlerini kullanır.
