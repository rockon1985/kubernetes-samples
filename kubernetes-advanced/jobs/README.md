Cron jobs are useful for creating periodic and recurring tasks, like running backups or sending emails. Cron jobs can also schedule individual tasks for a specific time, such as if you want to schedule a job for a low activity period.

# Creating a Job

You can create a job by specifying the [Cron format](https://en.wikipedia.org/wiki/Cron) in a yaml file:

```
kubectl apply -f simple-cron-job.yaml
```
