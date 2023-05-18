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
