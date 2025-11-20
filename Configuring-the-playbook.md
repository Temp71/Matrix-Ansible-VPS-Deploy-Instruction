Change these lines inside the vars.yml

matrix_domain: "mydomain.com"

matrix_server_fqn_matrix: "matrix.mydomain.com"

matrix_server_fqn_element: "element.mydomain.com"

matrix_homeserver_generic_secret_key: 'run this (pwgen -s 64 1) to generate Password'

postgres_connection_password: 'run this (pwgen -s 64 1) to generate Password'

matrix_authentication_service_config_secrets_encryption: 'run this (openssl rand -hex 32) to generate Password'


