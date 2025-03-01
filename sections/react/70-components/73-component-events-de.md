# Komponenten-Events

## Datenfluss

- parent → child: props
- child → parent: events

## Eigene Events

Eventhandler werden als Funktionen definiert und via props übergeben / erhalten.

## Eigene Events

Example:

```jsx
<Rating
  value={prodRating}
  onChange={(newRating) => onProdRatingChange(newRating)}
/>
```

<img src="assets/rating.png" style="width: 16em" />

## Eigene Events

Beispiel für Prop-Types einer Rating-Komponente:

```tsx
type RatingProps = {
  value: number;
  onChange?: (value: number) => void;
};
```

## Eigene Events

```tsx
const Rating = (props: RatingProps) => {
  const starIds = [1, 2, 3, 4, 5];
  return (
    <div>
      {starIds.map((id) => (
        <span
          onClick={() => {
            if (props.onChange) {
              props.onChange(id);
            }
          }}
          key={id}
        >
          {id <= props.value ? '★' : '☆'}
        </span>
      ))}
    </div>
  );
};
```

## Eigene Events

Verwendung einer Rating-Komponente:

```jsx
const [prodRating, setProdRating] = useState(3);
```

```jsx
<Rating
  value={prodRating}
  onChange={(newRating) => setProdRating(newRating)}
/>
```
