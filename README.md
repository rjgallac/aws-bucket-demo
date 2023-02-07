docker build -t rjgallac/my-apache2 .
docker run -p80:80 rjgallac/my-apache2



aws cloudformation create-stack \
--stack-name Static-Site-Testing-Rob \
--template-body file://site.template.yml \
--region eu-west-2

aws cloudformation delete-stack --stack-name Static-Site-Testing-Rob

aws s3 cp src/* s3://robs-static-bucket-name-1111

aws s3 sync src/* s3://robs-static-bucket-name-1111

aws s3 rb s3://robs-static-bucket-name-1111 --force 
aws s3 rm s3://robs-static-bucket-name-1111 --recursive

aws cloudformation list-stacks