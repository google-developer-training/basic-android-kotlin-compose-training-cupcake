Cupcake app
=================================

This app contains an order flow for cupcakes with options for quantity, flavor, and pickup date.
The order details get displayed on an order summary screen and can be shared to another app to
send the order.


Pre-requisites
--------------
* Experience with Kotlin syntax.
* How to create and run a project in Android Studio.
* How to create composable functions 


Getting Started
---------------
1. Install Android Studio, if you don't already have it.
2. Download the sample.
3. Import the sample into Android Studio.
4. Build and run the sample.


Flow Diagram
---------------
![cupcake app diagram (1)](https://github.com/user-attachments/assets/62f0a0aa-5497-4603-9f52-64cc759a7e01)

## Data Flow and Code Structure (with Diagram Explanation)

The diagram explains the overall data flow of the "Cupcake" app. The architecture and flow can be summarized as follows:

### User Interaction (Screens):
The user interacts with the app through four key screens:
1. **StartOrderScreen**: Users select the number of cupcakes.
2. **FlavorScreen**: Users select the cupcake flavor.
3. **PickupScreen**: Users choose a pickup date.
4. **SummaryScreen**: The final order details are displayed, and users can share the order.

### Cupcake Screens Enum:
The app navigates between screens using the `CupcakeScreen` enum, where each screen is associated with a title resource (e.g., `R.string.choose_flavor`).

### OrderViewModel:
The `OrderViewModel` manages the cupcake order state. It uses `MutableStateFlow` to store the order details, like quantity, flavor, and pickup date. The model also handles logic like price calculation, including adding a surcharge for same-day pickup.

- As users interact with the UI (selecting a quantity, flavor, or date), the `OrderViewModel` updates the `uiState`, which is observed by the UI to reflect the changes in real-time.

### Navigation:
The navigation between screens is handled using the `NavController`. Based on user actions (e.g., clicking "Next"), the app moves to the next screen, and the `OrderViewModel` updates the necessary state (e.g., quantity, flavor, or date).

### UI State and Updates:
The UI is reactive, meaning that it observes changes in the `uiState`. For example, the price is recalculated every time the user changes the quantity or pickup date, and the updated price is displayed in the UI.

### Order Summary:
The `SummaryScreen` displays the final order details and allows the user to share the order using an Android implicit intent.

