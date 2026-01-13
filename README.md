classDiagram
    direction TB

    %% ======================
    %% FACT TABLE
    %% ======================
    class Orders {
        <<Fact Table>>
        Order ID
        Order Date
        Customer ID
        Product ID
        Region
        Ship Mode
        Sales
        Quantity
        Profit
        Discount
    }

    %% ======================
    %% DIMENSION TABLES
    %% ======================
    class Dim_Date {
        <<Dimension>>
        Date
        Year
        Quarter
        Month
        Year-Month
    }

    class Dim_Product {
        <<Dimension>>
        Product ID
        Product Name
        Category
        Sub-Category
    }

    class Dim_Customer {
        <<Dimension>>
        Customer ID
        Customer Name
        Segment
    }

    class Dim_Geography {
        <<Dimension>>
        Country
        Region
        State
        City
    }

    class Dim_ShipMode {
        <<Dimension>>
        Ship Mode
    }

    class Dim_Returns {
        <<Dimension>>
        Order ID
        Returned
    }

    class Dim_People {
        <<Dimension>>
        Person
        Region
    }

    %% ======================
    %% RELATIONSHIPS (1 -> *)
    %% ======================
    Dim_Date "1" --> "*" Orders : filters
    Dim_Product "1" --> "*" Orders : filters
    Dim_Customer "1" --> "*" Orders : filters
    Dim_Geography "1" --> "*" Orders : filters
    Dim_ShipMode "1" --> "*" Orders : filters
    Dim_Returns "1" --> "*" Orders : filters
    Dim_People "1" --> "*" Dim_Geography : manages
