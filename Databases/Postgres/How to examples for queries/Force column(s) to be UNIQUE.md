```
CREATE TABLE IF NOT EXISTS authz.group_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES authz.groups(id) NOT NULL,
  subject uuid NOT NULL,
  joined_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  UNIQUE(group_id, subject)
);
```
