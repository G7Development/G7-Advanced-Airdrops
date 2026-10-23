# G7 Advanced Air Drops
**Author:** G7 Development  
**Resource folder:** `g7_airdrops`  
**Version:** 1.0.0

A new G7-authored resource architecture for configurable supply events, custom NUI alerts, server-validated crate claims, configurable rewards, expiry, admin controls, and an optional automatic event loop.

## Dependencies
- FiveM artifact supporting Lua 5.4
- `ox_lib`
- One supported framework/inventory combination for rewards (Qbox/QBCore with `qb-core` exports, ESX, or `ox_inventory`)

## Install
1. Place `g7_airdrops` in your resources folder.
2. Ensure your framework and inventory start before this resource.
3. Configure `shared/config.lua`; verify all reward item names exist in your inventory.
4. Add `ensure g7_airdrops` to `server.cfg`.
5. Grant admins ACE permission: `add_ace group.admin g7airdrops.admin allow`
6. Restart and inspect server/client console.

## Admin commands
- `/airdropcreate` — start a drop at your current position.
- `/airdropcancel [id]` — cancel one drop by ID or all active drops when no ID is supplied.
- `/airdropstatus` — show active/landed counts.
- `/airdropalerts` — mute/unmute custom NUI alerts locally.

The `/airdropcreate` command is admin-gated on the server when the request is processed. The configured cooldown applies to manual requests. `G7Drops.Drop.requireFlare` is disabled by default; if enabled, add the configured flare item to your inventory and use a separate item-use integration appropriate for your inventory.

## Configure
Edit `shared/config.lua` to change framework/inventory selection, admin groups, crate and aircraft models, drop positions, rewards, claim duration, active-drop cap, expiry, blip appearance, alert duration, and optional automatic events.

Rewards are awarded by the server only after a claim timer completes and the claimant is still close to the crate. Unknown item names or full inventories can cause individual rewards to fail. Test item names and framework export compatibility on a staging server before production.

## Notes
- Client-created world entities are local to each player. The server owns the drop state and reward decisions; for high-population production servers, consider a OneSync networked entity strategy and explicit entity ownership/cleanup.
- The aircraft/cargo visuals are best-effort client effects; actual server-side drop state is authoritative.
- The auto-event interval is configured in minutes. Automatic drops select from `G7Drops.Locations`.
- The initial locations are Cayo Perico examples. Replace them with locations appropriate to your map/server.
- This package was generated as a clean rebuild, not a line-by-line rename of the supplied resource. Runtime testing on your exact server is still required.


# G7 Advanced Air Drops Permissions
add_ace group.admin g7airdrops.admin allow
