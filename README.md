# Mihomo Linux Configuration

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Linux](https://img.shields.io/badge/Platform-Linux-blue.svg)](https://www.linux.org/)
[![Proxy: Clash](https://img.shields.io/badge/Proxy-Clash-green.svg)](https://github.com/MetaCubeX/mihomo)

A comprehensive and optimized Clash/Mihomo configuration for Linux systems with advanced proxy management, rule-based routing, and multi-interface support.

## 🌟 Features

### 🔧 Core Configuration
- **Multi-Port Support**: HTTP (7890), SOCKS (7891), Mixed (7893), Redir (9797), TProxy (9898)
- **TUN Mode**: System-level VPN with automatic routing
- **DNS Management**: Enhanced DNS with fake-ip mode and multiple fallback servers
- **Web Dashboard**: Built-in dashboard for configuration management
- **Health Checks**: Automatic proxy health monitoring

### 🌐 Proxy Groups
- **🤖 AUTO VPN**: Automatic fallback between Indonesia and Singapore WARP
- **🤖 AUTO DIRECT**: Automatic fallback between LAN and USB tethering
- **🇮🇩 WARP-ID**: Indonesia WARP servers
- **🇸🇬 WARP-SG**: Singapore WARP servers  
- **🇺🇸 WARP-US**: United States WARP servers
- **⚖️ Load Balancing**: Round-robin load balancing for optimal performance

### 🎯 Specialized Groups
- **Ai-Gh**: AI and GitHub services optimization
- **📺 STREAMING**: Streaming services (Netflix, Disney+, etc.)
- **🎮 GAMES**: Gaming services (Steam, BattleNet, EA Games)
- **GLOBAL**: Main proxy selection group

### 🛡️ Security & Privacy
- **Ad Blocking**: Comprehensive ad blocking rules
- **Privacy Protection**: Enhanced privacy with multiple DNS providers
- **Traffic Analysis**: TLS SNI sniffing and traffic analysis
- **Fake IP Filter**: Excludes sensitive domains from fake-ip mode

## 📁 Project Structure

```
mihomo-linux/
├── config.yaml              # Main configuration file
├── ASN.mmdb                 # ASN database for geo-routing
├── geoip.metadb             # GeoIP database
├── cache.db                 # Cache database
├── dashboard/               # Web dashboard files
├── ui/                      # Alternative UI files
├── provide/                 # Proxy provider configurations
│   ├── warp-id.yaml        # Indonesia WARP servers
│   ├── warp-sg.yaml        # Singapore WARP servers
│   ├── warp-us.yaml        # US WARP servers
│   ├── china.yaml          # China servers
│   ├── id.yaml             # Indonesia servers
│   ├── sg.yaml             # Singapore servers
│   ├── us.yaml             # US servers
│   ├── subscription.yaml   # Subscription servers
│   └── warp.yaml           # General WARP servers
└── rule_provider/          # Rule provider configurations
    ├── adblock.yaml        # Ad blocking rules
    ├── ai-gh.yaml          # AI/GitHub specific rules
    ├── battlenet.yaml      # BattleNet gaming rules
    ├── direct.yaml         # Direct connection rules
    ├── discord.yaml        # Discord rules
    ├── ea-games.yaml       # EA Games rules
    ├── facebook.yaml       # Facebook rules
    ├── instagram.yaml      # Instagram rules
    ├── reject.yaml         # Reject rules
    ├── speedtest.yaml      # Speed test rules
    ├── steam.yaml          # Steam gaming rules
    ├── streaming.yaml      # Streaming service rules
    ├── tiktok.yaml         # TikTok rules
    ├── umum.yaml           # General rules
    └── youtube.yaml        # YouTube rules
```

## 🚀 Quick Start

### Prerequisites
- Linux system with network interfaces
- Mihomo/Clash installed
- USB tethering or LAN connection available

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/latifangren/mihomo-linux.git
   cd mihomo-linux
   ```

2. **Configure network interfaces**
   - Ensure your USB tethering interface is named `usb-tether`
   - Ensure your LAN interface is named `enp0s25`
   - Modify these names in `config.yaml` if different

3. **Start Mihomo**
   ```bash
   mihomo -c config.yaml
   ```

4. **Access the dashboard**
   - Open your browser and go to `http://localhost:9090`
   - Default secret: `123456`

## ⚙️ Configuration Details

### Port Configuration
- **HTTP Proxy**: `7890` - Main HTTP proxy port
- **SOCKS Proxy**: `7891` - SOCKS5 proxy port
- **Mixed Port**: `7893` - Mixed proxy port
- **Redir Port**: `9797` - Redirection port
- **TProxy Port**: `9898` - Transparent proxy port
- **Web Dashboard**: `9090` - Configuration interface

### DNS Configuration
- **Primary DNS**: AdGuard, Google, Cloudflare (DoH)
- **Fallback DNS**: Same as primary with geo-filtering
- **Enhanced Mode**: Fake-IP for better performance
- **Listen Port**: `1053`

### TUN Configuration
- **Stack**: System-level VPN
- **Auto-route**: Automatic routing configuration
- **MTU**: 9000 for optimal performance
- **DNS Hijack**: Intercepts DNS queries on port 53

## 🎮 Gaming Optimization

### Supported Gaming Services
- **Steam**: Optimized routing for Steam services
- **BattleNet**: Blizzard games and services
- **EA Games**: Electronic Arts games
- **Discord**: Gaming communication platform

### Gaming Features
- **Low Latency**: Optimized proxy selection for gaming
- **UDP Support**: Full UDP support for gaming protocols
- **Auto-fallback**: Automatic failover for stable connections

## 📺 Streaming Services

### Supported Platforms
- **Netflix**: Optimized for different regions
- **Disney+**: Streaming service optimization
- **YouTube**: Enhanced YouTube experience
- **TikTok**: Social media optimization
- **Instagram**: Photo/video sharing platform
- **Facebook**: Social media platform

## 🔒 Security Features

### Ad Blocking
- Comprehensive ad blocking rules
- Privacy protection
- Malware domain blocking

### Privacy Protection
- **DNS Privacy**: DNS-over-HTTPS (DoH)
- **Traffic Analysis**: TLS SNI sniffing
- **Fake IP Filter**: Excludes sensitive domains

## 🌍 Geographic Optimization

### Regional Servers
- **Indonesia**: Local servers for better performance
- **Singapore**: Low-latency Asian gateway
- **United States**: Global access point
- **China**: Specialized routing for Chinese services

### Load Balancing
- **Round-robin**: Distributes traffic across multiple servers
- **Health Checks**: Automatic server health monitoring
- **Auto-fallback**: Seamless failover between servers

## 📊 Monitoring & Management

### Web Dashboard
- **Real-time Statistics**: Connection status and traffic
- **Proxy Management**: Easy proxy group switching
- **Rule Management**: Custom rule configuration
- **Logs**: Detailed connection logs

### Health Monitoring
- **Automatic Health Checks**: Every 5 minutes
- **Lazy Loading**: Health checks only when needed
- **Timeout Handling**: 5-second timeout for checks

## 🔧 Customization

### Adding New Proxies
1. Add proxy configuration to `provide/` directory
2. Update `proxy-providers` section in `config.yaml`
3. Add to appropriate proxy groups

### Custom Rules
1. Create new rule file in `rule_provider/` directory
2. Add rule provider configuration
3. Update rules section with new rule-set

### Interface Configuration
Modify the interface names in the `proxies` section:
```yaml
proxies:
  - name: USB-DIRECT
    type: direct
    interface-name: "your-usb-interface-name"
  
  - name: LAN-DIRECT
    type: direct
    interface-name: "your-lan-interface-name"
```

## 🐛 Troubleshooting

### Common Issues

1. **Interface Not Found**
   - Check interface names with `ip link show`
   - Update interface names in `config.yaml`

2. **DNS Issues**
   - Verify DNS port 1053 is not blocked
   - Check firewall settings

3. **TUN Mode Issues**
   - Ensure running with sufficient privileges
   - Check if TUN module is loaded

4. **Dashboard Access**
   - Verify port 9090 is accessible
   - Check secret configuration

### Debug Mode
Enable debug logging by changing `log-level` to `debug` in `config.yaml`:
```yaml
log-level: debug
```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/latifangren/mihomo-linux/issues)
- **Discussions**: [GitHub Discussions](https://github.com/latifangren/mihomo-linux/discussions)

## 🙏 Acknowledgments

- [Mihomo](https://github.com/MetaCubeX/mihomo) - The core proxy engine
- [Clash](https://github.com/Dreamacro/clash) - Original Clash project
- [BlackMatrix7](https://github.com/blackmatrix7/ios_rule_script) - Rule providers
- Community contributors for rule sets and configurations

---

**Note**: This configuration is optimized for Linux systems with specific network interfaces. Please adjust interface names and configurations according to your system setup. 