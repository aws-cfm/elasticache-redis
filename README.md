[![Build Status](https://travis-ci.org/cfn-modules/elasticache-redis.svg?branch=master)](https://travis-ci.org/cfn-modules/elasticache-redis)
[![NPM version](https://img.shields.io/npm/v/@cfn-modules/elasticache-redis.svg)](https://www.npmjs.com/package/@cfn-modules/elasticache-redis)

# cfn-modules: Elasticache Redis

Elasticache Redis.

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/elasticache-redis
```

## Usage

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Cluster:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        VpcModule: !GetAtt 'Vpc.Outputs.StackName' # required
        ClientSgModule: !GetAtt 'ClientSg.Outputs.StackName' # required
        AlertingModule: '' # optional
        BastionModule: '' # optional
        HostedZoneModule: '' # optional
        EngineVersion: '5.0.0' # optional
        CacheNodeType: 'cache.t2.micro' # optional
        TransitEncryption: 'true' # optional
        AuthToken: '' # optional
        SubDomainNameWithDot: 'redis.' # optional
      TemplateURL: './node_modules/@cfn-modules/elasticache-redis/module.yml'

```

## Examples

none

## Related modules

none

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>VpcModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/vpc">vpc module</a></td>
      <td></td>
      <td>yes</td>
      <td></td>
    </tr>
    <tr>
      <td>ClientSgModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/client-sg">client-sg module</a></td>
      <td></td>
      <td>yes</td>
      <td></td>
    </tr>
    <tr>
      <td>AlertingModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/alerting">alerting module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>BastionModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/search?q=keywords:cfn-modules:Bastion">module implementing Bastion</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>HostedZoneModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/search?q=keywords:cfn-modules:HostedZone">module implementing HostZone</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>EngineVersion</td>
      <td>Redis version</td>
      <td>5.0.0</td>
      <td>no</td>
      <td>['5.0.4', '5.0.0', '4.0.10', '3.2.6']</td>
    </tr>
    <tr>
      <td>CacheNodeType</td>
      <td>The compute and memory capacity of the nodes in the node group (shard).</td>
      <td>cache.t2.micro</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>TransitEncryption</td>
      <td>Enable encryption for data in transit? When transit encryption is enabled also specify an auth token.</td>
      <td>true</td>
      <td>no</td>
      <td>[true, false]</td>
    </tr>
    <tr>
      <td>AuthToken</td>
      <td>Password (16 to 128 characters) used to authenticate against Redis. Requried when TransitEncryption = true. Leave blank to disable password-protection.</td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>SubDomainNameWithDot</td>
      <td>Name that is used to create the DNS entry with trailing dot, e.g. §{SubDomainNameWithDot}§{HostedZoneName}. Leave blank for naked (or apex and bare) domain. Requires HostedZoneModule parameter!</td>
      <td>redis.</td>
      <td>no</td>
      <td></td>
    </tr>
  </tbody>
</table>

## Outputs

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Export</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ModuleId</td>
      <td>The ID of module: `ecs-cluster`</td>
      <td></td>
    </tr>
    <tr>
      <td>ModuleVersion</td>
      <td>The version of module: `1.0.0`</td>
      <td></td> 
    </tr>
    <tr>
      <td>StackName</td>
      <td>The name of CloudFormation Stack</td>
      <td></td>
    </tr>
    <tr>
      <td>ClusterName</td>
      <td>The name of the cluster</td>
      <td>`${AWS::StackName}-ClusterName`</td> 
    </tr>
    <tr>
      <td>PrimaryEndPointAddress</td>
      <td>The DNS address of the primary read-write cache node.</td>
      <td>`${AWS::StackName}-PrimaryEndPointAddress`</td> 
    </tr>
    <tr>
      <td>PrimaryEndPointPort</td>
      <td>The port that the primary read-write cache engine is listening on.</td>
      <td>`${AWS::StackName}-PrimaryEndPointPort`</td> 
    </tr>
  </tbody>
</table>
