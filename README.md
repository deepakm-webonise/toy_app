== Device Mesh

DeviceMesh is a mobile app where a group of users can create a video mesh on their mobile devices. 

1. VideoMesh - In this the group of users will mesh together their devices to form one single video mesh. The video which is played is split up across the various devices in the group to make one single video mesh.

2. FlashMesh: Another feature of the app is the creation of patterns from the flashlights of the devices. The users can create a dynamic pattern of the flashlights of the devices.

=== Getting Started

* Install mysql kindly refer [this](https://help.ubuntu.com/12.04/serverguide/mysql.html) link

----

=== Setup

1) Clone from the current repository.
   git clone -b develop git@github.com:webonise/DeviceMesh.git

2) Get the latest code from *develop* branch of the repository.

3) Add the database.yml in *config/* directory. For sample database.yml kindly refer [this](https://gist.github.com/erichurst/961978) link

4) Add raketask in crontab

   * * * * * bash --login -c 'cd /path/to/DeviceMesh && rake mesh_records:clear RAILS_ENV=environment'

5) Run the following commands:-

    cd <application_dir>

    bundle install       # Install the necessary gems

    rake db:setup        # Create the db, create the schema and load seed data.

    rails s              # Start the server


== README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


Please feel free to use a different markup language if you do not plan to run
<tt>rake doc:app</tt>.
