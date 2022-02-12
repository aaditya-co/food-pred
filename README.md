# Food Finder :hamburger: 📷:

As an introductory project to myself, I built an end-to-end **CNN Image Classification Model** which identifies the food in your image. 

I worked out with a pre-trained Image Classification Model that comes with Keras and then retrained it on the infamous **Food101** Dataset.

### Processing 

The Model actually beats the [**DeepFood**](https://arxiv.org/pdf/1606.05675.pdf) Paper's model which also trained on the same dataset.

The Accuracy aquired by DeepFood was **77.4%** and our model's **85%** .

> ##### **Dataset used :**  **`Food101`**

> ##### **Model Used :** **`EfficientNetB1`**

> ##### **Accuracy :** **`85%`**

## using

Finally after training the model, I have exported it as `.hdf5` files and then integrated it with **Streamlit Web App**. 

**Streamlit** turns data scripts into shareable web apps in minutes. 
Once I got the App working on my local device I then deployed it using Streamlit’s invite-only **[sharing feature](https://streamlit.io/sharing)**


> **[Working Demo](https://share.streamlit.io/adityaraj3644/food-pred/main/food-vision/app.py)**

Once an app is loaded, 

1. Upload an image of food. If you dont have one, use the images from `food-images/`
2. Once the image is processed, **`Predict`** button appears. Click it.
3. Once you click the **`Predict`** button, the model prediction takes place and the output will be displayed along with the model's **Top-5 Predictions**
4. And voilà, there you go.


## Implementation


1. #### Imported Food101 dataset from **[Tensorflow Datasets](https://www.tensorflow.org/datasets)** Module.

2. #### Becoming one with the Data : *Visualise - Visualize - Visualize*

3. #### Setup Global dtype policy to **`mixed_float16`** to implement [**Mixed Precision Training**](https://www.tensorflow.org/guide/mixed_precision)

   > Mixed precision is the use of both 16-bit and 32-bit floating-point types in a model during training to make it **run faster** and use **less memory**.

4. #### Building the Model Callbacks 

   As we are dealing with a complex Neural Network (EfficientNetB0) its a good practice to have few callbacks set up. Few ones I will be using throughtout this Notebook are :

   - **TensorBoard Callback :** TensorBoard provides the visualization and tooling needed for machine learning experimentation

   - **EarlyStoppingCallback :** Used to stop training when a monitored metric has stopped improving.

   - **ReduceLROnPlateau :** Reduce learning rate when a metric has stopped improving.


5. #### Built a  [Fine Tuning](https://www.tensorflow.org/tutorials/images/transfer_learning)  Model

   This part tool the longest. In Deep Learning, you have to know which nob does what. Once yoy get experienced you'll what nobs you should turn to get the results you want. 
   **Architecture** : **`EffficientNetB1`**
   

6. #### Evaluating and Deploying out Model to Streamlit

   Once we have our model ready, its cruicial to evaluate it on our **custom data** : *the data our model has never seen*.

   Training and evaluating a model on train and test data is cool, but making predictions on our own realtime images is another level.

   Once we are satisfied with the results, we can export the model as a `.hdf5`  which can be used in future for model deployment.



