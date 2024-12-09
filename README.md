[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/FFdZk26A)
# FinalProject

**Project Overview and Guidelines**

- **Project Scope**: For the selected project, each group will apply concepts from COSC 112 and COSC 113. Only include topics covered in the course; avoid using material not discussed in class.

- **Group Formation**:
  - Maximum of four (4) members per group.
  - Each group must designate a team lead, responsible for communication with the instructor and managing group tasks.
  - All group members must contribute to the coding portion of the project, not just the proposal/report/presentation.

- **Team Lead Responsibilities**:
  - Introduce themselves to the instructor.
  - Facilitate task delegation within the group.
  - Act as the primary contact for all instructor communications.

- **Proposal Submission**: Submit your project proposal document via the Blackboard submission box by ** December 6, 2024, at 11:59 pm**.

- **Project Requirements**:
  - Choose a project that aligns with the course themes, such as database applications, game development, or applied problem-solving.
  - Projects should have comparable scope and complexity.
  - While Java Swing/JavaFX tools are recommended, alternative tools may be used with justification.

- **Selecting a Project**:
  - Projects should directly relate to the course material.
  - Consider creating an applied project that utilizes learned tools to model and solve a meaningful problem.
  - Applied projects should include user-friendly features like command-line interfaces, GUIs, input parsing, and customization options.

- **Final Project Proposal Document**:
  - The proposal should provide a clear overview of the project the team will develop.
  - Include the following elements:
    - **Team and Application Description**: Brief introduction to the team and the application.
    - **Program Objectives**: Outline the goals of the program.
    - **Background**: Summarize the project’s background and restate its purpose.
    - **Algorithm Development**: Describe the main algorithms to be implemented.
    - **Wireframe** (optional): Basic visual representation of the application layout.
    - **Scope of Work**: Outline the tasks and milestones.
    - **Features**: List key features of the application.
    - **Success Measures**: Define how project success will be measured.
    - **Resources**: Identify any resources or tools needed.
    - **Concepts**: Specify course concepts applied in the project.
    - **Third-Party Libraries**: List any external libraries planned for use.
    - **Non-Standard GUI Design**: If applicable, outline any custom GUI elements.
    - **Image Repository**: Mention any visual assets and their sources.

Please adhere to these guidelines to ensure a well-structured and successful project.

Project:

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class EasyMeals {
    private List<String> ingredients;
    private int servings;

    // this is the default constructor
    public EasyMeals() {
        this.ingredients = new ArrayList<>();
        this.servings = 1; // default is single person
    }

    // overloaded constructor
    public EasyMeals(List<String> ingredients, int servings) {
        this.ingredients = ingredients != null ? ingredients : new ArrayList<>();
        this.servings = servings;
    }

    // method to set ingredients
    public void setIngredients() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the ingredients you have (type 'done' to finish):");

        while (true) {
            System.out.print("Ingredient: ");
            String ingredient = scanner.nextLine().trim().toLowerCase();
            if (ingredient.equals("done")) {
                break;
            }
            ingredients.add(ingredient);
        }
    }

    // method to set servings
    public void setServings() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("\nIs this meal for a family or a single person?");
        System.out.print("Type 'family' for family or 'single' for single person: ");
        String choice = scanner.nextLine().trim().toLowerCase();

        if (choice.equals("family")) {
            servings = 4;
        } else {
            servings = 1;
        }
    }

    // Method to suggest recipes
    public void suggestRecipes() {
        // Put in the code for recipes with their required ingredients
        String[][] recipes = {
                {"pasta", "pasta", "tomato sauce", "cheese"},
                {"omelette", "eggs", "cheese", "milk"},
                {"salad", "lettuce", "tomato", "cucumber"},
                {"stir-fry", "chicken", "soy sauce", "vegetables"},
                {"sandwich", "bread", "cheese", "lettuce"}
        };

        System.out.println("\nRecipes you can make:");
        boolean foundRecipe = false;

        for (String[] recipe : recipes) {
            String recipeName = recipe[0];
            boolean canMake = true;

            // Check if all ingredients for the recipe are available
            for (int i = 1; i < recipe.length; i++) {
                if (!ingredients.contains(recipe[i])) {
                    canMake = false;
                    break;
                }
            }

            if (canMake) {
                System.out.println("- " + capitalize(recipeName) + " (Serves " + servings + ")");
                foundRecipe = true;
            }
        }

        if (!foundRecipe) {
            System.out.println("No recipes matched your ingredients. Try adding more items!");
        }
    }

    // Helper method to capitalize recipe names
    private String capitalize(String word) {
        if (word == null || word.isEmpty()) return word;
        return word.substring(0, 1).toUpperCase() + word.substring(1);
    }

    // Method to display entered ingredients
    public void displayIngredients() {
        System.out.println("\nYou entered the following ingredients:");
        System.out.println(String.join(", ", ingredients));
    }

    // Main method
    public static void main(String[] args) {
        // Using the default constructor
        EasyMeals planner = new EasyMeals();

        // Input ingredients and servings
        planner.setIngredients();
        planner.setServings();

        // Display ingredients and suggest recipes
        planner.displayIngredients();
        planner.suggestRecipes();
    }
}

