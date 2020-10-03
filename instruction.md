# Odoo SaaS Kit (Installation & Configuration)

# Main Databases

    Main Database, e.g. odoo.local: * install saas_portal and saas_portal_* (optional) modules
user: odoo@local.com
pwd: odoo11

    Server Database, e.g. s1.odoo.local * install saas_server
user: s1odoo@local.com
pwd: odoo11

## Data Directory:

create data_dir (e.g. /odoo/data), this will be used to store: filestore, sessions, addons
give enough permission to the user who's running odoo (sudo chmod 775 -R $USER data/ && sudo chown -R $USER data/), addon "data_dir" to odoo.conf file.

## Databases organisation:
- for SaaS: odoo.local
- for SaaS Server: s1.odoo.local
- for templates: t1.odoo.local, t2.odoo.local...
- for clients: c1.odoo.local, c2.odoo.local...
and for each database you need to add a DNS record (`echo "127.0.0.1 odoo.local" >> /etc/hosts` ...)

## Issues:
* Tempalate creation issue:
- Make sure `DB Names` is not empty before creating a client, (e.g. `c%i.odoo.local`)
- I had to modify send_expiration_info() in order to set a value for expiration date.
* Pages issues:
- Some addons add more pages (e.g. `/page/start`...), this pages need to be updated
* Other issues:
- I had to install more addons (saas_* and saas_portal_*)
- The script `saas.py` is working now (it can creates databases, plan...) but the Server instance doesn't work (cannot connect correctly)

