# Argocd-install
Argo CD, Kubernetes ortamları için kullanılan bir GitOps Continuous Deployment aracıdır. Argo CD, GitOps’un temel yapıtaşı olan Single Source of Truth modelini referans alan bir mimariye sahiptir. Kubernetes tanım dosyalarını birçok farklı yöntemle yazabilir ve bu Kubernetes objelerini Argo CD aracılığıyla Kubernetes ortamlarına deploy edebiliriz. 

Argo CD belirli periyotlarda Kubernetes’e deploy edilmiş uygulamaları izler ve Git reposunda yer alan tanım dosyalarıyla karşılaştırmalar yapar. Herhangi bir farklılık durumunu kullanıcıyı bildirir veya istenilirse otomatik olarak senkronizasyon işlemini gerçekleştirir.
Argo CD'nin temel özellikleri:

# 1-GitOps Yaklaşımı:
Argo CD, GitOps prensiplerine dayanır. Bu prensiplere göre, uygulama durumu ve konfigürasyonu bir Git deposunda saklanır. Bu, uygulama durumu ve konfigürasyonunun kod gibi yönetilmesine ve takip edilmesine olanak tanır.
# 2-Sürekli Dağıtım:
Argo CD, Kubernetes üzerinde çalışan uygulamaların sürekli dağıtımını sağlar. Yeni sürümler, değişiklikler veya konfigürasyon güncellemeleri, Git deposundaki değişikliklere dayanarak otomatik olarak uygulanabilir.
# 3-Değişiklik İzleme ve Geri Alabilme:
Argo CD, yapılan değişiklikleri izler ve bu değişikliklere dayalı olarak uygulama durumunu günceller. Ayrıca, yapılan değişiklikleri geri alabilme yeteneği sunar.
# 4-Deklaratif Uygulama Tanımı:
Uygulama durumu ve konfigürasyonu, YAML tabanlı deklaratif dosyalar aracılığıyla tanımlanır. Bu dosyalar, uygulama, servis ve diğer kaynaklarını belirtir.
# 5-Çok Ortam Desteği:
Argo CD, farklı ortamlarda (örneğin, geliştirme, test, üretim) uygulama dağıtımını destekler. Her ortam için ayrı bir konfigürasyon tanımlanabilir.
# 6-Özelleştirilebilir Uygulama Durumu Kontrolü:
Argo CD, uygulama durumu kontrol sürecini özelleştirmek ve gerektiğinde özel kontrol noktaları eklemek için geniş bir esneklik sağlar.
# 7-Web Tabanlı Kullanıcı Arayüzü:
Argo CD, kullanıcılar için kullanımı kolay bir web tabanlı arayüz sağlar. Bu arayüz, uygulama durumu, geçmiş değişiklikler ve uygulamalar arasında geçiş yapma yeteneği sunar.
# 8-Açık Kaynak ve Geniş Ekosistem Desteği:
Argo CD, açık kaynak bir projedir ve Kubernetes ekosistemiyle uyumlu bir şekilde çalışır. Ayrıca, bir dizi eklenti ve entegrasyon sunan geniş bir ekosistemle birlikte gelir.

Argo CD, özellikle Kubernetes üzerinde çalışan mikro servis tabanlı uygulamalar gibi karmaşık uygulamaları yönetmek için kullanılır. GitOps yaklaşımını benimsemesi, sürekli dağıtım süreçlerini daha şeffaf ve tekrarlanabilir hale getirir.

![image](https://github.com/fuat-tirtar/argocd-install/assets/58062840/9ceaae96-8750-4f4d-b975-c562dfd1ad27)

# Argo CD Kurulumu
# Helm Reposunun Eklenmesi

helm repo add argo-cd https://argoproj.github.io/argo-helm <br>                                             
<br> helm repo update <br>
kubectl create namespace argocd <br>
helm install argocd argo-cd/argo-cd -n argocd <br>
kubectl get svc -n argocd argocd-server <br>
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d <br>
kubectl port-forward svc/argocd-server -n argocd 8080:443 <br>

