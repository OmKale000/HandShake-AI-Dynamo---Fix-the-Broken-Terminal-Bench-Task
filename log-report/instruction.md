There is an Apache access log at:

/app/access.log

Generate a JSON report at:

/app/report.json

Success criteria

1. Write the output to exactly /app/report.json.
2. The output must be valid JSON.
3. Include the key "total_requests".
4. Include the key "unique_ips".
5. Include the key "top_path".
6. Values must accurately summarize the supplied access log.