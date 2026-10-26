# Data

`shipments_demo.csv` contains 600 newly generated demonstration rows. They are not real shipments or an excerpt of the original dataset. Use them to explore the workflow, not to reproduce the original metrics.

The supplied original file has 100,000 rows and 29 columns. Keep your original `shipments.csv` locally (ignored by Git), or set `SHIPMENTS_CSV` to its location. Data source and redistribution permission were not provided, so no license is asserted for it.

## Original columns

- `shipment_id`
- `origin_hub`
- `destination_hub`
- `route_id`
- `scheduled_departure`
- `distance_km`
- `product_weight_kg`
- `fragile`
- `transport_mode`
- `vehicle_id`
- `vehicle_reliability`
- `planned_transit_hours`
- `scheduled_arrival`
- `origin_congestion_idx`
- `dest_congestion_idx`
- `actual_departure`
- `actual_arrival`
- `delay_minutes`
- `origin_hub_name`
- `destination_hub_name`
- `origin_country`
- `destination_country`
- `origin_region`
- `destination_region`
- `origin_lat`
- `origin_lon`
- `destination_lat`
- `destination_lon`
- `route_name`

Times are parsed as month/day/year followed by 24-hour time. Distance is in kilometers, weights in kilograms, transit durations in hours, and delays in minutes. Negative delays represent early arrivals.
