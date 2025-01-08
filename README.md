 # 🖥️ Jenkins Project
<br><br>
Bu proje, **Jenkins** kullanarak test otomasyonu süreçlerini kurmak ve yönetmek için hazırlanmıştır.  
Jenkins, CI/CD (Continuous Integration/Continuous Deployment) süreçlerini kolaylaştıran bir otomasyon sunucusudur.  
Bu proje, testlerin otomatik olarak çalıştırılması ve raporlanması için Jenkins'in nasıl yapılandırıldığını ve kullanıldığını göstermektedir.  
<br><br>

## ✨ Proje Özellikleri
<br><br>
- **CI/CD Entegrasyonu**: Jenkins kullanılarak sürekli entegrasyon ve teslimat süreçleri.  
- **Test Otomasyonu**: Selenium ve Cucumber framework'leri ile entegrasyon.  
- **Otomatik Raporlama**: Test sonuçlarının Jenkins üzerinde görselleştirilmesi.  
- **Planlanmış Testler**: Belirli aralıklarla veya kod değişikliklerinden sonra testlerin otomatik çalıştırılması.  
- **Pipeline Desteği**: Jenkins Pipeline ile esnek iş akışları oluşturma.  
<br><br>

## 📐 Kullanılan Teknolojiler ve Bağımlılıklar
<br><br>
- **Jenkins**: CI/CD süreçlerini yönetmek için kullanılan otomasyon sunucusu.  
- **Cucumber**: BDD framework.  
- **Selenium WebDriver**: UI test otomasyonu.  
- **JUnit**: Testlerin çalıştırılması.  
- **Maven**: Proje yönetimi ve bağımlılık yönetimi.  
<br><br>

## 🔧 Jenkins Kurulumu ve Yapılandırması
<br><br>
1. **Jenkins Kurulumu**  
   - Jenkins'i [resmi web sitesi](https://www.jenkins.io/) üzerinden indirip kurun.  
   - Başlatmak için aşağıdaki komutu kullanabilirsiniz:  
     `java -jar jenkins.war`  
<br><br>
2. **Gerekli Eklentiler**  
   - Jenkins üzerinden aşağıdaki eklentileri yükleyin:  
     - **Maven Integration Plugin**  
     - **JUnit Plugin**  
     - **HTML Publisher Plugin**  
<br><br>
3. **Job Oluşturma**  
   - Jenkins Dashboard üzerinden yeni bir job oluşturun.  
   - Kaynak kontrol bağlantısı olarak projenizin GitHub URL'sini ekleyin.  
   - Build adımında Maven komutlarını kullanarak testleri çalıştırın:  
     `mvn clean test`  
<br><br>
4. **Test Raporlarının Yayınlanması**  
   - HTML Publisher Plugin'i kullanarak test sonuçlarını Jenkins üzerinde görselleştirin.  
   - Rapor dizinini belirleyin:  
     `target/surefire-reports/*.html`  
<br><br>

## 📊 Jenkins Pipeline Örneği
<br><br>
Aşağıda Jenkins Pipeline için örnek bir `Jenkinsfile` bulunmaktadır:  
<br><br>

```groovy
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/seflekL/JenkinsProject.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Publish Reports') {
            steps {
                publishHTML([
                    reportDir: 'target/surefire-reports',
                    reportFiles: 'index.html',
                    reportName: 'Test Report'
                ])
            }
        }
    }
}

📫 İletişim
 GitHub: seflekL
