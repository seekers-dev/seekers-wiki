<h1 align="center">Seekers Wiki 📖</h1>

<div align="center">
    <a href="https://github.com/seekers-dev/wiki/actions/workflows/pages/pages-build-deployment">
        <img alt="pages-build-deployment" src="https://github.com/seekers-dev/wiki/actions/workflows/pages/pages-build-deployment/badge.svg">
    </a>
</div>

## Test locale

### Install requirements

```shell
sudo gem install jekyll bundler rake rexml webrick jekyll-feed jekyll-seo-tag just-the-docs webrick
```

```shell
cd docs
```

```shell
bundler install
```

### Host website

```shell
bundler exec jekyll serve
```

You can view the website on `http://127.0.0.1:4000/`.