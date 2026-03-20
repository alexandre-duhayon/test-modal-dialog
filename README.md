# HTML `<dialog>` — Native POC

Démonstration des cas d'usage de la balise HTML native `<dialog>`.

**Aucune dépendance** — HTML, CSS et JavaScript vanilla uniquement.

> Ouvrir ['index.html'](https://alexandre-duhayon.github.io/test-modal-dialog) directement dans un navigateur.

---

## Cas couverts

### 1. Modal — `showModal()`
Place la dialog dans le [top layer](https://developer.mozilla.org/en-US/docs/Glossary/Top_layer), crée un backdrop natif et bloque l'interaction avec le reste de la page. Trap focus et fermeture via `Escape` gérés nativement par le navigateur.

### 2. Non-modal — `show()`
Ouvre la dialog sans backdrop ni blocage de la page. La page reste entièrement interactive derrière.

### 3. `<form method="dialog">`
Un formulaire avec `method="dialog"` ferme la dialog à la soumission sans JavaScript. La valeur du bouton activé est exposée via `dialog.returnValue`.

### 4. `autofocus`
Par défaut, le focus va sur le premier élément focusable. L'attribut `autofocus` permet de cibler un élément spécifique à l'ouverture.

---

## Accessibilité

| Critère | Implémentation |
|---|---|
| Titre de la dialog | `aria-labelledby` pointant vers le `<h2>` interne |
| Champs de formulaire | Chaque `<input>` et `<select>` est dans un `<label>` |
| Trap focus | Natif via `showModal()` |
| Fermeture `Escape` | Native |
| Annonces live | `aria-live="polite"` sur le retour de `returnValue` |

---

## Structure

```
test-modal-dialog/
├── index.html   — Les 4 démos
└── styles.css   — Styles (BEM, ~40 lignes)
```

---

## Compatibilité

`<dialog>` est supporté nativement par tous les navigateurs modernes depuis 2022.
[Voir le support sur Can I Use](https://caniuse.com/dialog)
