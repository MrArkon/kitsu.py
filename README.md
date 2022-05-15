<h1 align="center">Kitsu.py</h1>
<p align="center">
    <a href="https://pypi.python.org/pypi/kitsu.py">
        <img src="https://img.shields.io/pypi/v/kitsu.py.svg?style=for-the-badge&color=orange&logo=&logoColor=white" />
    </a>
    <a href="https://github.com/MrArkon/kitsu.py/blob/master/LICENSE">
        <img src="https://img.shields.io/pypi/l/kitsu.py?style=for-the-badge" />
    </a>
    <a>
    <a href="https://www.codacy.com/gh/MrArkon/kitsu.py/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=MrArkon/kitsu.py&amp;utm_campaign=Badge_Grade">
        <img src="https://img.shields.io/codacy/grade/a04e4a4edbb84f6ea6d0c5a091a912a5?style=for-the-badge" />
    </a>
    <br> kitsu.py is an asynchronous API wrapper for Kitsu written in Python.
</p>

## Key Features
* Simple and modern Pythonic API using `async/await`
* Fully typed
* Filter & Limit functionality

## Requirements

Python 3.8+
* [aiohttp](https://pypi.org/project/aiohttp/)
* [python-dateutil](https://pypi.org/project/python-dateutil)

## Installing
To install the library, run the following commands:
```shell
# Linux/MacOS
python3 -m pip install -U kitsu.py

# Windows
py -3 -m pip install -U kitsu.py
```

## Usage

Search for an anime:
```python
import kitsu
import asyncio

client = kitsu.Client()

async def main():
    # Search a specific anime with the name
    anime = await client.search_anime("jujutsu kaisen", limit=1)
    
    print("Canonical Title: " + anime.canonical_title)
    print("Average Rating: " + str(anime.average_rating))
    
    # This returns a list of 5 animes in the spring season 2022
    animes_in_spring = await client.search_anime(limit=5, season_year=2022, season='spring')
    
    print(*[a.title for a in animes_in_spring], sep=", ")
    
    # Close the internal aiohttp ClientSession
    await client.close()

loop = asyncio.get_event_loop()
loop.run_until_complete(main())
```
This prints:
```
Canonical Title: Jujutsu Kaisen
Average Rating: 85.98
That Time I Got Reincarnated as a Slime: Ramiris to the Rescue, Blue Thermal, Q&A=E, Smol Adventures, Estab-Life: Great Escape
```
You can find more examples in the [examples](https://github.com/MrArkon/kitsu.py/tree/master/examples/) directory.
    
## Contributors
* [Dymattic](https://github.com/dymattic)

## License

This project is distributed under the [MIT](https://github.com/MrArkon/kitsu.py/blob/master/LICENSE.txt) license.
