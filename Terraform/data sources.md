These dont create anything, they are just a way to query some data from the cloud provider.
```
data "<PROVIDER>_<TYPE>" "<NAME>" {
  [CONFIG ...]
}
```

```
data "aws_vpc" "default" {
  default = true
}
```

```
data "aws_subnets" "default" {
  filter {
    name   = "vpc-id"
    values = [data.aws_vpc.default.id]
  }
}
```

