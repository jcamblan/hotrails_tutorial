web: bundle exec rails server -p $PORT -e $RAILS_ENV -b 0.0.0.0
worker: bundle exec que -w 2

postdeploy: bundle exec rake db:migrate && curl -X POST -d "{\"revision\":\"$CONTAINER_VERSION\",\"user\":\"scalingo\"}" "https://push.appsignal.com/1/markers?api_key=$APPSIGNAL_PUSH_API_KEY&name=$APPSIGNAL_APP_NAME&environment=$APPSIGNAL_APP_ENV"
