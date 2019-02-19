# App-cues demo

This demonstrates the static example for app cues. The example must be triggered
by a webserver. Opening this locally with your web browser using the file:// 
protocol will not work. 

## Demo

Add your project number and unique id to the index.html 


```
// NOTE: These values should be specific to the current user.
Appcues.identify("<project_id>", { // Replace with unique identifier for current user
    name: "John Doe",   // Current user's name
    email: "john.doe@example.com", // Current user's email
    created_at: 1234567890,    // Unix timestamp of user signup date

    // Additional user properties.
    // is_trial: false,
    // plan: "enterprise"
});
```

For example:
```
<script src="//fast.appcues.com/12345.js"></script>

<script>
    // NOTE: These values should be specific to the current user.
    Appcues.identify("asdvcs-3423423-sdfdsf-324rdsf-fsdf32-ee3", { // Replace with unique identifier for current user
        name: "John Doe",   // Current user's name
        email: "john.doe@example.com", // Current user's email
        created_at: 1234567890,    // Unix timestamp of user signup date

        // Additional user properties.
        // is_trial: false,
        // plan: "enterprise"
    });
</script>

```

### Locally

To run, pass the local html file to nginx 
in a docker container with the following run command.

```
docker run -v <this absolute path>:/usr/share/nginx/html -p 8080:80 nginx
```

For example

```
docker run -v /home/pl/go/src/github.com/peterlamar/javascript-workshop/appcues:/usr/share/nginx/html -p 8080:80 nginx
```

## Reference

[docker hub nginx](https://hub.docker.com/_/nginx)
[app cues install](https://docs.appcues.com/article/48-install-overview)
