# [AdventOfCode](https://github.com/MatthieuSKRZYPCZAK/AdventOfCode)

## Day 2

```javascript
const fs = require('fs');

fs.readFile('input.txt', 'utf8', (err, data) => {
    if (err) {
        console.error('Erreur :', err);
        return;
    }

    const lignes = data.split('\n');
    let total = 0;

    for (const ligne of lignes) {

        const match = ligne.match(/Game (\d+):/);
        // console.log(match);
        if (match) {
            const numeroJeu = match[1];

            const detailsCubes = ligne.split(': ')[1].split('; ').join(', ').split(', ');
            // console.log(detailsCubes);
            // Vérification de dépassement de la limite
            const depasseLimite = detailsCubes.some(detail => {
                const rouge = parseInt((detail.match(/(\d+) red/) || [0, 0])[1]);
                const vert = parseInt((detail.match(/(\d+) green/) || [0, 0])[1]);
                const bleu = parseInt((detail.match(/(\d+) blue/) || [0, 0])[1]);
                console.log("rouge : ", rouge, "vert : ", vert, "bleu : ", bleu);

                return rouge > 12 || vert > 13 || bleu > 14;
            });

            // Si ca ne dépasse pas, ajoute l'id au total
            if (!depasseLimite) {
                total += parseInt(numeroJeu);
            }
        }
    }

    console.log(total);
});


```