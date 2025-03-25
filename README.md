## <p align="center">VIRTUAL ART GALLERY</p>

### Objectives:

### <p align="center">Artists Table</p>

```
-- Create the Artists table
CREATE TABLE Artists (
    ArtistID INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,
    Biography TEXT,
    Nationality VARCHAR(100)
);

```

![image](https://github.com/user-attachments/assets/cc3e8f48-b709-44d6-9d6a-f741227a3097)

### <p align="center">Categories table</p>

```

-- Create the Categories table
CREATE TABLE Categories (
    CategoryID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL
);

```

![image](https://github.com/user-attachments/assets/353529c4-6c64-4db5-befe-854ee88dcb8a)


### <p align="center">Categories table</p>

```
-- Create the Artworks table
CREATE TABLE Artworks (
    ArtworkID INT PRIMARY KEY,
    Title VARCHAR(255) NOT NULL,
    ArtistID INT,
    CategoryID INT,
    Year INT,
    Description TEXT,
    ImageURL VARCHAR(255),
    FOREIGN KEY (ArtistID) REFERENCES Artists (ArtistID) ON DELETE CASCADE,
    FOREIGN KEY (CategoryID) REFERENCES Categories (CategoryID) ON DELETE SET NULL
);
```

![image](https://github.com/user-attachments/assets/79c71b97-aa77-4e34-ad73-1228a5d138b5)


### <p align="center">Exhibitions table</p>

```
-- Create the Exhibitions table
CREATE TABLE Exhibitions (
    ExhibitionID INT PRIMARY KEY,
    Title VARCHAR(255) NOT NULL,
    StartDate DATE,
    EndDate DATE,
    Description TEXT
);

```

![image](https://github.com/user-attachments/assets/e69c4fb5-be7e-433e-b3f6-4919eaa162c1)

### <p align="center">ExhibitionArtworks table (Many-to-Many relationship)</p>

```
-- Create the ExhibitionArtworks table (Many-to-Many relationship)
CREATE TABLE ExhibitionArtworks (
    ExhibitionID INT,
    ArtworkID INT,
    PRIMARY KEY (ExhibitionID, ArtworkID),
    FOREIGN KEY (ExhibitionID) REFERENCES Exhibitions (ExhibitionID) ON DELETE CASCADE,
    FOREIGN KEY (ArtworkID) REFERENCES Artworks (ArtworkID) ON DELETE CASCADE
);
```

![image](https://github.com/user-attachments/assets/b535cebf-f34a-4838-b9b1-9946e45fbb56)

### <p align="center">DML(Insert sample data to tables)</p>

#### inserting sample data into Artists  table

```
INSERT INTO Artists (ArtistID, Name, Biography, Nationality) VALUES
(1, 'Pablo Picasso', 'Renowned Spanish painter and sculptor.', 'Spanish'),
(2, 'Vincent van Gogh', 'Dutch post-impressionist painter.', 'Dutch'),
(3, 'Leonardo da Vinci', 'Italian polymath of the Renaissance.', 'Italian'),
(4, 'Claude Monet', 'French impressionist painter known for water lilies.', 'French'),
(5, 'Frida Kahlo', 'Mexican painter known for surreal and self-portraits.', 'Mexican'),
(6, 'Salvador Dalí', 'Spanish surrealist artist famous for "The Persistence of Memory".', 'Spanish'),
(7, 'Michelangelo', 'Italian sculptor, painter, and architect of the Renaissance.', 'Italian'),
(8, 'Rembrandt', 'Dutch Golden Age painter and master of light and shadow.', 'Dutch'),
(9, 'Jackson Pollock', 'American abstract expressionist painter.', 'American'),
(10, 'Edvard Munch', 'Norwegian painter famous for "The Scream".', 'Norwegian');

```

![image](https://github.com/user-attachments/assets/397749f5-7160-4e3f-9b7a-d3519534cc02)

#### Inserting sample data into Categories  table
```
INSERT INTO Categories (CategoryID, Name) VALUES
(1, 'Painting'),
(2, 'Sculpture'),
(3, 'Photography'),
(4, 'Digital Art'),
(5, 'Calligraphy');

```
![image](https://github.com/user-attachments/assets/108d3ebe-d178-4c6e-92b6-73584b77fb98)

#### iInserting sample data into Artworks table

```
INSERT INTO Artworks (ArtworkID, Title, ArtistID, CategoryID, Year, Description, ImageURL) VALUES
(1, 'Starry Night', 2, 1, 1889, 'A famous painting by Vincent van Gogh.', 'starry_night.jpg'),
(2, 'Mona Lisa', 3, 1, 1503, 'The iconic portrait by Leonardo da Vinci.', 'mona_lisa.jpg'),
(3, 'Guernica', 1, 1, 1937, 'Pablo Picasso\'s powerful anti-war mural.', 'guernica.jpg'),
(4, 'The Persistence of Memory', 6, 1, 1931, 'A surrealist painting by Salvador Dalí.', 'persistence_memory.jpg'),
(5, 'Water Lilies', 4, 1, 1919, 'A series of impressionist paintings by Claude Monet.', 'water_lilies.jpg'),
(6, 'The Scream', 10, 1, 1893, 'A well-known expressionist painting by Edvard Munch.', 'the_scream.jpg'),
(7, 'The Creation of Adam', 7, 1, 1512, 'A fresco painting by Michelangelo on the Sistine Chapel ceiling.', 'creation_adam.jpg'),
(8, 'The Night Watch', 8, 1, 1642, 'A large Baroque painting by Rembrandt.', 'night_watch.jpg'),
(9, 'No. 5, 1948', 9, 1, 1948, 'An abstract expressionist painting by Jackson Pollock.', 'no5_1948.jpg'),
(10, 'The Two Fridas', 5, 1, 1939, 'A famous double self-portrait by Frida Kahlo.', 'two_fridas.jpg');

```

![image](https://github.com/user-attachments/assets/f8f2970a-8d59-4871-9bd2-3877930dfcd9)

#### Inserting sample data into Artworks table

```
INSERT INTO Exhibitions (ExhibitionID, Title, StartDate, EndDate, Description) VALUES
(1, 'Modern Art Masterpieces', '2023-01-01', '2023-03-01', 'A collection of modern art masterpieces.'),
(2, 'Renaissance Art', '2023-04-01', '2023-06-01', 'A showcase of Renaissance art treasures.'),
(3, 'Impressionist Wonders', '2023-07-01', '2023-09-01', 'An exhibition highlighting impressionist art.'),
(4, 'Surrealist Visions', '2023-10-01', '2023-12-01', 'A showcase of surrealist artworks.'),
(5, 'Abstract Expressions', '2024-01-01', '2024-03-01', 'Exploring abstract expressionist works.');

```

#### Insert Data into the Exhibitions Table

```
INSERT INTO Exhibitions (ExhibitionID, Title, StartDate, EndDate, Description) VALUES
(1, 'Modern Art Masterpieces', '2023-01-01', '2023-03-01', 'A collection of modern art masterpieces.'),
(2, 'Renaissance Art', '2023-04-01', '2023-06-01', 'A showcase of Renaissance art treasures.'),
(3, 'Impressionist Wonders', '2023-07-01', '2023-09-01', 'An exhibition highlighting impressionist art.'),
(4, 'Surrealist Visions', '2023-10-01', '2023-12-01', 'A showcase of surrealist artworks.'),
(5, 'Abstract Expressions', '2024-01-01', '2024-03-01', 'Exploring abstract expressionist works.');

```
![image](https://github.com/user-attachments/assets/77b82488-b414-4aa4-b9d2-60ba532b28c7)

#### Insert Data into the ExhibitionArtworks Table

```
INSERT INTO ExhibitionArtworks (ExhibitionID, ArtworkID) VALUES
(1, 1),  -- Starry Night in Modern Art Masterpieces
(1, 2),  -- Mona Lisa in Modern Art Masterpieces
(1, 3),  -- Guernica in Modern Art Masterpieces
(2, 2),  -- Mona Lisa in Renaissance Art
(2, 7),  -- The Creation of Adam in Renaissance Art
(3, 5),  -- Water Lilies in Impressionist Wonders
(3, 8),  -- The Night Watch in Impressionist Wonders
(4, 4),  -- The Persistence of Memory in Surrealist Visions
(4, 6),  -- The Scream in Surrealist Visions
(5, 9),  -- No. 5, 1948 in Abstract Expressions
(5, 10); -- The Two Fridas in Abstract Expressions

```

![image](https://github.com/user-attachments/assets/4eba410d-1ed9-41a1-8b21-3dcc46f928c8)

### <p align="center">Queries</p>

#### 1. Retrieve the names of all artists along with the number of artworks they have in the gallery, and list them in descending order of the number of artworks.

```
SELECT a.Name, COUNT(art.ArtworkID) AS ArtworkCount
FROM Artists a
LEFT JOIN Artworks art ON a.ArtistID = art.ArtistID
GROUP BY a.Name
ORDER BY ArtworkCount DESC;

```
![image](https://github.com/user-attachments/assets/351df769-5a89-47c5-b641-4fe1893a765f)

#### 2. List the titles of artworks created by artists from 'Spanish' and 'Dutch' nationalities, and order them by the year in ascending order.

```
SELECT art.Title, a.Name, a.Nationality, art.Year
FROM Artworks art
JOIN Artists a ON art.ArtistID = a.ArtistID
WHERE a.Nationality IN ('Spanish', 'Dutch')
ORDER BY art.Year ASC;

```

![image](https://github.com/user-attachments/assets/259053f2-1384-4e20-b072-d4bbede2320b)

#### 3. Find the names of all artists who have artworks in the 'Painting' category, and the number of artworks they have in this category.
```
SELECT a.Name, COUNT(art.ArtworkID) AS PaintingCount
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
JOIN Categories c ON art.CategoryID = c.CategoryID
WHERE c.Name = 'Painting'
GROUP BY a.Name;


```

![image](https://github.com/user-attachments/assets/cab8d67d-fdbf-405b-b445-0d93736d4076)


#### 4. List the names of artworks from the 'Modern Art Masterpieces' exhibition, along with their artists and categories.

```
SELECT art.Title, a.Name AS Artist, c.Name AS Category
FROM ExhibitionArtworks ea
JOIN Artworks art ON ea.ArtworkID = art.ArtworkID
JOIN Artists a ON art.ArtistID = a.ArtistID
JOIN Categories c ON art.CategoryID = c.CategoryID
JOIN Exhibitions e ON ea.ExhibitionID = e.ExhibitionID
WHERE e.Title = 'Modern Art Masterpieces';

```

![image](https://github.com/user-attachments/assets/f4666cee-2859-46c8-aec9-818034f2937a)



#### 5. Find the artists who have more than two artworks in the gallery.

```
SELECT a.Name, COUNT(art.ArtworkID) AS ArtworkCount
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
GROUP BY a.Name
HAVING COUNT(art.ArtworkID) > 2;

```
![image](https://github.com/user-attachments/assets/ccd7b6ae-4f80-47dc-bb33-aa7dd83befbf)


#### 6. Find the titles of artworks that were exhibited in both 'Modern Art Masterpieces' and 'Renaissance Art' exhibitions.

```
SELECT art.Title
FROM ExhibitionArtworks ea1
JOIN Exhibitions e1 ON ea1.ExhibitionID = e1.ExhibitionID
JOIN ExhibitionArtworks ea2 ON ea1.ArtworkID = ea2.ArtworkID
JOIN Exhibitions e2 ON ea2.ExhibitionID = e2.ExhibitionID
JOIN Artworks art ON ea1.ArtworkID = art.ArtworkID
WHERE e1.Title = 'Modern Art Masterpieces'
AND e2.Title = 'Renaissance Art';

```
![image](https://github.com/user-attachments/assets/0a6860ff-4521-4141-bcfc-ad6f12738087)



#### 7. Find the total number of artworks in each category

```
SELECT c.Name AS Category, COUNT(a.ArtworkID) AS TotalArtworks
FROM Categories c
LEFT JOIN Artworks a ON c.CategoryID = a.CategoryID
GROUP BY c.Name;

```
![image](https://github.com/user-attachments/assets/f3b538a1-0b5b-4530-88aa-e6bb2001d711)


#### 8. List artists who have more than 3 artworks in the gallery.

```
SELECT a.Name, COUNT(art.ArtworkID) AS ArtworkCount
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
GROUP BY a.Name
HAVING COUNT(art.ArtworkID) > 3;

```

![image](https://github.com/user-attachments/assets/6dca447d-51b3-4d8f-8641-5566ba8d1459)

#### 9. Find the artworks created by artists from a specific nationality (e.g., Spanish).

```
SELECT art.Title, a.Name, a.Nationality
FROM Artworks art
JOIN Artists a ON art.ArtistID = a.ArtistID
WHERE a.Nationality = 'Spanish';

```

![image](https://github.com/user-attachments/assets/21a275c2-667b-4e27-8e50-92fd3ca0af0d)

#### 10. List exhibitions that feature artwork by both Vincent van Gogh and Leonardo da Vinci.

```
SELECT e.Title
FROM Exhibitions e
JOIN ExhibitionArtworks ea1 ON e.ExhibitionID = ea1.ExhibitionID
JOIN Artworks a1 ON ea1.ArtworkID = a1.ArtworkID
JOIN Artists ar1 ON a1.ArtistID = ar1.ArtistID
JOIN ExhibitionArtworks ea2 ON e.ExhibitionID = ea2.ExhibitionID
JOIN Artworks a2 ON ea2.ArtworkID = a2.ArtworkID
JOIN Artists ar2 ON a2.ArtistID = ar2.ArtistID
WHERE ar1.Name = 'Vincent van Gogh' AND ar2.Name = 'Leonardo da Vinci';

```
![image](https://github.com/user-attachments/assets/c1a352fb-84ce-48ca-93f1-d03b097e3f4a)

#### 11. Find all the artworks that have not been included in any exhibition.

```

SELECT art.Title
FROM Artworks art
LEFT JOIN ExhibitionArtworks ea ON art.ArtworkID = ea.ArtworkID
WHERE ea.ExhibitionID IS NULL;

```

![image](https://github.com/user-attachments/assets/c61c5248-3308-45c1-8bf9-899e36d52bfe)

#### 12. List artists who have created artworks in all available categories.
```
SELECT a.Name
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
JOIN Categories c ON art.CategoryID = c.CategoryID
GROUP BY a.Name
HAVING COUNT(DISTINCT art.CategoryID) = (SELECT COUNT(*) FROM Categories);

```
![image](https://github.com/user-attachments/assets/b2e28279-5796-42d6-a281-bfba40db24bb)
'

#### 13. List the total number of artworks in each category.
```
SELECT c.Name AS Category, COUNT(a.ArtworkID) AS TotalArtworks
FROM Categories c
LEFT JOIN Artworks a ON c.CategoryID = a.CategoryID
GROUP BY c.Name;

```
![image](https://github.com/user-attachments/assets/3625f206-8f7a-4cba-9839-86597c0417a5)


#### 14. Find the artists who have more than 2 artworks in the gallery.
```
SELECT a.Name, COUNT(art.ArtworkID) AS ArtworkCount
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
GROUP BY a.Name
HAVING COUNT(art.ArtworkID) > 2;

```
![image](https://github.com/user-attachments/assets/87cdbd5f-9720-466e-9ff1-e4fd6c946f75)


#### 15. List the categories with the average year of artworks they contain, only for categories with more than 1 artwork.

```
SELECT c.Name AS Category, AVG(art.Year) AS AvgYear
FROM Categories c
JOIN Artworks art ON c.CategoryID = art.CategoryID
GROUP BY c.Name
HAVING COUNT(art.ArtworkID) > 1;

```
![image](https://github.com/user-attachments/assets/a31cc445-685f-409c-87ad-32070ff2a456)

#### 16. Find the artworks that were exhibited in the 'Modern Art Masterpieces' exhibition.

```
SELECT art.Title
FROM Artworks art
JOIN ExhibitionArtworks ea ON art.ArtworkID = ea.ArtworkID
JOIN Exhibitions e ON ea.ExhibitionID = e.ExhibitionID
WHERE e.Title = 'Modern Art Masterpieces';

```

![image](https://github.com/user-attachments/assets/d9765efb-c384-4497-a5a5-b564bb977ed9)

#### 17. Find the categories where the average year of artworks is greater than the average year of all artworks.

```
SELECT c.Name AS Category, AVG(art.Year) AS AvgCategoryYear
FROM Categories c
JOIN Artworks art ON c.CategoryID = art.CategoryID
GROUP BY c.Name
HAVING AVG(art.Year) > (SELECT AVG(Year) FROM Artworks);

```


![image](https://github.com/user-attachments/assets/bae29e03-7ff6-4fe5-86f8-b611efee1fc9)

#### 18. List the artworks that were not exhibited in any exhibition.

```
SELECT art.Title
FROM Artworks art
LEFT JOIN ExhibitionArtworks ea ON art.ArtworkID = ea.ArtworkID
WHERE ea.ExhibitionID IS NULL;

```

![image](https://github.com/user-attachments/assets/1fb5d188-c203-427d-8925-210c71f7c23c)

#### 19. Show artists who have artworks in the same category as "Mona Lisa."

```
SELECT DISTINCT a.Name
FROM Artists a
JOIN Artworks art ON a.ArtistID = art.ArtistID
WHERE art.CategoryID = (SELECT CategoryID FROM Artworks WHERE Title = 'Mona Lisa');

```


![image](https://github.com/user-attachments/assets/451f60b4-5aea-40e3-a671-4b59170d8509)

#### 20. List the names of artists and the number of artworks they have in the gallery.

```
SELECT a.Name, COUNT(art.ArtworkID) AS ArtworkCount
FROM Artists a
LEFT JOIN Artworks art ON a.ArtistID = art.ArtistID
GROUP BY a.Name;

```


![image](https://github.com/user-attachments/assets/dfc756ca-b2d4-432a-aa86-a689f812fa06)

