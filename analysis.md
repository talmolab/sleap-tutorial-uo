# Activity 3: Analyzing SLEAP outputs

**Note:** If you haven't already, make sure you followed the instructions on **[setting up](setup.md)** before you get started.

If you want to train your own model from scratch, check out [Activity 1](labeling.md).

If you want to generate predictions using a trained model, check out [Activity 2](inference.md).

Here we'll assume that you have `data/predictions.slp` or `data/predictions.analysis.h5` present.

## Set up Jupyter Lab to use notebooks

If you'll be doing analysis within the SLEAP environment, we recommend first installing Jupyter Lab:
```
pip install jupyterlab
```
This can be started with this command which will open a new browser window with the notebook interface:
```
jupyter lab
```

Once it's open, you can follow along in the [`interactive_analysis.ipynb` notebook](interactive_analysis.ipynb).

## Next steps

- Check out a more advanced set of [analysis examples](https://sleap.ai/notebooks/Analysis_examples.html).