# Anisotropic Filtering Fix

The mod fixes the black line artifact when anisotropic filtering (AF) is enabled in Yuzu, by setting the mipmap filter of the sampler that samples the shadow map depth texture from "linear" (trilinear) to "nearest" (bilinear). Yuzu only increases the maximum anisotropic filtering for trilinear samplers, so this effectively disables AF for the shadow map sampler, as the value of the maximum anisotropic filtering for this sampler is at 1x (no AF).

This mod also sets the sampler for the terrain textures to trilinear instead of bilinear. This essentially activates anisotropic filtering in the first place, because of the same reason (AF is only increased on trilinear samplers). I don't know why the game uses bilinear instead of trilinear sampling. Maybe because it looks sharper (less blending) when AF is not possible, as on the Switch hardware for performance reasons, or it is a artistic choice.

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


<table width="100%">
  <tr>
  <th width="50%">Diffuse - AF not working</td>
  <th width="50%">Diffuse - fixed</td>
  </tr>
  <tr>
  <tr>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/bafb2aef039ef8d044dc66984d5f041681300d02/botw-diffuse-bilinear.png"></td>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/bafb2aef039ef8d044dc66984d5f041681300d02/botw-diffuse-trilinear.png"></td>
  </tr>
</table>

