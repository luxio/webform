webform
=======

The Webform module for DrupalGap. When viewing a webform enabled node in
DrupalGap, this module will automatically display the webform in the app.

Installation
============

## Download and enable the 7.x-3.x version of the Webform Service module:

- https://www.drupal.org/project/webform_service

## Patch the Webform Service module with the following patches:

- https://www.drupal.org/node/1683006#comment-8997195
- https://www.drupal.org/node/2048343#comment-9331515

Then in Drupal, go to admin/structure/services/list/drupalgap/resources and enable
   your desired service resources under "webform_submission". We recommend
   enabling at least the "create", "retrieve" and "index" resources. Visit the
   admin/people/permissions page in Drupal, and review the permissions you have
   set for Webform module. That will give you a better idea of what service
   resources you should consider enabling.

After enabling the service resources, it's a good idea to the clear all the
   caches in Drupal.

Usage
=====

This module tries to automate the webform features so you don't have to do
anything. But if you want to make manual calls to C.R.U.D. submissions,
here are some examples.

Note, the data object has property names that are equal to the particular
webform component id.

# Create
```
var webform_submission = {
  nid: "123",
  uid: "1",
  data: {
    1: "Hello"
  }
};
webform_submission_create(123, webform_submission, {
    success: function(result) {
      dpm(result);
    }
});
```
# Index
```
var query = {
  parameters: {
    nid: 123
  }
};
webform_submission_index(query, {
    success: function(results) {
      dpm(results);
    }
});
```

