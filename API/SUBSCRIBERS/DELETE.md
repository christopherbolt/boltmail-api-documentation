# Delete Subscriber

Delete a subscriber

Replace `TIMESTAMP` with timestamp (string  like '1535093670'), `PUBLICKEY` with public key (get it from [API keys tab](https://app.boltmail.nz/customer/api-keys/index) in your panel ), `{LIST-UNIQUE-ID}` with List Unique Id of the list and `{SUBSCRIBER-UNIQUE-ID}` with the Unique Id of the subscriber.

### HTTP Method
```
DELETE
```
### Endpoint
```
https://app.boltmail.nz/api/lists/{LIST-UNIQUE-ID}/subscribers/{SUBSCRIBER-UNIQUE-ID}
```
If you do not know the Unqiue Id of your subscriber you should first query the [Get Subscriber UID By Email](API/SUBSCRIBERS/SingleSubscriberByEmail.md) endpoint