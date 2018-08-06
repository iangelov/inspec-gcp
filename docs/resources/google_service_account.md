---
title: About the google_service_account Resource
platform: gcp
---

# google\_service\_account

Use the `google_service_account` InSpec audit resource to test properties of a GCP project IAM service account.

<br>s

## Availability

### Installation

This resource is available in the `inspec-gcp` [resource pack](https://www.inspec.io/docs/reference/glossary/#resource-pack).  To use it, add the following to your `inspec.yml` in your top-level profile:

    depends:
      inspec-gcp:
        git: https://github.com/inspec/inspec-gcp.git

You'll also need to setup your GCP credentials; see the resource pack [README](https://github.com/inspec/inspec-gcp#prerequisites).

### Version

This resource first became available in v0.3.0 of the inspec-gcp resource pack.

## Syntax

A `google_service_account` resource block declares the tests for a single GCP project IAM service account by project and name.

    describe google_service_account(project: 'chef-inspec-gcp', name: 'gcp-inspec-service-account') do
      its('display_name') { should eq 'gcp-inspec-service-account' }
      its('project_id') { should eq 'chef-inspec-gcp' }
    end

<br>

## Examples

The following examples show how to use this InSpec audit resource.

### Test that a GCP project IAM service account has the expected unique identifier

    describe google_service_account(project: 'chef-inspec-gcp', name: 'gcp-inspec-service-account') do
      its('unique_id') { should eq 12345678 }
    end

### Test that a GCP project IAM service account has the expected oauth2 client identifier

    describe google_service_account(project: 'chef-inspec-gcp', name: 'gcp-inspec-service-account') do
      its('oauth2_client_id') { should eq 12345678 }
    end

<br>

## Properties

*  `display_name`, `email`, `etag`, `name`, `oauth2_client_id`, `project_id`, `unique_id`

<br>


## GCP Permissions

Ensure the [Identity and Access Management (IAM) API](https://console.cloud.google.com/apis/library/iam.googleapis.com/) is enabled for the project.