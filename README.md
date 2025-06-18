# Mist 4610 Group Project 1


# Problem Description
My team am I are designing a data model for a "fake" local coffee shop named "Athens Cafe" where we strive to improve order processing, inventory tracking, employee management, and customer retention. 
As we all know, a coffee shop offers a variety of coffee beverages - ranging from classic coffee to special lattes and cold brews - as well as coffee beans, freshly baked pastries, and branded merchandise such as mugs and tote bags.
Customers have the opportunity to place orders in-store, where they can interact with baristas and employees in our cafe.
As an incentive, the coffee shop offers discounts on select items to encourage customers to return.
The ordering process involves customers selecting whatever they want, followed by baristas  preparing and serving the beverages while ensuring quality and efficiency.
In other words, customers order these products and are fulfilled by employees through the ordering process.
To improve customer satisfaction, customers have the opportunity to provide feedback based on their experiences with us that day. Feedback is important because it helps us maintain high standards and helps us refine our operations.
This datamodel will support inventory tracking by monitoring stock levels of coffee, coffee beans, and other ingredients; this ensures timely restocking and reduces wasted resources.
Employee management is another important aspect of our data model, with the system maintaining schedules, tracking hours worked, and tracking performance metrics to make work smoother and get the most out of our team.
Ultimately, by implementing this database, "Athens Cafe" aims to enhance its ability to meet customer needs, maintain high product quality, and create a data-driven approach to running daily operations.

# Data Model
![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Image%203-18-25%20at%2011.46%20AM.jpeg)
This data model is based off of a "fake" local Athens Coffee Shop and shows the relationships between different entities that we will need to use in our store.

The Customers entity represents the people that give the coffee shop business by making purchases; they are at the heart of the business. Customers have the attributes name, email, and phone number. Each customer can place multiple orders, establishing a one-to-many relationship between Customers and Orders.

The Orders entity records all purchases made by customers, detailing the attributes total amount, order date, and the payment method used. Orders are linked to OrderDetails, which breaks down each order into individual line items. Since an order consists of multiple items and each item can be part of multiple orders, there is a many-to-many relationship between Orders and MenuItems, resolved through the OrderDetails associative entity.

The MenuItems table represents all the food and drink options available. Each item has the attributes name, category (e.g., coffee, sandwich), price, and availability status. These items are also linked to the Inventory entity, which keeps track of how much we have in stock. Since each item in the menu has a supplier that provides it, there is a many-to-one relationship between Inventory and Suppliers, where each supplier can provide multiple inventory items, but a menu item can only have one supplier. The Suppliers entity stores the details of vendors that supply ingredients and goods to the coffee shop. It includes the attribiutes supplier names, contact information, and the type of supplies they provide.

The coffee shop also has employees who make the orders happen and manage overall operations. The Employees entity keeps track of employee attributes including name, role, salary, and hire date. Employees are responsible for processing orders, creating a one-to-many relationship between Employees and Orders. Additionally, employee work schedules are stored in the EmployeeSchedule table, which maintains records of shift start and end times.

To improve the coffee shop and get feedback, the business collects CustomerFeedback, where customers can rate their experience and leave comments on their orders. Each feedback entry is linked to both a customer and a specific order, establishing relationships between CustomerFeedback, Customers, and Orders.

The coffee shop also offers Discounts on certain orders, with the attributes discount percentage, description, and validity period. Each discount is applied to an order, forming a one-to-many relationship between Orders and Discounts.

Finally, the Payments table records financial transactions, including payment methods, amounts, and dates. Since each order results in a payment transaction, there is a one-to-one relationship between Orders and Payments.

I would also like to mention that the dashed lines indicate a non-identifying relationship which means that the child entity can exist independently of the parent entity. In contrast, the solid black lines indicate a idetnifying relationship which shows that the child can't exist independently from the parent entity.

# Data Dictionary
![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Orders)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Customers)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/OrderDetails)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Payments)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/MenuItems)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Discounts)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Employees)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/EmployeeSchedule)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Inventory)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/CustomerFeedback)

