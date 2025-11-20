# Flight search automation

The automation is going to be used to find the best offers for 2 way flights and store them into an excel file.

Example of offers saved in an excel file:

<img width="1890" height="211" alt="Screenshot 2025-11-20 075959" src="https://github.com/user-attachments/assets/4e1f5084-9408-403f-96ab-38e6caceaf2d" />

The automation uses queue items to search for flight offers. The queue name used is "FlightsToSearch" and uses the following JSON schema:

```
{
  "type": "object",
  "properties": {
    "DepartureAirport": {
      "type": "string",
      "description": "The IATA code for the departure airport"
    },
    "ArrivalAirport": {
      "type": "string",
      "description": "The IATA code for the destination airport"
    },
    "NumberOfAdults": {
      "description": "The number of people that are going to travel",
      "type": "integer",
      "minimum": 0
    },
    "DepartureDate": {
      "type": "string",
      "format": "date",
      "description": "Departure date"
    },
    "ReturnDate": {
      "type": "string",
      "format": "date",
      "description": "Return date"
    }
  },
  "$schema": "http://json-schema.org/draft-07/schema#"
}
```
The results found are stored in a storage bucket, named "FlightSearchBucket".
