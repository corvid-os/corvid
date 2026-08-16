# Corvid OS

An Arch-based Linux distro built to look good, be good for gaming, be good
for development, and hold up as a daily driver — all at once, not a narrow
niche. GNOME or Hyprland at install time, our own modular installer (Python +
GTK4/libadwaita), Btrfs with snapper and grub-btrfs, pacman plus paru.

The project is split across separate repos under the
[`corvid-os`](https://github.com/corvid-os) org, one per component so each
can be pulled and versioned on its own: this repo (`corvid`) for
meta/documentation, [`installer`](https://github.com/corvid-os/installer) for
Corvid Installer, [`iso`](https://github.com/corvid-os/iso) for the archiso
profile that builds the live/install ISO,
[`branding`](https://github.com/corvid-os/branding) for logo, icons,
Plymouth/GRUB themes, wallpapers and the palette, and
[`pkgbuilds`](https://github.com/corvid-os/pkgbuilds) for the `corvid-*`
package repo.

The full design lives in a private `corvid-os/prompt-el` repo (`design.md`) —
the brainstorming stage with all its scattered working files, which used to
live in a `prompt-el/` folder here, got compressed and moved there once the
design phase (M0) wrapped up.

Design is done. Currently in progress: the installer skeleton (M1) — see
`code.md` in `corvid-os/prompt-el` and the roadmap in `design.md`.
