
Assignment 2 Blazor Server Application of GroceryStore

Name: Harshdeep Harshdeep
Student ID:- 0788912
Date:- 09-04-2022
Time :- 5:00 PM


1. Create a Blazor app
    
    dotnet new blazorserver -o HarshdeepHarshdeepGroceryApp

    cd HarshdeepHarshdeepGroceryApp

2. Build a Food list Blazor app
    dotnet new razorcomponent -n Food -o Pages

3. Open the Food component in file editor and add an @page Razor directive to the top of the file with a relative URL of /food.

    Open Pages/Food.razor
    
    @page "/food"

    <PageTitle>Food</PageTitle>

    <h1>Food</h1>

    @code {

    }

4. Add the Food component to the navigation bar.

    <div class="nav-item px-3">
    <NavLink class="nav-link" href="food">
        <span class="oi oi-list-rich" aria-hidden="true"></span> Food
    </NavLink>
    </div>


    Save the Shared/NavMenu.razor file

5. Run the app by dotnet watch Run.

6. Add Foodlist file to the app folder and add a class by the name as FoodIteam.cs .

    Add the Code :- 

                public class FoodItem
        {
            public string? Category { get; set; }

            public int Price { get; set; }

            public int IsleNumber { get; set; }
        }



7. Return to the Food component
     
    Add the code :- 

    
         @page "/food"

        <PageTitle>Food</PageTitle>

        <h1>Food</h1>

        <ul>
            @foreach (var food in foods)
            {
                <li>@food.Category</li>
                <li>@food.Price</li>
                <li>@food.IsleNumber</li>
            }
        </ul>

8. The app requires UI elements for adding todo items to the list. Add a text input (<input>) and a button (<button>) below the unordered list.

   <input placeholder="Some FoodItem" @bind="newFood" />

    <input placeholder="Some Price" @bind="itemPrice" />

    <input placeholder="Number" @bind="number" />


    <button  @onclick="AddFoodItem">Add FoodItem</button>


9. Register the method for the button using the @onclick attribute.

    @code {
    private List<FoodItem> foods = new();
         private string? newFood;

         private int itemPrice;

          private int number;
         private void AddFoodItem()

        

10. To get the title of the new food item, add a newFood string field at the top of the @code block:

    private string? newFood;

Modify the text <input> element to bind newFood with the @bind attribute:

    <input placeholder="Some FoodItem" @bind="newFood" />


11. Update the AddFood method to add the FoodItem with the specified title to the list.

     {
       if (!string.IsNullOrWhiteSpace(newFood))
        {
            foods.Add(new FoodItem { Category = newFood });
            newFood = string.Empty;
        }

       else 
        {
            foods.Add(new FoodItem { Price = itemPrice });

            foods.Add(new FoodItem { IsleNumber = number });

           
        }



    }



