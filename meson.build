project('example')

application_id = 'org.example.Example'

prefix = get_option ('prefix')
bindir = join_paths (prefix, get_option ('bindir'))
datadir = join_paths (prefix, get_option ('datadir'))
libexecdir = join_paths (prefix, get_option ('libexecdir'))

service_conf = configuration_data()
service_conf.set('appid', application_id)
service_conf.set('libexecdir', libexecdir)

services = [
  'Tracker1',
  'Tracker1.Miner.Applications',
  'Tracker1.Miner.Extract',
  'Tracker1.Miner.Files',
  'Tracker1.Writeback',
]

foreach service: services
  configure_file (
    input: 'org.example.Example.@0@.service.in'.format(service),
    output: '@0@.@1@.service'.format(application_id, service),
    configuration: service_conf,
    install: true,
    install_dir: join_paths (datadir, 'dbus-1', 'services')
  )
endforeach

install_data (
  'example',
  install_dir: bindir
)