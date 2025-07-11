###✅ Test After This Setup
Run both:

Your Hour Tracker API at https://localhost:7198

Your API Gateway (e.g., on https://localhost:7153)
---

Then hit:
----
|Proxy URL |	Target Backend Call |
|https://localhost:7153/api/v1/auths/login	→ | https://localhost:7198/api/v1/auths/login|
|https://localhost:7153/api/v1/customers	→ | https://localhost:7198/api/v1/customers|
|https://localhost:7153/api/v1/customers/1	→ | https://localhost:7198/api/v1/customers/1|
