Launch templates are the modern version of launch configurations, which are now deprecated.

**Launch configurations**
❌ DEPRECATED
- Cannot modify
- Does not support spot instances


**Launch templates**
✅ Preferred and modern approach

- Cannot modify, but you **can create a new version**
- Each launch template can only support 1 type of instance, but an ASG can use multiple  launch templates.