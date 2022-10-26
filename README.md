[![Crates.io](https://img.shields.io/crates/v/bevy_4x_camera)](https://crates.io/crates/bevy_4x_camera)

A 4X style camera for bevy. [Demo](https://imgur.com/XIIDcIW)

Default Key Bindings:

- W / A / S / D / Arrow Keys / Mouse Left - Move along the horizontal plane
- Q / E / Mouse Right - Rotate around the center
- Mouse Wheel - Zoom

# Example

```rust
use bevy::prelude::*;
use bevy_4x_camera::{CameraRigBundle, FourXCameraPlugin};

fn main() {
    App::build()
        .add_plugins(DefaultPlugins)
        .add_plugin(FourXCameraPlugin)
        .add_startup_system(setup)
        .run();
}

fn setup(commands: &mut Commands) {
    commands
        // add the RTS-Camera-Bundle with config
        .spawn_bundle(CameraRigBundle::default())
        // add the actual camera as child
        .with_children(|cb| {
            cb.spawn_bundle(Camera3dBundle {
                transform: Transform::from_translation(Vec3::new(-20.0, 20., 0.0))
                    .looking_at(Vec3::ZERO, Vec3::Y),
                ..Default::default()
            });
        });
}
```

---

# Version Matching

| Bevy Version | `bevy_4x_camera` Version |
| ------------ | ------------------------ |
| `0.4.0`      | `0.1.*`                  |
| `0.8.0`      | `0.1.3`                  |
