# Migration `20200529190136-add-text-table`

This migration has been generated by Kai Wittmann at 5/29/2020, 7:01:36 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE TABLE `kkm2`.`Text` (
`id` int NOT NULL  AUTO_INCREMENT,`key` varchar(191) NOT NULL  ,`value` varchar(191)   ,
    PRIMARY KEY (`id`)
) DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200529185533-add-created-at..20200529190136-add-text-table
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
@@ -30,4 +30,10 @@
   service   Service  @relation(fields: [serviceId], references: [id])
   serviceId Int
   createdAt DateTime @default(now())
 }
+
+model Text {
+  id    Int     @default(autoincrement()) @id
+  key   String
+  value String?
+}
```


