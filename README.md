> **Announcement**
>
> Due to technical issues during the scheduled hackathon event, the new contest schedule
> will be as follows:
> **Now** start coding your solution
> **Wednesday 7:00 AM** Rest API will be published on this document
> **Wednesday 9:00 AM** The first order will be published
> **Every hour on the hour from Wednesday 9:00 AM to Thursday 7:00 PM** a new order will be published
> **Friday Morning** winner will be announced in front of all of ng-conf.  Glory and prizes will be had.

# ng-conf 2019 hackathon instructions

Welcome, intrepid engineer to Gamma Interstellar Shipping company! We are the first
(and currently only) service offering deliveries to any system throughout the Milky
Way Galaxy! We know that our monopoly in this industry won't last long, and that is
why we have enlisted you. The galaxy is a big place, and with so much demand for
movement of goods, it is easy to be wasteful of time and fuel by not first planning
the most cost-efficient route. If we are careless in this area, competitors will
quickly win over many of our best customers.

Our sales representatives are currently reaching out to clients and receiving shipping
orders. For each order, we need you to find a shipping route that requires the least
distance possible.

## Input

Here is an example shipping order:

```json
{
  "deliveries": [
    {
      "name": "ecstatic_mccarthy",
      "x": -980,
      "y": 970,
      "z": 2885
    },
    {
      "name": "angry_visvesvaraya",
      "x": -291,
      "y": -4816,
      "z": 1300
    },
    {
      "name": "admiring_heisenberg",
      "x": -2020,
      "y": -3532,
      "z": -1330
    },
    {
      "name": "sharp_goldberg",
      "x": 1811,
      "y": -2028,
      "z": -4328
    },
    {
      "name": "fervent_snyder",
      "x": -1656,
      "y": 4396,
      "z": 4160
    }
  ],
  "wormholes": [
    {
      "name": "suspicious_sinoussi",
      "alphaX": 3420,
      "alphaY": -3463,
      "alphaZ": 3175,
      "omegaX": -1068,
      "omegaY": -2432,
      "omegaZ": 4429
    }
  ],
  "hazards": [
    {
      "name": "hungry_allen",
      "x": 3228,
      "y": 2498,
      "z": 3421,
      "radius": 43
    }
  ]
}
```

### `deliveries`

Each object in the array describes a location where a delivery needs to be made.
For example:

```json
{
  "name": "ecstatic_mccarthy",
  "x": -980,
  "y": 970,
  "z": 2885
},
```

> **Note:**
>
> _Each shipping route starts at the shipment pickup location (0, 0, 0), and all
> other coordinates in the order are relative to that location in parsecs._

### `wormholes`

Wormholes that have been certified as stable are listed and available to use on the
shipping route. These wormholes allow instantaneous travel between two points (alpha
and omega). You may travel either way through the wormhole.
For example:

```json
{
  "name": "suspicious_sinoussi",
  "alphaX": 3420,
  "alphaY": -3463,
  "alphaZ": 3175,
  "omegaX": -1068,
  "omegaY": -2432,
  "omegaZ": 4429
}
```

### `hazards`

Not all of space is passable. Impassable zones near your shipping route will also be
specified. For political and/or insurance purposes, our ships are not allowed within
a distance specified in parsecs.

```json
{
  "name": "hungry_allen",
  "x": 3228,
  "y": 2498,
  "z": 3421,
  "radius": 43
}
```

## Output

Once you have determined the best route, you will need to submit your solution. The body
must be a JSON array. Each element of the array will list the next destination in the route. For wormholes, you will need to specify the step as an object as seen below.

For example:

```json
[
  "fervent_snyder",
  "admiring_heisenberg",
  "angry_visvesvaraya",
  { "wormholeName": "suspicious_sinoussi", "entryPoint": "omega" },
  "sharp_goldberg",
  "ecstatic_mccarthy"
]
```

> **Note**
>
> Your submission for a shipping order will be automatically rejected if you have
> submitted too recently. After your first submission for an order, you must wait
> 1 minute before submitting again. After your second submission for the same ordwer,
> you must wait 2 minutes, and so on. It is therefore in your best interest to only
> submit solutions you are confident in. DDoS attacks and other API abuse will not be
> tolerated.

## One more thing

Oh, and did we tell you? You are not alone. We have hired a whole crew of engineers
who will all be tackling this problem. Solutions for each shipping order will be
scored and points awarded according to the following rules:

- Each order will be worth `n` points, where `n` is the number of deliveries to be
  made.
- The submission that has the most efficient route (least number of kpc travelled)
  will be awarded `n` points, the submission with the second-most efficient route
  will be awarded `n-1` points, and so on.
- In the case that multiple submissions require the same travel distance, the
  submission received first will be awarded more points than subsequent submissions.

The engineer with the most points at the end of the contest will be declared the winner.
