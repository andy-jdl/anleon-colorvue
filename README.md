# anleon-getty

<img width="1183" height="552" alt="colorvue getty submission" src="https://github.com/user-attachments/assets/d208cb0f-6d2f-4282-9ec3-f57b8fe27760" />

## Brief

Using Linked Data representation field to display the dominant color and swatch palette of an image.
Uses [colorThief](https://lokeshdhakar.com/projects/color-thief/) to grab colors from any image.

LinkeData URL: https://data.getty.edu/museum/collection/object/c88b3df0-de91-4f5b-a9ef-7b2b9a6d8abb

## Stack
- vue
- javascript

## Running the project
- `npm i` to install dependencies.
- `npm run dev` to run project.

## Notes
Inspiration for this sample project came from the Art Institute of Chicago and The Harvard Museum of Art. Their response objects include dominant color and swatch palette colors respectively. I believe including this extra bit of information would help add another layer to manifests or objects that some might appreciate. A use case I can think of is setting the `background-color` to the image dominant color for added styling.

Given ample time, I would build the color thieving library in house to minimize 3rd party libraries. It seems to be a solved problem at this point.
