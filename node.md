###notes :
agenda 
- infra as a code design
- you can used ( Ansible, CloudFormation, Terraform, Packer )
- immutable deployment with terraform

Design infrastructure :
- design a good design ? 
   - make a simple 1 service one capability
- how to create a good design ? 
    - keep calm & leave your ego ?, listen to the input from others.
    - think / memikirkan feedback cari orang lain
    - empower the people ( every team must have power to changes, so on and so forth)
    - infra as a code it must easy to maintain. 
    - review the design 
    
    
Domparison between ansible, cloudformaation , terraform : 
- ansible :      
   - prosedural ( jadi gak bisa simpen state sebelumnya )
- cloudformation : 
   - prosedural 
- terraform :
   - declarative, could be parsed into separate section
   - selalu baca .tf file 
   - nanti digabung dalam 1 stack, nanti disimpan dalam 1 tfstate
   - tfstate nya disimpan di s3, jadi semua orang bisa get state yg terakhir.
   - terraform kasih feedback lagi ngapain.
   - `terrafrom plan` <- command buat planning ngapain terraform 
   - best practives using terraform ? 
        - when using s3 using version-ing. 
        - split into mdoular module, so you can reuse it.
        
- immutable deployment with terraform :
   - how to achieve that : 
        - we need (configuration management, infrastructures orchestration, AWS Image Creator)
        - configuration management : 
            - using ansible
        - infrastructures orchestrations : 
            - 
        - make a new AMI : 
            - using packer for make new AMI
            - store AMI nya di s3
            - fill the AMI with ansible scripts setup.
          
        
        

###questions and answers: 
1. kubernetes vs terraform : 
   - make cubernetest cluster infra using terraform.
   - kubernetes used for deploy services.
   - ( deployment = kubernetes / nomad )
   - ( infra = terraform )
2. how terraform works if new provider is added:  
    - download binary 
3. ansible strong point: 
    - config management 
4. packer strong point: 
    - buat bikin AMI 
    - ngurusin applikasi
    - get latest API from ubuntu

5. why we need new security group ? 
    - so we need 2 security group for blue green deployment, so the old one will be drained and will be terminated
    
6. http://capistranorb.com/ (need check and learn more)    

7. if we want to revert, don't revert s3. just update terraform.

8. if update AMI / bug patch like kernel bug  ?
    - update module and separate application module, service module ?, need to discuss with  

8. https://cloud.oracle.com/en_US/ravello 

9 packer berubah bikin AMI, trus karena AMI berubah maka terraform di execute.

10. terraform klo workflow yg complex agak susah, klo workflow yg complex bisa pake kubernetes.

