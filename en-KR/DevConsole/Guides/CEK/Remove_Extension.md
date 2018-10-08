# Disabling and deleting an extension

You can delete an extension, in the status prior to the review request, on the page to [enter the basic extension information](/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo).

![](/DevConsole/Resources/Images/DevConsole-Remove_Extension.png)

However, you cannot delete the extensions in the following statuses:

* Extension under review
* Extension in service

You can always cancel a review and delete the extensions under review.

![](/DevConsole/Resources/Images/DevConsole-Cancel_Submission.png)

If the extension is in service after passing the review, you can delete it after canceling the service. If you cancel the service, the status of the extension is changed to a **{{ book.DevConsole.cek_status_dev }}** status.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>A check from the Clova operations team is required to cancel a service. To stop the service of an extension, contact the operations team at <a href="mailto:{{ book.ExtensionAdminEmail }}">{{ book.ExtensionAdminEmail }}</a>.</p>
</div>
