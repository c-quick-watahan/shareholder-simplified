## ShareHolder

```sql
shareholders (
  shareholder_number PRIMARY KEY,
  personal_details_id INTEGER REFERENCES personal_details(id),
  password VARCHAR(255),
  goca_member_id INTEGER REFERENCES goca_members(goca_member_number) NULL,
  applicable_units INTEGER,
  last_login TIMESTAMP,
  shareholder_type ENUM('individual', 'corporate'),
  representative_name VARCHAR(255) NULL,  -- Only for corporate
  representative_title VARCHAR(255) NULL, -- Only for corporate
  interim_stock_count INTEGER,
  yearend_stock_count INTEGER,
  next_term_expected_units INTEGER,
  notes TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
)
```

```sql
personal_details (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  name_kana VARCHAR(255),
  dob DATE,
  default_address_id INTEGER REFERENCES addresses(id),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
)
```

```sql
addresses (
  id SERIAL PRIMARY KEY,
  postal_code VARCHAR(10),
  prefecture VARCHAR(50),
  address1 VARCHAR(255),
  address2 VARCHAR(255),
  phone VARCHAR(20),
  landline VARCHAR(20),
  created_at TIMESTAMP DEFAULT NOW()
)
```

## Goca Members

```sql
goca_members (
  goca_member_number BIGINT PRIMARY KEY, # varchar?
  shareholder_id INTEGER REFERENCES shareholders(shareholder_number) NULL,
  date_of_birth DATE,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
)
```

## Benefit

```sql
benefits (
  benefit_id SERIAL PRIMARY KEY,
  benefit_name VARCHAR(255),
  application_period_id INTEGER REFERENCES application_periods(application_period_id),
  benefit_details TEXT,
  one_line_comment VARCHAR(500),
  image_path VARCHAR(255),
  lottery_flag BOOLEAN DEFAULT false,
  maximum_num_winners INTEGER NULL, -- Only for lottery items
  sort_order INTEGER,
  storage_requirement ENUM('frozen', 'refrigerated', 'room_temperature'),
  requires_goca_auth BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
)
```

## Application Periods

```sql
application_periods (
  application_period_id SERIAL PRIMARY KEY,
  start_date TIMESTAMP,
  end_date TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
)
```
