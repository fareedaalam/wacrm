# migration
npx supabase link --project-ref esulodqvklgrsahhemig 

# go to supabase and run this query in sql editor
ALTER DATABASE postgres SET search_path TO "$user", public, extensions;
ALTER ROLE postgres SET search_path TO "$user", public, extensions;

# export token
 export SUPABASE_ACCESS_TOKEN=<Your Token>

# push db
 npx supabase db push

 #http to https ngrok
 ngrok http 3000
