# GCP Cloud IAM - If you have to add one service account to one role
```
resource "google_project_iam_member" "sa-tosecurity-monitoring8" {
  member  = "serviceAccount:sa-tosecurity-monitoring@pj-becfr-security-mon.iam.gserviceaccount.com"
  project = "pj-becfr-security-mon"
  role    = "roles/compute.networkAdmin"
}
```
#

# GCP Cloud IAM - If you have to add one service account to many roles

```
resource "google_project_iam_member" "member-role" {
  for_each = toset([
    "roles/owner",
    "roles/compute.instanceAdmin",
    "roles/compute.instanceAdmin.v1",
    "roles/compute.networkViewer",
    "roles/compute.securityAdmin",
    "roles/iam.serviceAccountAdmin",
    "roles/serviceusage.serviceUsageAdmin",
    "roles/iam.serviceAccountUser",
    "roles/storage.admin",
    "roles/cloudsql.admin",
    "roles/resourcemanager.organizationAdmin",
    "roles/iam.securityReviewer"
  ])
  role    = each.key
  member  = "serviceAccount:sa-tosecurity-monitoring@pj-becfr-security-mon.iam.gserviceaccount.com"
  project = "pj-becfr-security-mon"
}

```
#

# GCP Cloud IAM - If you have to add group to one role
```
resource "google_project_iam_member" "sa-tosecurity-monitoring3" {
  member  = "group:be_gcp_security_assessment@carrefour.com"
  project = "pj-becfr-security-mon"
  role    = "roles/securitycenter.adminEditor"
}
```
