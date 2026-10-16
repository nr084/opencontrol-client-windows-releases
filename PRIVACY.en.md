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

## Service and local files (0.6)

The interface runs as an ordinary user. The LocalSystem service receives VPN parameters and the password through a local Windows pipe with restricted permissions; remote clients are rejected. Credentials remain in memory for the connection, are not written to disk by the service and are not sent to the developer. Closing the client process ends its session.

When explicitly selected by the user, export and two-way synchronization write connections and saved passwords to a chosen local CFG. CFG passwords use Kerio's reversible D3S format; DPAPI protection applies to the OpenControl store, not a portable CFG. Synchronization includes deletions and can be unlinked in Settings. Uninstall preserves the user's store and selected external files.
