# Lucid Solutions status rollout

This repository remains `Clicki-Digital/uptime`. The public service owner/brand is Lucid Solutions. Existing monitors, monitored-site names, issue history and monitoring settings are unchanged.

## Before switching the custom domain

1. Merge the companion Lucid website PR first so `/service-updates/` exists.
2. Confirm `status.getlucid.solutions` has a DNS-only CNAME to `Clicki-Digital.github.io`. It currently redirects to `status.clicki.digital`; remove/bypass that old redirect for the new canonical host.
3. Merge this PR. The new logo under `assets/` triggers the existing Static Site CI. If needed, run Static Site CI manually on master.
4. In repository Pages settings, set the custom domain to `status.getlucid.solutions` (the generated CNAME uses the same value). Wait for DNS/certificate checks and enable HTTPS. The integration may not have permission to change Pages settings.
5. Update the repository homepage/Web link to `https://status.getlucid.solutions` after confirming it serves the new site. Upptime also derives its homepage from the configured cname.
6. Keep `status.clicki.digital` as a permanent HTTPS redirect to the new host using the DNS/edge provider, preserving paths and query strings. GitHub Pages supports one custom hostname; another CNAME alone does not configure a second custom certificate/domain.
7. Verify both hosts, HTTP→HTTPS, existing `/history/...` links and `/incident/...` links. Avoid a redirect loop between old and new hosts.

For Cloudflare, an edge redirect for the old hostname requires a proxied record and a valid edge certificate. The new primary hostname can remain DNS only for direct GitHub Pages HTTPS. No DNS/redirect rules or Pages settings are changed by this source PR.

## Incident publishing

Create an issue using the staff service-incident template. Review the text, then apply the existing `status` label. This extra staff step avoids automatically promoting an unreviewed public submission into a status incident. Upptime uses that label for incident history. Leave site-specific monitor labels off manual incidents so automated recovery does not close a manually managed provider incident.

Use timestamped comments for investigating/identified/monitoring/resolved updates, and close the issue when resolved. Its public record remains available in GitHub and Upptime. The site rebuilds periodically; run Static Site CI if generated pages need refreshing. GitHub/Upptime API limits and provider outages may delay displays. Staff runbook content belongs in the private Lucid repository, not in this public repository.
