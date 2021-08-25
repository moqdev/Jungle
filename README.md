# Jungle

\_Lighthouse Labs Web Development Bootcamp Project

A mini e-commerce application built with Rails 4.2 for purposes of teaching Rails by example.

Technologies used include [Ruby/Rails](https://rubyonrails.org/), [Postgres](https://postgresql.org), [Bootstrap](https://getbootstrap.com/), [RSpec](https://rspec.info/), and [Capybara](https://github.com/teamcapybara/capybara) for development and testing.
Automated testing using RSpec was also added.

![image](https://user-images.githubusercontent.com/77746888/130875115-613aa912-4b52-46a3-9528-46a28f7d5e4e.png)

## Dependencies

Jungle requires [Ruby/Rails 4.2](https://rubyonrails.org/) and [Postgres 9.x](https://www.postgresql.org/).

See `Gemfile` for gem dependencies.

### **Support Setup**

Install [Ruby/Rails 4.2](https://rubyonrails.org/).

Install [Postgres](https://www.postgresql.org).

Sign up for a [Stripe](https://stripe.com) account for payment testing.

### **Database Setup**

Log into Postgres as a user with superuser privileges. For example:

```sh
sudo -u postgres psql
```

Execute the following to create the development database:

```postgres
CREATE USER jungle_development WITH NOSUPERUSER PASSWORD 'development';
CREATE DATABASE jungle_devlopment OWNER jungle_development;
GRANT ALL ON DATABASE jungle_devlopment TO jungle_development;
```

### **Jungle Setup**

Execute the following to set up Jungle:

```sh
cd <project-directory>
git clone https://github.com/d0ugr/jungle
cd jungle
bundle install
```

Create `config/database.yml` by copying `config/database.example.yml`.

Create `config/secrets.yml` by copying `config/secrets.example.yml`.

These files can be used as is, or modify them to match database login credentials.

To create, load and seed the database, run:

```sh
bin/rake db:reset
```

Create `.env` by copying `.env.example` and modify the Stripe keys to match the ones from your account. The admin login credentials can be changed or used as-is for testing if you like.

### **Running Jungle Server**

To start the server normally use:

```sh
bin/rails server
```

If running under a Vagrant virtual machine use:

```sh
bin/rails server -b 0.0.0.0
```

## **Testing**

### **Stripe Testing**

When making purchases using Jungle, use credit card number 4111 1111 1111 1111 for testing successful orders.

More information in their docs: <https://stripe.com/docs/testing#cards>

### **Model Testing**

To run all automated RSpec model tests. `--format documentation` provides a more readable output when running this on the command line.

```sh
bin/rspec [--format documentation]
```

### **Feature Testing**

Feature tests are executed using Capybara and Poltergeist. These tests are much slower than model tests so running only the one you might be working on is recommended:

```sh
bin/rspec spec/features/filename_spec.rb
```
