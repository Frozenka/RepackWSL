# Eng :
## 🛠️ WSL Disk Space Optimization  

Are you using WSL and noticing an abnormally full disk, especially with **Exegol** after each update?  

💡 **Why does this happen?**  
WSL does not properly release disk space when a file is deleted. Even after cleaning up files or uninstalling packages, the occupied space remains unchanged.  

🔧 **Solution**: This PowerShell one-liner forces WSL disk optimization to reclaim lost space.  

---

## 🚀 Quick Execution  

📌 **Open PowerShell as administrator and run this command:**  
```powershell
wsl --shutdown; $vhdxPath = Get-ChildItem -Path "$env:LOCALAPPDATA\Packages" -Filter "CanonicalGroupLimited.Ubuntu_*" | Select-Object -First 1 | ForEach-Object { "$($_.FullName)\LocalState\ext4.vhdx" }; if (Test-Path $vhdxPath) { Optimize-VHD -Path $vhdxPath -Mode Full; Write-Output "Optimization completed: $vhdxPath" } else { Write-Output "ext4.vhdx file not found." }
```

   

# FR :
## 🛠️ Optimisation de l'espace disque WSL  

Vous utilisez WSL et constatez un problème d’espace disque anormalement plein, notamment avec **Exegol** après chaque mise à jour ?  

💡 **Pourquoi ce problème ?**  
WSL ne libère pas correctement l’espace disque lorsqu’un fichier est supprimé. Même après avoir nettoyé des fichiers ou désinstallé des packages, l’espace occupé reste inchangé.  

🔧 **Solution** : Ce one-liner PowerShell permet de forcer l’optimisation du disque de WSL pour récupérer l’espace perdu.  

---

## 🚀 Exécution rapide  

📌 **Ouvrez PowerShell en mode administrateur et exécutez cette commande :**  
```powershell
wsl --shutdown; $vhdxPath = Get-ChildItem -Path "$env:LOCALAPPDATA\Packages" -Filter "CanonicalGroupLimited.Ubuntu_*" | Select-Object -First 1 | ForEach-Object { "$($_.FullName)\LocalState\ext4.vhdx" }; if (Test-Path $vhdxPath) { Optimize-VHD -Path $vhdxPath -Mode Full; Write-Output "Optimisation terminée : $vhdxPath" } else { Write-Output "Fichier ext4.vhdx introuvable." }
```

