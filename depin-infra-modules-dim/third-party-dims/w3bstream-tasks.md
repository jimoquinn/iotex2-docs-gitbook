# 👨‍💻 W3bstream Tasks

{% hint style="info" %}
This documentation is currently being updated. Please check back later for the latest version.
{% endhint %}

```go
type Task struct {
	// This is the task ID, it's unique within the W3bstream network
	ID             uint64   `json:"id"`
	// This is the DePIN Project ID, as minted on-chain within the ioID module
	ProjectID      uint64   `json:"projectID"`
	// This represent a specific version for the project file in case it's been updated
	ProjectVersion string   `json:"projectVersion"`
	// This array aggregates a number of data messages to be processed together
	Data           [][]byte `json:"data"`
	// This is the device (or "client") DID, as minted on-chain within the ioID module
	ClientID       string   `json:"clientID"`
	// This is the signature of the task from the sequencer who created the task (only tasks from trusted sequencers are processed by W3bstream in the current release)
	Signature      string   `json:"signature"`
}
```

{% @github-files/github-code-block %}
