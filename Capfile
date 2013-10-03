load 'deploy' if respond_to?(:namespace)

set :application, "bu.chsta.be"
set :user, "arbox"
ssh_options[:auth_methods] = ['publickey']

set :repository,  "./public"
set :scm, :none

server "ldvpc78.uni-trier.de", :app, :web, :db, :primary => true

set :use_sudo, false

set :deploy_to, '/var/www/sites/bu.chsta.be/htdocs'
set :deploy_via, :copy

set :copy_dir, './tmp/capistrano'
set :copy_remote_dir, "#{deploy_to}/tmp/capistrano"

namespace :remote do

  desc <<-DESC
    Create directory required by copy_remote_dir.
  DESC
  task :create_copy_remote_dir, :roles => :app do
    print "    creating #{copy_remote_dir}.\n"
    run "mkdir -p #{copy_remote_dir}"
  end

end

# Custom tasks for our local machine.
namespace :local do
  
  desc <<-DESC
    Create directory required by copy_dir.
  DESC
  task :create_copy_dir do
    print "    creating #{copy_dir}.\n"
    system "mkdir -p #{copy_dir}"
  end

end

# Callbacks.
before 'deploy:setup', 'local:create_copy_dir', 'remote:create_copy_remote_dir'

# Override default tasks which are not relevant to a non-rails app.
namespace :deploy do
  task :migrate do
    puts "    not doing migrate because not a Rails application."
  end
  task :finalize_update do
    puts "    not doing finalize_update because not a Rails application."
  end
  task :start do
    puts "    not doing start because not a Rails application."
  end
  task :stop do 
    puts "    not doing stop because not a Rails application."
  end
  task :restart do
    puts "    not doing restart because not a Rails application."
  end
end

after 'deploy:create_symlink' do
  run "ln -nfs #{shared_path}/projects #{current_path}/projects"
end
