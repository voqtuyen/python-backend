## I. Problem Statement
#### Steps to reproduce
1. A sqlite database model has a nullable column.
2. Change this column to nullable=False.
3. Perform database migration.
4. Apply these changes to existing database.

#### Error message

`sqlalchemy.exc.OperationalError: (sqlite3.OperationalError) Cannot add a NOT NULL column with default value NULL`

## II. Description
- SQLAlchemy uses Alembic to generate migration scripts. However, in this case Alembic does not correctly know how to handle setting 
a field from `nullable=True` to `nullable=False` when the column already has null values in it. Alembic will create a script that updates 
this column property that contains this:
  ```python3
  def upgrade():
      # ### commands auto generated by Alembic - please adjust! ###
      op.alter_column('cfbox', 'created_by',
                 existing_type=sa.VARCHAR(length=64),
                 nullable=False)
      # ### end Alembic commands ###


  def downgrade():
      # ### commands auto generated by Alembic - please adjust! ###
      op.alter_column('cfbox', 'created_by',
                 existing_type=sa.VARCHAR(length=64),
                 nullable=True)
      # ### end Alembic commands ###
  ```
- Howeber, since it can't figure out that all the existing nulls in the database, the database will reject this change as 
it would leave nulls inside a column that isn't nullable.
  ```bash
  [SQL: ALTER TABLE cfbox ALTER COLUMN created_by SET NOT NULL]
  (Background on this error at: http://sqlalche.me/e/14/e3q8)
  ```

## III. Solution




## IV. Reference
1. https://github.com/miguelgrinberg/Flask-Migrate/issues/81  
2. https://sqlalchemy-migrate.readthedocs.io/en/v0.7.1/faq.html  
3. https://dev.to/meseta/alembic-setting-a-column-to-nullable-true-if-it-already-has-data-in-it-3nb7
