# Project Responsive Web Design using Bootstrap
## Date:

## AIM:
To create a simplified clone of Dribbble (https://dribbble.com/) landing page.


## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Insert the necessary CSS and JavaScript files as external in order to use Bootstrap.

### Step 5:
Create a HTML file and include the needed Bootstrap components.

### Step 6:
Publish the website in the LocalHost.

## PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dribbble-like Layout with Rating</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1e1e1e;
            color: white;
        }

        /* Navigation Bar */
        header {
            background-color: #ff4a56;
            padding: 15px;
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 10;
        }

        header .logo {
            font-size: 24px;
            font-weight: bold;
        }

        header nav {
            display: flex;
            gap: 15px;
        }

        header nav a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }

        header nav a:hover {
            text-decoration: underline;
        }

        /* Search Bar */
        .search-bar {
            display: flex;
            justify-content: center;
            padding-top: 70px; /* Space for fixed navbar */
        }

        .search-bar input {
            padding: 10px;
            width: 80%;
            max-width: 500px;
            border-radius: 25px;
            border: 1px solid #333;
            background-color: #444;
            color: white;
            font-size: 16px;
        }

        .search-bar input::placeholder {
            color: #bbb;
        }

        /* Featured Section */
        .featured {
            background-color: #333;
            padding: 40px;
            text-align: center;
        }

        .featured h2 {
            font-size: 36px;
            margin-bottom: 20px;
        }

        .featured p {
            font-size: 18px;
            color: #bbb;
        }

        /* Main Content Section */
        .main-content {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            padding: 30px;
            padding-top: 150px; /* Padding for the fixed navbar */
        }

        .card {
            background-color: #333;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            transition: all 0.3s ease-in-out;
        }

        .card:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
        }

        .card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .card-body {
            padding: 15px;
        }

        .card-body h3 {
            font-size: 18px;
            margin: 0;
        }

        .card-body p {
            font-size: 14px;
            color: #ccc;
            margin-top: 10px;
        }

        /* Star Rating */
        .star-rating {
            display: flex;
            gap: 5px;
            margin-top: 10px;
        }

        .star-rating span {
            font-size: 20px;
            cursor: pointer;
            color: #ccc;
            transition: color 0.2s ease;
        }

        .star-rating span:hover,
        .star-rating span.rated {
            color: #ffca28; /* Gold color for rated stars */
        }

        /* Buttons */
        .card-button {
            display: flex;
            justify-content: space-between;
            padding-top: 10px;
        }

        .card-button button {
            background-color: #ff4a56;
            border: none;
            color: white;
            padding: 10px;
            font-size: 14px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .card-button button:hover {
            background-color: #e74c3c;
        }

        /* New Arrivals Section */
        .new-arrivals-btn {
            text-align: center;
            padding: 20px;
        }

        .new-arrivals-btn button {
            background-color: #3498db;
            border: none;
            color: white;
            padding: 12px 24px;
            font-size: 16px;
            border-radius: 25px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .new-arrivals-btn button:hover {
            background-color: #2980b9;
        }

        /* Footer */
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 15px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        footer .credit {
            font-size: 14px;
            color: #bbb;
        }

    </style>
</head>
<body>

    <!-- Navigation Bar -->
    <header>
        <div class="logo">Dribbble</div>
        <nav>
            <a href="#">Explore</a>
            <a href="#">Shots</a>
            <a href="#">Designers</a>
            <a href="#">Jobs</a>
        </nav>
    </header>

    <!-- Search Bar -->
    <div class="search-bar">
        <input type="text" placeholder="Search for dresses, designers...">
    </div>

    <!-- Featured Section -->
    <div class="featured">
        <h2>Featured Dresses</h2>
        <p>Explore our curated collection of elegant and trendy dresses perfect for any occasion.</p>
    </div>

    <!-- New Arrivals Button -->
    <div class="new-arrivals-btn">
        <button onclick="toggleNewArrivals()">Show New Arrivals</button>
    </div>

    <!-- Main Content Section -->
    <div class="main-content" id="designs-container">
        <!-- Card 1 -->
        <div class="card">
            <img src="b4.png" alt="Dress 1">
            <div class="card-body">
                <h3>Elegant Evening Gown</h3>
                <p>This luxurious evening gown features intricate beadwork, perfect for a night to remember.</p>
                <!-- Rating System -->
                <div class="star-rating" onclick="rateDesign(event, 1)">
                    <span class="star" data-index="1">&#9733;</span>
                    <span class="star" data-index="2">&#9733;</span>
                    <span class="star" data-index="3">&#9733;</span>
                    <span class="star" data-index="4">&#9733;</span>
                    <span class="star" data-index="5">&#9733;</span>
                </div>
            </div>
            <div class="card-button">
                <button>Buy Now</button>
                <button onclick="toggleLike(this)">&#10084;</button>
            </div>
        </div>

        <!-- Card 2 -->
        <div class="card">
            <img src="b3.png" alt="Dress 2">
            <div class="card-body">
                <h3>Floral Summer Dress</h3>
                <p>This lightweight floral dress is perfect for warm weather, offering a relaxed and chic style.</p>
                <!-- Rating System -->
                <div class="star-rating" onclick="rateDesign(event, 2)">
                    <span class="star" data-index="1">&#9733;</span>
                    <span class="star" data-index="2">&#9733;</span>
                    <span class="star" data-index="3">&#9733;</span>
                    <span class="star" data-index="4">&#9733;</span>
                    <span class="star" data-index="5">&#9733;</span>
                </div>
            </div>
            <div class="card-button">
                <button>Buy Now</button>
                <button onclick="toggleLike(this)">&#10084;</button>
            </div>
        </div>

        <!-- Card 3 -->
        <div class="card">
            <img src="b6.png" alt="Dress 3">
            <div class="card-body">
                <h3>Red Carpet Ready Dress</h3>
                <p>This glamorous red dress with a plunging neckline is perfect for making a statement at any event.</p>
                <!-- Rating System -->
                <div class="star-rating" onclick="rateDesign(event, 3)">
                    <span class="star" data-index="1">&#9733;</span>
                    <span class="star" data-index="2">&#9733;</span>
                    <span class="star" data-index="3">&#9733;</span>
                    <span class="star" data-index="4">&#9733;</span>
                    <span class="star" data-index="5">&#9733;</span>
                </div>
            </div>
            <div class="card-button">
                <button>Buy Now</button>
                <button onclick="toggleLike(this)">&#10084;</button>
            </div>
        </div>

        <!-- Card 4 -->
        <div class="card">
            <img src="b7.png" alt="Dress 4">
            <div class="card-body">
                <h3>Vintage Lace Dress</h3>
                <p>This elegant vintage lace dress combines classic charm with modern sophistication, perfect for formal events or a romantic evening out.</p>
                <!-- Rating System -->
                <div class="star-rating" onclick="rateDesign(event, 4)">
                    <span class="star" data-index="1">&#9733;</span>
                    <span class="star" data-index="2">&#9733;</span>
                    <span class="star" data-index="3">&#9733;</span>
                    <span class="star" data-index="4">&#9733;</span>
                    <span class="star" data-index="5">&#9733;</span>
                </div>
            </div>
            <div class="card-button">
                <button>Buy Now</button>
                <button onclick="toggleLike(this)">&#10084;</button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="credit">
            Developed and Designed by Aaron Alex
        </div>
    </footer>

</body>
</html>

```


## OUTPUT:
![Screenshot (87)](https://github.com/user-attachments/assets/878608bb-24c4-4c0e-a542-0d3b0dcf7951)


## RESULT:
The Project for responsive web design using Bootstrap is completed successfully.
