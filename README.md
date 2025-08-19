# Harbor Guard

[![Next.js](https://img.shields.io/badge/Next.js-15.4.6-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.1.0-blue?style=flat-square&logo=react)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Prisma](https://img.shields.io/badge/Prisma-6.14.0-2D3748?style=flat-square&logo=prisma)](https://www.prisma.io/)
[![Docker](https://img.shields.io/badge/Docker-enabled-2496ED?style=flat-square&logo=docker)](https://www.docker.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

A comprehensive container security scanning platform that provides an intuitive web interface for managing and visualizing security assessments of Docker images.

## Installation

### Docker (Recommended)

Run Harbor Guard using Docker with a single command:

```bash
docker run -p 3000:3000 ghcr.io/harborguard/harborguard:latest
```

To give Harbor Guard access to your local images:

```bash
docker run -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/harborguard/harborguard:latest
```

Access the application at `http://localhost:3000`

## Screenshots

<div align="center">
  <img src="assets/home.png" alt="Harbor Guard Dashboard" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);" width="800">
  <p><em>Harbor Guard Dashboard - Container security scanning made simple</em></p>
</div>

### Development Setup

1. Clone the repository:
```bash
git clone https://github.com/HarborGuard/HarborGuard.git
cd HarborGuard
```

2. Install dependencies:
```bash
npm install
```

3. Set up the database:
```bash
npx prisma migrate dev
```

4. Start the development server:
```bash
npm run dev
```

## Purpose

Harbor Guard is a modern web application designed to streamline container security management by providing a unified interface for multiple scanning tools and advanced visualization capabilities.

### Multi-Tool Security Scanning

<div align="center">
  <img src="assets/scan.png" alt="Harbor Guard Scans" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);" width="800">
  <p><em>Harbor Guard Dashboard - Container security scanning made simple</em></p>
</div>

Harbor Guard integrates and orchestrates multiple industry-standard security scanning tools:

- **[Trivy](https://github.com/aquasecurity/trivy)** - Comprehensive vulnerability scanner for containers
- **[Grype](https://github.com/anchore/grype)** - Vulnerability scanner by Anchore  
- **[Syft](https://github.com/anchore/syft)** - Software Bill of Materials (SBOM) generator
- **[Dockle](https://github.com/goodwithtech/dockle)** - Container image linter for security and best practices
- **[OSV Scanner](https://github.com/google/osv-scanner)** - Open Source Vulnerability database scanner
- **[Dive](https://github.com/wagoodman/dive)** - Docker image layer analysis and optimization tool

### Quality of Life Improvements

Harbor Guard addresses common pain points in container security workflows:

- **Unified Dashboard** - Single interface for all scanning tools instead of managing multiple CLI outputs
- **Historical Tracking** - Persistent storage and comparison of scan results over time
- **Report Export** - Download individual tool reports or complete ZIP packages for compliance
- **Real-time Monitoring** - Live scan progress tracking with WebSocket integration
- **Smart Filtering** - Dynamic filtering and sorting of vulnerabilities by severity, package, or CVE
- **Interactive Charts** - Click-to-navigate scatter plots for vulnerability analysis

### Optimized Visualization Strategy

<div align="center">
  <img src="assets/libraries.png" alt="Harbor Guard Library" style="border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);" width="800">
  <p><em>Harbor Guard Dashboard - Container security scanning made simple</em></p>
</div>


The platform employs several innovative approaches to vulnerability data visualization:

#### Library Vulnerability Scatterplot
- **Multi-dimensional mapping** - X-axis represents severity levels, Y-axis shows vulnerability counts
- **Interactive filtering** - Toggle visibility by severity level with real-time count updates
- **Clickable exploration** - Navigate directly to library-specific analysis from chart points
- **Color-coded severity** - Consistent color scheme across all interfaces (red/orange/yellow/blue)

#### Layer-by-Layer Analysis
- **Horizontal tab navigation** - Each Docker layer gets its own tab for focused analysis
- **Dynamic sizing** - Tab layout adapts to any number of layers without breaking
- **File system exploration** - Detailed view of files added/modified in each layer
- **Size optimization insights** - Visual indicators for layer sizes and optimization opportunities

#### Findings Management
- **Severity-based grouping** - Organize findings by Critical, High, Medium, Low severity
- **Progress tracking** - Visual indicators for scan completion and remediation status
- **Export flexibility** - Individual JSON reports or complete ZIP archives
- **API accessibility** - Public REST endpoints for programmatic access to scan data

## Features

### 🔍 Comprehensive Scanning
- Support for 6 major container security tools
- Automatic vulnerability detection and classification
- Software Bill of Materials (SBOM) generation
- Container best practices validation
- Layer-by-layer image analysis

### 📊 Advanced Visualization
- Interactive vulnerability scatter plots
- Historical scan comparison charts
- Real-time progress monitoring
- Severity-based filtering and grouping
- Responsive design for all screen sizes

### 🚀 Developer Experience
- Modern React 19 + Next.js 15 architecture
- TypeScript for type safety
- Prisma ORM for database management
- Tailwind CSS for styling
- shadcn/ui component library

### 📈 Enterprise Ready
- RESTful API for programmatic access
- Bulk report export capabilities
- Persistent scan history
- Scalable database design
- Docker-first deployment

## API Endpoints

Harbor Guard provides REST API endpoints for programmatic access:

### Scan Reports
- `GET /api/image/[name]/scan/[scanId]/[reportType]` - Download individual tool reports
- `GET /api/image/[name]/scan/[scanId]/download` - Download complete scan package
- `GET /api/scans` - List all scans
- `POST /api/scans/start` - Initiate new scan

### Docker Integration
- `GET /api/docker/images` - List local Docker images
- `GET /api/docker/search` - Search Docker Hub
- `GET /api/docker/info` - Docker daemon information

## Architecture

Harbor Guard is built with modern web technologies:

- **Frontend**: React 19 + Next.js 15 with App Router
- **Styling**: Tailwind CSS + shadcn/ui components
- **Database**: SQLite with Prisma ORM
- **Charts**: Recharts for data visualization
- **Icons**: Tabler Icons + Lucide React
- **State Management**: React Context + Custom hooks

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Run the test suite: `npm test`
6. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

- 🐛 [Report Issues](https://github.com/HarborGuard/HarborGuard/issues)
- 💬 [Discussions](https://github.com/HarborGuard/HarborGuard/discussions)
- 📧 [Email Support](mailto:support@harborguard.io)

## Acknowledgments

Special thanks to the maintainers of the integrated security tools:
- Aqua Security (Trivy)
- Anchore (Grype, Syft)
- goodwithtech (Dockle)
- Google (OSV Scanner)
- wagoodman (Dive)

---

<div align="center">
  <strong>Harbor Guard</strong> - Securing containers, one scan at a time.
</div>