# Web Image Scraper

A modern, efficient web image scraping application with a sleek GUI interface. This application allows you to download images from any website with advanced features like dynamic content loading, multi-threaded downloads, and smart image filtering.



## Features

### Core Functionality
- **Smart Image Detection**: Automatically detects and extracts images from web pages
- **Dynamic Content Support**: Uses Selenium for JavaScript-heavy websites with lazy loading
- **Multi-threaded Downloads**: Concurrent downloading for faster performance
- **Intelligent Filtering**: Filter images by size, format, and other criteria
- **Duplicate Prevention**: Automatic handling of duplicate filenames
- **Progress Tracking**: Real-time progress updates and detailed logging

### User Interface
- **Modern GUI**: Clean, intuitive interface built with Tkinter
- **Real-time Progress**: Live progress bar and status updates
- **Configurable Settings**: Customizable download parameters
- **Statistics Display**: Download statistics and folder management
- **Error Handling**: Comprehensive error reporting and recovery

### Advanced Features
- **Background Image Detection**: Extracts images from CSS background properties
- **Relative URL Resolution**: Automatically converts relative URLs to absolute
- **Content Type Validation**: Verifies image content before downloading
- **Flexible Output**: Customizable output directory and file naming
- **Resource Management**: Efficient memory and network resource usage

## Installation

### Prerequisites
- Python 3.7 or higher
- Chrome browser (for Selenium functionality)
- Internet connection

### Step 1: Download
```bash

cd Download_images_from_website
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Verify Installation
```bash
python src/gui.py
```

## Usage Guide

### Starting the Application
1. Navigate to the project directory
2. Run the application:
   ```bash
   python src/gui.py
   ```

### Basic Usage
1. **Enter Website URL**: Input the target website URL in the URL field
2. **Configure Settings**:
   - **Output Directory**: Choose where to save downloaded images
   - **Dynamic Loading**: Enable for JavaScript-heavy websites
   - **Max Images**: Limit the number of images to download
   - **Min File Size**: Filter out small images (in KB)
   - **Threads**: Number of concurrent download threads

3. **Start Scraping**: Click "Start Scraping" to begin the process
4. **Monitor Progress**: Watch the progress bar and output log
5. **Access Downloads**: Use "Open Downloads" to view downloaded images

### Configuration Options

#### URL Input
- Supports both HTTP and HTTPS URLs
- Automatically adds HTTPS prefix if protocol is missing
- Validates URL format before processing

#### Output Directory
- Default: `downloads` folder in project directory
- Can be changed using the "Browse" button
- Creates directory automatically if it doesn't exist

#### Dynamic Loading (Selenium)
- **Enabled**: Uses Chrome browser to load JavaScript content
- **Disabled**: Uses direct HTTP requests (faster, but limited)
- Recommended for modern websites with dynamic content

#### Image Filtering
- **Max Images**: Limits total downloads (0 = no limit)
- **Min File Size**: Excludes images smaller than specified size
- **Supported Formats**: JPG, PNG, GIF, BMP, WebP, SVG

#### Performance Settings
- **Threads**: Controls concurrent downloads (1-10 recommended)
- Higher thread count = faster downloads but more resource usage

### Advanced Usage

#### Command Line Interface
For automation or advanced usage, you can directly use the core scraper:

```python
from src.image_scraper import ImageScraper

# Initialize scraper
scraper = ImageScraper(output_dir="my_images", max_workers=3)

# Scrape images
downloaded = scraper.scrape_images(
    url="https://example.com",
    use_selenium=True,
    max_images=20,
    min_size=5120  # 5KB minimum
)

print(f"Downloaded {len(downloaded)} images")
```

## Project Structure

```
Download_images_from_website/
├── src/
│   ├── image_scraper.py    # Core scraping engine
│   └── gui.py              # GUI interface
├── downloads/              # Default output directory
├── assets/                 # Project assets
├── requirements.txt        # Python dependencies
├── README.md              # This file
└── scrap-img.py           # Legacy script (deprecated)
```

## Technical Details

### Dependencies
- **requests**: HTTP library for web requests
- **beautifulsoup4**: HTML parsing and extraction
- **selenium**: Browser automation for dynamic content
- **webdriver-manager**: Automatic Chrome driver management
- **lxml**: Fast XML/HTML parser
- **tkinter**: GUI framework (built-in with Python)

### Architecture
- **Modular Design**: Separated core logic and UI components
- **Thread Safety**: Safe concurrent operations
- **Error Recovery**: Robust error handling and recovery
- **Resource Management**: Efficient memory and network usage
- **Logging System**: Comprehensive logging and debugging

### Image Detection Algorithm
1. Parse HTML content for `<img>` tags
2. Extract `src`, `data-src`, and `data-lazy-src` attributes
3. Search for CSS background images in style attributes
4. Convert relative URLs to absolute URLs
5. Validate image URLs and content types
6. Filter images based on user criteria

## Troubleshooting

### Common Issues

#### Chrome Driver Issues
**Problem**: WebDriver errors or Chrome not found
**Solution**: 
- Ensure Chrome browser is installed
- The application automatically downloads the correct driver
- Check internet connection for driver download

#### No Images Found
**Problem**: Application reports no images found
**Solution**:
- Verify the website URL is correct and accessible
- Try enabling "Dynamic Loading" for JavaScript-heavy sites
- Check if the website blocks automated access
- Reduce minimum file size filter

#### Slow Downloads
**Problem**: Downloads are taking too long
**Solution**:
- Increase number of threads (but not more than 10)
- Check internet connection speed
- Reduce maximum images limit
- Disable Selenium if not needed

#### Permission Errors
**Problem**: Cannot create files or directories
**Solution**:
- Ensure write permissions to output directory
- Try running with administrator privileges
- Check available disk space

### Performance Optimization

#### For Large Websites
- Enable Dynamic Loading only if necessary
- Limit maximum images to reasonable number
- Increase minimum file size to filter small images
- Use higher thread count for faster downloads

#### For Slow Connections
- Reduce thread count to 1-2
- Increase timeout values in code if needed
- Process smaller batches of images

## Contributing

We welcome contributions to improve this project! Here's how you can help:

1. **Report Issues**: Submit bug reports or feature requests
2. **Code Contributions**: Fork the project and submit pull requests
3. **Documentation**: Help improve documentation and guides
4. **Testing**: Test the application on different platforms and websites

### Development Setup
1. Fork the repository
2. Create a virtual environment
3. Install development dependencies
4. Make your changes
5. Test thoroughly
6. Submit a pull request

## Legal and Ethical Considerations

### Responsible Usage
- **Respect Robots.txt**: Check website's robots.txt file
- **Rate Limiting**: Don't overload websites with requests
- **Copyright**: Respect image copyrights and usage rights
- **Terms of Service**: Follow website terms and conditions

### Best Practices
- Use reasonable delays between requests
- Don't scrape copyrighted content for redistribution
- Respect website bandwidth and resources
- Only download images you have rights to use

 ### Author
 Giduturi Yashmieen



## Support

For support, questions, or feature requests:
- Check the troubleshooting section above
- Review existing issues in the project repository
- Create a new issue with detailed information

## Changelog

### Version 2.0.0 (Current)
- Complete rewrite with modern Python practices
- New GUI interface with advanced features
- Multi-threaded downloading
- Dynamic content support with Selenium
- Improved error handling and logging
- Smart image detection and filtering
- Progress tracking and statistics

### Version 1.0.0 (Legacy)
- Basic image scraping functionality
- Simple command-line interface
- Limited error handling

---


*Building tomorrow's software, today.*