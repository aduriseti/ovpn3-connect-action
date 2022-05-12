Based on "https://github.com/golfzaptw/action-connect-ovpn/issues/36#issuecomment-746201549"

# Preparing repo secrets:
- OVPN_CONFIG: copy your raw .ovpn config to this secret - it cant reference any other cert,secret, or tls files - i.e. must be self-contained
- OVPN_USER: copy your username (if applicable) to this secret - NO NEWLINE
- OVPN_PASS: copy your password (if applicable) to this secret - NO NEWLINE

# Usage:
```
- name: Connect VPN
  uses: aduriseti/ovpn3-connect-action@v1
  with:
    ovpn-config:  ${{ secrets.OVPN_CONFIG }}
    vpn-user:     ${{ secrets.VPN_USER }}
    vpn-pass:     ${{ secrets.VPN_PASS }}
.........
USE VPN CONNECTION HERE
.........
- name: Kill VPN Connection
  if: always()
  run: |
    sudo pkill openvpn  
```