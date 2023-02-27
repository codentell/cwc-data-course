+++
title = "01. Basic Querying 👩‍🏫🧑‍🏫"
weight = 1
tags = ["sql"] 
+++

```python
from sqlalchemy import create_engine
from sqlalchemy import Column, Integer, String, Float

from sqlalchemy.ext.declarative import declarative_base
Base = declarative_base()
class BaseballPlayer(Base):
    __tablename__ = "player"
    player_id = Column(String, primary_key=True)
    birth_year = Column(Integer)
    birth_month = Column(Integer)
    birth_day = Column(Integer)
    birth_country = Column(String)
    birth_state = Column(String)
    birth_city = Column(String)
    name_first = Column(String)
    name_last = Column(String)
    name_given = Column(String)
    weight = Column(Integer)
    height = Column(Integer)
    bats = Column(String)
    throws = Column(String)
    debut = Column(String)
    final_game = Column(String)
# Create Database Connection
engine = create_engine('sqlite:///./resources/database.sqlite')

Base.metadata.create_all(engine)

from sqlalchemy.orm import Session
session = Session(bind=engine)
# Print all of the player names in the database
players = session.query(BaseballPlayer)
for player in players:
    print(player.name_given)

# Find the number of players from the USA
usa = session.query(BaseballPlayer).\
    filter(BaseballPlayer.birth_country == 'USA').count()
print(f"There are {usa} players from the USA")

# Find those players who were born before 1990
born_before_1990 = session.query(BaseballPlayer).\
    filter(BaseballPlayer.birth_year < 1990).count()
    
print(f"{born_before_1990} players were born before 1990")

# Find those players from the USA who were born after 1989
born_after_1989 = session.query(BaseballPlayer).\
    filter(BaseballPlayer.birth_year > 1989).filter(BaseballPlayer.birth_country == "USA").\
    count()
print(f"{born_after_1989} USA players were born after 1989")

# Statistical analysis
from scipy import stats
from numpy import mean
# Filter for players born before 1940, and for players born in or after 1940
born_before_1940_height = session.query(BaseballPlayer).\
    filter(BaseballPlayer.birth_year < 1940)

born_after_1940_height = session.query(BaseballPlayer).\
    filter(BaseballPlayer.birth_year >= 1940)

# Number of players born before 1940
born_before_1940_height.count()

# Number of players born after 1940
born_after_1940_height.count()

# Filter out null values from lists
pre_1940_height_list = []
for player in born_before_1940_height:
    if type(player.height) == int:
        pre_1940_height_list.append(player.height)
        
post_1940_height_list = []
for player in born_after_1940_height:
    if type(player.height) == int:
        post_1940_height_list.append(player.height)        
# Average height for pre-1940 players
mean(pre_1940_height_list)

# Average height for post-1940 players
mean(post_1940_height_list)

# Unpaired (independent) t-test
stats.ttest_ind(post_1940_height_list, pre_1940_height_list)

```