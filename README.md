Device Mesh
===========

DeviceMesh is a mobile app where a group of users can create a mesh on their mobile devices. 

1. VideoMesh- In this the group of users will mesh together their devices to form one single video mesh. The video which is played is split up across the various devices in the group to make one single video mesh.

2. FlashMesh- Another feature of the app is the creation of patterns from the flashlights of the devices. The users can create a dynamic pattern of the flashlights of the devices.

====

### Getting Started

1. Requires Ruby 1.9.3

2. Requires **mysql** kindly refer [this](https://help.ubuntu.com/12.04/serverguide/mysql.html) link for installation procedure. 


### Setup

1. Clone from the current repository.
   ```
   git clone -b develop git@github.com:webonise/DeviceMesh.git
   ```

2. Get the latest code from **develop** branch of the repository.

3. Add the **database.yml** in *config/* directory. For sample database.yml kindly refer [this](https://gist.github.com/erichurst/961978) link.

4. Add **raketask** in crontab.
   ```
   * * * * * bash --login -c 'cd /path/to/DeviceMesh && rake mesh_records:clear RAILS_ENV=environment'
   ```

5. Run the following commands:-
   ```
   cd /root/to/application

   bundle install       # Install the necessary gems

   rake db:setup        # Create the db, create the schema and load seed data.

   rails s              # Start the server
   ```

### API List

| Method |         Url        |                    Usage                               |
|--------|--------------------|--------------------------------------------------------|
| POST   | /macpi/login       | Authenticate user and save their information.          |
| POST   | /macpi/create_mesh | Allows authenticated user to create a mesh.            |
| GET    | /macpi/fetch_mesh  | Fetch list of all meshes.                              |
| GET    | /macpi/join_mesh   | Allows authenticated user to join already created mesh |
| GET    | /macpi/pattern     | Fetch the mesh pattern.                                |

### login

Authenticate user and save their information.

* Method: POST

| Request Parameters |  Type   |
|--------------------|---------|
| device_token       | String  |
| first_name         | String  |
| last_name          | String  |
| uuid               | String  |
| device_type        | String  |
| width              | Integer |
| height             | Integer |
| signed_key         | String  |

* Example:
```ruby
Parameters: {
  token: 'APA91bHFeSpfTY2vw3Urrw43ArG-opcEFqvu0WCoV6z_WwV9ovNUvwPtUulbHoaZNPjf-GiJGTAue7JtU3VsfpyQWmpVZkwyZqI7IwPSkZsb9r-fIGNfOQyJFUR1NOU7Yx0hPJhLxzTaV86tw-LqjoPWv40OY1tcAA', 
  first_name: 'Deepak',
  last_name: 'Mahakale', 
  uuid: '909171549134433', 
  device_type: 'android',
  width: 480, 
  height: 872, 
  signed_key: 'f85af4570403b8961d5a5acfe8a60b10f9c54407' }
```

### create_mesh

Allows authenticated user to create a mesh.

* Method: POST

* Video Mesh

| Request Parameters |  Type   |
|--------------------|---------|
| mesh_name          | String  |
| mesh_type          | String  |
| url                | String  |
| video_width        | String  |
| video_height       | String  |
| uuid               | String  |
| latitude           | Float   |
| longitude          | Float   |
| signed_key         | String  |

* Example:
```ruby
Parameters: {
  mesh_name: 'Test', 
  mesh_type: 'video'
  url: 'http://www.youtube.com/watch?v=5UvgL4P9q_M', 
  video_height: '320', 
  video_width: '640', 
  uuid: '909171549134433', 
  latitude: 18.5109569,
  longitude: 73.7773981, 
  signed_key: '75f38b08f5291e885ce7d441613c3f08e3e61fd2' }
```

* Video Mesh

| Request Parameters |  Type   |
|--------------------|---------|
| mesh_name          | String  |
| mesh_type          | String  |
| pattern_id         | Integer |
| uuid               | String  |
| latitude           | Float   |
| longitude          | Float   |
| signed_key         | String  |

* Example:
```ruby
Parameters: {
  mesh_name: 'Test', 
  mesh_type: 'video'
  pattern_id: 1, 
  uuid: '909171549134433', 
  latitude: 18.5109569,
  longitude: 73.7773981, 
  signed_key: '75f38b08f5291e885ce7d441613c3f08e3e61fd2' }
```

