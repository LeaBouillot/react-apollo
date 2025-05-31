# Note erreurs

## erreur 1

L’erreur `ERR_PACKAGE_PATH_NOT_EXPORTED` liée à `postcss` est assez courante avec certaines versions de Node.js et des dépendances qui ne gèrent pas bien le système d’exports du package.

### Explication rapide

Le paquet `postcss-safe-parser` essaie d’accéder à un chemin interne (`./lib/tokenize`) dans le paquet `postcss` qui n’est pas exporté dans la configuration `exports` du `package.json` de `postcss`.  
Depuis Node.js 12+ et surtout 14+, la résolution des modules respecte cette règle stricte, ce qui bloque l’import.

### Solutions

- Mettre à jour les dépendances :  
  Vérifie que tous tes paquets sont à jour, notamment `postcss`, `postcss-safe-parser`, `react-scripts`, etc.

```bash
npm update
```

---

## erreur 2

```
opensslErrorStack: [
  'error:03000086:digital envelope routines::initialization error',
  'error:0308010C:digital envelope routines::unsupported'
],
library: 'digital envelope routines',
reason: 'unsupported',
code: 'ERR_OSSL_EVP_UNSUPPORTED'
```

Cette erreur est liée à une incompatibilité entre Node.js 17+ (ou version 20 comme dans ton cas) et la version de Webpack utilisée, due aux changements dans OpenSSL 3.0 intégré à Node.js.

### Contexte

Node.js 17+ utilise OpenSSL 3.0, qui a désactivé certains algorithmes par défaut, ce qui cause cette erreur lors du build avec Webpack (souvent via `react-scripts`).

### Solutions

* Utiliser la variable d’environnement pour forcer l’ancienne implémentation :

```bash
export NODE_OPTIONS=--openssl-legacy-provider
npm start
```


