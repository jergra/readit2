this project, from a tutorial by Classsed, is a clone of reddit.com

to install deployment version (C:\readit) at Digital Ocean, follow instructions at
	deploy:				https://www.youtube.com/watch?v=xqHyMAlRtYw&t=70s
	update after deployment:	https://www.youtube.com/watch?v=z9OBKbSBOuw&t=3s
----------
Useful info for deployment version:

ssh key pair procedure:
	in windows: go to C:\
	type: bash
	type: cd home/jergra43/.ssh
	delete two files: id_rsa, id_rsa.pub
		rm id_rsa
		rm id_rsa.pub
	type: ssh-keygen
	accept defaults
	type: cat ~/.ssh/id_rsa.pub
		this outputs to the terminal the contents of id_rsa.pub
		copy this content
	paste this content into the space provided at the web-hosting company
	copy the ipv4 address provided by the web-hosting company (it will be, for this example: 128.199.5.69)
	still at same linux command prompt, type:
		ssh root@128.199.5.69
	you are now inside the web-hosting company server and can begin to add files to it

	extra notes:
		to look at a linux file called id_rsa.pub:
			vim is_rsa.pub
		to exit vim:
			:q
		to begin inputting to a vim file:
			i
		to exit and save changes:
			Esc
			:x
		to look at a list of files in linux folder:
			ll (or ls)
		to copy something at a linux prompt:
			cp <something>
		to delete something at a linux prompt:
			rm <something>

------------------------------
local version at 'C:\readitLocal' (both server and client can be started with 'npm run dev'):
--------------------------------
start pgadmin from windows
    password: !Virgil43
go to pgadmin12
    password: password

from readit prompt, this runs database:
    npm run dev

from readit prompt, to get database prompt:
    psql -d readit -U postgres
        password is: password
    (this username and password are set in: ormconfig.json)



destroy all tables in the database and remake:
    1. delete all migration files in the migration folder
    2. run the following
        npm run typeorm schema:drop
        npm run typeorm migration:run

adding new table to the database:
    create a migration file in the migration folder:
        npm run typeorm migration:generate -- --name migration-file-name-mentioning-new-table
    run the migration file that you have just createdwoo:
        npm run typeorm migration:run