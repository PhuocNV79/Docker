1. Xoá tất cả container ngoại trừ my_container : `docker rm $(docker ps -a | grep -v "my_container" | awk 'NR>1 {print $1}')`
