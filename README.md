# U^2-Net HTTP

This is an HTTP service wrapper of the model: [U^2-Net: Going Deeper with Nested U-Structure for Salient Object Detection](https://github.com/NathanUA/U-2-Net) (Qin et al, Pattern Recognition 2020)

The deploy folder contains configuration files for deployment as serverless container with Knative.

# Usage:

```bash
docker run --rm -p 8080:80 docker.io/cyrildiagne/u2net-http
```

# Test:

```bash
curl -F "data=@test.jpg" http://localhost:8080 -o result.png
```

# Development

- Clone this repository: `git clone https://github.com/cyrildiagne/u2net-http.git`
- Go into the cloned directory: `cd u2net-http`
- Clone the official [U^2-Net repository](https://github.com/NathanUA/U-2-Net)
- Download the pretrained model [u2net.pth](https://drive.google.com/file/d/1ao1ovG1Qtx4b7EoskHXmi2E9rp5CHLcZ/view)
- Put the file inside the `U-2-Net/saved_models/u2net/` folder.

# Build from source:

### Option 1 - Locally with virtualenv

```bash
virtualenv venv
venv/bin/activate
```

```bash
pip install torch==0.4.1
pip install -r requirements.txt
```

```
python main.py
```

### Option 2 - Using Docker

After you've retrieved the U^2-Net model.

Download Resnet checkpoint
```
curl https://download.pytorch.org/models/resnet34-333f7ec4.pth -o resnet34-333f7ec4.pth
```

```
docker build -t u2net .
docker run --rm -p 8080:8080 u2net
```
