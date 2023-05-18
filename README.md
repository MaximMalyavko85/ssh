более надежный

KEY_PUBLIC (red)
KEY_PRIVATE


1 CLIENT ---------------> ssh user@server ---------------> SERVER
  KEY_PRIVATE                                              KEY_PUBLIC
  KEY_PUBLIC

2 CLIENT <--------------- prove u own KEY_PUBLIC <--------------- (send 'bruh') <- SERVER 
                          by decripting this message

3 CLIENT ---------------> sure messge was 'bruh' ---------------> SERVER 

4 CLIENT <--------------- welcome <--------------- SERVER 


> ssh-keygen
> --> /home/username/.ssh
> copy KEY_PUBLIC --> ssh-copy-id username@remote_host
> or cat ~/.ssh/id_rsa.pub   (ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCqql6MzstZYh1TmWWv11q5...)

ssh username@remote_host >> yes

