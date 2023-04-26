# pyspark-aws
aws pyspark utilities
from abc import ABC, abstractmethod
from typing import Dict

class Database(ABC):
    @abstractmethod
    def query(self, query_string: str) -> Dict:
        pass

class MySQLDatabase(Database):
    def query(self, query_string: str) -> Dict:
        # Implement query logic for MySQL database
        pass

class PostgreSQLDatabase(Database):
    def query(self, query_string: str) -> Dict:
        # Implement query logic for PostgreSQL database
        pass

class DatabaseFactory:
    def create_database(self, db_type: str) -> Database:
        if db_type == 'mysql':
            return MySQLDatabase()
        elif db_type == 'postgres':
            return PostgreSQLDatabase()
        else:
            raise ValueError('Invalid database type')

# Example usage
factory = DatabaseFactory()
database = factory.create_database('mysql')
result = database.query('SELECT * FROM users')
