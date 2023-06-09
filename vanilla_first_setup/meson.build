pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
moduledir = join_paths(pkgdatadir, 'vanilla_first_setup')
gnome = import('gnome')

gnome.compile_resources('vanilla-first-setup',
  'vanilla-first-setup.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'vanilla-first-setup.in',
  output: 'crystal-first-setup',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

configure_file(
  input: 'vanilla-first-setup-processor.in',
  output: 'crystal-first-setup-processor',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

subdir('utils')
subdir('defaults')
subdir('layouts')
subdir('views')
subdir('scripts')

vanilla_first_setup_sources = [
  '__init__.py',
  'main.py',
  'window.py',
  'dialog.py',
]

install_data(vanilla_first_setup_sources, install_dir: moduledir)
