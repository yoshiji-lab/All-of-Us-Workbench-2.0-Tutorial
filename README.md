# All-of-Us-Workbench-2.0-Tutorial

## Navigating the workbench

If you have already been using the workbench 1.0, you can access Verily by clicking `open researcher workbench`:

**IMAGE HERE**

Make sure to sign in to Verily with your All of Us email aka `your-user-name@researchallofus.org`.

The tabs you should check out are:
- **Home**: displays your recent workspaces and running apps. 
- **Workspaces**: displays your workspaces.
  - you should have access to `CERC All of Us v9`. If not, contact Satoshi. 
- **Data collections**: displays the types of data you have access to
  - Genomic data is found within the All of Us Controlled Tier data, which requires training to access.
- **Pods**: displays your billing accounts
  - if `cerc-aou` does not exist, contact Satoshi to be added.

## Navigating your workspace

Open the CERC All of Us v9 tab. You should see an **Overview** tab with a description of the workspace.

### Resources

In the **Resources** tab, you will see a list of the resources available in this workspace, which include folders of data as well as Google Cloud buckets for storage.

You can preview folder contents by selecting one and clicking `Browse` on the top right. You can preview notebooks and text files without booting up an app by selecting them and clicking `Preview`. To view a bucket in Google Cloud's website, click `Open in GCP`. 

### Apps

An app, aka a Virtual Machine (VM), is the environment in which you will run code and access data.

## Creating an app

Create an app in the **Apps** tab by clicking `New app instance`. 

You can then specify the type of app you want to run. For our purposes, it's best to stick with `AoU Jupyter` as a general purpose app. For analyses working with large data tables, you can use `JupyterLab Spark cluster for AoU`. This is analogous to Workbench 1.0's Hail option. 

Next, choose the default config. You can customize it in the `Compute options` section. There, make sure `Zone` is set to `us-central1-a`.
