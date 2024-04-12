# POE-PART1---PROG6112
This is for PART 1 POE PROG Work....

In order to RUN the CODE, 
(1) First Build the Solution.
(2) Then once the Solution is Built,
(3) Run the CODE AND Wait.

(4) Finally Test the Code...
******************************************************************

namespace RecipeApplication
{
    class Recipe
    {
        // This is a Set Private Fields to store any Recipe Details //
        private string[] ingredients;
        private string[] units;
        private string[] steps;
        private double[] quantities;

        // Below is the Constructor to initialize Empty Recipe//
        public Recipe()
        {
            // Initializing the Empty Arrays for Ingredients, Quantities, Units and Steps
            ingredients = new string[0];
            units = new string[0];
            steps = new string[0];
            quantities = new double[0];
        }

            // Method to Enter the Recipe Details //
            public void EnterDetails()
        {
            // Make the User to Enter the Number of Ingriedients //
            Console.Write("Enter the Number of Ingredients: ");
            int numIngredients = int.Parse(Console.ReadLine());

            // Initialize the Arrays with the Correct Size //
            ingredients = new string[numIngredients];
            quantities = new double[numIngredients];
            units = new string[numIngredients];

            // Prompt the User to Enter the Details for each Ingriedient //
            for (int i = 0; i < numIngredients; i++)
            {
                Console.WriteLine($"Enter Details for Ingredients #{i + 1}:");
                Console.Write("Name: ");
                ingredients[i] = Console.ReadLine();
                Console.Write("Quantity: ");
                quantities[i] = double.Parse(Console.ReadLine());
                Console.Write("Unit of Measurement: ");
                units[i] = Console.ReadLine();
            }

            // Promt the User to Enter the Number of Steps //
            Console.Write("Enter the Number of Steps: ");
            int numSteps = int.Parse(Console.ReadLine());

            // Initialize the Steps Array with the Correct Size //
            steps = new string[numSteps];

            // Promt the User to Enter the Details for Each Step //
            for (int i = 0; i < numSteps; i++)
            {
                Console.Write($"Enter Step #{i + 1}: ");
                steps[i] = Console.ReadLine();
            }

        }
            // Method to Display the Recipe //
            public void DisplayRecipe()
        {
            // Display all Ingredients & Quantities //
            Console.WriteLine("Ingredients: ");
            for (int i = 0; i < ingredients.Length; i++)
            {
                Console.WriteLine($"- {quantities[i]} {units[i]} of {ingredients[i]}");
            }

            // Display All Steps //
            Console.WriteLine("Steps: ");
            for (int i = 0; i < steps.Length; i++)
            {
                Console.WriteLine($"- {steps[i]}");
            }
        }

            // Methood to Scale the Recipe //
            public void ScaleRecipe(double factor)
        {
            // Multiply al the Quantities by the Set Scale Factor //
            for (int i = 0; i < quantities.Length; i++)
            {
                quantities[i] *= factor;
            }
        }

            // Method to Reset Quantities to Half //
            public void ResetQuatities()
        {
            // Reset All the Quantities to their Original Values //
            for (int i = 0; i < quantities.Length; i++)
            {
                quantities[i] /= 2;
            }

        }
            // Method to Clear Entire Recipe //
            public void ClearRecipe()
        {
            // Reset All the Arrays to Empty //
            ingredients = new string[0];
            quantities = new double[0];
            units = new string[0];
            steps = new string[0];
        }
    }

    class Program
    { 
        static void Main(string[] args)
        {
            // Instantiate a Recipe Object //
            Recipe recipe = new Recipe();

            // Main Program Loop
            while (true)
            {

            // Display Menu Options //
            Console.WriteLine("Enter '1' - To Enter Recipe Details");
            Console.WriteLine("Enter '2' - To Display Recipe Details");
            Console.WriteLine("Enter '3' - To Scale Recipe");
            Console.WriteLine("Enter '4' - To Reset Quantities");
            Console.WriteLine("Enter '5' - To Clear Recipe");
            Console.WriteLine("Enter '6' - To Exit");

            // Read User Choice //
            string choice = Console.ReadLine();
                switch (choice)
                {
                    case "1":
                        // Enter Recipe Details //
                        recipe.EnterDetails();
                        break;

                    case "2":
                        // Display the Recipe //
                        recipe.DisplayRecipe();
                        break;

                    case "3":
                        // Scale the Recipe //
                        Console.Write("Enter the Scaling Factor (0.5, 2 or 3): ");
                        double factor = double.Parse(Console.ReadLine());
                        recipe.ScaleRecipe(factor);
                        break;

                    case "4":
                        // Reset Quantities //
                        recipe.ResetQuatities();
                        break;

                    case "5":
                        // Clear the Recipe //
                        recipe.ClearRecipe();
                        break;

                    case "6":
                        // Exit the program //
                        Console.WriteLine("Exiting the Program ......");
                        return;

                    default:
                        // Invalid Choice Selection //
                        Console.WriteLine("Selection Invalid. Please select a Valid Choice. ");
                        break;
                }
            }
        }  
    }
}
