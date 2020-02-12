# HashiCorp Packer Orb

## Example
For this example, any required cloud provider auth would be stored as environment variables within CircleCi.

Arguments such as variables can be passed to the Packer build command via the `args` parameter

```yaml
version: 2.1

orbs:
  aws-cli: salaxander/packer@0.1

jobs:
  packer-example:
    executor: packer/default
    steps:
      - checkout
      - packer/build:
          template: packer.json
          args: -var aws_region=us-east-1

workflows:
  version: 2
  packer:
    jobs:
      - packer-example
```