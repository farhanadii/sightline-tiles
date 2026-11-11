# Sightline building tiles

Building outlines and street addresses for built-up Sydney, cut into small JSON tiles for the
[Sightline](https://sightline-haven.vercel.app) app. Served by GitHub Pages at
`https://farhanadii.github.io/sightline-tiles/tiles/`.

Built by `build_tiles.py` and `build_tiles_overture.py` in the Sightline project. Don't edit by hand.

## Format
- `tiles/index.json`: tile size in degrees (0.0025, about 250 m) and, for each row `y`, runs of
  `x` as `[first, count, ...]`. A tile key is `x_y` = `floor(lng / tile)_floor(lat / tile)`.
- `tiles/x_y.json`: `{"b": [buildings], "p": [address points]}`. A building has an `id`, an
  outline (`r`: `[[lat, lng], ...]`, or `q`: steps of 0.00001 degrees from the previous corner),
  and when known an address `a`, suburb `s`, name `n` and number of levels `l`.

- `area/sydney.json`: rents and sale prices by postcode (last two quarters), each suburb's postcode,
  and the list of `area/da/` squares. `area/da/x_y.json` (0.01 degree squares): development
  applications as `[lat, lng, address, what, status, cost, new dwellings, storeys, lodged]`.

- `area/postcodes.geojson`: postal areas with each postcode's typical unit and house sale (`unit`, `house`),
  for the app's price map.

## Sources and licences
- Postal areas: Australian Bureau of Statistics, ASGS 2021, CC BY 4.0.
- Rents and sale prices: NSW Rent and Sales Report, NSW Department of Communities and Justice,
  CC BY 4.0.
- Development applications: NSW Planning Portal Online DA Data API, NSW Department of Planning,
  Housing and Infrastructure, CC BY 4.0.
- © OpenStreetMap contributors, ODbL 1.0 (City of Sydney buildings).
- © Overture Maps Foundation, ODbL 1.0, including OpenStreetMap and machine-detected building
  footprints (suburban buildings).
- Street addresses from Overture Maps addresses, based on G-NAF © Geoscape Australia, licensed
  under the Open G-NAF End User Licence Agreement.

These tiles are a derived database and are shared under the same ODbL 1.0 licence.

Only open data is here: no Microburbs data and no Sightline estimates.
