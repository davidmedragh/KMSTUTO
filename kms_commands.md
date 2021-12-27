aws kms encrypt --key-id 6d33bc3b-d592-411d-9ea7-25cb80afcd1f --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt

aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt

aws kms re-encrypt --destination-key-id 6d33bc3b-d592-411d-9ea7-25cb80afcd1f --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt 

aws kms enable-key-rotation --key-id 6d33bc3b-d592-411d-9ea7-25cb80afcd1f

aws kms get-key-rotation-status --key-id 6d33bc3b-d592-411d-9ea7-25cb80afcd1f

aws kms generate-data-key --key-id 6d33bc3b-d592-411d-9ea7-25cb80afcd1f --key-spec AES_256
