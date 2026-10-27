# Pull request activity evidence — 26 October 2026 (UTC)

GitHub Search API measurements for GitHub repositories owned by **Blacksp1d3r**, collected on **27 October 2026**.

## Results

| Metric | PRs | GitHub search |
| --- | ---: | --- |
| Created on 26 October | **656** | [Open search](https://github.com/search?q=is%3Apr%20user%3ABlacksp1d3r%20created%3A2026-10-26&type=pullrequests) |
| Created **and** merged on 26 October | **557** | [Open search](https://github.com/search?q=is%3Apr%20user%3ABlacksp1d3r%20created%3A2026-10-26%20merged%3A2026-10-26&type=pullrequests) |
| Merged on 26 October, irrespective of creation date | **561** | [Open search](https://github.com/search?q=is%3Apr%20user%3ABlacksp1d3r%20merged%3A2026-10-26&type=pullrequests) |

**Method:** GitHub REST Search API `GET /search/issues`, using `is:pr user:Blacksp1d3r` and the date qualifiers above; the reported numbers came from the `total_count` field. GitHub dates use **UTC** for these queries.

## Reproduce via GitHub CLI

Authenticate with an account that can read the relevant repositories, then run:

```sh
gh api -X GET search/issues -f q='is:pr user:Blacksp1d3r created:2026-10-26' --jq '.total_count'
gh api -X GET search/issues -f q='is:pr user:Blacksp1d3r created:2026-10-26 merged:2026-10-26' --jq '.total_count'
gh api -X GET search/issues -f q='is:pr user:Blacksp1d3r merged:2026-10-26' --jq '.total_count'
```

## Verification limitations

Most repositories included in these numbers were **private** at the time of measurement. Public visitors cannot independently reproduce the full counts, even though this evidence document is public. The figures refer to pull request activity, not a verified world record, unique lines of code, or proof of software quality. Search counts may change if indexing, access or repository visibility changes.

## Screenshots

You can add **redacted** screenshots showing each search query and its result count to this folder, without exposing private repository names, PR titles or internal details. No screenshots are included in this commit.
