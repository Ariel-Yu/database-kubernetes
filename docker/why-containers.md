# Why container?
- Library compatibility to consider
- Dependency to consider
- Set up working environment usually takes long time
- Different Dev, Test, Prod environment makes deployment complicated

## Operating system
- Hardware infrastructure
- OS kernel
  - Linux
    - Linux distributions
      - Ubuntu
      - Fedora
  - Window
  - XNU
    - XNU distributions
      - Mac OS
- Applications `what really makes different operating system`
  - User interfaces
  - Drivers
  - Compilers
  - File systems
  - Developer tools
  - ...

## Virtual machines vs containers
### Virtual machines
- Hardware infrastructure
- OS
- Hypervisor
- Virtual machines
  - OS - can be any OS kernel
    - Linux
    - Windows
  - Libs/Deps
  - Applications
> More utilization of resources, more isolation, larger in size, slower to spin up

### Containers
- Hardware infrastructure
- OS - the OS kernel is shared among all containers 
- Docker
- Container
  - Libs/Deps
  - Applications
> Less utilization of resources, less isolation, smaller in size, faster to spin up
