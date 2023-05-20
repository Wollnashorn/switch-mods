# The Legend of Zelda: Tears of the Kingdom 1.1.0 - 1.1.1

# Anisotropic Filtering Fix
The mod fixes possible black line artifacts when anisotropic filtering (AF) is enabled in Yuzu, by setting the mipmap filter of the sampler that samples the shadow map depth texture from "linear" (trilinear) to "nearest" (bilinear). Yuzu only increases the maximum anisotropic filtering for trilinear samplers, so this effectively disables AF for the shadow map sampler, as the value of the maximum anisotropic filtering for this sampler is at 1x (no AF).

This mod also sets the terrain texture sampler to trilinear instead of bilinear. This essentially activates anisotropic filtering in the first place for the same reason (AF is only increased on trilinear samplers). I don't know why the game uses bilinear instead of trilinear sampling. Maybe because it looks sharper (less blending) when AF is not possible for performance reasons, as it is on the Switch hardware, or maybe it is an artistic choice.

### To see an effect you need to set anisotropic filtering to 2x, 4x, 8x or 16x in Yuzu's advanced graphics settings

<table width="100%">
  <tr>
  <th width="50%">Original - AF not working properly</td>
  <th width="50%">Fixed - Ground textures are sharper on shallow viewing angles</td>
  </tr>
  <tr>
  <tr>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/8698284c84b11028fd04340d6b2bbe9215efc4a8/totk-anisotropic-broken.webp"></td>
  <td><img src="https://gist.github.com/Wollnashorn/45e31c53f753788e194ddfbb3116de3c/raw/8698284c84b11028fd04340d6b2bbe9215efc4a8/totk-anisotropic-fixed.webp"></td>
  </tr>
</table>
