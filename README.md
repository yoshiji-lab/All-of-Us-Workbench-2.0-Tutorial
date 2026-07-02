# All-of-Us-Workbench-2.0-Tutorial

## Navigating the workbench

If you have already been using the workbench 1.0, you can access Verily by clicking `open researcher workbench`:

<img width="631" height="259" alt="Screenshot 2026-07-02 at 1 39 58 PM" src="https://github.com/user-attachments/assets/a1f112c2-afe4-4eb3-a978-87345e89198d" />

Make sure to sign in to Verily with your All of Us email: `your-user-name@researchallofus.org`.

The tabs you should check out are:
- **Home**: displays your recent workspaces and running apps. 
- **Workspaces**: displays your workspaces.
  - you should have access to the `CERC All of Us v9` workspace. If not, contact Satoshi. 
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

- Click `New app instance` in the **Apps** tab.

- Specify the type of app you want to run. It's best to stick with `AoU Jupyter` as a general purpose app. For analyses working with large data tables, you can use `JupyterLab Spark cluster for AoU`. This is analogous to Workbench 1.0's Hail option. 

- Choose the default config. You can customize it in the `Compute options` section.
  - There, make sure `Zone` is set to `us-central1-a`
  - Choose a `Machine type` to set number of CPUs, cores, and RAM
  - Keep your `Data disk size` low if you can.
  - Set `Autostop` so your app pauses after a certain amount of time left idle (1 hour is probably good). 

- In `Review details`, optionally give your app a descriptive name. Then click `Create app`. 

## Working in an app

Your app will take some time to boot up. Once active, you will be able to pause and resume via the `Stop` and `Start` buttons. Pausing reduces the app's cost per hour. Please pause your app when you are done for the day so we don't charge the CERC extra money.

When you are done your analysis and have saved your results in a google bucket, delete the app via the 3 dots in the top right corner. 

Click on the app name to open **JupyterLab**. Here, you can navigate the filesystem via the terminal or clicking folders on the left panel. 

### Working in the CERC workspace

Open the `workspace` folder. This is where we will do our analyses. 

## Storage options

`workspace-bucket`: use this bucket to store results permanently. 
- NOTE: storage space costs money! Please add files sparingly.
- this bucket is `read-only`. You can read the data inside via local paths, but can only write with the `gcloud storage` command (analogous to `gsutil`) as explained in the next section.

`scratch-bucket`: anything added to this bucket will be automatically deleted after 14 days.
- this is a good landing spot for temporary outputs before deciding what to save to workspace-bucket
- you can read and write to it directly using its local path
- please keep your results organized in a user specific folder!

`notebooks`: this is a bucket for storing notebooks and other scripts.
- please create a folder for your own scripts so we keep things organized
- do not use this to store data!! 

**Creating your own folder**: you are free to create your own folder under `workspace/` and send outputs there.
- NOTE: anything created outside of a bucket will be permanently deleted when you delete your app!
- unlike Workbench 1.0, there is no option to retain a persistent disk after deleting an app

<img width="246" height="239" alt="image" src="https://github.com/user-attachments/assets/d5e68c96-0405-4fed-856c-1bf5ad60c085" />

## Setting environment variables

To access data and the workspace bucket, run the following code once at the beginning of your notebook:

`%run ~/workspace/notebooks/Setting_Env_Variables.ipynb`

This sets the OS variables `WORKSPACE-BUCKET`, `WORKSPACE_CDR`, and `GOOGLE_CLOUD_PROJECT`.

To upload files to the workspace bucket, run:

`gcloud storage cp -r local/results/folder/path $WORKSPACE_BUCKET/your_name_analysis/`

## Accessing data

NOTE: for anyone wanting to access ACAF files, Satoshi cleaned them up and stored them under `workspace/workspace-bucket/GWAS_core/acaf_snp_qc_oct052025`

**THIS SECTION IS A WORK IN PROGRESS, WILL UPDATE AS I MESS AROUND**
