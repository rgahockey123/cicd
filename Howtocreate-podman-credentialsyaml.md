cat ~/.config/containers/auth.json | base64
# this generates the entire auth.job into base64 encoding.
This value is then placed in the podman-credentials.yaml file in the config.json section
The encoded value in auth.json is generated when you do:

podman login -u='rgahockey3+rich' -p='NCRPE7P6UUZ5KRJE3DMEE1DBBTBO0GY3TRHEYXQXW1NQRRS6WZX9MXA8JG0U36SD' quay.io
