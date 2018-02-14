# Scout Inventory

This application enables a Scout Group to manage their inventory. Scout Troop Masters create events
(camps) and reserve material. The application is responsible for flagging overlapping lendings and
letting humans take care of the rest. Inventory Masters are responsible for managing the actual
data-entry of the inventory: pictures, description, etc.

Security is minimal: beyond being associated with a single Scout Group, all Users in the same Group
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
    - Products that are already reserved for the same date range are dimmed, to
        indicate unavailability
    - The product list may be restricted to a single Category
* User reserves Product for Event
    - Actual dates for reservation are -1 .. +1, meaning if the event is from
        Thu to Sat, the actual reservation will be Wed to Sun
* User sends reservation request
    - The reservation request is sent to one or more people
    - The reservation request email has a link to see the list of products
    - The reservation request email can be printed as a check list for easy
        on-the-ground marking and note taking
    - The reservation request contains a short alpha-numeric string that identifies
        it and can be used to return to the same list later (think bit.ly short code)
* User browses list of Events
    - List displays events that have closed in the past two weeks and all future events
* User prints a reservation list for a specific Event
    - Each product on the list has a checkbox, for easy bookkeeping while on-site
* User adds a Note on a Product in an Event
    - Indicates future repairs or things that may have happened to the Product
    - It may be easier to display the reservation list and have a Notes field
        next to each event
* Admin registers product Category

## Product Examples

Scout Groups should record every possible products that a Scout Troop can take with them when they
go on an expedition:

* Flags
* Tents
* Kitchen ustensils
* Propane tanks
* Projectors
* etc.

# Technical Notes

This is a Ruby on Rails 5.2 application, running on Ruby 2.5 and using PostgreSQL 10.x.
