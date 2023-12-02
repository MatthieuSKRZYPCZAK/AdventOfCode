# [AdventOfCode](https://github.com/MatthieuSKRZYPCZAK/AdventOfCode)

## Day 1

```javascript
const fs = require('fs');

fs.readFile('input.txt', 'utf8', (err, data) => {
    if(err) {
        console.error('erreur :', err);
        return;
    }

    const lignes = data.split('\n');
    const resultats = [];
    let final = 0;

    for (const ligne of lignes) {
        if(ligne.trim() !=='') {
            const chiffres = ligne.match(/\d/g);
            
            if (chiffres.length >= 2){
                const premierChiffre = chiffres[0];
                const dernierChiffre = chiffres[chiffres.length - 1];
                resultats.push(premierChiffre + dernierChiffre);
            } else {
                resultats.push(chiffres + chiffres);
            }
        }
    }
    for (const result of resultats) {
        final = final + parseInt(result);
    }
    console.log(final);
});

```



