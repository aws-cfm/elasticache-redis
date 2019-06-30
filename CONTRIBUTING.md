# Contributor Guide

## Update Redis engine version

```
$ aws elasticache describe-cache-engine-versions --engine redis --query "CacheEngineVersions[].EngineVersion"
```
