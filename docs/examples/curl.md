# API Request Examples

## MLB Schedule

### Get MLB Schedule
```bash
curl -H "x-api-key: YOUR_API_KEY" \
     "https://api.twlvgaming.com/api/v1/mlb/schedule"
```

Example Response:
```json
[
  {
    "game_id": "778764",
    "game_date": "3/12",
    "game_datetime": "2025-03-12T19:10:00Z",
    "away_name": "Minnesota Twins",
    "home_name": "Boston Red Sox",
    "venue_name": "Fenway Park"
  },
  {
    "game_id": "778765",
    "game_date": "3/12",
    "game_datetime": "2025-03-12T20:05:00Z",
    "away_name": "New York Yankees",
    "home_name": "Toronto Blue Jays",
    "venue_name": "Rogers Centre"
  }
]
```

## Ticket Check

### Check Ticket Status
```bash
curl -H "x-api-key: YOUR_API_KEY" \
     "https://api.twlvgaming.com/api/v1/tickets/check?ticket_id=10111874"
```

Example Response:
```json
{
  "ticket": {
    "ticket_id": "10111874",
    "game_id": "778764",
    "game_date": "3/12",
    "game_status": "Final",
    "inning_state": "Bottom",
    "current_inning": 9,
    "away_team": "Minnesota Twins",
    "home_team": "Boston Red Sox",
    "away_runs": 5,
    "home_runs": 6,
    "total_strikeouts": 27,
    "ticket_home_score_range": "6-7",
    "ticket_away_score_range": "3-5",
    "ticket_strikeout_range": "20+",
    "rally_tab_payout_amount": 50,
    "ticket_status": "REDEEMED",
    "game_outcome_status": "WINNER",
    "away_score_match": "MATCH",
    "home_score_match": "MATCH",
    "strikeout_match": "MATCH",
    "is_added": true
  }
}
```

### Error Examples

#### Missing API Key
```bash
curl "https://api.twlvgaming.com/api/v1/tickets/check?ticket_id=10111874"
```

Response:
```json
{
  "error": "Unauthorized",
  "details": "Invalid or missing API key"
}
```

#### Invalid Ticket ID
```bash
curl -H "x-api-key: YOUR_API_KEY" \
     "https://api.twlvgaming.com/api/v1/tickets/check?ticket_id=99999999"
```

Response:
```json
{
  "error": "Not Found",
  "details": "Ticket not found with ID: 99999999"
}
```

#### Rate Limit Exceeded
```json
{
  "error": "Too Many Requests",
  "details": "Rate limit exceeded. Please try again later."
}
``` 