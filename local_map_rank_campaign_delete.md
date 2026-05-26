# Map Rank Tracker — DeleteCampaign

Permanently deletes a Map Rank Tracker campaign and all of its collected data.

Does not consume API units. Requires a Bearer Token.

## Endpoint

```
DELETE https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/:campaignId
```

## Path Parameters

| Parameter | Required | Type | Description |
|---|---|---|---|
| `campaignId` | Yes | string | Campaign UUID to delete. |

## Example Request

```
curl --request DELETE \
  --url https://api.semrush.com/apis/v4/map-rank-tracker/v0/campaigns/0410f1d2-2bdb-4554-a761-0c15d636105b \
  --header 'Authorization: Bearer ${YOUR_TOKEN}'
```

## Example Response

```json
{
  "meta": {
    "success": true,
    "status_code": 200,
    "request_id": "e5f62f24ec2cfebd6ac5aac8d5104e18"
  },
  "data": {}
}
```

## See Also

- [CreateCampaign](local_map_rank_campaign_create.md)
- [GetCampaign](local_map_rank_campaign_get.md)
- [UpdateCampaign](local_map_rank_campaign_update.md)
- [Map Rank Tracker Overview](local_map_rank_overview.md)
