# Packs Repository Mirror Layout

This tree mimics the external GitHub Pages repository structure for dynamic quiz question packs.

Structure:
- packs/<theme>/<level>/<type>/current/*.json
  * theme: general (future: categories)
  * level: icebreaker | easy | medium | hard | expert
  * type: open_ended | multiple_choice
  * current: symlink/alias dir for latest version (future: v1, v2...)

Add new versions by creating v2/ then updating current/.

Index file (to be generated): index.json
