# Installation

### Prerequisites

- A digital ocean account
- Ruby
- Bundler

### Generate an API key
Head on over to [digital ocean](https://cloud.digitalocean.com/settings/applications). Click the button labeled "Generate new token"

Copy the token.

Add the following to your shell profile:
```
export DIGITAL_OCEAN_TOKEN='YOUR_API_TOKEN'
```

Install prerequisites and boot a digital ocean machine:
```
./bin/setup
```

Generate an SSH key:

# Configure ssh
```
vagrant ssh-config >> ~/.ssh/config
```

Provision a pairing box:
```
ansible-playbook pairing.yml -i ansible/inventory
```

## Testing
```
rake
```
