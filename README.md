# goolila.com
personal site with Hugo

# Deploy

```
rm -r public
export AWS_PROFILE=goolila
hugo
aws s3 sync public s3://goolila.com
```

## thumbnails
brew install imagemagick ghostscript
convert -thumbnail 512 src.jpg dst.jpg
