# spinnaker-halyard
Ansible role for installing and configuring Netflix's Spinnaker via Halyard on GCE

#### Prerequisite

- Platform: Ubuntu 16.04 
- Cloud Provider: GCE
- Ansible Version: 2.4.2.0
- Spinnaker Version  1.6.2 and above

#### Default Vars

| Vars                                     | Description                              |
| :--------------------------------------- | :--------------------------------------- |
| spinnaker_halyard_installation_script_url | String. URL for downloading halyard      |
| hal_user                                 | String: User under which halyard is configured |
| hal_version                              | String: Version of Spinnake Halyard to setup |
| spinnaker_project_id                     | String: Name of GCP Project spinnaker will be setup for |
| spinnaker_deck_url                       | String: Custom FQDN for Spinnaker Deck/UI |
| spinnaker_api_url                        | String: Custom FQDN for Spinnaker Gate/API |
| front50_service_account_name             | String: Name of Front50 service account  |
| front50_service_account_member           | String: Front50 Service account member   |
| spinnaker_oauth_client_id                | String: Oauth Client ID                  |
| spinnaker_oauth_client_secret            | String: Oauth Client Secret              |
| spinnaker_oauth_provider                 | String: Oauth Provider                   |
| spinnaker_gsuite_admin_username          | String: Google GSUITE admin username     |
| spinnaker_gsuite_domain                  | String: Google GSUITE domain             |
| spinnaker_slack_bot_name                 | String: Slack bot name                   |
| spinnaker_slack_token                    | String: Slack bot token                  |
| jenkins_master_name                      | String: Jenkins master name              |
| jenkins_base_url                         | String: Jenkins master FQDN              |
| jenkins_username                         | String: Jenkins username                 |
| jenkins_user_password                    | String: Jenkins username password/api token |
| spinnaker_gcs_bucket_location            | String: Spinnaker GCS bucket location    |
| spinnaker_gcs_bucket_name                | String: Spinnaker GCS bucket name used by Front50 |
| spinnaker_service_account_filename       | String: Spinnaker Service account filename |



#### Assumptions

- Service account for configuring spinnaker is encrypted with KMS and is uploaded in GCS bucket in this case it is `gs://spinnaker-halyard` where *key-ring* used for KMS encryption is `spinnaker-halyard` and *key* is `spinnaker`. For more details refer [Cloud KMS](https://cloud.google.com/kms/docs/encrypt-decrypt)
- Service account `spinnaker-halyard` is having **dwd** enabled as per [Spinnaker authorization Google Groups](https://www.spinnaker.io/setup/security/authorization/google-groups/)
- Service account `spinnaker-halyard` having following IAM role assigned 
  - compute.instanceAdmin
  - compute.networkAdmin
  - compute.securityAdmin
  - compute.storageAdmin
- For simplication purpose we are using only one service account across the entire setup
- Front50 is using GCS as storage option. It is assumed the bucket already exist and have versioning enabled

#### Notes

This playbook is tested for basic setup of spinnaker with all the feature set enabled

#### License

MIT

