# The Legend of Zelda: Breath of the Wild 1.6.0
# 1080p
Makes Breath of the Wild run with 1080p instead of 900p in docked mode, resulting in a clearer picture on common resolutions.
</br></br>

# Disable FXAA
Disables the FXAA pass the game applies to the framebuffer in docked mode, so that the image can be cleanly downscaled or better post-process antialiasing solutions can be used such as Yuzu's SMAA implementation. Recommended with the 1080p mod.
</br></br>

# Anisotropic Filtering Fix

The mod fixes the black line artifact when anisotropic filtering (AF) is enabled in Yuzu, by setting the mipmap filter of the sampler that samples the shadow map depth texture from "linear" (trilinear) to "nearest" (bilinear). Yuzu only increases the maximum anisotropic filtering for trilinear samplers, so this effectively disables AF for the shadow map sampler, as the value of the maximum anisotropic filtering for this sampler is at 1x (no AF).

This mod also sets the terrain texture sampler to trilinear instead of bilinear. This essentially activates anisotropic filtering in the first place for the same reason (AF is only increased on trilinear samplers). I don't know why the game uses bilinear instead of trilinear sampling. Maybe because it looks sharper (less blending) when AF is not possible for performance reasons, as it is on the Switch hardware, or maybe it is an artistic choice.

### To see an effect you need to set anisotropic filtering to 2x, 4x, 8x or 16x in Yuzu's advanced graphics settings

<table width="100%">
  <tr>
  <th width="50%">Original - Black line artifact and no AF</td>
  <th width="50%">Fixed - Ground textures are much sharper and no shadow artifacts</td>
  </tr>
  <tr>
  <tr>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/bafb2aef039ef8d044dc66984d5f041681300d02/botw-anisotropic-broken.png"></td>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/bafb2aef039ef8d044dc66984d5f041681300d02/botw-anisotropic-fixed.webp"></td>
  </tr>
</table>


<table width="100%">
  <tr>
  <th width="50%">Shadows - broken</td>
  <th width="50%">Shadows - fixed</td>
  </tr>
  <tr>
  <tr>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/7118597e1a59d0e980d95c29777b35e25fb2d05b/botw-shadows-broken.png"></td>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/7118597e1a59d0e980d95c29777b35e25fb2d05b/botw-shadows-fixed.png"></td>
  </tr>
</table>

