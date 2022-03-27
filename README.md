# ElasticSearch-Go


# Golang Elasticsearch Example MacOS
golang kullanarak elasticsearch ile basit bir örnek yapacağız ilk olarak elasticsearch' ü tanıyalım.
Elasticsearch ; text üzerinden doğrudan arama yapmak yerine, indexler üzerinden arama yaparak çok hızlı bir şekilde sonuçlar üretir.
ElasticSearch Avantajları Nelerdir?
Dağıtık ve yüksek ölçeklenebilir yapıda çalışabilir.
Açık kaynaklıdır.
RestfullAPI desteği vardır.
Gerçeğe yakın zamanlıdır. Bu sayede, veriler kaydedildikten saniyeler sonra SearchElastic ile yapılan aramalarda bulunabilirler.
Kolay bir şekilde yedekleme yapılabilir.
Alternatiflerine göre çok az kaynak kullanarak çalışır.
İndeksleme yaptığı için, arama sonuçlarını hızlı bir şekilde verir.
Dokümanları JSON olarak indekslediğinden, birçok programlama dilini destekler.
Veri tipine uygun olarak mapping yapabilir.
Hızlı ve kolay kurulum imkanına sahiptir.
MongoDB, NoSQL, Cassandra ve HBase gibi veri tabanlarından ElasticSearch'e veri aktarımına izin verir.
Otomatik tamamlama özelliği vardır.

# ElasticSearch Nasıl Çalışır?
ElasticSearch'e herhangi bir veri kaydedilirken, veri içerisinde daha önceden belirlenen alanlar indekslenir. ElasticSearch, bu işlemi veri kaydının ilk anında gerçekleştirdiği ve verileri indeks listesine göre sınıflandırdığı için, arama sonuçlarına hızlıca ulaşabilir.
ElasticSearch Temel Kavramları Nelerdir?
Indice: Klasik arama motorlarında veri tabanları üzerinden arama gerçekleştirilirken, ElasticSearch aramaları "Indice" olarak adlandırılan indeks dosyaları üzerinden gerçekleştirilir. ElasticSearch Clusterlarında birden fazla veri tabanı (Indice) bulunabilir.
Type: İlişkisel veri tabanlarındaki tablolardır ve verileri mantıksal bölümlere ayırır. ElasticSearch, aynı indeks içerisinde birden fazla Type barındırabilir.
Document: ElasticSearch içerisindeki Type yapılarında yer alan satırları temsil eder ve Type'ler bu yapılardan oluşur.
Mapping: İndekslenen verilerin hangi veri tipinde olduğunun tanımlandığı işlemdir.
Field: Diğer veri tabanı türlerindeki Column (Sütun) ElasticSearch'te Field (Alan) olarak adlandırılır. Her bir Document birden fazla Field (Alan) barındırabilir.
Cluster: Bir veya daha fazla düğümün toplamıdır. Cluster sayesinde tüm verileri içeren indeks oluşturma ve arama kabiliyetleri oluşur.

# İşlemler:
# 1- HomeBrew Kurulumu.
HomeBrew kurulumu için https://brew.sh/index_tr kaynağınız inceleyebilirsiniz.
# 2- ElasticSearch Kurulum.(MacOs-M1)
HomeBrew kurulu ise terminali açıyoruz ve aşşağıdaki kodları sırasıyla çalıştırıyoruz. MacOS sürümleri arasında da elasticsearch kurulum komutları değişiklik göstermektedir standart "brew install ElasticSearch" komutu çalışmamaktadır. aşağıda ki komutlarda ilk olarak elasticsearch yüklüyoruz ve son iki satır da ise ayağa kaldırıyoruz.
brew tap elastic/tap
brew install elastic/tap/elasticsearch-full
brew services start elastic/tap/elasticsearch-full
elasticsearch

# 3- Golang Code.

package main

import (

"log"

"github.com/elastic/go-elasticsearch/v7"

)

func main() {

cfg := elasticsearch.Config{

Addresses: []string{

"http://localhost:9200",

},

}
es, _ := elasticsearch.NewClient(cfg)

log.Println(es.Info())

}

kod içeriğince elasticsearch 3. sınfı kütüphanesini import ediyoruz. elasticsearch.Config içeriğine okunacak adresimizi tanımlıyoruz elasticsearch 9200 portunda çalışmaktadır. Config içeriğinde tls sertifika, Username, Password, Transport vb. işlemleride yapılmaktadır ama bu örneğimizde gerekmediği için kullanılmamıştır. sonrasında ise elasticsearch standart okunan json formatını okuyoruz.
elasticsearch' ü kapatmak için ise "brew services stop elastic/tap/elasticsearch-full" komutunu terminalde çalıştırmanız yeterlidir.

![image](https://user-images.githubusercontent.com/92402372/160298950-16d2c4b5-cf3f-413d-9bab-78c3c5a99c63.png)
![image](https://user-images.githubusercontent.com/92402372/160298960-8121a5de-e119-4c09-b375-caf10d00fb19.png)
![image](https://user-images.githubusercontent.com/92402372/160298964-c2eae2a7-fa9d-4ece-b708-c0b5c4729a82.png)



)