![Datamodel](https://github.com/agd0221/MIST4610Project/blob/main/Suppliers)

# Queries

<img width="850" alt="image" src="https://github.com/user-attachments/assets/5a689b5e-a7e9-4f72-83ba-c141a6775ac9" />

Query 1 (Simple):
Query 1 retrieves a list of all employees, displaying their EmployeeID, Name, and Role. It directly pulls the necessary information from the Employees table without any joins or filters.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/7c5b47ca-8e49-4791-8e50-4553b7a62ba7" />

This query is useful for managers and HR teams who need a quick overview of all employees within the organization, along with their roles. It can serve as a foundation for more detailed employee reports, such as identifying specific roles within departments, tracking employee performance, or even managing schedules.

Query 2 (Simple):
Query 2 retrieves the Rating and Comments from the CustomerFeedback table where the Rating is less than or equal to 3.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/0a41de53-c276-45b3-acaf-bd8d3222caa8" />

This query helps managers quickly identify negative or critical customer feedback. By filtering for ratings of 3 or lower, it allows managers to focus on areas that may need attention, such as customer service or product quality. Reviewing this feedback can lead to actionable insights, allowing businesses to address customer concerns, improve their offerings, and enhance overall customer satisfaction. 

Query 3 (Simple):
Query 3 retrieves the Name, Price, and Availability for each menu item from the MenuItems table. This simple query provides key details about the menu items, allowing businesses to quickly view essential product information.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/a00d477c-23b6-4e0b-a3e8-42f5fe27ae04" />

This query is particularly useful for businesses that need an overview of their menu offerings. By selecting the name, price, and availability of each menu item, it provides a snapshot of the products available for customers to order.

Query 4 (Simple):
Query 4 retrieves the Name, Role, ShiftDate, ShiftStartTime, and ShiftEndTime for each employee by joining the Employees and EmployeeSchedule tables. It connects the two tables on the EmployeeID and Employees_EmployeeID to get the employee’s schedule information.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/7f88538b-002b-4610-855c-9d1e62f547d4" />

This query provides a detailed view of each employee's scheduled shifts, including the date and start and end times of their shifts. By joining the Employees and EmployeeSchedule tables, the query enables managers to track when each employee is scheduled to work. This information is crucial for scheduling, shift planning, and resource management. It also helps HR teams or managers ensure proper staffing levels, avoid scheduling conflicts, and monitor employee availability.

Query 5 (Complex):
Query 5 lists the quantity of each inventory item along with the name of the supplier that provides the item where the quantity in stock is below 100 units. The results are ordered in ascending order based on quantity, showing the items with the lowest stock first.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/511ec4c8-f539-42c5-b11f-f440d328eda3" />

Query 5 allows managers to quickly identify which inventory items are running low and which suppliers provide these items. By focusing on items with quantities below 100, managers can prioritize reordering essential ingredients, beverages, or supplies before they run out. Listing the results in ascending order based on quantity makes it easier to spot the most critically low items first, allowing for timely restocking and smooth coffee shop operations. 

Query 6 (Complex):
Query 6 lists each menu item along with the total quantity of that item ordered across all orders. It joins the MenuItems and OrderDetails tables to calculate the total quantity ordered for each item, groups the results by item, and orders them in descending order based on the total quantity ordered.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/738d263a-7023-49f8-9d22-96be2d203cfc" />

Query 6 enables managers to see which menu items are the most popular based on the total quantity ordered. This helps with decisions such as inventory planning, promotional focus, and menu adjustments. By identifying top-selling items, managers can ensure that sufficient inventory is maintained, streamline the supply chain for these high-demand products, and potentially create promotions or bundles around them. Sorting the results in descending order highlights the best-selling items at the top, allowing managers to prioritize attention on the most impactful menu offerings.

Query 7 (Complex):
Query 7 retrieves the OrderDateTime, Name of the menu item, and the total quantity of that menu item ordered (TotalQuantity) for each specific day. It joins the Orders, OrderDetails, and MenuItems tables to calculate the total quantity ordered for each item, then compares the total quantity to identify the most ordered item for each day.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/c25b37cd-0365-4de8-9ac4-e546f032c09e" />

This query helps businesses identify the top-selling menu item for each day based on the total quantity ordered. By using a subquery to calculate the maximum total quantity ordered on each day, the query ensures that only the highest-selling item for each day is returned. Sorting and grouping the results by order date and item name allows managers to easily track which menu items are most popular.

Query 8 (Complex):
Query 8 retrieves the supplier names, the number of menu items each supplier provides (ItemsSupplied), and the percentage of total menu items supplied by each supplier (PercentOfTotalItems). The results are grouped by supplier and sorted by the percentage of menu items each supplier provides.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/fd16509d-54ae-4623-890f-b9bd4afa11e6" />

This query allows managers to understand which suppliers are responsible for the most menu items and whether there are any suppliers underutilized. This query helped highlight we are not fully utilizing our suppliers.

Query 9 (Complex):
Query 9 retrieves the names, emails, and the total number of orders (referred to as "CustomerVisits") placed by each customer. It joins the Customers table with the Orders table to count how many orders each customer has placed, grouped by their name and email. 

<img width="450" alt="image" src="https://github.com/user-attachments/assets/20904053-f14b-47dd-9e5c-b3196faa9d0c" />

This query helps businesses track the number of visits for each customer. By grouping the data by customer Name and Email, it allows the business to gain insights into customer engagement. With this information, managers can identify frequent visitors. By knowing the visit count for each customer, businesses can assess customer retention and identify potential areas for improvement in customer experience.

Query 10 (Complex):
Query 10 retrieves the OrderID, CustomerID, and OrderDateTime for orders that contain items with discounts applied. The query uses an EXISTS clause to check if there are any records in the OrderDetails table that correspond to the order, and whether the order has a discount associated with it.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/d2c5f19b-8215-4e2d-8a10-074ab633d24a" />

This query is useful for businesses looking to identify orders that involved discounted items. By using the EXISTS clause, it checks if the OrderDetails table contains any items that are linked to discounts in the Discounts table.

# Database Information
Name of the database: al_Group_47114_G9


