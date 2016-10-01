localcloud-efs
=========

This is a pretty straightforward role that is meant to be used on Amazon EC2  instances that wish to mount an EFS (Elastic File System) volume. 

Requirements
------------

This role will asume that you have your EC2 instrance set up, and placed in correct security group, as well as that you have your EFS filesystem created and you have its Filesystem ID at hand. Please reffer to [EFS Getting Started Guide](https://aws.amazon.com/efs/getting-started/) if you don't have either of these.



Role Variables
--------------

`box_user`
User that will be the owner of mounted volume. The role assumes user exists and will default to root.

`box_group`
Group that will be the owner of mounted volume. The role assumes group exists and will default to root.

`efs_id`
Elastic File System id. You get this one when you create a new filesystem in AWS

`efs_mount_point`
Where your filesystem will be mounted to on the host. This defaults to /efs_data

`aws_region`
Your AWS region where this filesistem resides. Your filesystem and your EC2 instances must be in the same region. This will default to eu-west-1


Dependencies
------------

This role has no external dependencies.

Example Playbook
----------------


```yml
- hosts: servers
  roles:
    - dmitrybelyakov.localcloud-efs

  vars:
    box_user: ubuntu
    efs_id: fs-c87236
    efs_mount_point: /efs_data
    aws_region: eu-west-1

```

License
-------

The MIT License (MIT)
Copyright (c) 2016 Dmitry Belyakov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


