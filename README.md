более надежный
Пароль можно подобрать
практически невозможно запомнить
один пароль на все
можно подсмотреть

SSH — это зашифрованный протокол, который используется для взаимодействия компьютера с сервером и его управления. Для работы по протоколу можно использовать один из основных способов авторизации — связку логин/пароль либо SSH-ключи. О недостатках первого способа мы уже написали. Теперь рассмотрим особенности SSH-ключей.

Благодаря SSH-ключам можно произвести аутентификацию без пароля. Ключи представляют собой набор из сотен различных символов, включая латиницу верхнего и нижнего регистров, а также спецсимволы. Общая длина часто составляет от 1024 до 4096 бит. 

Для аутентификации нужно два SSH-ключа — открытый и закрытый.

KEY_PUBLIC (red)
Открытый, или публичный, ключ доступен всем. Он используется для шифрования данных при обращении к серверу. Проще говоря, это набор символов, при помощи которых мы шифруем информацию.
При передаче публичного ключа не нужно подстраховываться — даже если он попадет в руки злоумышленников, они не смогут его использовать. Открытый ключ — лишь замок на двери, за которой находится важная информация. Без второго SSH-ключа он не имеет смысла. 


KEY_PRIVATE
Закрытый, или приватный, SSH-ключ — это ключ к замку. Он расшифровывает данные. С ним нужно быть в разы осторожнее: хранить, соблюдая правила безопасности, и не передавать вторым лицам. Забегая вперед, скажем, что при генерации SSH-ключей закрытый ключ можно и нужно запаролить, чтобы обеспечить дополнительную защиту. 

При создании пользователя на сервере ему можно разрешить вход по SSH-ключу. Для этого необходимо указать открытый ключ. Когда пользователь захочет подключиться, он отправит запрос на сервер. После чего сервер ответит случайной фразой, которую пользователь шифрует. 

Нужно создать пару ключей: приватный (закрытый) ключ и публичный (открытый) ключ. Приватный ключ нужно хранить и никогда никому не показывать. Публичный ключ можно показывать всем и распространять свободно.

Эти ключи связаны друг с другом таким образом, что зашифровав информацию одним ключом, расшифровать ее можно только другим. Например, если ваш друг зашифрует письмо вашим публичным ключом, то прочитать его сможете только вы, потому что для этого нужен ваш приватный ключ. И наоборот: если вы зашифруете что-то своим приватным ключом, то расшифровать его можно только вашим публичным ключом. Так как публичный ключ доступен всем, любой может расшифровать это сообщение. Но он может быть уверен, что сообщение пришло именно от вас. В этом заключается идея цифровой подписи.


1 CLIENT ---------------> ssh user@server ---------------> SERVER
  KEY_PRIVATE                                              KEY_PUBLIC
  KEY_PUBLIC

2 CLIENT <--------------- prove u own KEY_PUBLIC <--------------- (send 'bruh') <- SERVER 
                          by decripting this message

3 CLIENT ---------------> sure messge was 'bruh' ---------------> SERVER 

4 CLIENT <--------------- welcome <--------------- SERVER 


> ssh-keygen
> --> Enter passphrase (empty for no passphrase): bruh (лучше не вводить)
> --> /home/username/.ssh
> copy KEY_PUBLIC --> ssh-copy-id username@remote_host
> or cat ~/.ssh/id_rsa.pub   (ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCqql6MzstZYh1TmWWv11q5...)

ssh username@remote_host >> yes

