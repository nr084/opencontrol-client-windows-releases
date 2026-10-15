# Privacy

[Русский](PRIVACY.md)

OpenControl for Windows sends credentials to the corporate server you specify over
TLS after validating its certificate. IP packets matching server routes travel through
the encrypted tunnel. The organization operating the server determines its data
handling. The client developer does not provide access to that server.

There is no telemetry, advertising SDK or automatic log upload. Certificate inspection
contacts the selected server without sending a password. The external GitHub link opens
a GitHub page governed by GitHub’s policy.

Profiles are local. Retaining a password is optional and uses current-user Windows
DPAPI protection. Session-only passwords are not written to settings. The in-memory
activity history contains connection states, not traffic contents. Deleting a profile
removes its retained secret. MSI uninstall does not automatically remove profiles.

User-excluded networks use the regular connection outside VPN, including DNS servers within those networks. The exclusion list is stored locally and applies to all profiles. Windows notifications contain the connected profile name, never passwords.
