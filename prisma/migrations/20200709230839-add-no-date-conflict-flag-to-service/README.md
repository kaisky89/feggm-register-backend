# Migration `20200709230839-add-no-date-conflict-flag-to-service`

This migration has been generated by Kai Wittmann at 7/9/2020, 11:08:39 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
ALTER TABLE `kkm2`.`Service` ADD COLUMN `noDateConflict` boolean NOT NULL DEFAULT false ;
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200707222159-add-additional-info-to-service..20200709230839-add-no-date-conflict-flag-to-service
--- datamodel.dml
+++ datamodel.dml
@@ -2,9 +2,9 @@
 // learn more about it in the docs: https://pris.ly/d/prisma-schema
 datasource db {
   provider = "mysql"
-  url = "***"
+  url      = env("DATABASE_URL")
 }
 generator client {
   provider = "prisma-client-js"
@@ -16,8 +16,9 @@
   registrationStartsAt    DateTime?
   registrationEndsAt      DateTime?
   numberOfAllowedVisitors Int
   additionalInfo          String?
+  noDateConflict          Boolean   @default(false)
   visitors                Visitor[]
   createdAt               DateTime  @default(now())
 }
```


