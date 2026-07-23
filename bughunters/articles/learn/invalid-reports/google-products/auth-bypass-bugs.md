Auth bypass vulnerability reports are challenging for the Google security team
because they often require a deep understanding of the product in order to
understand and differentiate between intended behavior and security problems.

When reporting a bug like this, we ask you to consider three things:

## 1. There can be two or more equivalent permissions

![There can be two or more equivalent permissions](https://storage.googleapis.com/bughunters-article-images/equivalent-permissions.png)

In a Role-Based Access Control system, everything that is not allowed is
forbidden. But at the same time, there can be more than one way to allow the
same action.

In other words, not having permission to do something doesn't always mean that
it can't be done, it might just need to be done differently. Services with very
granular permissions, or services that can be managed through more than one
product often have equivalent sets of permissions that might give the impression
of lateral escalation vulnerabilities.

For example, if an owner revokes the "Move" permission from a user, but leaves
the "Copy" and "Delete" permissions, those permissions still allow the user to
perform actions that are equivalent to moving a file. The user just has to copy
the file to the new location and delete the old file. Even if the owner revokes
the "Move" permission, that doesn't stop the user from doing something
equivalent to it with the other permissions they have.

### Conclusion

When processing reports of this type, we consider whether the intended use of
the product is likely to require granular revocation or restrictions of
privileges (e.g. in a corporate environment), and whether the revocation of
privileges is clear enough to the owner. Reports of this type might require
input from our privacy, abuse, or legal teams, so they might take significantly
longer to resolve. It is common that these issues are not resolved by spot
implementation fixes, but by large-scale, longer term product redesign.

## 2. Multiple roles can include the same permissions

![Multiple roles can include the same permissions](https://storage.googleapis.com/bughunters-article-images/multiple-roles.png)

If there are two roles that grant the same permission, and your report claims
that only one of the roles should grant the permission, consider the negative
security impact of doing so.

If an owner who wants to grant this permission to a user, has to grant the user
a more privileged role, that might force the owner to give more permissions to a
user than they should have. Based on the least-privilege principle, it might be
safer to grant a permission to a role, than to grant another role (which
includes that permission, and more) to a user.

### Conclusion

When processing reports of this type, we consider if the role you are proposing
as an alternative is significantly more privileged than the permission at hand.
If, in balance, it is better for the permission to stay on the less privileged
role, we might just adjust the documentation to make it more clear.

For example:

*   If the documentation says "Users **must** have the OWNER role on the file to
    change the file name", and you find out that a user with the EDITOR role is
    also able to change the file name, we consider this to be a vulnerability,
    because the documentation explicitly requires the EDITOR role (the word
    **must** implies an obligation).
*   If the documentation says "The OWNER of the file **can** change the
    filename", then we might just fix the documentation to clarify that an
    EDITOR is also able to change the file name (the word **can** implies a
    possibility, but not an obligation).

Note that we might make exceptions in some cases, when it is clear that the
intent of the product was to restrict access, regardless of the documentation.
In case of doubt, we'll ask the team for input.

## 3. Some access control checks might not be obvious externally

![Some access control checks might not be obvious externally](https://storage.googleapis.com/bughunters-article-images/access-control-checks.png)

Often, for usability reasons, some interfaces don't show or expose all the
functionality that the user is permitted to use. If you find out that it is
possible to access some functionality that the UI does not permit by calling an
API or making an HTTP request, please consider if the permission is really
unintended and has actual security-related consequences.

In order to centralize access control checks as much as possible, and reduce the
possibility of errors, permissions are often checked very deep in the stack, as
close as possible to the data they control, and are done in such a way that
works for all interfaces into the service. The internal way to represent these
permissions follows some internal logic that is usually documented in internal
technical documentation.

On the other hand, external facing documentation often describes how the end
user interfaces work, and what functionality and use-cases are implemented. This
means that it is possible that external documentation only explains the intended
functionality available to the roles, without going deep into the details of
every permission implemented in the service.

### Conclusion

When processing reports of this type, we take into consideration the practical
security-related consequences to the product (including whether the access has
any security impact or not), and how the product might change in the future
(including possible future features and internal functionality). Ultimately, it
is possible that the only change to be made as a result of a bug report of this
kind is a documentation change, or that the bug can be simply closed as "working
as intended".

For example, it is possible that querying public data through an otherwise
admin-only interface returns public data instead of an error. Or it is possible
that some fields that are meant to be secret are returned as empty values
(zeros, empty strings, default values, or similar), as they are filtered out
deeper in the stack. It is also possible that certain functionality is only
accessible through an API, or by modifying HTTP requests.
