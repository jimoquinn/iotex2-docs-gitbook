# ioID Identities

{% hint style="info" %}
This documentation is being updated, please check back soon for up to date content.&#x20;
{% endhint %}

## Registed an IoTeX DePIN Project ID

```
ioctl ioid register "ProjectName"
```

## Set Project Name

```
Request ioIDs $NEW_NAME $PROJECT_ID
```

## Get Project Metadata

```
ioctl ioid project -p $PRJECT_ID
```

output:

```json
Project #41 detail:
{
	"projectContract": "0x6972C35dB95258DB79D662959244Eaa544812c5A",
	"name": "iotexlab3",
	"owner": "0x00e27ACAF1d3D58861DF710719fc97C43fC976f6",
	"deviceNFT": "0x0000000000000000000000000000000000000000",
	"appliedIoIDs": "1",
	"activedIoIDs": "0",
}
```

## Request ioIDs

```
ioctl ioid apply -p $PROJECT_ID -a $ID_COUNT
```

## Assign a Device NFT Contrac to a Ptoject

```
ioctl ioid device $DEVICE_NFT_CONTRACT_ADDRESS -p $PROJECT_ID
```
