# Orca Restaurant POS — Update Channel

Hosts the auto-update artifacts for Orca Restaurant POS (RestaurantPOS).

- **`manifest.json`** — update manifest read by the in-app updater
  (Back Office → Software Update). Served via raw:
  `https://raw.githubusercontent.com/Orcanxt/Restaurant-DesktopEXE/main/manifest.json`
- **EXE builds** — published as GitHub **Release** assets (download anonymously).

## Publishing a new build
1. Bump `<Version>` in `RestaurantPOS.csproj` (and `installer/OrcaPOS.iss`).
2. Build compressed: `dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:IncludeNativeLibrariesForSelfExtract=true -p:EnableCompressionInSingleFile=true`.
3. `gh release create vX.Y.Z RestaurantPOS.exe --repo Orcanxt/Restaurant-DesktopEXE`.
4. Update `manifest.json` (`version`, `url`, `sha256`) and push.