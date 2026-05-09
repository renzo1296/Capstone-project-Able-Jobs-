Setup
Docker Setup
Install Docker here: https://docs.docker.com/engine/install/
Create new postgres container by running:
docker run --name anyNameYouWant -e POSTGRES_PASSWORD=anyPasswordYouWant -p 5431:5432 -d postgres
wait for it to complete, might take some time
Connect to it within the container by running:
docker exec -it anyNameYouWant psql -U postgres -d postgres
Create the database and table by running:
CREATE DATABASE ablejobs;
\c ablejobs
copy the contents in sql/schema.sql file and paste and Enter.
Now you can disconnect by running:
\q
Environment variable setup
Copy the .env.example file and rename it to .env
set SECRET_KEY to anything (e.g. SECRET_KEY=fdslfxzvckzxc)
set PGUSER=postgres
set PGPASSWORD=anyPasswordYouWant (the password you set upon starting the postgres container)
set PGHOST=localhost
set PGPORT=5431
set PGDATABASE=ablejobs
set SSL in 3 ways:
set SSL=true if connecting to a PostgreSQL server over SSL/TLS with a certificate signed by a trusted Certificate Authority (CA)
set SSL=<base64_encoded_root_CA> if connecting to PostgreSQL server over SSL/TLS using a self-signed or privately signed certificate
The value should be the base64-encoded root CA certificate.
Sample command (Linux): base64 -w 0 my_root_ca.crt
leave SSL unset if connecting without SSL/TLS (not recommended for prod)
set SUPABASE_URL=<your_supabase_project_url_here>
set SUPABASE_ANON_KEY=<your_supabase_anon_key_kere>
set SUPABASE_BUCKET_NAME=ablejobs
set BREVO_API_KEY=<your_brevo_api_key_here>
Bun setup
Install bun here: https://bun.sh/docs/installation
Setup project (only if not yet setup previously) by running:
bun i
Running project
Start the project by running:
bun dev
