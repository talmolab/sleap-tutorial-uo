# Activity 2: Tracking and inspecting predictions

**Note:** If you haven't already, make sure you followed the instructions on **[setting up](setup.md)** before you get started.

To do this activity, we'll need a trained model that can predict poses on new data.

If you want to train your own model from scratch, check out [Activity 1](labeling.md).

If you want to use a pre-trained model, download this repository and use the ones in the [`data/models/`](https://github.com/talmolab/sleap-tutorial-uo/tree/main/data/models) folder.

## 1. Inference through the GUI

Let's start by activating our environment if it is not yet:
```
conda activate sleap_v1.2.0a2
```

And open the SLEAP GUI:
```
sleap-label
```

Let's add a video to predict on by going to **File** → **Add Videos...**. If you downloaded this repository, navigate to the `data` folder and add the provided `fly_clip.mp4`. Save the project to a new file, such as `fly_clip.predictions.slp` by going to **File** → **Save**.

**Tip:** We recommend running inference in a new project so that our predicted and manual labels don't get mixed up. It also helps to have predictions for each video stored separately to facilitate organization and analysis.

Next, let's set up our inference job with our trained models by going to **Predict...** → **Run Inference...** and select the models that you trained from the drop-downs on each tab:

![Select model](images/select-model.png)

If you don't see the models in the dropdown, click on **Select training config file...** (at the bottom of the drop-down) and browse to the model folder. You can select either `initial_config.json` or `training_config.json` from that folder (it doesn't matter which).


Back in the first panel (**Inference Pipeline**), let's now set up the tracking so we can associate instances across time.

For the tutorial, let's try the `simple` tracker and specify that we always have 2 instances in each frame. This will help with tracking ambiguities.

Set the **Predict On** target to the `entire video`.

Your GUI should look like this when configured:

![Inference config](images/inference-config.png)

Now just click **Run** to start tracking! This may take a little while if running on a computer without a GPU.