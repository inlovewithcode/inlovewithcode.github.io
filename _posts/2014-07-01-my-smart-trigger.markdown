---
author: guidedmissile
comments: true
date: 2014-07-01 12:24:20+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/07/01/my-smart-trigger/
slug: my-smart-trigger
title: My Smart Trigger
wordpress_id: 183
categories:
- Oracle
---

`
-- My Smart Trigger help me to updated all newly discovered hosts into my main inventory
-- Features : Adds server if not in my main table
-- : If server is already present, checks for services detected and updates record acc.
create or replace trigger "NEW_DISCOVERED_HOSTS_T1"
BEFORE
insert on "NEW_DISCOVERED_HOSTS"
for each row
declare
tmp number;
tmp_service number;
tmp_service_name varchar(200);
begin
tmp := 1;
tmp_service := 1;
-- checking
if :new."HOSTNAME" is not null then
for c in ( select SERVICE from server_inventory where lower(hostname) = lower(:new."HOSTNAME") )
loop
tmp := 0; -- found row
tmp_service_name := '' || c."SERVICE";
if instr(LOWER(c."SERVICE"),LOWER(:new."SERVICE"),1) > 0 then
tmp_service := 0; -- found service
end if;
end loop;
end if;
-- fixing/adding
if tmp = 0 then
if tmp_service = 0 then
-- row found, service found
null;
else -- row found, service not found
update server_inventory
set last_updated = sysdate,
last_updated_by = 42,
service = :new."SERVICE" || ';' || tmp_service_name,
DATA_SOURCE = 'Auto Detect'
where trim(lower(hostname)) = trim(lower(:new."HOSTNAME"));
end if;
else
-- row not found
insert into server_inventory(hostname, service, DATA_SOURCE, last_updated, last_updated_by)
values(trim(lower(:new."HOSTNAME")), :new."SERVICE", 'Auto Detect', sysdate, 42);
end if;
end;
-- END OF BODY
`
