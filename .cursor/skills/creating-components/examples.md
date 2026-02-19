# Code Templates

### Component with props

```tsx
type Props = {
  title: string;
  className?: string;
  onClick: () => void;
};

export const Button: React.FC<Props> = ({ title, className, onClick }) => (
  <button className={className} onClick={onClick}>
    {title}
  </button>
);
```

### Component without props

```tsx
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

### Component with logic (explicit return)

```tsx
import { useState } from 'react';

type Props = {
  items: string[];
  onSelect: (item: string) => void;
};

export const ItemList: React.FC<Props> = ({ items, onSelect }) => {
  const [selected, setSelected] = useState<string | null>(null);

  const handleClick = (item: string) => {
    setSelected(item);
    onSelect(item);
  };

  return (
    <ul>
      {items.map((item) => (
        <li key={item} onClick={() => handleClick(item)}>
          {item} {selected === item && '(selected)'}
        </li>
      ))}
    </ul>
  );
};
```

### Props with complex types

```tsx
type Props = {
  user: {
    id: string;
    name: string;
  };
  isActive?: boolean;
  className?: string;
  onEdit: (id: string) => void;
  onDelete?: (id: string) => void;
};

export const UserCard: React.FC<Props> = ({
  user,
  isActive,
  className,
  onEdit,
  onDelete,
}) => (
  <div className={className}>
    <h3>{user.name}</h3>
    {isActive && <span>Active</span>}
    <button onClick={() => onEdit(user.id)}>Edit</button>
    {onDelete && <button onClick={() => onDelete(user.id)}>Delete</button>}
  </div>
);
```
