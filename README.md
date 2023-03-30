# nginx
Notes about nginx

### How to serve static content?

The easiest way to do it, is to create alias to a file. Add `location` in the `server` section.

```nginx
location /docs {
    alias /path/to/my/docs/README.md;
}
```
