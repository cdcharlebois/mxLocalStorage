![badge](https://img.shields.io/badge/mendix-6.10.3-green.svg)
![badge](https://img.shields.io/badge/mendix-7.3.0-green.svg)

# LocalStorage Reader and Writer

Write information to the client's browser, and read it when they return.

### Installation

1. Install the widgets in your project
2. Include the **Writer** widget on a page with context and use that context to supply the value to be written to LocalStorage 
    > Note, it's helpful to use [This JSON Web Tokens Module](https://appstore.home.mendix.com/link/app/38385/FlowFabric-BV/JSON-Web-Tokens) when writing to localstorage to encrypt the data.
    
3. Include the **Reader** widget on your app's homepage or other page _from which_ you'd like to trigger an action.
4. Configure the widget's settings:
    - **Writer**
        + `LocalStorage Key Name`: The name of the key for which the value will be saved
        + `Overwrite?` : if set to **No**, the widget will not overwrite the value of the LocalStorage item if the key is found to exist already.
        + `Value to Store`: microflow that **Returns a string** of the value to be saved in LocalStorage (Tip: use [This JSON Web Tokens Module](https://appstore.home.mendix.com/link/app/38385/FlowFabric-BV/JSON-Web-Tokens))
    - **Reader**
        + `LocalStorage Key Name`: The name of the key for which the value will be read
        + `Entity to Create`: The widget needs to create an entity in order to pass a parameter into the microflow, so choose that entity here.
        + `Attribute to use`: Choose the attribute (on the `Entity to Create`) where the value from the LocalStorage item will be set.
        + `On Found`: The microflow to run when the Localstorage item is found 

### Typical usage scenario

- Useful to allow anonymous users to store information in your application (using an identifier and JWT tokens). 
- "remember me" functionality

### Known Limitations

none

###### Based on the Mendix Widget Boilerplate

See [AppStoreWidgetBoilerplate](https://github.com/mendix/AppStoreWidgetBoilerplate/) for an example
