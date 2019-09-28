# frozen_string_literal: true

ENV['RACK_ENV'] ||= 'development'

require 'require_smasher'
require_gems 'grape', 'grape-entity', 'grape_logging', 'pg', 'sequel', 'erb', 'yaml'
require_file "config/environments/#{ENV['RACK_ENV']}"
require_dirs 'config/initializers'

namespace :db do
  desc 'Run migrations'
  task :migrate, [:version] do |_t, args|
    puts 'Running migration ...'
    version = args[:version].to_i if args[:version]
    ORM::Database.migrate(version)
  end

  task :seeds do
    puts 'Running seeds ...'
    require_relative 'db/seeds/seed'
    error_message = 'Seeds only can be executed in Development environment'
    raise StandardError, error_message unless ENV['RACK_ENV'] == 'development'

    Seeds.execute
  end
end

task :default do
  'Finished!'
end
