## Simple select query
curl --location 'https://dbtslpaeeibttjmcmypd.supabase.co/rest/v1/customers' \
--header 'apikey: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImRidHNscGFlZWlidHRqbWNteXBkIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MjMxODYxMjAsImV4cCI6MjAzODc2MjEyMH0.DTg25D2W8M0LQR-K0bLxL7wb5jngDUTBQeCT9zm5Swg'

## Select query with where clause
curl --location 'https://dbtslpaeeibttjmcmypd.supabase.co/rest/v1/customers?select=customer_id%2Cfirst_name%2Clast_name&first_name=ilike.*li*&order=first_name.desc&limit=10' \
--header 'apikey: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImRidHNscGFlZWlidHRqbWNteXBkIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MjMxODYxMjAsImV4cCI6MjAzODc2MjEyMH0.DTg25D2W8M0LQR-K0bLxL7wb5jngDUTBQeCT9zm5Swg'

## Query to HTTP Request Converter
https://supabase.com/docs/guides/api/sql-to-rest
