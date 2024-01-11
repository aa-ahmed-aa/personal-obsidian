[[linux]]

#### list groups 
`groups`

#### add user to group 
`sudo usermod -a -G microk8s ahmed`

#### reload user in a group to reflect you changes 
`newgrp microk8s`

#### list all gruops users 
`getent group`

#### get the groups of specific user 
`groups ahmed`