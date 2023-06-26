---
layout: post
title:  Sonification of planet orbit data
date:   2023-06-26
description: Interactive data sonification and visualization using Tone.js and Three.js
tags: formatting links
---
## Introduction
This is some background to my data sonification project, which can be experienced live [here](https://phber.github.io/Solarsounds.js/). 
Sonification is the process that translates data into sound, or the aural counterpart to visualization. In this project, I decided to combine the two in order to _sonivisualize_ (yes, I just made that word up) orbital data from our solar system. The tools I used were [Three.js](https://github.com/mrdoob/three.js/) (visualization), [Tone.js](https://github.com/Tonejs/Tone.js) (sound effects) and some [Python](https://github.com/astropy/astropy) (data retrieval). In this post I will focus on the sound mapping of data, but if you are interested in the visualization, all codecan be found in the project's [GitHub repo](https://github.com/phber/Solarsounds.js).

## Background

### Kepler's _Harmonices Mundi_

> "The heavenly motions are nothing but a continuous song for several voices, perceived not by the ear but by the intellect, a figured music which sets landmarks in the immeasurable flow of time."
>
> -- <cite>Johannes Kepler, _Harmonices Mundi_, Book V, Chapter 7</cite>

The philosophical concept of _musica universalis_ originated in Ancient Greece, and regards Pythagorean proportions in the movements of celestial bodies as a form of music. The theory was later developed by 16th-century astronomer Johannes Kepler, whl updated the theory by proposing that the harmony was produced, not just by the planets’ positions, but by the relationship between the distances of the planets from the sun to their orbital periods. Kepler thought that very occasionally, and possibly not since the time of creation, all of the planets “sang” together in perfect harmony<d-cite key="[https://www.univ.ox.ac.uk/news/keplers-harmonices-mundi/"></d-cite>.

Finally, he discovered a property of the planets which fit the ratios startlingly well. Kepler found that the angular speeds of each planet at aphelion and perihelion, as measured from the Sun, produced consonant ratios. He was thence able to write down scales which he claimed each planet followed as a result of its changing angular velocity around its elliptical orbit. Mercury's range of notes would be the largest, since its eccentricity was the most marked; Venus's scale consisted of only one note. However, Kepler thought that the notes in these scales would be continually changing, producing a tone similar to a siren.

![kepler-scales](https://1.bp.blogspot.com/-mnP8XLDr6oY/W7iyx0EmPXI/AAAAAAAAvrM/5EoGEXImsJMmJHRqN3vYVhMfhefqGZieQCLcBGAs/s1600/planetary%2Bmusic.jpg)


### Retreiving Solar System Data
To retrieve orbital data for the solar system , I used the Python library [AstroPy](https://github.com/astropy/astropy), which estimates planet ephemerides (orbits) using a combination of algorithms (such as Kepler's equations). I also decided to include some planetary "facts" from [NASA](https://nssdc.gsfc.nasa.gov/planetary/factsheet/).


## Data Mapping

This table shows how I mapped data variables into sound. The choices were mostly arbitrary, and although they use some of Kepler's conceived scales, they are not an accurate sound representation of his harmonical ideas. For example, Kepler pointed out that his harmonies are experienced with the sun as a center point, while I use a geocentric perspective. 
<center>
    
| Data parameter | Mapping | Description |
| :-----------: | :------------: | :------------: |
| Orbital Velocity      | Pitch   | Discretized and mapped to Kepler's scales     |
| Distance to Earth       | Volume   |  Relative to the planet's max. and min. distance in its orbit   |
| Planet Radius    | Attack       | Radius relative to Earth  |
| Planet Temperature   | Vibrato frequency     |  Temperature relative to Earth (in Kelvin)  |
| Planet Density   | Vibrato  depth    |  Density relative to Earth (kg/m3)   |

</center>

