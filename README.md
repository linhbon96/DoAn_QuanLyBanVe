��#   D o A n 
 Movie-API \
react-movie\src\components

# Movie Booking System - Database Schema

## Database Tables Overview

### 1. Users Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| UserId | INTEGER | Yes | User Identifier |
| UserName | VARCHAR | No | Username/Login Name |
| PasswordHash | VARCHAR | No | MD5 Encrypted Password |
| Role | VARCHAR | No | User Classification |

### 2. Movies Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| MovieId | INTEGER | Yes | Movie Identifier |
| Title | TEXT | No | Movie Title |
| Description | TEXT | No | Movie Introduction |
| ReleaseDate | TIMESTAMPTZ | No | Premiere Date |
| Genre | TEXT | No | Movie Genre |
| Duration | TEXT | No | Duration (minutes) |
| ImageUrl | TEXT | No | Cover Image Path |

### 3. Showtimes Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| ShowtimeId | INTEGER | No | Showtime Identifier |
| MovieId | INTEGER | No | Movie Identifier |
| TheaterId | INTEGER | No | Theater Room Identifier |
| ShowDate | TIMESTAMPTZ | Yes | Screening Date |
| ShowHour | INTERVAL | No | Screening Time |

### 4. Theaters Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| TheaterId | INTEGER | No | Theater Room Identifier |
| Name | TEXT | No | Theater Room Name |
| Rows | INTEGER | No | Seat Rows |
| Columns | INTEGER | No | Seat Columns |
| Location | TEXT | Yes | Location |

### 5. Seats Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| Id | INTEGER | No | Seat Identifier |
| Rows | TEXT | No | Seat Row |
| Columns | INTEGER | No | Seat Column |
| IsAvailable | BOOLEAN | No | Seat Status (Locked/Available) |
| ShowTimeId | TEXT | No | Showtime Location |
| OrderId | INTEGER | Yes | Order Identifier |
| LockedUntil | TIMESTAMPTZ | Yes | Seat Lock Time Limit |

### 6. Tickets Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| TicketId | INTEGER | No | Ticket Identifier |
| MovieId | INTEGER | No | Movie Identifier |
| ShowtimeId | INTEGER | No | Showtime Identifier |
| TheaterId | INTEGER | No | Theater Room Identifier |
| Price | NUMERIC | No | Ticket Price |
| UserId | INTEGER | Yes | User Identifier |
| SeatId | INTEGER | Yes | Seat Identifier |

### 7. TicketInfo Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| TicketInfoId | INTEGER | No | Ticket Info Identifier |
| TicketId | INTEGER | No | Ticket Identifier |
| OrderId | INTEGER | Yes | Order Identifier |
| UserId | INTEGER | Yes | User Identifier |

### 8. Items Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| ItemId | INTEGER | No | Item Identifier |
| Name | VARCHAR | No | Item Name |
| Price | NUMERIC | Yes | Item Price |

### 9. ItemOrders Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| OrderId | INTEGER | No | Order Identifier |
| ItemId | INTEGER | No | Item Identifier |
| Quantity | INTEGER | Yes | Quantity |

### 10. Orders Table
| Column | Data Type | Nullable | Description |
|--------|-----------|----------|-------------|
| Id | INTEGER | No | Order Identifier |
| OrderDate | INTEGER | No | Order Date |
| TotalAmount | NUMERIC | Yes | Total Payment |

## Relationships
- Each Movie can have multiple Showtimes
- Each Showtime belongs to a specific Theater and Movie
- Each Ticket is associated with a Movie, Showtime, Theater, and Seat
- Users can have multiple Tickets and Orders
- Orders can contain multiple Items (through ItemOrders)

## Database Design Principles
- Use of foreign keys to maintain referential integrity
- Normalized database structure
- Flexible schema to support various booking scenarios

