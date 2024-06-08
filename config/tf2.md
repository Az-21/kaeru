```c
/// Sound
volume 0.2                                        // Game volume
snd_musicvolume 0.2                               // Music volume
voice_scale 1                                     // Fix choppy voice comms (receiver end)

/// Damage
hud_combattext_batching 1                         // Batch damage dealt for a time window
hud_combattext_batching_window 2                  // Batch damage for 2 seconds

/// Viewmodel settings
tf_use_min_viewmodels 1                           // Enable mini-viewmodels
fov_desired 90                                    // Field of view
viewmodel_fov 60                                  // Viewmodel field of view

/// Hitsound
tf_dingalingaling 1                               // Enable hitsound
tf_dingaling_volume 0.8                           // Hitsound volume
tf_dingalingaling_repeat_delay 0                  // Hitsound plays on every instance of damage
tf_dingaling_pitchmaxdmg 10                       // Deeper bass on hig damage
tf_dingaling_pitchmindmg 240                      // Tinny bass on low damage

/// Killsound
tf_dingalingaling_lasthit 1                       // Enable killsound
tf_dingaling_lasthit_volume 0.8                   // Killsound volume

/// General options
sensitivity 1.1                                   // Mouse sensitivity 
cl_autoreload 1                                   // Autoreload after a delay
hud_fastswitch 1                                  // Switch weapons instantly
cl_spraydisable 0                                 // Enable sprays
cl_cloud_settings 0                               // Don't sync settings to Steam Cloud
hud_classautokill 0                               // Don't kill player for switching class outside spawn

/// Sniper rifle
cl_autorezoom 0                                   // Don't re-zoom sinper rifle after firing
tf_sniper_fullcharge_bell 1                       // Play a sound cue to indicate sniper rifle is fully charged

/// Medigun
tf_medigun_autoheal 1                             // Continue healing without holding M1
hud_medichealtargetmarker 1                       // Show '+' icon over players who need healing
hud_medicautocallers 1                            // Damaged players automatically call for medic
hud_medicautocallersthreshold 99                  // Players below 99% health will automatically call for medic

/// Pyroland
pyro_vignette_distortion 0                        // Disable pyroland distortion
pyro_dof 0                                        // Disable pyroland depth of field
```
