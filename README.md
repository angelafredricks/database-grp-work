Bookstoredb



-- DATA QUERIES FOR TABLES
USE bookstoredb;
-- Insert  AUTHOR 

INSERT INTO author (firstName, lastName, bio) VALUES
('George', 'Orwell', 'Author of dystopian novels.'),
('Chinua', 'Achebe', 'Renowned Nigerian novelist.'),
('J.K.', 'Rowling', 'British author of Harry Potter series.'),
('Ngugi', 'wa Thiong\'o', 'Kenyan writer and academic.'),
('Gabriel', 'Garcia Marquez', 'Colombian author and Nobel laureate.');

-- Insert LANGUAGE 
INSERT INTO bookLanguage (languageName) VALUES 
('English'), ('Swahili'), ('French'), ('German'), ('Spanish');

-- Insert Publisher
INSERT INTO publisher (publisherName) VALUES 
('Penguin Random House'), ('HarperCollins'), ('Macmillan'), 
('Oxford University Press'), ('Nation Media Group');


INSERT INTO book (title, isbn, price, synopsis, publicationDate, publisherID, languageID)
VALUES
('1984', '9780451524935', 12.99, 'A dystopian novel by George Orwell.', '1949-06-08', 1, 1),
('Animal Farm', '9780451526342', 10.50, 'A satirical tale by George Orwell.', '1945-08-17', 1, 1),
('Things Fall Apart', '9780385474542', 11.20, 'A classic African novel.', '1958-06-17', 2, 1),
('No Longer at Ease', '9780435905283', 10.00, 'Sequel to Things Fall Apart.', '1960-10-01', 2, 1),
('Harry Potter and the Sorcerer\'s Stone', '9780590353427', 15.00, 'First in the Harry Potter series.', '1997-06-26', 1, 1),
('Harry Potter and the Chamber of Secrets', '9780439064871', 15.50, 'Second in the Harry Potter series.', '1998-07-02', 1, 1),
('Wizard of the Crow', '9780099520644', 14.99, 'Political satire by Ngugi wa Thiong\'o.', '2006-04-10', 3, 1),
('Petals of Blood', '9780435908445', 13.75, 'A critique of post-colonial Kenya.', '1977-06-16', 3, 1),
('One Hundred Years of Solitude', '9780060883287', 17.25, 'A landmark in magical realism.', '1967-05-30', 4, 5),
('Love in the Time of Cholera', '9780307389732', 16.50, 'A romantic epic.', '1985-09-05', 4, 5),
('The Hobbit', '9780547928227', 13.90, 'A prelude to Lord of the Rings.', '1937-09-21', 1, 1),
('Lord of the Rings', '9780618640157', 19.99, 'Epic fantasy trilogy.', '1954-07-29', 1, 1),
('A Man of the People', '9780435905291', 9.99, 'Political satire by Achebe.', '1966-01-01', 2, 1),
('The River Between', '9780435905482', 8.75, 'Story of two villages in conflict.', '1965-01-01', 3, 2),
('Decolonising the Mind', '9780435909879', 10.25, 'Reflections on language and culture.', '1986-01-01', 3, 1),
('Death Constant Beyond Love', '9780140157352', 12.45, 'Short story by Marquez.', '1970-08-01', 4, 5)



-- Insert  bookAuthor
-- George Orwell (authorID = 1)
INSERT INTO bookAuthor (authorID, bookID) VALUES (1, 1), (1, 2);

-- Chinua Achebe (authorID = 2)
INSERT INTO bookAuthor (authorID, bookID) VALUES (2, 3), (2, 4), (2, 13);

-- J.K. Rowling (authorID = 3)
INSERT INTO bookAuthor (authorID, bookID) VALUES (3, 5), (3, 6), (3, 17);

-- Ngugi wa Thiong'o (authorID = 4)
INSERT INTO bookAuthor (authorID, bookID) VALUES (4, 7), (4, 8), (4, 14), (4, 15);

-- Gabriel Garcia Marquez (authorID = 5)
INSERT INTO bookAuthor (authorID, bookID) VALUES (5, 9), (5, 10), (5, 16);


-- Insert  CUSTOMER data
INSERT INTO customer (firstName, lastName, email, phoneNumber) VALUES
('Alice', 'Wambui', 'alice@example.com', '+254700000001'),
('Brian', 'Odhiambo', 'brian@example.com', '+254700000002'),
('Cynthia', 'Kariuki', 'cynthia@example.com', '+254700000003'),
('David', 'Mutiso', 'david@example.com', '+254700000004'),
('Eva', 'Njeri', 'eva@example.com', '+254700000005');

-- Insert Country
INSERT INTO country (countryName) VALUES
('Kenya'), ('Uganda'), ('Tanzania');

-- Insert address
INSERT INTO address (street, city, zipCode, countryID) VALUES
('Moi Avenue', 'Nairobi', '00100', 1),
('Tom Mboya Street', 'Kisumu', '40100', 1),
('Lumumba Road', 'Mombasa', '80100', 1),
('Kololo Lane', 'Kampala', '00200', 2),
('Ubungo Street', 'Dar es Salaam', '00300', 3);

-- Insert address status
INSERT INTO addressStatus (statusName) VALUES
('Home'), ('Work'), ('Shipping');

-- Insert Customer address
INSERT INTO customerAddress (customerID, addressID, statusID) VALUES
(1, 1, 1), -- Alice, Home
(2, 2, 3), -- Brian, Shipping
(3, 3, 1), -- Cynthia, Home
(4, 4, 2), -- David, Work
(5, 5, 1); -- Eva, Home

-- Insert Shipping Method
INSERT INTO shippingMethod (methodName, cost) VALUES
('Standard Delivery', 3.50),
('Express Delivery', 7.00),
('Pickup Point', 0.00);

-- Insert Order status
INSERT INTO orderStatus (statusValue) VALUES
('Pending'), ('Processing'), ('Shipped'), ('Delivered'), ('Cancelled');

-- Insert Customer Order
INSERT INTO customerOrder (customerID, statusID, methodID) VALUES
(1, 1, 1),  -- Alice, Pending, Standard
(2, 2, 2),  -- Brian, Processing, Express
(3, 3, 3);  -- Cynthia, Shipped, Pickup Point

-- Insert OrderLine
-- Order 1 (Alice)
INSERT INTO orderLine (bookID, orderID, quantity, unitPrice) VALUES
(1, 1, 1, 12.99), -- 1984
(5, 1, 1, 15.00); -- Harry Potter 1

-- Order 2 (Brian)
INSERT INTO orderLine (bookID, orderID, quantity, unitPrice) VALUES
(3, 2, 2, 11.20), -- Things Fall Apart
(4, 2, 1, 10.00); -- No Longer at Ease

-- Order 3 (Cynthia)
INSERT INTO orderLine (bookID, orderID, quantity, unitPrice) VALUES
(6, 3, 1, 15.50), -- Harry Potter 2
(7, 3, 1, 14.99); -- Wizard of the Crow

-- Insert Order History
-- Order 1
INSERT INTO orderHistory (orderID, statusID) VALUES 
(1, 1); -- Pending

-- Order 2
INSERT INTO orderHistory (orderID, statusID) VALUES 
(2, 1), 
(2, 2); -- Processing

-- Order 3
INSERT INTO orderHistory (orderID, statusID) VALUES 
(3, 1), 
(3, 2), 
(3, 3); -- Shipped





















