# Navigate To — Nav2 external skill

Marketplace package for the `navigate_to` capability (`external_ros_node` → Nav2 `NavigateToPose`).

```bash
npx agenticros skills install /navigate-to
# or: npx agenticros skills install chrismatthieu/navigate-to
# or: "skillRefs": ["chrismatthieu/navigate-to"]
```

AgenticROS does **not** launch Nav2. Bring up Nav2 on the robot (or sim), then install this skill and restart the gateway / MCP server.

## Mission example

```json
{
  "mission": {
    "name": "go to dock",
    "steps": [
      {
        "id": "nav",
        "capability": "navigate_to",
        "inputs": { "x": 2.1, "y": 0.4, "yaw": 0 }
      }
    ]
  }
}
```

## Requirements

- Nav2 advertising `navigate_to_pose` (namespaced under the robot namespace when applicable)
- Transport that supports actions (local DDS, rosbridge, or WebRTC). Zenoh action support depends on your bridge configuration.
