# Scout Inventory

This application enables a Scout Group to manage their inventory. Scout Troop Masters create events
(camps) and reserve material. The application is responsible for flagging overlapping lendings and
letting humans take care of the rest. Inventory Masters are responsible for managing the actual
data-entry of the inventory: pictures, description, etc.

Security is minimal: beyond being associated with a single Scout Group, all User in the same Group
can do everything: manage inventory, reserve products, etc.

## Main Use Cases

* Admin registers Group
* Admin registers first User in Group
    - Email, password, name
* User adds products to inventory
    - Products may have 0..N pictures
    - Products have a single description
    - Products may have 0..N notes from previous Events
    - Products belong to 0..N categories
* User adds User to Group
    - Email, password, name
* User removes User from Group
    - Last user can't leave
    - Can't remove self
* User registers Event
* User browses Products
    - Products that are already reserved for the same date range are be dimmed, to
        indicate unavailability
    - Products
* User reserves Product for Event
* User sends reservation request
* User browses list of Events
* User prints a reservation list for a specific Event
    - Each product on the list has a checkbox, for easy bookkeeping while on-site
* User adds a Note on a Product in an Event
    - Indicates future repairs or things that may have happened to the Product
    - It may be easier to display the reservation list and have a Notes field
        next to each event

## Technical Notes

This is a Ruby on Rails 5.2 application, running on Ruby 2.5 and using PostgreSQL 10.x.
