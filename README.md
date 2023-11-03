# Certificates

Create SSL Certificate Authority & SSL Domain Certificate signed

## Prerequisites

1. shell prompt
2. [openssl](https://www.google.com/search?q=how+to+install+openssl+linux)

## Installation

```bash
git clone https://gitlab.com/mbasri/generate-custom-certificates ~/generate-custom-certificates
cd ~/generate-custom-certificates
chmod +x /run
```

## Usage

```bash
./run [create|open] [ca|domain] <ca> <domain name>
```

> Make sure that the `run` file can be executed  ```chmod +x ~/generate-custom-certificates/run```

### Usage example

```bash
# Create root CA folder
mkdir -p certificates.d/test.com

# !!! Copy '.vars' file AND UPDATE IT AS YOU NEED.
cp example.d/example.com/.vars certificates.d/test.com/.vars

# Create the Certificate Authority
./run create ca test.com

# Check your Certificate Authority
./run open ca test.com

# Create the Domain Certificate signed by the Certificate Authority
./run create domain test.com subtest

# Check your Domain Certificate
./run open domain test.com subtest
```

### Variables

Template variables is presents here `~/generate-custom-certificates/example.d/example.com/.vars`
This file need to be present on each root 'Certificate Authority' folder.

#### Available varriables

| Name |  Value example | Limit
|------| -------------|-------------|
| COUNTRY | FR | Only 2 characters |
| STATE | Ile-De-France | |
| CITY | Paris | |
| ORGANISATION | My organisation | |
| ORGANISATION_UNIT | My organisation unit | |
| EMAIL | contact@mysite.com | |
| VALID_DAYS | 1825 | Number of the days in integer|

> Make sure that all the variables is set on the following file  `~/generate-custom-certificates/certificates.d/<My CA>/.vars` otherwise the script will fail

## Author

* [**Mohamed BASRI**](https://gitlab.com/mbasri)

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details
