
# Gradio: Build Machine Learning Web Apps — in Python

Gradio is an open-source Python library that is used to build machine learning and data science demos and web applications.

With Gradio, you can quickly create a beautiful user interface around your machine learning models or data science workflow and let people "try it out" by dragging-and-dropping in their own images,
pasting text, recording their own voice, and interacting with your demo, all through the browser.


Gradio is useful for:

- **Demoing** your machine learning models for clients/collaborators/users/students.

- **Deploying** your models quickly with automatic shareable links and getting feedback on model performance.

- **Debugging** your model interactively during development using built-in manipulation and interpretation tools.

## Quickstart

**Prerequisite**: Gradio requires Python 3.7 or higher, that's all!

### What Does Gradio Do?

One of the *best ways to share* your machine learning model, API, or data science workflow with others is to create an **interactive app** that allows your users or colleagues to try out the demo in their browsers.

Gradio allows you to **build demos and share them, all in Python.** And usually in just a few lines of code! So let's get started.

### Hello, World

To get Gradio running with a simple "Hello, World" example, follow these three steps:

1\. Install Gradio using pip:

```bash
pip install gradio
```

2\. Run the code below as a Python script or in a Jupyter Notebook (or [Google Colab](https://colab.research.google.com/drive/18ODkJvyxHutTN0P5APWyGFO_xwNcgHDZ?usp=sharing)):

```python
import gradio as gr

def greet(name):
    return "Hello " + name + "!"

demo = gr.Interface(fn=greet, inputs="text", outputs="text")
demo.launch()
```


3\. The demo below will appear automatically within the Jupyter Notebook, or pop in a browser on [http://localhost:7860](http://localhost:7860) if running from a script:

![`hello_world` demo](demo/hello_world/screenshot.gif)

### The `Interface` Class

You'll notice that in order to make the demo, we created a `gradio.Interface`. This `Interface` class can wrap any Python function with a user interface. In the example above, we saw a simple text-based function, but the function could be anything from music generator to a tax calculator to the prediction function of a pretrained machine learning model.

The core `Interface` class is initialized with three required parameters:

- `fn`: the function to wrap a UI around
- `inputs`: which component(s) to use for the input (e.g. `"text"`, `"image"` or `"audio"`)
- `outputs`: which component(s) to use for the output (e.g. `"text"`, `"image"` or `"label"`)

Let's take a closer look at these components used to provide input and output.

### Components Attributes

We saw some simple `Textbox` components in the previous examples, but what if you want to change how the UI components look or behave?

Let's say you want to customize the input text field — for example, you wanted it to be larger and have a text placeholder. If we use the actual class for `Textbox` instead of using the string shortcut, you have access to much more customizability through component attributes.

```python
import gradio as gr

def greet(name):
    return "Hello " + name + "!"

demo = gr.Interface(
    fn=greet,
    inputs=gr.Textbox(lines=2, placeholder="Name Here..."),
    outputs="text",
)
demo.launch()
```

![`hello_world_2` demo](demo/hello_world_2/screenshot.gif)

### Multiple Input and Output Components

Suppose you had a more complex function, with multiple inputs and outputs. In the example below, we define a function that takes a string, boolean, and number, and returns a string and number. Take a look how you pass a list of input and output components.

```python
import gradio as gr

def greet(name, is_morning, temperature):
    salutation = "Good morning" if is_morning else "Good evening"
    greeting = f"{salutation} {name}. It is {temperature} degrees today"
    celsius = (temperature - 32) * 5 / 9
    return greeting, round(celsius, 2)

demo = gr.Interface(
    fn=greet,
    inputs=["text", "checkbox", gr.Slider(0, 100)],
    outputs=["text", "number"],
)
demo.launch()
```

![`hello_world_3` demo](demo/hello_world_3/screenshot.gif)

You simply wrap the components in a list. Each component in the `inputs` list corresponds to one of the parameters of the function, in order. Each component in the `outputs` list corresponds to one of the values returned by the function, again in order.

### An Image Example

Gradio supports many types of components, such as `Image`, `DataFrame`, `Video`, or `Label`. Let's try an image-to-image function to get a feel for these!

```python
import numpy as np
import gradio as gr

def sepia(input_img):
    sepia_filter = np.array([
        [0.393, 0.769, 0.189], 
        [0.349, 0.686, 0.168], 
        [0.272, 0.534, 0.131]
    ])
    sepia_img = input_img.dot(sepia_filter.T)
    sepia_img /= sepia_img.max()
    return sepia_img

demo = gr.Interface(sepia, gr.Image(shape=(200, 200)), "image")
demo.launch()
```

![`sepia_filter` demo](demo/sepia_filter/screenshot.gif)

When using the `Image` component as input, your function will receive a NumPy array with the shape `(width, height, 3)`, where the last dimension represents the RGB values. We'll return an image as well in the form of a NumPy array.

You can also set the datatype used by the component with the `type=` keyword argument. For example, if you wanted your function to take a file path to an image instead of a NumPy array, the input `Image` component could be written as:

```python
gr.Image(type="filepath", shape=...)
```

Also note that our input `Image` component comes with an edit button 🖉, which allows for cropping and zooming into images. Manipulating images in this way can help reveal biases or hidden flaws in a machine learning model!

You can read more about the many components and how to use them in the [Gradio docs](https://gradio.app/docs).

### Blocks: More Flexibility and Control

Gradio offers two classes to build apps:

1\. **Interface**, that provides a high-level abstraction for creating demos that we've been discussing so far.

2\. **Blocks**, a low-level API for designing web apps with more flexible layouts and data flows. Blocks allows you to do things like feature multiple data flows and demos, control where components appear on the page, handle complex data flows (e.g. outputs can serve as inputs to other functions), and update properties/visibility of components based on user interaction — still all in Python. If this customizability is what you need, try `Blocks` instead!

### Hello, Blocks

Let's take a look at a simple example. Note how the API here differs from `Interface`.

```python
import gradio as gr

def greet(name):
    return "Hello " + name + "!"

with gr.Blocks() as demo:
    name = gr.Textbox(label="Name")
    output = gr.Textbox(label="Output Box")
    greet_btn = gr.Button("Greet")
    greet_btn.click(fn=greet, inputs=name, outputs=output)

demo.launch()
```

![`hello_blocks` demo](demo/hello_blocks/screenshot.gif)

Things to note:

- `Blocks` are made with a `with` clause, and any component created inside this clause is automatically added to the app.
- Components appear vertically in the app in the order they are created. (Later we will cover customizing layouts!)
- A `Button` was created, and then a `click` event-listener was added to this button. The API for this should look familiar! Like an `Interface`, the `click` method takes a Python function, input components, and output components.

### More Complexity

Here's an app to give you a taste of what's possible with `Blocks`:

```python
import numpy as np
import gradio as gr

def flip_text(x):
    return x[::-1]

def flip_image(x):
    return np.fliplr(x)

with gr.Blocks() as demo:
    gr.Markdown("Flip text or image files using this demo.")
    with gr.Tabs():
        with gr.TabItem("Flip Text"):
            text_input = gr.Textbox()
            text_output = gr.Textbox()
            text_button = gr.Button("Flip")
        with gr.TabItem("Flip Image"):
            with gr.Row():
                image_input = gr.Image()
                image_output = gr.Image()
            image_button = gr.Button("Flip")
    
    text_button.click(flip_text, inputs=text_input, outputs=text_output)
    image_button.click(flip_image, inputs=image_input, outputs=image_output)
    
demo.launch()
```

![`blocks_flipper` demo](demo/blocks_flipper/screenshot.gif)

A lot more going on here! We'll cover how to create complex `Blocks` apps like this in the [building with blocks](https://github.com/gradio-app/gradio/tree/main/guides/3\)building_with_blocks) section for you.

Congrats, you're now familiar with the basics of Gradio! 🥳....
