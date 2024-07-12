# gptdbs

This repo will contains some data apps、AWEL operators、AWEL workflow templates and agents which build upon GPT-DB.

- [apps](/apps)
- [workflow](/workflow)
- [agents](/agents)
- [operators](/operators)
- [resources](/resources)

## Quick Start
At first you need to install [GPT-DB](https://docs.gptdb.site/docs/quickstart) project.

We will show how to install a gptdbs from the official repository to your local GPT-DB environment.

### Activate python virtual environment

Change to your GPT-DB project directory and run the following command to activate your virtual environment:
```bash
conda activate gptdb_env
```

Make sure you have installed the required packages:
```bash
pip install poetry
```

### List the available flows

```bash
gptdb app list-remote
```

```bash
# Those workflow can be installed.
                       gptdbs In All Repos                        
┏━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃       Repository ┃ Type      ┃                            Name ┃
┡━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ khulnasoft-lab/gptdbs │ operators │            awel-simple-operator │
│ khulnasoft-lab/gptdbs │ workflow  │          awel-flow-example-chat │
│ khulnasoft-lab/gptdbs │ workflow  │ awel-flow-simple-streaming-chat │
│ khulnasoft-lab/gptdbs │ workflow  │       awel-flow-web-info-search │
│  fangyinc/gptdbs │ workflow  │          awel-flow-example-chat │
│  fangyinc/gptdbs │ workflow  │ awel-flow-simple-streaming-chat │
│     local/gptdbs │ operators │            awel-simple-operator │
│     local/gptdbs │ workflow  │          awel-flow-example-chat │
│     local/gptdbs │ workflow  │ awel-flow-simple-streaming-chat │
│     local/gptdbs │ workflow  │       awel-flow-web-info-search │
│     local/gptdbs │ workflow  │        awel-simple-example-chat │
│     local/gptdbs │ workflow  │          rag-save-url-to-vstore │
│     local/gptdbs │ workflow  │       rag-url-knowledge-example │
└──────────────────┴───────────┴─────────────────────────────────┘
```

### List all installed gptdbs

```bash
gptdb app list
```

```bash
                                                                   Installed gptdbs
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃                            Name ┃ Type     ┃ Repository       ┃                                                                                Path ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│          awel-flow-example-chat │ flow     │ aries-ckt/gptdbs │          ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/awel-flow-example-chat │
│      awel-flow-rag-chat-example │ flow     │ aries-ckt/gptdbs │      ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/awel-flow-rag-chat-example │
│ awel-flow-simple-streaming-chat │ flow     │ khulnasoft-lab/gptdbs │ ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/awel-flow-simple-streaming-chat │
│       awel-flow-web-info-search │ flow     │ khulnasoft-lab/gptdbs │       ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/awel-flow-web-info-search │
│    awel-list-to-string-operator │ operator │ local/gptdbs     │    ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/awel-list-to-string-operator │
│       rag-url-knowledge-example │ flow     │ local/gptdbs     │       ~/.gptdbs/packages/b8bc19cefb00ae87d6586109725f15a1/rag-url-knowledge-example │
└─────────────────────────────────┴──────────┴──────────────────┴─────────────────────────────────────────────────────────────────────────────────────┘
```

### Install a gptdbs from official repository

```bash
gptdb app install awel-flow-simple-streaming-chat
```

### View all gptdbs In GPT-DB

Wait 10 seconds, then open the web page of GPT-DB, you will see the new AWEL flow in web page.

Like this:

<p align="center">
  <img src="./assets/img/awel_flow_simple_streaming_chat.jpg" width="1200" />
</p>


### Chat With Your gptdbs.

```bash
gptdb run flow -n awel_flow_simple_streaming_chat \
--model "chatgpt_proxyllm" \
--stream \
--messages 'Write a quick sort algorithm in Python.'
```

Output:
```bash
You: Write a quick sort algorithm in Python.
Chat stream started
JSON data: {"model": "chatgpt_proxyllm", "stream": true, "messages": "Write a quick sort algorithm in Python.", "chat_param": "1ecd35d4-a60a-420b-8943-8fc44f7f054a", "chat_mode": "chat_flow"}
Bot:
Sure! Here is an implementation of the Quicksort algorithm in Python:

\```python
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]
        less = [x for x in arr[1:] if x <= pivot]
        greater = [x for x in arr[1:] if x > pivot]
        return quicksort(less) + [pivot] + quicksort(greater)

# Test the algorithm with a sample list
arr = [8, 3, 1, 5, 9, 4, 7, 2, 6]
sorted_arr = quicksort(arr)
print(sorted_arr)
\```

This code defines a `quicksort` function that recursively partitions the input list into two sublists based on a pivot element, and then joins the sorted sublists with the pivot element to produce a fully sorted list.
🎉 Chat stream finished, timecost: 5.27 s
```

**Note**: just AWEL flow(workflow) support run with command line for now.

### Uninstallation

```bash
gptdb app uninstall awel-flow-simple-streaming-chat
```

### More commands

You can run `gptdb app --help` to see more commands. The output will be like this:
```bash
Usage: gptdb app [OPTIONS] COMMAND [ARGS]...

  Manage your apps(gptdbs).

Options:
  --help  Show this message and exit.

Commands:
  install      Install your gptdbs(operators,agents,workflows or apps)
  list         List all installed gptdbs
  list-remote  List all available gptdbs
  uninstall    Uninstall your gptdbs(operators,agents,workflows or apps)
```
Run `gptdb run flow --help` to see more commands for running flows. The output will be like this:
```bash
Usage: gptdb run flow [OPTIONS]

  Run a AWEL flow.

Options:
  -n, --name TEXT           The name of the AWEL flow
  --uid TEXT                The uid of the AWEL flow
  -m, --messages TEXT       The messages to run AWEL flow
  --model TEXT              The model name of AWEL flow
  -s, --stream              Whether use stream mode to run AWEL flow
  -t, --temperature FLOAT   The temperature to run AWEL flow
  --max_new_tokens INTEGER  The max new tokens to run AWEL flow
  --conv_uid TEXT           The conversation id of the AWEL flow
  -d, --data TEXT           The json data to run AWEL flow, if set, will
                            overwrite other options
  -e, --extra TEXT          The extra json data to run AWEL flow.
  -i, --interactive         Whether use interactive mode to run AWEL flow
  --help                    Show this message and exit.
```

Run `gptdb repo --help` to see more commands for managing repositories. The output will be like this:

```bash
Usage: gptdb repo [OPTIONS] COMMAND [ARGS]...

  The repository to install the gptdbs from.

Options:
  --help  Show this message and exit.

Commands:
  add     Add a new repo
  list    List all repos
  remove  Remove the specified repo
  update  Update the specified repo
```


## What's the `repo`? 

**A repository is a collection of gptdbs.**

The `gptdbs` can manage by multiple repositories, the official repository is [khulnasoft-lab/gptdbs](https://github.com/khulnasoft-lab/gptdbs).

And you can add you own repository by `gptdb repo add --repo <repo_name> --url <repo_url>`, example:
- Your git repo: `gptdb repo add --repo fangyinc/gptdbs --url https://github.com/fangyinc/gptdbs.git`
- Your local repo: `gptdb repo add --repo local/gptdbs --url /path/to/your/repo`


## How to create a gptdbs?

### Clone the `gptdbs` repository

### Create a python environment

```bash
conda create -n gptdbs python=3.10
conda activate gptdbs
```

### Install the required packages

```bash
pip install poetry
pip install gptdb
```

### Create a new workflow template

```bash
gptdb new app -n my-awel-flow-example-chat
```

### Create a new operator

```bash
gptdb new app -t operator -n my-awel-operator-example
```