# MEP System Map

> Initial source-derived draft. Every inventory item remains **Needs Review** until human validation. This is a navigation and discovery index, not a functional specification or statement of intended business behavior.

## 1. Purpose and Maintenance Rules

This map helps the PRD Reviewer find affected application areas and helps Automation Test Generator v2 locate routes and frontend evidence.

- Preserve source-observed facts separately from user-confirmed rules.
- Keep route parameters, duplicate registrations, access guards, and feature-flag alternatives visible.
- Treat source behavior as observed implementation, not necessarily intended behavior.
- Add deep module documentation only when a task needs it.
- Revalidate affected areas after relevant source changes.
- Do not treat a registered route as accessible to every user. Guards and menus apply permissions, company checks, and feature flags.

## 2. Repository and Inventory Scope

- Frontend: `C:/Users/Yusuf Zaki/mceasy-vsms`, Git revision `6cb2c0975`.
- Framework: Vue 2.6 and Vue Router 3 in HTML5 history mode.
- Inspected: `src/router/routes.js`, imported `src/router/allRoutes/*.js`, router guards, both vertical sidebar variants, and referenced `src/router/views/**` entries.
- Cross-checked: routes vs navigation; page imports vs likely page-level components; nested/lazy routes; permissions and feature flags.
- Excluded from detailed inspection: generated assets, dependencies, deployment files, backend rules, and reusable components without page evidence.
- Knowledge location: this `MEPDocs` repository already contained the map, so it remains at the root and planned module details use `modules/`. Confirm this during review.

## 3. Page and Feature Inventory

Evidence shows the declaring route and first statically discoverable page component. Missing component paths indicate redirect/action/conditional resolution or an import not statically resolved.

