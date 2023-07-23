 *Hi! I'm Daniel Stein*

- 👀 I’m interested in expanding my coding expertise 
- 🤝  I’m looking to collaborate on web/mobile applications 

<!---
danieljuliusstein/danieljuliusstein is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
**Connect with me:**

[<img alt="twitter" width="35px" src="twitter.svg" />](https://twitter.com/danielj_stein)
[<img alt="linked in profile" width="35px" src="linkedin.svg" />](https://www.linkedin.com/in/daniel-stein-8a36b8276/)
[<img alt="instagram" width="35px" src="instagram.svg" />](https://www.instagram.com/danieljuliusstein/)

**Languages and Tools:**

<img alt="github" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/8700c04d-91a1-456a-a7ab-e02341ecc8b8" />
<img alt="python" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/ee06c772-0425-4445-90fa-856ee118d124" />
<img alt="react" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/f40738bc-1988-49d7-a01a-e88ef65889b4" />
<img alt="css" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/e4e79320-425a-46aa-9e66-453124400ae6" />
<img alt="html" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/b7d62bb5-7f77-46dc-9996-df05be40dc09" />
<img alt="visual studio" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/595aba80-a6ac-44b3-9475-8fd5dac70cbd" />

<br>
</br>

**Learning:**

<img alt="mySql" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/91247300-5607-4eb5-bbcb-30ddde790362" />
<img alt="sql" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/c272d6ed-c9e7-441c-abe5-efc8e5222e0d" />
<img alt="nodejs" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/1dd19886-d4ba-4978-b9bf-73f2975d623b" />
<img alt="react" width="35px" src="https://github.com/danieljuliusstein/danieljuliusstein/assets/69329733/52427d05-d604-43ab-a495-122351cc8157" />

------------------------

**Portfolio/My Work:**

[<img alt="simon" width="100px" src="simon.svg" />](https://github.com/danieljuliusstein/Python-Projects-/blob/main/Simon%20Game)
[<img alt="mario" width="100px" src="mario-removebg-preview.png" />](https://github.com/danieljuliusstein/Mario-Game)
[<img alt="crypto" width="150px" src="Crypto.png" />](https://github.com/danieljuliusstein/HTML-/blob/main/CryptoValueCalculator)

------------------------

<p align="left"> <img src="https://komarev.com/ghpvc/?username=danieljuliusstein&label=Profile%20views&color=0e75b6&style=flat" alt="danieljuliusstein" /> </p>

<p align="left">
</p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=danieljuliusstein&show_icons=true&locale=en" alt="danieljuliusstein" /></p>
// This app initially started from Flavio Copes analytics example
// but diverged quite a bit to generate images as well as track views
// https://flaviocopes.com/count-visits-static-site/

const express = require('express')
const app = express()

// no db - so global var to keep track of count
let counter = 0

function getCountImage(count) {
  // This is not the greatest way for generating an SVG but it'll do for now
  const countArray = count.toString().padStart(6, '0').split('');

  const parts = countArray.reduce((acc, next, index) => `
        ${acc}
        <rect id="Rectangle" fill="#000000" x="${index * 32}" y="0.5" width="29" height="29"></rect>
        <text id="0" font-family="Courier" font-size="24" font-weight="normal" fill="#00FF13">
            <tspan x="${index * 32 + 7}" y="22">${next}</tspan>
        </text>
`, '');

  return `<?xml version="1.0" encoding="UTF-8"?>
<svg width="189px" height="30px" viewBox="0 0 189 30" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <title>Count</title>
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      ${parts}
    </g>
</svg>
`
}

// get the image
app.get('/count.svg', (req, res) => {
  counter++;

  // This helps with GitHub's image cache 
  //   see more: https://rushter.com/counter.svg
  res.set({
  'content-type': 'image/svg+xml',
  'cache-control': 'max-age=0, no-cache, no-store, must-revalidate'
  })

  // Send the generated SVG as the result
  res.send(getCountImage(counter));
})

const listener = app.listen(process.env.PORT, () => {
  console.log('Your app is listening on port ' + listener.address().port)
})
