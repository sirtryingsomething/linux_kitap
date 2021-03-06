# Log Dosyalarının Konumları

Kişisel çalışmalarınızda ve Virtual Host tanımlamalarında, kullanıcının kotası dahilinde log kaydı tutmak isterseniz, log dosyalarını kullanıcı dizini altına koyabilirsiniz. Genelde **"/home/kullanıcı\_adı/logs/"** dizini altına tüm ilgili log dosyaları konabilir. Bu şekilde her kullanıcı için daha kolay takip edilebilir ve muntazam bir loglama yapmış olursunuz. Hosting ortamında log dosyalarının kullanıcı dizini altında tutulması tercih edilmelidir, günümüz koşullarında bir web sitesinin regülasyonlardan dolayı en az iki sene loglarının saklanması gerekmektedir. Log dosyalarını bu şekilde oluşturduğunuzda, bu log dosyalarını otomatik olarak döndürecek script çok basit olacaktır: aşağıdaki dosyayı /etc/logrotate.d/home adı ile kaydedebilirsiniz.

```bash
/home/*/logs/*log {
        daily
        rotate 8
        missingok
        compress
        delaycompress
        postrotate
        /usr/sbin/apachectl graceful
        endscript
}
```



