# Navigate To — Nav2 external skill

Marketplace package for the `navigate_to` capability (`external_ros_node` → Nav2 `NavigateToPose`).

```bash
npx agenticros skills install @agenticros/navigate-to
# or: npx agenticros skills install chrismatthieu/navigate-to
# or: "skillRefs": ["@agenticros/navigate-to"]
```

AgenticROS does **not** launch Nav2 on a real robot. On **sim-amr**, use the built-in Nav2 bringup:

```bash
agenticros up sim-amr --nav2 --headless
npx agenticros skills install @agenticros/navigate-to
# then run_mission with navigate_to (see examples/navigate-to/)
```

On a physical robot, bring up your own Nav2 stack, then install this skill and restart the gateway / MCP server.

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

Clear sim goal (person cylinder is at `(2.5, 0)`): `{ "x": 2.0, "y": 1.0 }`.

## Requirements

- Nav2 advertising `navigate_to_pose` (namespaced under the robot namespace when applicable)
- Transport that supports actions (local DDS, rosbridge, or WebRTC). Zenoh action support depends on your bridge configuration.
- Sim: `agenticros up sim-amr --nav2` (requires `ros-$ROS_DISTRO-nav2-bringup`)
