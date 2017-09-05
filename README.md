# chgautomatica
Automação de Chgs na ServiceNow com CURL

Um dos meios de criar uma automação, é criação de uma API SOAP para consumo externo.

O caminho na ServiceNow para a criação é: *Servicos web do sistema > Servico web com script > Servico SOAP de script*

Para mais informações de criação e manutenção: 

http://wiki.servicenow.com/index.php?title=Outbound_SOAP_Web_Service#gsc.tab=0


Após criada, criamos um arquivo XML para conseguir fazer um POST na ServiceNow, segue o exemplo:

```
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
  xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance"
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:xsd="http://www.w3.org/1999/XMLSchema"
>
    <SOAP-ENV:Body>
        <ns1:execute xmlns:ns1="http://www.service-now.com/" SOAP-ENC:root="1">
            <obj xsi:type="xsd:string">{"chaves": "Valores"}</obj>
        </ns1:execute>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Um exemplo de chamada no terminal ou no arquivo de execução: 

```
curl -H "Content-Type: text/xml; charset=utf-8" -d @seu_arquivo.xml -u user:password "https://instance.service-now.com/urlapi.do?SOAP"
```


