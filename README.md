![Recipe_App](https://github.com/user-attachments/assets/428b33a2-fac7-4b31-9424-888d37da7616)


# Table of Contents

1. [Brief Description](#brief-description)  
2. [Before Installing and Running the Project](#before-installing-and-running-the-project)  
3. [Functionality Used](#functionality-used)   
4. [Additional Features Analysis](#additional-features-analysis)  
   - [Authentication and Authorization](#authentication-and-authorization-1)  
   - [Responsive Design](#responsive-design-1)  
   - [CSS and Tailwind](#css-and-tailwind-1)  
   - [CRUD](#crud-1)  
5. [Final Conclusion](#final-conclusion)
6. [Code Snippets](#code-snippets)  
   - [Authentication and Authorization](#authentication-and-authorization-3)  
   - [Responsive Design](#responsive-design-3)  
   - [CSS and Tailwind](#css-and-tailwind-3)  



## Brief Description

The Recipe App is a modern digital recipe book that allows users to view, create, edit, update, and delete recipes stored in a database. It can also be viewed on any device due to the responsive design. Additionally, it has an individual login for extra safety.

![Static Badge](https://img.shields.io/badge/Third_Year-Beginner-blue)




### Before installing and running the project:

There are frameworks like Tailwind that will need to be installed before reviewing the Recipe App. If needed, the following resources I found to be very helpful:
https://github.com/CHT2520/intro-to-tailwind

https://github.com/CHT2520/intro-to-tailwind/blob/main/getting_started_with_nodejs.md



## Functionality Used
- Authentication and authorization using Laravel
- Responsive design
- CSS and Tailwind
- Fixing my CRUD functionality


## Additional Features Analisis
**Authentication and authorization**

Description:

I implemented fully functioning authentication and authorization in the Recipe App to manage user roles and access levels. This system ensures that some users have higher clearance, allowing them to add and delete recipes, while others are limited to just viewing them. By doing this, I can control who has the ability to modify content, which is crucial for maintaining app security and proper functionality. To further enhance security, I used password hashing in the database. This ensures that user passwords are stored securely, making them safe even in the event of an attack.

Why I Used This Functionality: 

I learned a lot about authentication and authorization through this implementation, especially as a new developer. Understanding how to secure user access based on roles has been eye-opening. It’s incredibly important when building applications that require different permissions, and it helped me understand the core of building secure applications.

Things I Could Improve:

While authentication and authorization were successfully implemented, I plan to improve it by adding a feature in the future where users can create their own accounts. This will give users more control over their profiles and roles within the app, making the system better.


**Responsive design**

Description: 

I implemented responsive design to ensure the app functions smoothly across devices. This was done using CSS media queries, particularly with the @media (max-width: 768px) query to modify the layout for smaller screens. However, it took me a while to fully understand how positioning, Flexbox, and grids work in the context of responsiveness. I watched several tutorials, which helped me better understand how to make the app adapt to different screen sizes effectively. From there, I got the idea to use @media. The result is a fully functional app that looks good and works well on both laptops and phones.

Why I Used This Functionality: 

As a person who is constantly switching from laptop to phone, I know how important it is for websites to work smoothly on both. Even Brightspace updated their website for that reason in the last few days. I liked that I got to fix a problem I am constantly having and learn something new in the process.

Things I Could Improve: 

Although the responsive design works well, there's always room for improvement. One area to focus on would be optimizing images for mobile devices, as it can enhance performance and load time on smaller screens. As we know, if a page is loading for more than two seconds, people are more likely to click off the website. In the future, I plan to improve this further by implementing additional media query breakpoints to ensure better support across all screen sizes and orientations.


**CSS and Tailwind**

Description: 

This is the first time I used Tailwind, and I had a lot of issues with the installation and, after that, with the implementation. I used it to help streamline the styling process and create a responsive, clean design. Tailwind's utility-first approach allowed me to do a lot without having to write much custom CSS. I didn't go too much in-depth with using Tailwind for my project, but I used it to add fonts and colors, change the size of the text, and make the text invisible when it reaches certain pixel values, all with just one line of code. Despite the learning curve, I found it to be an efficient tool for quickly building responsive interfaces.

Why I Used This Functionality: 

I chose Tailwind because I thought it would be a simpler version of CSS or Bootstraps. I expected it to make the design process faster, but I ended up overestimating my current skills and couldn't use it to the extent to which I wanted. Even though it offers customizable styling it still took me some time to get the hang of it. I am happy that i got the opportunity to learn and use a new technology.

Things I Could Improve: 

While Tailwind helped me a lot in building the app, I could improve my understanding of how to create more reusable components and avoid repetitive code. In the future, I plan to explore Tailwind's configuration options more thoroughly and maybe even use custom themes to make the styling even more efficient. Additionally, I would like to better understand how to use Tailwind in larger-scale applications to ensure maintainability and scalability.


**CRUD**

After assignment one feedback, I saw that I had some issues with the routes, more specifically with the delete and update. I didn't want to leave this mistake, so I have removed it.


## Final Conclusion
I regret that I couldn't get the Eloquent relationships to work. I have been trying, but every time I keep getting errors that the certificate_id already exists. Then, when I try to send the database, it just errors out. Excluding that, overall, I have learned a lot of new techniques from both assignments, and in my opinion, those are skills I will be able to use in the industry when I graduate.


## Code Snippets

**Authentication and authorization**: 

Here’s a sample from the `UserSeeder`:
```

public function run(): void
    {
        DB::table('users')->insert(['name' => 'Kate Hutton', 'email' => 'k.l.hutton@hudstudent.ac.uk', 'password' => Hash::make('password'),'role_id' => 2]);
        DB::table('users')->insert(['name' => 'Yousef Miandad', 'email' => 'y.miandad@hudstudent.ac.uk', 'password' => Hash::make('letmein'),'role_id' => 2]);
        DB::table('users')->insert(['name' => 'Sunil Laxman', 'email' => 's.laxman@hudstudent.ac.uk', 'password' => Hash::make('password2'),'role_id' => 1]);
    }

```

Here’s a sample from the `AuthController`

```

function login(Request $request)
{
    $userDetails = [
        "email" => $request->email,
        "password" => $request->password
    ];

    if (Auth::attempt($userDetails)) {
        $request->session()->regenerate();
        return redirect('/recipes');
    }
    return back();
}

```
**Responsive design**


Here’s a sample from the `Styles.css`
```

/* This Media Queries is allowing the screen to be resized to a phone size and to still work. */
@media (max-width: 768px) {
  .navbar {
      flex-direction: column;
      align-items: center;
  }

  .nav-links {
      flex-direction: column;
      align-items: center;
  }

  .nav-links li {
      margin: 10px 0;
  }

  .app-title {
      font-size: 1.75rem; 
  }

  .main-title {
      font-size: 1.5rem; 
  }

  .recipe-item {
      font-size: 1rem; 
  }

  .content {
      margin: 0 10px; 
      padding-top: 150px; 
  }

  input, textarea, select {
      font-size: 0.875rem; 
      padding: 8px 16px; 
  }

  button {
      font-size: 0.875rem; 
      padding: 8px 16px; 
  }

  h1 {
      font-size: 1.5rem;
      margin-top: 50px; 
  }
}

```

**CSS and Tailwind**

Here’s a sample from the index.blade
```
    <x-layout title="List the recipes">

    <h1 class="text-center my-12 font-poppins text-3xl text-gray-800 md:text-4xl lg:text-5xl hidden md:block">
    Here's a list of recipes</h1>

```

Here’s a sample from the layout.blade
```
<ul class="nav-links">
                    <li><a href="/recipes"class="text-stone-50">Home</a></li>
                    @can('edit')
                    <li><a href="/recipes/create"class="text-stone-50">Add Recipe</a></li>
                    @endcan
                    <li><a href="/recipes/about"class="text-stone-50">About</a></li>
                    @guest
                    <li><a href="/login"class="text-stone-50">Sign in</a></li>
                    @endguest
                </ul>



```
