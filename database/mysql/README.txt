# Ansible mysql module provide different parameter that can be used to achive
# different objective as outile below.
# important tips when creating playbook for msql
#    name-> database name, file or list of names
#    state -> import, present, absent, dumb, 
#    target -> location on the remote host , of the dumb fileto read from 
#              or write to. Uncompressed  SQL fles aw wellas bzip2,gz
#    login_port -> default 3306. port of the sql server
#    login_unix_socket -> The part to the unix domain socket for local connections
#    login_password
#    login_user
#    login_host -> default is localhost
#    ignore_tables -> A list of table names that will be ignored in dump of the form
#                     database_name.table_name
#    connect_timeout -> Default is 30. The connection timeout when connecting to mysql server
#    single_transaction -> (no|yes) Execute the dump in a single transaction. default is no
#    config_file -> Specify the config file from which user and password are to be read.
#    client_key -> path to the client private key
#    client_cert -> The path to the client public key certificate
#    ca_cert ->The path to the certificate authority (CA) certificate.
#              This option, if used, must specify the certificate as used by the server. 
