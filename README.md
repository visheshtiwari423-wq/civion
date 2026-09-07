# civion  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-full: 9999px;
  --shadow-sm: 0 1px 2px rgba(16, 24, 40, 0.05);
  --shadow-card: 0 2px 8px -2px rgba(16, 24, 40, 0.06), 0 1px 4px -1px rgba(16, 24, 40, 0.04);
  --shadow-md: 0 4px 16px -4px rgba(16, 24, 40, 0.08), 0 2px 6px -2px rgba(16, 24, 40, 0.04);
  --shadow-lg: 0 12px 32px -6px rgba(16, 24, 40, 0.12), 0 4px 12px -2px rgba(16, 24, 40, 0.06);
  --shadow-teal-glow: 0 0 24px rgba(15, 76, 92, 0.25);
  /* Transitions */
  --transition-fast: 150ms cubic-bezier(0.4, 0, 0.2, 1);
  --transition-normal: 250ms cubic-bezier(0.4, 0, 0.2, 1);
  --transition-smooth: 350ms cubic-bezier(0.16, 1, 0.3, 1);
}
# Push Civion to GitHub Repository
param(
    [string]$Token = ""
)
$RepoUrl = "https://github.com/visheshtiwari423-wq/civion.git"
if ($Token -ne "") {
    $RepoUrl = "https://${Token}@github.com/visheshtiwari423-wq/civion.git"
}
Write-Host "==========================================================" -ForegroundColor Cyan
Write-Host "  CIVION -> GITHUB REPOSITORY DEPLOYMENT" -ForegroundColor Green
Write-Host "  Target: https://github.com/visheshtiwari423-wq/civion.git" -ForegroundColor Yellow
Write-Host "==========================================================" -ForegroundColor Cyan
Set-Location $PSScriptRoot
git branch -M main
git remote remove origin 2>$null
git remote add origin $RepoUrl
git add .
git commit -m "first commit - complete civion platform with authority command center and resident portal" 2>$null
Write-Host ""
Write-Host "Pushing all code, styles, and configurations to GitHub..." -ForegroundColor Cyan
git push -u origin main
if ($LASTEXITCODE -eq 0) {
    Write-Host ""

