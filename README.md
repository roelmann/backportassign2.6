backportassign2.6
=================

Backport of the work done for Assign 2.6 into Moodle2.5 - Minor changes only

Copy the mod/assign from 2.6 into 2.5
  There appears to be a bug in locallib.php - requireallteammemberssubmit needs
  to be updated conditionally based on whether it is set - database does not
  need to be updated if teamsubmission isn't being used and requireallteammemberssubmit
  is not set. 
  This seems to be fine in 2.6 as it is, but needs this edit in 2.5 - May need to check
  if this means I've missed something else somewhere that means this works in 2.6.

  Line 555+
        $update->teamsubmission = $formdata->teamsubmission;
        if (isset($formdata->requireallteammemberssubmit)) {
            $update->requireallteammemberssubmit = $formdata->requireallteammemberssubmit;
        }
        if (isset($formdata->teamsubmissiongroupingid)) {
            $update->teamsubmissiongroupingid = $formdata->teamsubmissiongroupingid;
        }

Copy course/moodleform_mod.php from 2.6 into 2.5

Don't forget to go to the admin/notifications page to update the assign module to the new code
