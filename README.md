**SOP CICD**<br>
<br>
Created By:<br>
Andrian Ramadhan Febriana<br>
Red Hat Certified Architect in OpenShift<br>
andrian.r.febriana@gmail.com<br>
089653599531<br>
<br>

1. Clone <https://github.com/andrianrf/cicd-template-manifests.git>
2. Agar pipeline bisa clone dari git private repository, edit file base/1-pipeline/1-secret-github-creds.yaml
3. Agar pipeline bisa push ke docker repository edit file base/1-pipeline/2-secret-docker-creds.yaml
4. Pada cluster openshift, buat namespace demo
5. Pada argocd buat application dengan parameter seperti berikut:

| Application Name | demo                                                       |
| ---------------- | ---------------------------------------------------------- |
| Sync Policy      | Automatic                                                  |
| Prune Resources  | Checked                                                    |
| Self Heal        | Checked                                                    |
| Repository URL   | <https://github.com/andrianrf/cicd-template-manifests.git> |
| Revision         | main                                                       |
| Path             | base                                                       |
| Namespace        | demo                                                       |

6. Pada repository tambahkan webhook <https://github.com/andrianrf/backoffice-be/settings/hooks/new> dengan parameter sebagai berikut:

| Payload URL  | <https://el-pipeline-demo.apps.&lt;clusterName&gt;.&lt;baseDomain>&gt; |
| ------------ | ---------------------------------------------------------------------- |
| Content type | application/json                                                       |
| Secret       | demo                                                                   |

7. Selesai
