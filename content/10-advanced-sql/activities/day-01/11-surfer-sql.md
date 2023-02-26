+++
title = "11. Surfer SQL 👩‍🎓👨‍🎓"
weight = 11
tags = ["advanced sql"] 
+++

In today’s final activity, you will test your SQLAlchemy skills and update your Surfer database.

## Instructions

* Modify the `Surfer` class created during the previous activity so that it will function with SQLAlchemy. Use the following parameters:

    * `__tablename__` should be "surfers".

    * `surfer_id` should be an integer and the primary key.

    * `name` should be a string capable of holding 255 characters.

    * `hometown` should be a string capable of holding 255 characters.

    * `rank` should be an integer.

* Create a new class called `Board`, which will function with SQLAlchemy and meet the following parameters:

    * `__tablename__` should be "surfboards".

    * `id` should be an integer and the primary key.

    * `surfer_id` should be an integer that references a surfer id in the "surfers" column.

    * `board_name` should be a string capable of holding 255 characters.

    * `color` should be a string capable of holding 255 characters.

    * `length` should be an integer.

* Pull a list of all of the surfers and surfboards already inside the database.

* Push a new surfer and surfboard to the tables in the database.

---

```python
# Import SQL Alchemy
from sqlalchemy import create_engine
# Import and establish Base for which classes will be constructed 
from sqlalchemy.ext.declarative import declarative_base
Base = declarative_base()
# Import modules to declare columns and column data types
from sqlalchemy import Column, Integer, String, Float

# Create Surfer and Board classes
# ----------------------------------
class Surfer(Base):
    __tablename__ = 'surfers'
    id = Column(Integer, primary_key=True)
    name = Column(String(255))
    hometown = Column(String(255))
    wipeouts = Column(Integer)
    rank = Column(Integer)


class Board(Base):
    __tablename__ = 'surfboards'
    id = Column(Integer, primary_key=True)
    surfer_id = Column(Integer)
    board_name = Column(String(255))
    color = Column(String(255))
    length = Column(Integer)
# Create specific instances of the Surfer and Board classes
# ----------------------------------
# Create a new surfer named "Bruno"
surfer = Surfer(name='Bruno', hometown="LA", rank=10)
# Create a new board and associate it with a surfer's ID
board = Board(surfer_id=1, board_name="Awwwyeah", color="Blue", length=68)

# Create Database Connection
# ----------------------------------
# Establish Connection
engine = create_engine("sqlite:///surfer.sqlite")
conn = engine.connect()
# Create both the Surfer and Board tables within the database
Base.metadata.create_all(conn)
# To push the objects made and query the server we use a Session object
from sqlalchemy.orm import Session
session = Session(bind=engine)
# Add "Bruno" to the current session
session.add(surfer)
# Add "Awwwyeah" to the current session
session.add(board)
# Commit both objects to the database
session.commit()

# Query the database and collect all of the surfers in the Surfer table
surfer_list = session.query(Surfer)
for bro in surfer_list:
    print(bro.name)
    print(bro.hometown)
    print(bro.rank)
```