# Python_Individual_Work_2_15.06

1. Define classes Client, Items, Transaction
2. Write the logic so that each client can purchase one of several items in a single transaction
3. Make a printout of data with nested loops

The program should print out:
* all clients
* all transactions of a client
* all items purchased in each transaction of the client

```py
class Client:
  number_of_clients = 0

  def __init__(self, id, name):
    self.id = id
    self.name = name
    self.transactions = []
    Client.number_of_clients += 1

  def add_transaction(self, transaction):
    self.transactions.append(transaction)

class Item:
  number_of_items = 0

  def __init__(self, id, name, price):
    self.id = id
    self.name = name
    self.price = price
    Item.number_of_items += 1

class Transaction:
  def __init__(self, id, client, items):
    self.id = id
    self.client = client
    self.items = items

  def process_transaction(self):
    self.client.add_transaction(self)

clients = []
clients.append(Client('3543', 'Peter'))
clients.append(Client('8799', 'Mary'))
clients.append(Client('1256', 'Susie'))

items = []
items.append(Item('345', 'Couch', '1100'))
items.append(Item('665', 'Mirror', '90'))
items.append(Item('22', 'Carpet', '350'))
items.append(Item('545', 'Lamp', '82'))
items.append(Item('180', 'Chair', '65'))

transactions = [
  Transaction('243545', clients[2], [items[2], items[1]]),
  Transaction('546598', clients[0], [items[4]]),
  Transaction('568590', clients[1], [items[0], items[1], items[2]]),
  Transaction('313556', clients[0], [items[2], items[3]]),
  Transaction('124567', clients[2], [items[3], items[0]])
]
for transaction in transactions:
  transaction.process_transaction()

print(f'We have {Client.number_of_clients} clients in our shop:')

for client in clients:
  print(f'Client: {client.name}, ID: {client.id}')
  for transaction in client.transactions:
    print(f'Transaction ID: {transaction.id}')
    for item in transaction.items:
      print(f'Item purchased: {item.name} - EUR {item.price}')
```
