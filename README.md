# ==============================================
# System defualts
# ==============================================

# Avoid creating .DS_Store files on network volumes
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true

# Disable the 'Are you sure you want to open this application? 
defaults write com.apple.LaunchServices LSQuarantine -bool false

# Save JPEG for screenshots instead of PNG for small footprint\n"
defaults write com.apple.screencapture type jpg

# Show battery level percentage.
defaults write com.apple.menuextra.battery ShowPercent -string "YES"

# Minimize windows into application icon.
defaults write com.apple.dock minimize-to-application -int 1


# ==============================================
# Finder Settings
# ==============================================

# Show filename extensions 
defaults write NSGlobalDomain AppleShowAllExtensions -bool true

# Disable the warning when changing a file extension 
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false

# Show path bar
defaults write com.apple.finder ShowPathbar -bool true

# Show status bar
defaults write com.apple.finder ShowStatusBar -bool true

# Disable the warning before emptying the Trash
defaults write com.apple.finder WarnOnEmptyTrash -bool false

# Show icons for hard drives, servers, and removable media on the desktop
- defaults write com.apple.finder ShowExternalHardDrivesOnDesktop -bool true 
- defaults write com.apple.finder ShowHardDrivesOnDesktop -bool true 
- defaults write com.apple.finder ShowMountedServersOnDesktop -bool true 
- defaults write com.apple.finder ShowRemovableMediaOnDesktop -bool true

# Enable quit finder menu item.
defaults write com.apple.finder QuitMenuItem -int 1

# Enable list view by default.
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"

# Search the current folder by default.
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

## Security


# Enable Firewall (specific services, stealth mode, logging).
sudo defaults write /Library/Preferences/com.apple.alf globalstate -int 1
sudo defaults write /Library/Preferences/com.apple.alf stealthenabled -int 1
sudo defaults write /Library/Preferences/com.apple.alf loggingenabled -int 1

# Reload Firewall.
launchctl unload /System/Library/LaunchAgents/com.apple.alf.useragent.plist
sudo launchctl unload /System/Library/LaunchDaemons/com.apple.alf.agent.plist
sudo launchctl load /System/Library/LaunchDaemons/com.apple.alf.agent.plist
launchctl load /System/Library/LaunchAgents/com.apple.alf.useragent.plist

# Turn Bluetooth off.
sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 0
sudo launchctl unload /System/Library/LaunchDaemons/com.apple.blued.plist
sudo launchctl load /System/Library/LaunchDaemons/com.apple.blued.plist
