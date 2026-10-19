# Bull queue dashboard

The backend mounts Bull Board at `/api/admin/queues`. It shows the email,
audit, and portfolio-link verification queues, including waiting, active,
completed, failed, and delayed jobs.

Access requires a valid admin JWT and the configured admin second-factor
challenge. The route is mounted behind the existing admin middleware and is
never anonymous. Keep it private to the operations network and do not expose
it through a public reverse-proxy location.

The dashboard is operational tooling; Prometheus and Grafana remain the
source for long-term metrics and alerting. Queue mutations made in Bull Board
are audited by the queue workers and should be recorded in the incident log.