| Page / Feature | Route | Primary Module | Related Modules | Frontend Entry / Evidence | Status |
| --- | --- | --- | --- | --- | --- |
| 403 | `/403/` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:197` → `mceasy-vsms/src/router/views/utility/403` | Needs Review |
| 404 | `/404/` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:202` → `mceasy-vsms/src/router/views/utility/404` | Needs Review |
| auth | `/authenticate/:auth` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:112` | Needs Review |
| Forgot Password | `/forgotpassword/` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:48` → `mceasy-vsms/src/router/views/account/forgotpassword/email` | Needs Review |
| Reset Password | `/forgotpassword/reset` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:80` → `mceasy-vsms/src/router/views/account/forgotpassword/resetpassword` | Needs Review |
| Password Changed | `/forgotpassword/result` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:96` → `mceasy-vsms/src/router/views/account/forgotpassword/result` | Needs Review |
| OTP Verification | `/forgotpassword/verification` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:64` → `mceasy-vsms/src/router/views/account/forgotpassword/verification` | Needs Review |
| Login | `/login/` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:7` → `mceasy-vsms/src/router/views/account/login` | Needs Review |
| logout | `/logout/` | Authentication | — | `mceasy-vsms/src/router/allRoutes/auth.js:155` | Needs Review |
| CDM Security Monitoring | `/cdm-security-monitoring/` | CDM Security Monitoring | — | `mceasy-vsms/src/router/allRoutes/cdm-security-monitoring.js:7` → `mceasy-vsms/src/router/views/cdm-security-monitoring/` | Needs Review |
| Chat | `/chat` | Chat | Dashboard | `mceasy-vsms/src/router/allRoutes/chat.js:5` → `mceasy-vsms/src/router/views/dashboards` | Needs Review |
| Company Ticket | `/company-ticket/` | Company Tickets | — | `mceasy-vsms/src/router/allRoutes/companyTicket.js:7` → `mceasy-vsms/src/router/views/company-ticket/TicketLists` | Needs Review |
| Control Tower V2 | `/controltower-2/` | Control Tower | Temporary Tracking | `mceasy-vsms/src/router/allRoutes/controlTower.js:23` → `mceasy-vsms/src/router/views/controltower-2/indexV2.vue` | Needs Review |
| Control Tower | `/controltower/` | Control Tower | Temporary Tracking | `mceasy-vsms/src/router/allRoutes/controlTower.js:6` → `mceasy-vsms/src/router/views/controltower` | Needs Review |
| Cost Management | `/cost-management/` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:7` → `mceasy-vsms/src/router/views/cost-management/` | Needs Review |
| Detail Other Cost Management | `/cost-management/other/:id` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:133` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Create Other Cost Management | `/cost-management/other/create` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:112` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Detail Cost Management | `/cost-management/travel-cost/:id` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:49` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Create Cost Management | `/cost-management/travel-cost/create` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:28` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Detail Vehicle Cost Management | `/cost-management/vehicle/:id` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:91` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Create Vehicle Cost Management | `/cost-management/vehicle/create` | Cost Management | Fleet Tasks, Master Data | `mceasy-vsms/src/router/allRoutes/costManagement.js:70` → `mceasy-vsms/src/router/views/cost-management/fleet-task-cost` | Needs Review |
| Master Customer Contract Detail | `/master/contract/customer/:contractId` | Customer Contracts | Master Data | `mceasy-vsms/src/router/allRoutes/customer-contract.js:29` → `mceasy-vsms/src/router/views/master/contract/customer-contract/form`; file is not imported by `src/router/routes.js` | Needs Review |
| Master Customer Contract Create | `/master/contract/customer/create` | Customer Contracts | Master Data | `mceasy-vsms/src/router/allRoutes/customer-contract.js:7` → `mceasy-vsms/src/router/views/master/contract/customer-contract/form`; file is not imported by `src/router/routes.js` | Needs Review |
| Dashboard | `/` | Dashboard | Driver Score, Maintenance, Delivery | `mceasy-vsms/src/router/routes.js:70` → `mceasy-vsms/src/router/views/dashboards/index` | Needs Review |
| Dashboard Direct | `/dashboard` | Dashboard | Driver Score, Maintenance, Delivery | `mceasy-vsms/src/router/routes.js:39` → `mceasy-vsms/src/router/views/dashboards/index` | Needs Review |
| Dashboard Scheduler | `/scheduler` | Dashboard | Driver Score, Maintenance, Delivery | `mceasy-vsms/src/router/routes.js:144` → `mceasy-vsms/src/router/views/dashboards/contents/scheduler` | Needs Review |
| Create Dashboard Scheduler | `/scheduler/create` | Dashboard | Driver Score, Maintenance, Delivery | `mceasy-vsms/src/router/routes.js:167` → `mceasy-vsms/src/router/views/dashboards/contents/scheduler/form` | Needs Review |
| Update Dashboard Scheduler | `/scheduler/update/:id` | Dashboard | Driver Score, Maintenance, Delivery | `mceasy-vsms/src/router/routes.js:188` → `mceasy-vsms/src/router/views/dashboards/contents/scheduler/form` | Needs Review |
| Delivery | `/delivery` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:10` → `mceasy-vsms/src/router/views/delivery` | Needs Review |
| Delivery Detail | `/delivery/:id` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:91` → `mceasy-vsms/src/router/views/delivery/form` | Needs Review |
| Delivery Accurate | `/delivery/accurate/list` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:108` → `mceasy-vsms/src/router/views/delivery/accurate` | Needs Review |
| Delivery Create | `/delivery/create` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:58` → `mceasy-vsms/src/router/views/delivery/form` | Needs Review |
| Delivery Create Bulk | `/delivery/create-bulk` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:75` → `mceasy-vsms/src/router/views/delivery/create-bulk` | Needs Review |
| Delivery Import | `/delivery/import` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:41` → `mceasy-vsms/src/router/views/delivery/import/contents/Upload.vue` | Needs Review |
| Delivery Import Detail | `/delivery/import/:id` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:46` → `mceasy-vsms/src/router/views/delivery/import/contents/Process.vue` | Needs Review |
| Delivery Import Result | `/delivery/import/:id/result` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:51` → `mceasy-vsms/src/router/views/delivery/import/contents/Result.vue` | Needs Review |
| Track DO | `/delivery/track/:data` | Delivery | Fleet Tasks, Invoices | `mceasy-vsms/src/router/allRoutes/delivery.js:214` → `mceasy-vsms/src/router/views/delivery/track/index` | Needs Review |
| Delivery Request List | `/delivery-request` | Delivery Requests | Fleet Tasks | `mceasy-vsms/src/router/allRoutes/deliveryRequest.js:36` → `mceasy-vsms/src/router/views/delivery-request/contents/List` | Needs Review |
| Delivery Request Detail | `/delivery-request/:id` | Delivery Requests | Fleet Tasks | `mceasy-vsms/src/router/allRoutes/deliveryRequest.js:41` → `mceasy-vsms/src/router/views/delivery-request/contents/Detail` | Needs Review |
| Fleet Task Request Detail | `/fleet-task-request/:id` | Delivery Requests | Fleet Tasks | `mceasy-vsms/src/router/allRoutes/deliveryRequest.js:46` → `mceasy-vsms/src/router/views/delivery-request/contents/DetailFleetTask` | Needs Review |
| Delivery Scheduler | `/delivery-scheduler` | Delivery Scheduler | — | `mceasy-vsms/src/router/allRoutes/delivery-scheduler.js:7` → `mceasy-vsms/src/router/views/delivery-scheduler` | Needs Review |
| Delivery Scheduler Detail | `/delivery-scheduler/:id` | Delivery Scheduler | — | `mceasy-vsms/src/router/allRoutes/delivery-scheduler.js:39` → `mceasy-vsms/src/router/views/delivery-scheduler/detail` | Needs Review |
| Delivery Scheduler Create | `/delivery-scheduler/create` | Delivery Scheduler | — | `mceasy-vsms/src/router/allRoutes/delivery-scheduler.js:23` → `mceasy-vsms/src/router/views/delivery-scheduler/create` | Needs Review |
| List Driver Score V2 | `/driverscore/` | Driver Score | — | `mceasy-vsms/src/router/allRoutes/driverScore.js:6` → `mceasy-vsms/src/router/views/driverscore/driverscore-v2/index-v2` | Needs Review |
| List Configuration V2 | `/driverscore/configuration` | Driver Score | — | `mceasy-vsms/src/router/allRoutes/driverScore.js:65` → `mceasy-vsms/src/router/views/driverscore/configuration/index-v2` | Needs Review |
| Detail Driver Score V2 | `/driverscore/detaildriverscore/:driverId` | Driver Score | — | `mceasy-vsms/src/router/allRoutes/driverScore.js:25` → `mceasy-vsms/src/router/views/driverscore/driverscore-v2/DetailDriverScore-v2` | Needs Review |
| Warning Details | `/driverscore/detaildriverscore/map` | Driver Score | — | `mceasy-vsms/src/router/allRoutes/driverScore.js:46` → `mceasy-vsms/src/router/views/driverscore/detailmap` | Needs Review |
| Fleet Availability | `/fleet-availability` | Fleet Availability | — | `mceasy-vsms/src/router/allRoutes/fleet-availability.js:7` → `mceasy-vsms/src/router/views/fleet-availability` | Needs Review |
| Fleet Task | `/fleet-task/` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:9` → `mceasy-vsms/src/router/views/fleet-task/` | Needs Review |
| Fleet Task Detail | `/fleet-task/:id` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:95` → `mceasy-vsms/src/router/views/fleet-task/form-v2` | Needs Review |
| Fleet Task Attach Delivery | `/fleet-task/:id/attach-delivery` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:79` → `mceasy-vsms/src/router/views/fleet-task/attach-delivery` | Needs Review |
| Fleet Task Create | `/fleet-task/create` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:63` → `mceasy-vsms/src/router/views/fleet-task/attach-delivery` | Needs Review |
| Fleet Task Import | `/fleet-task/import` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:46` → `mceasy-vsms/src/router/views/fleet-task/import/contents/Upload.vue` | Needs Review |
| Fleet Task Import Detail | `/fleet-task/import/:id` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:51` → `mceasy-vsms/src/router/views/fleet-task/import/contents/Process.vue` | Needs Review |
| Fleet Task Import Result | `/fleet-task/import/:id/result` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:56` → `mceasy-vsms/src/router/views/fleet-task/import/contents/Result.vue` | Needs Review |
| Track FO | `/fleet-task/track/:data` | Fleet Tasks | Delivery, Settings | `mceasy-vsms/src/router/allRoutes/fleetTask.js:112` → `mceasy-vsms/src/router/views/fleet-task/liveTrack/index` | Needs Review |
| Integration | `/setting/integration/` | Integration | — | `mceasy-vsms/src/router/allRoutes/integration.js:5` → `mceasy-vsms/src/router/views/integration/` | Needs Review |
| Delivery Invoice | `/delivery/invoice/form` | Invoices | Delivery | `mceasy-vsms/src/router/allRoutes/delivery.js:129` → `mceasy-vsms/src/router/views/invoice/form` | Needs Review |
| Invoice List | `/invoice` | Invoices | Delivery | `mceasy-vsms/src/router/allRoutes/delivery.js:150` → `mceasy-vsms/src/router/views/invoice` | Needs Review |
| Invoice Create | `/invoice/create` | Invoices | Delivery | `mceasy-vsms/src/router/allRoutes/delivery.js:171` → `mceasy-vsms/src/router/views/invoice/delivery-list` | Needs Review |
| Invoice Form | `/invoice/form` | Invoices | Delivery | `mceasy-vsms/src/router/allRoutes/delivery.js:192` → `mceasy-vsms/src/router/views/invoice/invoice-form` | Needs Review |
| Land Measurement | `/land-measurement/` | Land Measurement | — | `mceasy-vsms/src/router/allRoutes/land-measurement.js:8` → `mceasy-vsms/src/router/views/land-measurement` | Needs Review |
| Land Measurement Create | `/land-measurement/create` | Land Measurement | — | `mceasy-vsms/src/router/allRoutes/land-measurement.js:30` → `mceasy-vsms/src/router/views/land-measurement/form` | Needs Review |
| Land Measurement View | `/land-measurement/view/:id?` | Land Measurement | — | `mceasy-vsms/src/router/allRoutes/land-measurement.js:47` → `mceasy-vsms/src/router/views/land-measurement/form` | Needs Review |
| List License | `/license/` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:7` → `mceasy-vsms/src/router/views/license` | Needs Review |
| License Fleet Import Driver | `/license/fleet/import/driver` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:79` → `mceasy-vsms/src/router/views/license/importDriverDoc` | Needs Review |
| License Fleet Import Fleet | `/license/fleet/import/fleet` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:94` → `mceasy-vsms/src/router/views/license/importVehicleDoc` | Needs Review |
| License Setting | `/license/licensesetting/` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:110` → `mceasy-vsms/src/router/views/license/licensesetting` | Needs Review |
| License Reminder | `/license/reminder` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:25` → `mceasy-vsms/src/router/views/license/reminder` | Needs Review |
| Create License Reminder | `/license/reminder/create` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:43` → `mceasy-vsms/src/router/views/license/form` | Needs Review |
| Update License Reminder | `/license/reminder/update/:id` | Licenses | — | `mceasy-vsms/src/router/allRoutes/license.js:61` → `mceasy-vsms/src/router/views/license/form` | Needs Review |
| Live Streaming Trackvision | `/live-streaming/` | Live Streaming | — | `mceasy-vsms/src/router/allRoutes/trackvision.js:6` → `mceasy-vsms/src/router/views/live-streaming/` | Needs Review |
| Liveview | `/liveview/` | Live View | — | `mceasy-vsms/src/router/allRoutes/liveView.js:3` | Needs Review |
| Service | `/maintenance/` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:7` → `mceasy-vsms/src/router/views/maintenance` | Needs Review |
| List Service Alert | `/maintenance/servicealert` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:175` → `mceasy-vsms/src/router/views/maintenance/servicealert` | Needs Review |
| Email Alert Create | `/maintenance/servicealert/emailcreate/:id?` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:250` → `mceasy-vsms/src/router/views/maintenance/servicealert/CreateEmail` | Needs Review |
| History Email Service Alert | `/maintenance/servicealert/historyemail` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:225` → `mceasy-vsms/src/router/views/maintenance/servicealert/historyemail` | Needs Review |
| Email Service Alert | `/maintenance/servicealert/sendingemail` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:200` → `mceasy-vsms/src/router/views/maintenance/servicealert/sendingemail` | Needs Review |
| Service Group | `/maintenance/servicegroup/` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:275` → `mceasy-vsms/src/router/views/maintenance/servicegroup/` | Needs Review |
| Add Component Schedule | `/maintenance/servicegroup/servicedetailcomponent/:ssgroupId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:370` → `mceasy-vsms/src/router/views/maintenance/servicegroup/forms/ServiceDetailForm` | Needs Review |
| Detail Component Schedule | `/maintenance/servicegroup/servicedetailcomponent/:ssgroupId/:serviceId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:396` → `mceasy-vsms/src/router/views/maintenance/servicegroup/forms/ServiceDetailForm` | Needs Review |
| Detail Group Service | `/maintenance/servicegroup/servicegroupdetail/:ssgroupId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:318` → `mceasy-vsms/src/router/views/maintenance/servicegroup/detail` | Needs Review |
| Duplicate Group Service | `/maintenance/servicegroup/servicegroupdetail/:ssgroupId/:duplicate` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:344` → `mceasy-vsms/src/router/views/maintenance/servicegroup/detail` | Needs Review |
| Scheduled Conflict | `/maintenance/servicegroup/servicegroupdetail/conflict/:ssgroupId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:301` → `mceasy-vsms/src/router/views/maintenance/servicegroup/detail/ConflictPage` | Needs Review |
| Service Order List | `/maintenance/serviceorder` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:469` → `mceasy-vsms/src/router/views/maintenance/serviceorder` | Needs Review |
| Maintenance Detail Service Order | `/maintenance/serviceorder/detail/:id` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:454` → `mceasy-vsms/src/router/views/maintenance/serviceorder/detail` | Needs Review |
| Maintenance Create Service Order | `/maintenance/serviceorder/form` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:439` → `mceasy-vsms/src/router/views/maintenance/serviceorder/form` | Needs Review |
| List Service Schedule | `/maintenance/serviceschedule` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:31` → `mceasy-vsms/src/router/views/maintenance/serviceschedule` | Needs Review |
| Create Service Schedule | `/maintenance/serviceschedule/add/:vehicleId?` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:125` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/formserviceschedule` | Needs Review |
| Detail Service Schedule | `/maintenance/serviceschedule/detailserviceschedule/:vehicleId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:100` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/detailserviceschedule` | Needs Review |
| Log Maintenance Detail Service Shceduler | `/maintenance/serviceschedule/detailserviceschedule/log/:vehicleId` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:422` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/detailserviceschedule/log` | Needs Review |
| Form Service Schedule | `/maintenance/serviceschedule/formserviceschedule/:vehicleId?/:serviceId?/:serviceType` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:150` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/formserviceschedule` | Needs Review |
| Service Schedule Import | `/maintenance/serviceschedule/import` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:56` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/import` | Needs Review |
| Service Schedule Import Detail | `/maintenance/serviceschedule/import/process` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:85` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/import/contents/Process.vue` | Needs Review |
| Service Schedule Import Result | `/maintenance/serviceschedule/import/result` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:91` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/import/contents/Result.vue` | Needs Review |
| Service Schedule Import | `/maintenance/serviceschedule/import/upload` | Maintenance | — | `mceasy-vsms/src/router/allRoutes/maintenance.js:79` → `mceasy-vsms/src/router/views/maintenance/serviceschedule/import/contents/Upload.vue` | Needs Review |
| Marketplace | `/marketplace/` | Marketplace | — | `mceasy-vsms/src/router/allRoutes/marketplace.js:6` → `mceasy-vsms/src/router/views/marketplace` | Needs Review |
| Marketplace Product Detail | `/marketplace/product/detail` | Marketplace | — | `mceasy-vsms/src/router/allRoutes/marketplace.js:23` → `mceasy-vsms/src/router/views/marketplace/components/ProductCard/ProductDetail` | Needs Review |
| Master Home Page Deprecated | `/master-deprecated/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:38` → `mceasy-vsms/src/router/views/master` | Needs Review |
| Master Home Page | `/master/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:8` → `mceasy-vsms/src/router/views/master/index-v2` | Needs Review |
| Master Address | `/master/address/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:256` → `mceasy-vsms/src/router/views/master/address` | Needs Review |
| Master Address Create | `/master/address/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:275` → `mceasy-vsms/src/router/views/master/address/form` | Needs Review |
| Master Address Import | `/master/address/import/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:313` → `mceasy-vsms/src/router/views/master/address/ImportPage` | Needs Review |
| Master Address Import Result | `/master/address/importresult/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:334` → `mceasy-vsms/src/router/views/master/address/ImportResultPage` | Needs Review |
| Master Address Update | `/master/address/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:294` → `mceasy-vsms/src/router/views/master/address/form` | Needs Review |
| Master Contract | `/master/contract/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:909` → `mceasy-vsms/src/router/views/master/contract/` | Needs Review |
| Master Customer | `/master/customer/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:356` → `mceasy-vsms/src/router/views/master/customer` | Needs Review |
| Master Customer Create | `/master/customer/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:381` → `mceasy-vsms/src/router/views/master/customer/form` | Needs Review |
| Master Customer Import | `/master/customer/import` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:505` → `mceasy-vsms/src/router/views/master/customer/import/contents/Upload.vue` | Needs Review |
| Master Customer Import Detail | `/master/customer/import/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:510` → `mceasy-vsms/src/router/views/master/customer/import/contents/Process.vue` | Needs Review |
| Master Customer Import Result | `/master/customer/import/:id/result` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:515` → `mceasy-vsms/src/router/views/master/customer/import/contents/Result.vue` | Needs Review |
| Master Customer Update | `/master/customer/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:406` → `mceasy-vsms/src/router/views/master/customer/form` | Needs Review |
| Master Customer Create Address | `/master/customer/update/:uuid/address/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:431` → `mceasy-vsms/src/router/views/master/customer/address` | Needs Review |
| Master Customer Update Address | `/master/customer/update/:uuid/address/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:457` → `mceasy-vsms/src/router/views/master/customer/address` | Needs Review |
| Master Employee | `/master/employee/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:524` → `mceasy-vsms/src/router/views/master/employee` | Needs Review |
| Master Employee Create | `/master/employee/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:543` → `mceasy-vsms/src/router/views/master/employee/form` | Needs Review |
| Master Employee Detail | `/master/employee/employeedetail/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:564` → `mceasy-vsms/src/router/views/master/employee/form` | Needs Review |
| Riwayat Perjalanan Pengemudi | `/master/employee/employeehistorydriver/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:585` → `mceasy-vsms/src/router/views/master/employee/employeehistorydriver` | Needs Review |
| Master Employee Import | `/master/employee/import/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:613` → `mceasy-vsms/src/router/views/master/employee/ImportPage` | Needs Review |
| Master Employee Import Result | `/master/employee/importresult/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:634` → `mceasy-vsms/src/router/views/master/employee/ImportResult` | Needs Review |
| Master Fleet | `/master/fleet/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:67` → `mceasy-vsms/src/router/views/master/fleet` | Needs Review |
| Master Fleet Create | `/master/fleet/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:86` → `mceasy-vsms/src/router/views/master/fleet/form` | Needs Review |
| Master Fleet Update | `/master/fleet/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:111` → `mceasy-vsms/src/router/views/master/fleet/form` | Needs Review |
| Master Fleet Update History | `/master/fleet/update/history/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:135` → `mceasy-vsms/src/router/views/master/fleet/UpdateHistory` | Needs Review |
| Master Ibeacon | `/master/ibeacon/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1158` → `mceasy-vsms/src/router/views/master/ibeacon` | Needs Review |
| Master RFID and Face Recognition | `/master/identification/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1052` → `mceasy-vsms/src/router/views/master/rfid-facerecognition` | Needs Review |
| Master RFID Import | `/master/identification/import/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1073` → `mceasy-vsms/src/router/views/master/rfid-facerecognition/ImportPage` | Needs Review |
| Master RFID Import Result | `/master/identification/importresult/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1098` → `mceasy-vsms/src/router/views/master/rfid-facerecognition/ImportResult` | Needs Review |
| Master Orthophoto | `/master/orthophoto/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1178` → `mceasy-vsms/src/router/views/master/orthophoto` | Needs Review |
| Master Product | `/master/product/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:742` → `mceasy-vsms/src/router/views/master/product` | Needs Review |
| Master Product Create | `/master/product/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:764` → `mceasy-vsms/src/router/views/master/product/form` | Needs Review |
| Master Product Import | `/master/product/import` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:830` → `mceasy-vsms/src/router/views/master/product/import/contents/Upload.vue` | Needs Review |
| Master Product Import Detail | `/master/product/import/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:835` → `mceasy-vsms/src/router/views/master/product/import/contents/Process.vue` | Needs Review |
| Master Product Import Result | `/master/product/import/:id/result` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:840` → `mceasy-vsms/src/router/views/master/product/import/contents/Result.vue` | Needs Review |
| Master Product Update | `/master/product/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:786` → `mceasy-vsms/src/router/views/master/product/form` | Needs Review |
| Master RFID | `/master/rfid/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1035` → `mceasy-vsms/src/router/views/master/rfid` | Needs Review |
| RFID Reader Detail | `/master/rfid/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1141` → `mceasy-vsms/src/router/views/master/rfid/form` | Needs Review |
| Master RFID History Tag | `/master/rfid/history-tag/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1123` → `mceasy-vsms/src/router/views/master/rfid/history/history-tag` | Needs Review |
| Master Ritage | `/master/ritage/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1194` → `mceasy-vsms/src/router/views/master/ritage` | Needs Review |
| Master Ritage Create | `/master/ritage/create` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1210` → `mceasy-vsms/src/router/views/master/ritage/form` | Needs Review |
| Master Ritage Update | `/master/ritage/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1226` → `mceasy-vsms/src/router/views/master/ritage/form` | Needs Review |
| Master RJM | `/master/rjm/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1242` → `mceasy-vsms/src/router/views/master/rjm` | Needs Review |
| Master RJM Create | `/master/rjm/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1258` → `mceasy-vsms/src/router/views/master/rjm/form` | Needs Review |
| Master RJM Update | `/master/rjm/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1274` → `mceasy-vsms/src/router/views/master/rjm/form` | Needs Review |
| Master Route | `/master/route/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:848` → `mceasy-vsms/src/router/views/master/route` | Needs Review |
| Master Route Create | `/master/route/create` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:868` → `mceasy-vsms/src/router/views/master/route/form` | Needs Review |
| Master Route Update | `/master/route/update/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:888` → `mceasy-vsms/src/router/views/master/route/form` | Needs Review |
| Master Service | `/master/service/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:182` → `mceasy-vsms/src/router/views/master/service` | Needs Review |
| Add Master Service Maintenance | `/master/service/maintenance/addservice` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:196` → `mceasy-vsms/src/router/views/master/service/maintenance/form` | Needs Review |
| Update Master Service Maintenance | `/master/service/maintenance/updateservice/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:211` → `mceasy-vsms/src/router/views/master/service/maintenance/form` | Needs Review |
| Service Spare Part Add | `/master/service/sparepartsadd` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:226` → `mceasy-vsms/src/router/views/master/service/parts/FormParts` | Needs Review |
| Service Spare Part Update | `/master/service/sparepartsupdate/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:241` → `mceasy-vsms/src/router/views/master/service/parts/FormParts` | Needs Review |
| Master Tracking | `/master/tracking/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:161` → `mceasy-vsms/src/router/views/master/tracking` | Needs Review |
| Master User | `/master/user/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:656` → `mceasy-vsms/src/router/views/master/user` | Needs Review |
| Master Vendor Contract | `/master/vendor-contract/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:941` → `mceasy-vsms/src/router/views/master/vendor-contract` | Needs Review |
| Master Vendor Contract Detail | `/master/vendor-contract/:vendorId/:contractId/:versionId` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:987` → `mceasy-vsms/src/router/views/master/vendor-contract/form` | Needs Review |
| Master Vendor Contract Addendum History | `/master/vendor-contract/:vendorId/:contractId/:versionId/addendum-history` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:1010` → `mceasy-vsms/src/router/views/master/vendor-contract/addendum-history` | Needs Review |
| Master Vendor Contract Create | `/master/vendor-contract/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:964` → `mceasy-vsms/src/router/views/master/vendor-contract/form` | Needs Review |
| Master Vendor | `/master/vendor/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:675` → `mceasy-vsms/src/router/views/master/vendor` | Needs Review |
| Master Vendor Detail | `/master/vendor/:id` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:719` → `mceasy-vsms/src/router/views/master/vendor/form` | Needs Review |
| Master Vendor Create | `/master/vendor/create/` | Master Data | — | `mceasy-vsms/src/router/allRoutes/master.js:697` → `mceasy-vsms/src/router/views/master/vendor/form` | Needs Review |
| Notification Log | `/notification/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:7` → `mceasy-vsms/src/router/views/notification/indexV2` | Needs Review |
| Notifikasi | `/notification/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:25` → `mceasy-vsms/src/router/views/notification/index` | Needs Review |
| Advanced Driver Assistance System | `/notification/adas/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:306` → `mceasy-vsms/src/router/views/notification/adas` | Needs Review |
| Advanced Driver Assistance System Detail | `/notification/adas/map/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:332` → `mceasy-vsms/src/router/views/notification/adas/detailmap` | Needs Review |
| Notification Detail | `/notification/detail/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:357` → `mceasy-vsms/src/router/views/notification/components/detail/` | Needs Review |
| Perilaku Pengemudi | `/notification/driverbehavior/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:51` → `mceasy-vsms/src/router/views/notification/driverbehavior` | Needs Review |
| Perilaku Pengemudi Detail | `/notification/driverbehavior/map/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:77` → `mceasy-vsms/src/router/views/notification/driverbehavior/detailmap` | Needs Review |
| Driver Monitoring System | `/notification/drivermonitoringsystem/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:105` → `mceasy-vsms/src/router/views/notification/drivermonitoringsystem` | Needs Review |
| Driver Monitoring System Detail | `/notification/drivermonitoringsystem/map/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:133` → `mceasy-vsms/src/router/views/notification/drivermonitoringsystem/detailmap` | Needs Review |
| General | `/notification/general/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:161` → `mceasy-vsms/src/router/views/notification/general` | Needs Review |
| General Detail | `/notification/general/map/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:187` → `mceasy-vsms/src/router/views/notification/general/detailmap` | Needs Review |
| Notification Setting | `/notification/setting/` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:215` → `mceasy-vsms/src/router/views/notification/notificationsetting` | Needs Review |
| Email Notification Create | `/notification/setting/email` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:248` → `mceasy-vsms/src/router/views/notification/notificationsetting/detail/DeliveryForm` | Needs Review |
| Email Notification Detail | `/notification/setting/email/:id` | Notifications | Video Tracking, Vehicle Media | `mceasy-vsms/src/router/allRoutes/notification.js:277` → `mceasy-vsms/src/router/views/notification/notificationsetting/detail/DeliveryForm` | Needs Review |
| Onboarding | `/onboarding` | Onboarding | — | `mceasy-vsms/src/router/routes.js:209` → `mceasy-vsms/src/router/views/onboarding/index` | Needs Review |
| Profile | `/profile/` | Profile | — | `mceasy-vsms/src/router/routes.js:234` → `mceasy-vsms/src/router/views/profile/index` | Needs Review |
| Add Email | `/profile/addemail` | Profile | — | `mceasy-vsms/src/router/routes.js:259` → `mceasy-vsms/src/router/views/profile/add/email` | Needs Review |
| Add Number | `/profile/addnumber` | Profile | — | `mceasy-vsms/src/router/routes.js:284` → `mceasy-vsms/src/router/views/profile/add/phoneNo` | Needs Review |
| Change Email | `/profile/changeemail` | Profile | — | `mceasy-vsms/src/router/routes.js:309` → `mceasy-vsms/src/router/views/profile/update/email` | Needs Review |
| Change Number | `/profile/changenumber` | Profile | — | `mceasy-vsms/src/router/routes.js:334` → `mceasy-vsms/src/router/views/profile/update/phoneNo` | Needs Review |
| Fleet Task Instant Create | `/fleet-task-instant/create` | Quick Assignment | — | `mceasy-vsms/src/router/allRoutes/fleet-task-instant.js:7` → `mceasy-vsms/src/router/views/fleet-task-instant/create-fleet-task-instant` | Needs Review |
| Fleet Task Instant Detail | `/fleet-task-instant/detail/:id` | Quick Assignment | — | `mceasy-vsms/src/router/allRoutes/fleet-task-instant.js:30` → `mceasy-vsms/src/router/views/fleet-task-instant/detail` | Needs Review |
| Fleet Task Instant Import | `/fleet-task-instant/import` | Quick Assignment | — | `mceasy-vsms/src/router/allRoutes/fleet-task-instant.js:65` → `mceasy-vsms/src/router/views/fleet-task-instant/import/index.vue` | Needs Review |
| Live Track Fleet Task Instant | `/fleet-task-instant/track/:data` | Quick Assignment | — | `mceasy-vsms/src/router/allRoutes/fleet-task-instant.js:53` → `mceasy-vsms/src/router/views/fleet-task-instant/live-track` | Needs Review |
| Report | `/report/` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:7` → `mceasy-vsms/src/router/views/report` | Needs Review |
| Report Alert | `/report/alert` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:508` → `mceasy-vsms/src/router/views/report/list/alert` | Needs Review |
| Report Cost Analysis | `/report/cost-analysis` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:798` → `mceasy-vsms/src/router/views/report/list/cost-analysis` | Needs Review |
| Custom Report | `/report/custom/:id` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:834` → `mceasy-vsms/src/router/views/report/components/CustomReportPage` | Needs Review |
| Report Delivery History | `/report/delivery-history` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:120` → `mceasy-vsms/src/router/views/report/tms/delivery-history` | Needs Review |
| Report Delivery Load | `/report/delivery-load` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:145` → `mceasy-vsms/src/router/views/report/tms/delivery-load` | Needs Review |
| Report Delivery Plan vs Actual | `/report/delivery-plan-vs-actual` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:170` → `mceasy-vsms/src/router/views/report/tms/delivery-plan-actual` | Needs Review |
| Report Detail PTO | `/report/detail-pto` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:596` → `mceasy-vsms/src/router/views/report/list/detail-pto` | Needs Review |
| Report Detail Vehicle Trip | `/report/detail-vehicle-trip` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:311` → `mceasy-vsms/src/router/views/report/list/detail-vehicle-trip` | Needs Review |
| Report Door | `/report/door` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:543` → `mceasy-vsms/src/router/views/report/list/door` | Needs Review |
| Report Driver Score | `/report/driver-score` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:708` → `mceasy-vsms/src/router/views/report/list/driver-score` | Needs Review |
| Report Expenses | `/report/expenses` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:195` → `mceasy-vsms/src/router/views/report/tms/expenses` | Needs Review |
| Report Fleet Utilization | `/report/fleet-utilization` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:853` → `mceasy-vsms/src/router/views/report/tms/fleet-utilization` | Needs Review |
| Report Fleet Utilization IJP | `/report/fleet-utilization-ijp` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:871` → `mceasy-vsms/src/router/views/report/list/fleet-utilization-ijp` | Needs Review |
| Report Fuel | `/report/fuel` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:329` → `mceasy-vsms/src/router/views/report/list/fuel` | Needs Review |
| Report Fuel Recapitulation | `/report/fuel-recapitulation` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:889` → `mceasy-vsms/src/router/views/report/list/fuel-recapitulation` | Needs Review |
| Report Trip Between Geofences | `/report/geofences-trip` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:726` → `mceasy-vsms/src/router/views/report/list/trips-between-geofences` | Needs Review |
| Report Geolocation | `/report/geolocation` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:418` → `mceasy-vsms/src/router/views/report/list/geolocation` | Needs Review |
| Report Geofence Duration | `/report/geolocation-durations` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:816` → `mceasy-vsms/src/router/views/report/list/geolocation-durations` | Needs Review |
| Report Route Geolocation | `/report/geolocationroute` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:237` → `mceasy-vsms/src/router/views/report/list/geolocationroute` | Needs Review |
| Report Historical Offline | `/report/historical-offline` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:614` → `mceasy-vsms/src/router/views/report/list/historical-offline` | Needs Review |
| Report History Connectivity Gps | `/report/history-connectivity-gps` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:632` → `mceasy-vsms/src/router/views/report/list/history-connectivity-gps` | Needs Review |
| Report History Route | `/report/history-route` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:744` → `mceasy-vsms/src/router/views/report/list/history-route` | Needs Review |
| Report Driver Management | `/report/management-driver` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:472` → `mceasy-vsms/src/router/views/report/list/management-driver` | Needs Review |
| Report Management Vehicle | `/report/management-vehicle` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:346` → `mceasy-vsms/src/router/views/report/list/management-vehicle` | Needs Review |
| Report Offline Device | `/report/offline-device` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:219` → `mceasy-vsms/src/router/views/report/list/offline-device` | Needs Review |
| Report Overspeed Duration | `/report/overspeed-duration` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:670` → `mceasy-vsms/src/router/views/report/list/overspeed-duration` | Needs Review |
| Report Scheduler | `/report/scheduler/` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:49` → `mceasy-vsms/src/router/views/report/scheduler` | Needs Review |
| Report Scheduler Create | `/report/scheduler/create` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:66` → `mceasy-vsms/src/router/views/report/scheduler/form` | Needs Review |
| Report Scheduler History | `/report/scheduler/history` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:102` → `mceasy-vsms/src/router/views/report/scheduler/history` | Needs Review |
| Report Scheduler Update | `/report/scheduler/update/:id` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:84` → `mceasy-vsms/src/router/views/report/scheduler/form` | Needs Review |
| Report Service Schedule | `/report/service-schedule` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:690` → `mceasy-vsms/src/router/views/report/list/service-schedule` | Needs Review |
| Report Summary Alert | `/report/summary-alert` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:490` → `mceasy-vsms/src/router/views/report/list/summary-alert` | Needs Review |
| Report Daily Summary Driver | `/report/summary-day-driver` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:454` → `mceasy-vsms/src/router/views/report/list/summary-day-driver` | Needs Review |
| Report Daily Summary Fuel | `/report/summary-day-fuel` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:400` → `mceasy-vsms/src/router/views/report/list/summary-fuel-daily` | Needs Review |
| Report Summary Day Vehicle | `/report/summary-day-vehicle` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:364` → `mceasy-vsms/src/router/views/report/list/summary-day-vehicle` | Needs Review |
| Report Summary Engine | `/report/summary-engine` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:436` → `mceasy-vsms/src/router/views/report/list/summary-engine` | Needs Review |
| Report Summary Engine PTO | `/report/summary-engine-pto` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:560` → `mceasy-vsms/src/router/views/report/list/summary-engine-pto` | Needs Review |
| Report Summary Fuel | `/report/summary-fuel` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:382` → `mceasy-vsms/src/router/views/report/list/summary-fuel` | Needs Review |
| Report Summary Geolocation | `/report/summary-geolocation` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:525` → `mceasy-vsms/src/router/views/report/list/summary-geolocation` | Needs Review |
| Report Summary Ritage | `/report/summary-ritage` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:925` → `mceasy-vsms/src/router/views/report/list/summary-ritage` | Needs Review |
| Report Summary Ritage Route | `/report/summary-ritage-route` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:762` → `mceasy-vsms/src/router/views/report/list/summary-ritage-route` | Needs Review |
| Report Summary Sensor Ciomas | `/report/summary-sensor-ciomas` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:907` → `mceasy-vsms/src/router/views/report/list/summary-sensor-ciomas` | Needs Review |
| Report Summary Stopped | `/report/summary-stopped` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:293` → `mceasy-vsms/src/router/views/report/list/summary-stopped` | Needs Review |
| Report Summary Working Hours | `/report/summary-working-hours` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:652` → `mceasy-vsms/src/router/views/report/list/summary-working-hours` | Needs Review |
| Report Temperature | `/report/temperature` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:275` → `mceasy-vsms/src/router/views/report/list/temperature` | Needs Review |
| Report Time Window | `/report/time-window` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:578` → `mceasy-vsms/src/router/views/report/list/time-window` | Needs Review |
| Report Vehicle Status | `/report/vehicle-status` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:780` → `mceasy-vsms/src/router/views/report/list/vehicle-status` | Needs Review |
| Report Vehicle Trip | `/report/vehicle-trip` | Reports | Delivery, Master Data, Maintenance | `mceasy-vsms/src/router/allRoutes/report.js:257` → `mceasy-vsms/src/router/views/report/list/vehicle-trip` | Needs Review |
| Route | `/route/` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:6` → `mceasy-vsms/src/router/views/route` | Needs Review |
| Route Monitoring | `/route/monitoring/` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:24` → `mceasy-vsms/src/router/views/route/monitoring/` | Needs Review |
| Route Tracking | `/route/monitoring/public-tracking` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:103` → `mceasy-vsms/src/router/views/route/public-tracking/` | Needs Review |
| Route Planning | `/route/planning/` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:42` → `mceasy-vsms/src/router/views/route/planning/` | Needs Review |
| Route Planning Form | `/route/planning/form/:routeRecordId?` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:66` → `mceasy-vsms/src/router/views/route/planning/form` | Needs Review |
| Route Planning Update History | `/route/planning/update-history/:routeRecordId` | Route Management | — | `mceasy-vsms/src/router/allRoutes/route.js:84` → `mceasy-vsms/src/router/views/route/planning/listhistory` | Needs Review |
| Route Optimization | `/route-optimization` | Route Optimization | Delivery, Master Data | `mceasy-vsms/src/router/allRoutes/route-optimization.js:18` → `mceasy-vsms/src/router/views/route-optimization` | Needs Review |
| Route Optimization Detail | `/route-optimization/:id` | Route Optimization | Delivery, Master Data | `mceasy-vsms/src/router/allRoutes/route-optimization.js:52` → `mceasy-vsms/src/router/views/route-optimization/detail` | Needs Review |
| Route Reoptimization Setting | `/route-optimization/:id/re-optimize` | Route Optimization | Delivery, Master Data | `mceasy-vsms/src/router/allRoutes/route-optimization.js:86` → `mceasy-vsms/src/router/views/route-optimization/re-optimize` | Needs Review |
| Route Optimization Detail Setting | `/route-optimization/:id/setting` | Route Optimization | Delivery, Master Data | `mceasy-vsms/src/router/allRoutes/route-optimization.js:69` → `mceasy-vsms/src/router/views/route-optimization/setting` | Needs Review |
| Route Optimization Create | `/route-optimization/create` | Route Optimization | Delivery, Master Data | `mceasy-vsms/src/router/allRoutes/route-optimization.js:35` → `mceasy-vsms/src/router/views/route-optimization/create` | Needs Review |
| Sales Order | `/sales-order` | Sales Orders | — | `mceasy-vsms/src/router/allRoutes/sales-order.js:6` → `mceasy-vsms/src/router/views/sales-order` | Needs Review |
| Sales Order Detail | `/sales-order/:id` | Sales Orders | — | `mceasy-vsms/src/router/allRoutes/sales-order.js:50` → `mceasy-vsms/src/router/views/sales-order/detail` | Needs Review |
| Sales Order Create | `/sales-order/create` | Sales Orders | — | `mceasy-vsms/src/router/allRoutes/sales-order.js:28` → `mceasy-vsms/src/router/views/sales-order/detail` | Needs Review |
| Setting Deprecated | `/setting-deprecated/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:37` → `mceasy-vsms/src/router/views/setting` | Needs Review |
| Setting | `/setting/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:8` → `mceasy-vsms/src/router/views/setting/index-v2` | Needs Review |
| Setting Additional Cost | `/setting/additional-cost/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:719` → `mceasy-vsms/src/router/views/setting/additional-cost` | Needs Review |
| Management Asset | `/setting/asset/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1111` → `mceasy-vsms/src/router/views/setting/asset` | Needs Review |
| Management GPS | `/setting/asset/gps` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1048` → `mceasy-vsms/src/router/views/setting/asset/setGps` | Needs Review |
| History GPS | `/setting/asset/gps/history/:imei` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1067` → `mceasy-vsms/src/router/views/setting/asset/components/gps/historyGps` | Needs Review |
| Management Domain | `/setting/asset/subDomain` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1026` → `mceasy-vsms/src/router/views/setting/asset/subDomain` | Needs Review |
| List Company Profile Setting | `/setting/company/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:351` → `mceasy-vsms/src/router/views/setting/company` | Needs Review |
| Company Profile Address | `/setting/company/address` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:374` → `mceasy-vsms/src/router/views/master/address/form` | Needs Review |
| Company Profile Address Update | `/setting/company/address/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:397` → `mceasy-vsms/src/router/views/master/address/form` | Needs Review |
| Setting Cost Category | `/setting/cost-category/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1087` → `mceasy-vsms/src/router/views/setting/cost-category` | Needs Review |
| Setting Custom Field | `/setting/custom-field/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1133` → `mceasy-vsms/src/router/views/setting/custom-field` | Needs Review |
| Setting Custom Field Delivery | `/setting/custom-field/delivery` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1160` → `mceasy-vsms/src/router/views/setting/custom-field/delivery` | Needs Review |
| Setting Custom Field Quick Assignment | `/setting/custom-field/quick-assignment` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1183` → `mceasy-vsms/src/router/views/setting/custom-field/quick-assignment` | Needs Review |
| Setting Delivery | `/setting/delivery/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:766` → `mceasy-vsms/src/router/views/setting/delivery` | Needs Review |
| List Employee Setting | `/setting/employee/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:302` → `mceasy-vsms/src/router/views/setting/employee` | Needs Review |
| Setting Engine Off Automation | `/setting/engine-off/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1333` → `mceasy-vsms/src/router/views/setting/cut-off/index.vue` | Needs Review |
| Detail Setting Engine Off Automation | `/setting/engine-off/detail/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1357` → `mceasy-vsms/src/router/views/setting/cut-off/form.vue` | Needs Review |
| History Setting Engine Off Automation | `/setting/engine-off/history/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1401` → `mceasy-vsms/src/router/views/setting/cut-off/contents/HistoryTab` | Needs Review |
| Import Setting Engine Off Automation | `/setting/engine-off/import/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1377` → `mceasy-vsms/src/router/views/setting/cut-off/import/index.vue` | Needs Review |
| Setting Fleet Task | `/setting/fleet-task/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:789` → `mceasy-vsms/src/router/views/setting/fleet-task` | Needs Review |
| List Fleet Setting | `/setting/fleet/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:500` → `mceasy-vsms/src/router/views/setting/fleet` | Needs Review |
| List Fleet Group Setting | `/setting/fleetgroup` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:422` → `mceasy-vsms/src/router/views/setting/fleetgroup` | Needs Review |
| Form Fleet Group | `/setting/fleetgroup/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:473` → `mceasy-vsms/src/router/views/setting/fleetgroup/form` | Needs Review |
| Fleet Group Detail | `/setting/fleetgroup/update/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:446` → `mceasy-vsms/src/router/views/setting/fleetgroup/form` | Needs Review |
| List General Setting | `/setting/general/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:327` → `mceasy-vsms/src/router/views/setting/general` | Needs Review |
| Setting Live View | `/setting/live-view` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:586` → `mceasy-vsms/src/router/views/setting/liveview` | Needs Review |
| List Maintenance Setting | `/setting/maintenance` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:519` → `mceasy-vsms/src/router/views/setting/maintenance` | Needs Review |
| Log Maintenance Setting | `/setting/maintenance/log/:type` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:532` → `mceasy-vsms/src/router/views/setting/maintenance/logHistory` | Needs Review |
| Setting Service Parts | `/setting/maintenance/parts` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:571` → `mceasy-vsms/src/router/views/setting/maintenance/parts` | Needs Review |
| Setting Service Activity | `/setting/maintenance/service` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:600` → `mceasy-vsms/src/router/views/setting/maintenance/service` | Needs Review |
| Import Service Activity | `/setting/maintenance/service/upload` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:615` → `mceasy-vsms/src/router/views/setting/maintenance/service/importComponentService` | Needs Review |
| Setting Notification List | `/setting/notification` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1279` → `mceasy-vsms/src/router/views/setting/notification` | Needs Review |
| Add Setting Notification | `/setting/notification/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1297` → `mceasy-vsms/src/router/views/setting/notification/formV2` | Needs Review |
| Detail Setting Notification | `/setting/notification/detail/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1315` → `mceasy-vsms/src/router/views/setting/notification/formV2` | Needs Review |
| List Odometer Setting | `/setting/odometer` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:548` → `mceasy-vsms/src/router/views/setting/odometer` | Needs Review |
| Management Whitelabel | `/setting/personalization/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:916` → `mceasy-vsms/src/router/views/setting/personalization` | Needs Review |
| Management Banner | `/setting/personalization/banner` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:984` → `mceasy-vsms/src/router/views/setting/personalization/banner` | Needs Review |
| Management Color | `/setting/personalization/color` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:942` → `mceasy-vsms/src/router/views/setting/personalization/color` | Needs Review |
| Company Contact | `/setting/personalization/contact` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1005` → `mceasy-vsms/src/router/views/setting/personalization/contact` | Needs Review |
| Management Logo | `/setting/personalization/logo` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:963` → `mceasy-vsms/src/router/views/setting/personalization/logo` | Needs Review |
| Setting Product | `/setting/product/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:743` → `mceasy-vsms/src/router/views/setting/product` | Needs Review |
| Setting Shift | `/setting/shift/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1421` → `mceasy-vsms/src/router/views/setting/shift` | Needs Review |
| Setting Shift Create | `/setting/shift/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1437` → `mceasy-vsms/src/router/views/setting/shift/form` | Needs Review |
| Setting Shift Detail | `/setting/shift/detail/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1454` → `mceasy-vsms/src/router/views/setting/shift/form` | Needs Review |
| Setting Template Delivery Order | `/setting/template/delivery-order/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:78` → `mceasy-vsms/src/router/views/setting/template/delivery-order` | Needs Review |
| Setting Template Delivery Order Detail | `/setting/template/delivery-order/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:124` → `mceasy-vsms/src/router/views/setting/template/delivery-order/detail` | Needs Review |
| Setting Template Delivery Order Create | `/setting/template/delivery-order/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:100` → `mceasy-vsms/src/router/views/setting/template/delivery-order/detail` | Needs Review |
| Setting Fleet Task Expense | `/setting/template/fleet-task-expense/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:148` → `mceasy-vsms/src/router/views/setting/template/fleet-task-expense` | Needs Review |
| Detail Fleet Task Expense | `/setting/template/fleet-task-expense/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:196` → `mceasy-vsms/src/router/views/setting/template/fleet-task-expense/create` | Needs Review |
| Create Fleet Task Expense | `/setting/template/fleet-task-expense/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:172` → `mceasy-vsms/src/router/views/setting/template/fleet-task-expense/create` | Needs Review |
| Setting Token | `/setting/token` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:632` → `mceasy-vsms/src/router/views/setting/token` | Needs Review |
| Setting Token API | `/setting/token-api` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:647` → `mceasy-vsms/src/router/views/setting/development` | Needs Review |
| Setting Token API V1 | `/setting/token-api/v1` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:670` → `mceasy-vsms/src/router/views/setting/development/token-v1` | Needs Review |
| Setting Token API V2 | `/setting/token-api/v2` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:694` → `mceasy-vsms/src/router/views/setting/development/token-v2` | Needs Review |
| Setting Tracker & Sensor | `/setting/tracker-sensor/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:812` → `mceasy-vsms/src/router/views/setting/tracker-sensor` | Needs Review |
| Fuel Sensor Setting | `/setting/tracker-sensor/fuel` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:876` → `mceasy-vsms/src/router/views/setting/tracker-sensor/fuel` | Needs Review |
| Update Fuel Sensor Setting | `/setting/tracker-sensor/fuel/update/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:895` → `mceasy-vsms/src/router/views/setting/tracker-sensor/fuel/UpdateFuel` | Needs Review |
| Idle & Parking Limit Times | `/setting/tracker-sensor/idle-parking` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:831` → `mceasy-vsms/src/router/views/setting/tracker-sensor/idle-parking` | Needs Review |
| Idle & Parking Limit Times Update | `/setting/tracker-sensor/idle-parking/update/:vehicleId` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:852` → `mceasy-vsms/src/router/views/setting/tracker-sensor/idle-parking/UpdateIdle` | Needs Review |
| List User Setting | `/setting/user/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:222` → `mceasy-vsms/src/router/views/setting/user` | Needs Review |
| Create Setting Group User | `/setting/user/groupcreate` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:248` → `mceasy-vsms/src/router/views/setting/user/GroupCreate` | Needs Review |
| Update Setting Group User | `/setting/user/groupupdate/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:275` → `mceasy-vsms/src/router/views/setting/user/GroupCreate` | Needs Review |
| Setting Webhook | `/setting/webhook` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1208` → `mceasy-vsms/src/router/views/setting/webhook` | Needs Review |
| Create Webhook | `/setting/webhook/create` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1225` → `mceasy-vsms/src/router/views/setting/webhook/form` | Needs Review |
| Detail Webhook | `/setting/webhook/detail/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1261` → `mceasy-vsms/src/router/views/setting/webhook/WebhookDetail` | Needs Review |
| Update Webhook | `/setting/webhook/update/:id` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:1243` → `mceasy-vsms/src/router/views/setting/webhook/form` | Needs Review |
| Sub Setting | `/subsetting/` | Settings | Delivery, Fleet Tasks, Maintenance | `mceasy-vsms/src/router/allRoutes/setting.js:65` → `mceasy-vsms/src/router/views/setting/subsetting` | Needs Review |
| Components | `/components/:name` | Support & Utility | — | `mceasy-vsms/src/router/allRoutes/others.js:86` | Needs Review |
| Contact Us | `/contactus/` | Support & Utility | — | `mceasy-vsms/src/router/allRoutes/others.js:43` → `mceasy-vsms/src/router/views/contactus/` | Needs Review |
| help | `/help/` | Support & Utility | — | `mceasy-vsms/src/router/allRoutes/others.js:6` → `mceasy-vsms/src/router/views/help/` | Needs Review |
| User Logs | `/logs/` | Support & Utility | — | `mceasy-vsms/src/router/allRoutes/others.js:68` → `mceasy-vsms/src/router/views/log/` | Needs Review |
| Tracking Temporary Liveview | `/fleet/live-track/:id` | Temporary Tracking | Master Data | `mceasy-vsms/src/router/allRoutes/trackingTemp.js:79` → `mceasy-vsms/src/router/views/trackingtemp/liveview` | Needs Review |
| Tracking Temporary | `/trackingtemp/` | Temporary Tracking | Master Data | `mceasy-vsms/src/router/allRoutes/trackingTemp.js:7` → `mceasy-vsms/src/router/views/trackingtemp/` | Needs Review |
| Tracking Temporary Add | `/trackingtemp/create` | Temporary Tracking | Master Data | `mceasy-vsms/src/router/allRoutes/trackingTemp.js:25` → `mceasy-vsms/src/router/views/trackingtemp/form` | Needs Review |
| Tracking Temporary Map | `/trackingtemp/liveview` | Temporary Tracking | Master Data | `mceasy-vsms/src/router/allRoutes/trackingTemp.js:61` → `mceasy-vsms/src/router/views/trackingtemp/liveview` | Needs Review |
| Tracking Temporary Update | `/trackingtemp/update/:id` | Temporary Tracking | Master Data | `mceasy-vsms/src/router/allRoutes/trackingTemp.js:43` → `mceasy-vsms/src/router/views/trackingtemp/form` | Needs Review |
| Unsubscribe Digest | `/unsubscribe/digest/:type` | Unsubscribe | — | `mceasy-vsms/src/router/allRoutes/unsubscribe.js:3` → `mceasy-vsms/src/router/views/unsubscribe/digest` | Needs Review |
| Unsubscribe Digest Result | `/unsubscribe/digest/:type/result` | Unsubscribe | — | `mceasy-vsms/src/router/allRoutes/unsubscribe.js:21` → `mceasy-vsms/src/router/views/unsubscribe/digest/ResultPage` | Needs Review |
| Vehicle Media | `/vehicle-media` | Vehicle Media | — | `mceasy-vsms/src/router/allRoutes/trackvision.js:67` → `mceasy-vsms/src/router/views/media/` | Needs Review |
| Video History Trackvision | `/video-history/` | Video History | — | `mceasy-vsms/src/router/allRoutes/trackvision.js:28` → `mceasy-vsms/src/router/views/video-history/indexV2` | Needs Review |
| Video History Trackvision Download | `/video-history/download` | Video History | — | `mceasy-vsms/src/router/allRoutes/trackvision.js:50` → `mceasy-vsms/src/router/views/video-history/download` | Needs Review |
| Video History 3 | `/videohistory-3/:vehicleId?` | Video History | — | `mceasy-vsms/src/router/allRoutes/videoHistory.js:27` → `mceasy-vsms/src/router/views/video-history/` | Needs Review |
| Video History 3 Download | `/videohistory-3/download` | Video History | — | `mceasy-vsms/src/router/allRoutes/videoHistory.js:6` → `mceasy-vsms/src/router/views/video-history/download` | Needs Review |
| Track Video V2 | `/trackvideo-2/` | Video Tracking | — | `mceasy-vsms/src/router/allRoutes/trackVideo.js:26` → `mceasy-vsms/src/router/views/live-streaming/` | Needs Review |
| Track Video | `/trackvideo/` | Video Tracking | — | `mceasy-vsms/src/router/allRoutes/trackVideo.js:6` | Needs Review |

## 4. Module Catalog

“Partial” means routes/pages are inventoried but comprehensive behavior is intentionally not documented. Detail paths are planned, not existing files.

| Module | Detail File | Known Pages | Coverage |
| --- | --- | ---: | --- |
| Authentication | `modules/authentication.md` (planned) | 9 | Partial |
| CDM Security Monitoring | `modules/cdm-security-monitoring.md` (planned) | 1 | Partial |
| Chat | `modules/chat.md` (planned) | 1 | Partial |
| Company Tickets | `modules/company-tickets.md` (planned) | 1 | Partial |
| Control Tower | `modules/control-tower.md` (planned) | 2 | Partial |
| Cost Management | `modules/cost-management.md` (planned) | 7 | Partial |
| Customer Contracts | `modules/customer-contracts.md` (planned) | 2 | Partial |
| Dashboard | `modules/dashboard.md` (planned) | 5 | Partial |
| Delivery | `modules/delivery.md` (planned) | 9 | Partial |
| Delivery Requests | `modules/delivery-requests.md` (planned) | 3 | Partial |
| Delivery Scheduler | `modules/delivery-scheduler.md` (planned) | 3 | Partial |
| Driver Score | `modules/driver-score.md` (planned) | 4 | Partial |
| Fleet Availability | `modules/fleet-availability.md` (planned) | 1 | Partial |
| Fleet Tasks | `modules/fleet-tasks.md` (planned) | 8 | Partial |
| Integration | `modules/integration.md` (planned) | 1 | Partial |
| Invoices | `modules/invoices.md` (planned) | 4 | Partial |
| Land Measurement | `modules/land-measurement.md` (planned) | 3 | Partial |
| Licenses | `modules/licenses.md` (planned) | 7 | Partial |
| Live Streaming | `modules/live-streaming.md` (planned) | 1 | Partial |
| Live View | `modules/live-view.md` (planned) | 1 | Partial |
| Maintenance | `modules/maintenance.md` (planned) | 23 | Partial |
| Marketplace | `modules/marketplace.md` (planned) | 2 | Partial |
| Master Data | `modules/master-data.md` (planned) | 63 | Partial |
| Notifications | `modules/notifications.md` (planned) | 14 | Partial |
| Onboarding | `modules/onboarding.md` (planned) | 1 | Partial |
| Profile | `modules/profile.md` (planned) | 5 | Partial |
| Quick Assignment | `modules/quick-assignment.md` (planned) | 4 | Partial |
| Reports | `modules/reports.md` (planned) | 49 | Partial |
| Route Management | `modules/route-management.md` (planned) | 6 | Partial |
| Route Optimization | `modules/route-optimization.md` (planned) | 5 | Partial |
| Sales Orders | `modules/sales-orders.md` (planned) | 3 | Partial |
| Settings | `modules/settings.md` (planned) | 68 | Partial |
| Support & Utility | `modules/support-and-utility.md` (planned) | 4 | Partial |
| Temporary Tracking | `modules/temporary-tracking.md` (planned) | 5 | Partial |
| Unsubscribe | `modules/unsubscribe.md` (planned) | 2 | Partial |
| Vehicle Media | `modules/vehicle-media.md` (planned) | 1 | Partial |
| Video History | `modules/video-history.md` (planned) | 4 | Partial |
| Video Tracking | `modules/video-tracking.md` (planned) | 2 | Partial |

## 5. Cross-Module Relationships

| Source Module | Related Module | Relationship | Evidence Source | Confidence / Status |
| --- | --- | --- | --- | --- |
| Dashboard | Driver Score | Dashboard widgets navigate to the Driver Score list. | `mceasy-vsms/src/router/views/dashboards/default.vue:3078` | Confirmed by Source |
| Dashboard | Maintenance | Dashboard source contains an embedded service scheduler view. | `mceasy-vsms/src/router/views/dashboards/contents/maintenance/ServiceScheduler.vue` | Confirmed by Source |
| Dashboard | Delivery | Dashboard source contains order-management views and delivery-status widgets. | `mceasy-vsms/src/router/views/dashboards/contents/OrderManagement.vue`; `mceasy-vsms/src/router/views/dashboards/components/DeliveryStatusWidget.vue` | Confirmed by Source |
| Delivery Requests | Fleet Tasks | The route tree exposes `/fleet-task-request/:id` with a fleet-task request detail component. | `mceasy-vsms/src/router/allRoutes/deliveryRequest.js:46` | Confirmed by Source |
| Fleet Tasks | Delivery | Fleet-task forms attach and transfer delivery orders and import the delivery-order API. | `mceasy-vsms/src/router/views/fleet-task/form-v2.vue:1276`; `mceasy-vsms/src/router/views/fleet-task/form-v2.vue:1319` | Confirmed by Source |
| Delivery | Invoices | Delivery routing registers a delivery-invoice form backed by an invoice component. | `mceasy-vsms/src/router/allRoutes/delivery.js:129` | Confirmed by Source |
| Invoices | Delivery | Invoice creation uses delivery-list and delivery-focused components. | `mceasy-vsms/src/router/allRoutes/delivery.js:171`; `mceasy-vsms/src/router/views/invoice/components/Delivery/index.vue` | Confirmed by Source |
| Route Optimization | Delivery | The optimization wizard has an Attach Delivery step and delivery-order IDs. | `mceasy-vsms/src/router/views/route-optimization/create.vue:48`; `mceasy-vsms/src/router/views/route-optimization/create.vue:295` | Confirmed by Source |
| Route Optimization | Master Data | The optimization wizard selects vehicle IDs as resources. | `mceasy-vsms/src/router/views/route-optimization/create.vue:183`; `mceasy-vsms/src/router/views/route-optimization/lib/fields/vehicle-list-fields.js` | Confirmed by Source |
| Cost Management | Fleet Tasks | Travel-cost routes use the fleet-task-cost implementation. | `mceasy-vsms/src/router/allRoutes/costManagement.js:28` | Confirmed by Source |
| Cost Management | Master Data | Vehicle-cost routes and fields are explicit. | `mceasy-vsms/src/router/allRoutes/costManagement.js:70`; `mceasy-vsms/src/router/views/cost-management/lib/fields/vehicleCostFields.js` | Confirmed by Source |
| Notifications | Video Tracking | ADAS notification detail renders the shared video player. | `mceasy-vsms/src/router/views/notification/adas/detailmap.vue:6` | Confirmed by Source |
| Notifications | Vehicle Media | General notifications open a media modal for alert evidence. | `mceasy-vsms/src/router/views/notification/general/index.vue:294` | Confirmed by Source |
| Reports | Delivery | Delivery history, load, and plan-vs-actual reports are registered. | `mceasy-vsms/src/router/allRoutes/report.js:120`; `:145`; `:170` | Confirmed by Source |
| Reports | Master Data | Reports explicitly cover vehicle and driver management. | `mceasy-vsms/src/router/allRoutes/report.js:346`; `:472` | Confirmed by Source |
| Reports | Maintenance | A service-schedule report is registered. | `mceasy-vsms/src/router/allRoutes/report.js` → `src/router/views/report/list/service-schedule` | Confirmed by Source |
| Settings | Delivery | A delivery settings page is registered. | `mceasy-vsms/src/router/allRoutes/setting.js:766` | Confirmed by Source |
| Settings | Fleet Tasks | A fleet-task settings page is registered. | `mceasy-vsms/src/router/allRoutes/setting.js:789` | Confirmed by Source |
| Settings | Maintenance | Service activity configuration and import are registered. | `mceasy-vsms/src/router/allRoutes/setting.js:600`; `:615` | Confirmed by Source |
| Customer Contracts | Master Data | Customer-contract pages contain a vehicle table, though their route file is unregistered. | `mceasy-vsms/src/router/views/master/contract/customer-contract/components/VehiclesTable.vue` | Confirmed by Source |
| Control Tower | Temporary Tracking | Control Tower V2 contains a temporary-tracking modal; ownership is unclear. | `mceasy-vsms/src/router/views/controltower-2/Modal/ModalTempTracking.vue` | Needs Review |
| Chat | Dashboard | The `/chat` route resolves to the dashboards component; this may be a placeholder. | `mceasy-vsms/src/router/allRoutes/chat.js:5` | Needs Review |

## 6. Uncertainties and Validation Required

1. `/notification/` is registered twice as `Notification Log` and `Notifikasi`, backed by `indexV2` and `index`. Validate the effective/intended implementation.
2. `customer-contract.js` declares create/detail routes but is not imported by `routes.js`. Confirm whether it is missing, deprecated, or injected elsewhere.
3. Live View, Track Video, and Control Tower select implementations through source logic and/or flags. Validate active variants by company/environment.
4. Sidebar variants use permissions, module aliases, and feature flags. Route presence is not proof of role access.
5. Nested wrapper/empty-child pairs were collapsed when they describe one URL; declared-record counts retain them.
6. Unreferenced `index.vue` candidates are mostly nested UI. Notable legacy-looking candidates include `driverscore/index.vue`, `driverscore/configuration/index.vue`, `master/driver/index.vue`, and `setting/tracker/index.vue`; confirm whether any are independently reachable.
7. `/chat` resolves to the dashboard component. Confirm whether intentional, placeholder, or obsolete.
8. Horizontal navigation contains template/demo links. Validate whether that layout is deployed; unmatched links were not promoted into inventory.
9. Static inspection cannot verify runtime-only routes, remote UI, environment-specific registration, or backend-driven navigation.
10. Confirm whether this standalone repository is the agreed shared location or should later adopt `docs/knowledge/`.

## 7. Initial Inventory Statistics

| Measure | Discovered Count | Interpretation |
| --- | ---: | --- |
| Route declarations scanned | 340 | 338 registered plus 2 in an unregistered route file |
| Registered route records | 338 | Includes nested layout records and catch-all |
| Page / feature entries | 334 | Wrapper duplicates/catch-all excluded; duplicate implementations retained |
| Distinct route patterns | 333 | Parameters preserved |
| Modules | 38 | Source-supported ownership groupings |
| Relationships: Confirmed by Source | 20 | Direct route/component evidence |
| Relationships: Needs Review | 2 | Meaning needs validation |

Counts are discovered counts, not proof of absolute completeness.

## 8. Initial Change Log

| Date | Area | Detected Change | Affected Pages / Modules | Action |
| --- | --- | --- | --- | --- |
| 2026-10-11 | Initial generation | Source-derived inventory at revision `6cb2c0975` | Entire map | Pending user validation |

