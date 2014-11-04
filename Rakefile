require 'rake/docker_lib'

ARCHIVE='debian.tgz'

Rake::DockerLib.new("registry.deliverous.net/deliverous/wheezy", no_cache: true) do
    if not File.exists?(ARCHIVE) or Rake.application.options.build_all then
        sh 'sudo', 'debootstrap', '--variant=minbase', 'wheezy', 'wheezy'
        sh "sudo tar -cz -C wheezy --numeric-owner . > #{ARCHIVE}"
        sh 'sudo', 'rm', '-rf', 'wheezy'
    end
end