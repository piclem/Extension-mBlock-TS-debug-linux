# Extension-mBlock_TS_1.3-debug-linux

Version modifiée du fichier `technologie-services-uno.s2e` pour l'import de l'extension Technologie Services sous mBlock v4.0.4 sous Ubuntu.

## Problèmes

#### 1. Problème au dézippage

Lors de l'import de l'extension proposée par Technologie Services, une première erreur survient.
Un "rezippage" manuel permet de résoudre ce problème (voir ci-dessous)

#### 1. Problème à l'import

Lors de l'import du zip corrigé, une seconde erreur survient, due au fichier `s2e` corrompu.

## Solution

La solution est présentée pour l'extension Uno (`extension-tsuno.zip`).

#### Etape 1 : dézipper l'extension

Manuellement, ou en utilisant `unzip extension-tsuno.zip`.

#### Etape 2 : modifier/remplacer le fichier `*.s2e`

Manuellement, ou en utilisant les commandes suivantes dans le dossier dézippé :

 - `mv technologie-services-uno.s2e technologie-services-uno.s2e.bak`
 - `git clone https://github.com/piclem/Extension-mBlock_TS_1.3-debug-linux ~/Downloads/ && cp ~/Downloads/piclem/Extension-mBlock_TS_1.3-debug-linux/technologie-services-uno.s2e technologie-services-uno.s2e`

#### Etape 3 : re-zipper l'extension

Elle peut être renommée `extension-tsuno_.zip` par exemple.

#### Etape 4: vérification de l'import 

Dans mBlock : `Choix des extensions` > `Gérer les extensions` > `Install from Zip...` et sélectionner le nouveau `zip` (`extension-tsuno_.zip`).

## Explications

Le format `s2e` semble être du `JSON`. En renommant le fichier `.s2e` en `.json`, on peut vérifier sa validité (glisser-déposer dans firefox par exemple). On s'aperçoit que certains caractères posent problème:
 - `\[` et `\]`, les crochets n'étant pas censés être échappés
 - les virgules en fin de liste 
La correction de ces problèmes résoud l'import dans mBlock
