## Sprint Planning – 3 Steps

スプリント計画 ― 3 つのステップ

### 1. スプリントのゴールを決める

1. Develop Sprint Goal

Define what we want to accomplish in the next 2 weeks in one clear sentence.
次の 2 週間で達成したいことを、1 つの明確な文章で定義する。

Example / 例:
"Users can login and select benefits for their application"
「ユーザーがログインして、申請に必要な優待を選べるようになる」

Purpose / 目的:
Keeps everyone focused on the same outcome
全員が同じ成果を目指せるようにするため

Question to ask / 自問すべき質問:
"What will users be able to do when we're done?"
「このスプリントが終わったとき、ユーザーは何ができるようになっているか？」 2. Breakdown the Necessary Features

### 2. 必要な機能を洗い出す

2. Breakdown the Necessary Features

List the main features needed to achieve the sprint goal.
スプリントゴールを達成するために必要な主な機能をリストアップする。

Example / 例:
Login page, Benefits selection page, Application form
ログインページ、優待選択ページ、申請フォーム

Purpose / 目的:
Identify all the pieces that need to be built
開発すべき要素をすべて明確にするため

Question to ask / 自問すべき質問:
"What features do we need to make this goal happen?"
「このゴールを達成するには、どんな機能が必要か？」 3. Breakdown into Tasks

### 3. 機能を具体的なタスクに分解する

3. Breakdown into Tasks
   Convert each feature into specific work items that can be assigned to team members.
   各機能を、担当者に割り当てられる具体的な作業項目に分解する。

Example / 例:
"Build login form UI", "Create authentication API", "Design benefits database"
「ログインフォームの UI を作る」「認証 API を作る」「優待データベースを設計する」

Purpose / 目的:
Create actionable work that individuals can complete
実行可能なタスクを作成し、個々人が着手できるようにするため

Question to ask / 自問すべき質問:
"What specific tasks need to be done to build each feature?"
「各機能を作るには、どんな具体的なタスクが必要か？」

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

## PersonalDetails

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

## Addresses

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

## Benefits

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
