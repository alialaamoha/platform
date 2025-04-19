
ansible-project/
├── ansible.cfg          # Configuration file for Ansible
├── inventory/           # Inventory files (hosts)
│   ├── production       # Production inventory file
│   └── staging          # Staging inventory file
├── group_vars/          # Variables for groups of hosts
│   ├── all.yml          # Variables for all groups
│   └── webservers.yml   # Variables for the 'webservers' group
├── host_vars/           # Variables for individual hosts
│   ├── host1.yml        # Variables for 'host1'
│   └── host2.yml        # Variables for 'host2'
├── roles/               # Roles directory
│   ├── common/          # Example role: 'common'
│   │   ├── tasks/       # Tasks for the role
│   │   │   └── main.yml # Main tasks file
│   │   ├── handlers/    # Handlers for the role
│   │   │   └── main.yml # Main handlers file
│   │   ├── templates/   # Jinja2 templates
│   │   ├── files/       # Static files
│   │   ├── vars/        # Role-specific variables
│   │   │   └── main.yml # Main variables file
│   │   ├── defaults/    # Default variables
│   │   │   └── main.yml # Main defaults file
│   │   ├── meta/        # Metadata about the role
│   │   │   └── main.yml # Main metadata file
│   │   └── README.md    # Documentation for the role
│   └── webserver/       # Example role: 'webserver'
├── playbooks/           # Playbooks directory
│   ├── site.yml         # Main playbook
│   ├── webservers.yml   # Playbook for webservers
│   └── dbservers.yml    # Playbook for database servers
├── library/             # Custom modules
├── module_utils/        # Custom module utilities
├── filter_plugins/      # Custom filter plugins
└── README.md            # Documentation for the project