# eInk Art Gallery - Home Assistant Add-on

A Home Assistant add-on for the [eInk Art Gallery](https://github.com/kotope/eink-art-gallery) project, enabling seamless integration with Home Assistant for managing and displaying images on e-ink displays.

## About eInk Art Gallery

eInk Art Gallery is a standalone Docker-based application for managing and displaying images for e-ink displays. It provides:

- **Web-based Gallery Management UI** - Intuitive interface for managing your image collection
- **REST API** - Full-featured API for programmatic control
- **Display Configuration** - YAML-based configuration system for different e-ink display models
- **Metadata Management** - SQLite-based metadata tracking for images
- **Image Optimization** - Automatic image processing for e-ink displays

For more information about the core project, visit [eInk Art Gallery on GitHub](https://github.com/kotope/eink-art-gallery).

## Installation

### Prerequisites

- Home Assistant instance running
- Docker support enabled (most Home Assistant installations include this)
- ~200MB free disk space for the add-on

### Add the Repository

1. In Home Assistant, go to **Settings** → **Add-ons & automations** → **Add-on Store**
2. Click the menu icon (⋮) in the top-right corner
3. Select **Repositories**
4. Add the repository URL: `https://github.com/kotope/eink-art-gallery-addon`
5. Click **Add**

### Install the Add-on

1. Go back to the **Add-on Store**
2. Search for "eInk Art Gallery"
3. Click on the add-on
4. Click **Install**
5. Wait for installation to complete

### Start the Add-on

1. Click the **Start** button
2. Enable **Start on boot** if desired
3. The add-on will be available at `http://homeassistant.local:8112` (or your Home Assistant IP:8112)

## Configuration

### Basic Settings

The add-on exposes the following configuration options in Home Assistant:

- **Port** - Web interface port (default: 8112)
- **Data directory** - Shared storage location for images and metadata

### Storage

Images and metadata are stored in the Home Assistant **share** folder, making them persistent and accessible:

- `images/` - Directory for image files
- `metadata.db` - SQLite database for image metadata
- `config.json` - Application configuration

## Usage

### Web Interface

Access the web interface at:

```
http://<your-home-assistant-ip>:8112
```

### Main Features

1. **Gallery View** - Browse and manage your image collection
2. **Image Upload** - Add new images to the gallery
3. **Display Settings** - Configure display parameters
4. **Image Preview** - See how images will appear on your display

### Supported Architectures

- **aarch64** (ARM 64-bit) - Raspberry Pi 4, etc.
- **amd64** (x86-64) - Traditional computers
- **armhf** (ARM 32-bit) - Raspberry Pi 3, Pi Zero W, etc.

## Troubleshooting

### Port Already in Use

If port 8112 is already in use, you can modify it:

1. In Home Assistant, go to the add-on settings
2. Change the port to an available one (e.g., 8113)
3. Restart the add-on

### Connection Issues

If you can't access the web interface:

1. Ensure the add-on is running (check in Add-ons → eInk Art Gallery)
2. Check firewall settings
3. Verify you're using the correct IP address and port
4. Check the add-on logs for errors

### Permission Issues

If you encounter permission issues with stored images:

1. Check that the share folder has proper permissions
2. Restart the add-on to reinitialize the data directory

## Logs

View the add-on logs in Home Assistant:

1. Go to **Settings** → **Add-ons & automations** → **Add-ons**
2. Click on eInk Art Gallery
3. Click the **Logs** tab

## Security Notice

⚠️ **Important**: This add-on does not currently include authentication. It's designed for use within your local network only. Do not expose the eInk Art Gallery interface to the internet without additional security measures.

## Support and Issues

- For issues specific to this Home Assistant add-on, please check the [GitHub repository](https://github.com/kotope/eink-art-gallery-addon)
- For issues with the core eInk Art Gallery application, visit [eInk Art Gallery](https://github.com/kotope/eink-art-gallery)

## Development

### Building Locally

```bash
# Build the add-on for your architecture
docker build -t eink-art-gallery:local -f eink-art-gallery/Dockerfile .

# Run the built image
docker run -p 8112:8112 -v data:/data/eink_art eink-art-gallery:local
```

### Structure

```
eink-art-gallery-addon/
├── eink-art-gallery/           # Add-on source
│   ├── build.yaml              # Build configuration
│   ├── config.yaml             # Add-on configuration schema
│   ├── Dockerfile              # Docker build instructions
│   └── rootfs/                 # Container filesystem
│       ├── app/                # Application code
│       └── etc/services.d/     # Service startup/shutdown scripts
├── repository.yaml             # Repository metadata
└── README.md                   # This file
```

## License

This add-on is based on the [eInk Art Gallery](https://github.com/kotope/eink-art-gallery) project, which is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Support

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/tokorhon)

For issues and feature requests, please open an issue on the project repository.

---

**Enjoying eInk Art Gallery?** Consider supporting the original project on GitHub!
