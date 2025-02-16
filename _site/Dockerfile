# Use the official Ruby image from the Docker Hub
FROM ruby:2.7

# Install dependencies
RUN apt-get update -qq && \
    apt-get install -y build-essential libpq-dev nodejs

# Upgrade RubyGems to a compatible version
RUN gem update --system 3.3.22

# Set the working directory
WORKDIR /usr/src/app

# Copy the Gemfile and Gemfile.lock into the image
COPY Gemfile* ./

# Install the gems specified in the Gemfile
RUN bundle install

# Copy the rest of the application code into the image
COPY . .

# Expose port 3000 to the host
EXPOSE 3000

# Command to run the Jekyll server
CMD ["bundle", "exec", "jekyll", "serve", "--host", "0.0.0.0", "--port", "3000"]