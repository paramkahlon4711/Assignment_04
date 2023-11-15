# Project 04

## Description
in this assignment i will be exception proofing the pixell transactions bank app 


## Author
Param 

## Assignment
1. adding the Transaction Type Validation and Transaction Amount Validation to incorporate the data validation to add transaction is valid or not :
if transaction_type not in valid_transaction_types:
                valid_record = False
                error_message += 'Invalid transaction type. '

 try:
                # Extract the transaction amount from the third column
                transaction_amount = float(row[2])
            except ValueError:
                valid_record = False
                error_message += 'Non-numeric transaction amount. '
2. Collecting  Invalid Records to procide differently if any records identified as invalid :
rejected_records.append((row, error_message))
## code modification
preparing for Troubleshooting by copying bank_data and the deleting all files except first entry and then running:
try:
    os.system('cls' if os.name == 'nt' else 'clear')

    with open('bank_data.csv', 'r') as csv_file:
        reader = csv.reader(csv_file)
to:
print("\nREJECTED RECORDS\n================")

## code modification 
Updating code by run and Debug code, updating and adding some command to troubleshoot in which correcting the formula and value correction is included, with including  rejected records and error message in code:
ry:
                # Extract the transaction amount from the third column
                transaction_amount = float(row[2])
            except ValueError:
                valid_record = False
                error_message += 'Non-numeric transaction amount. '

            if valid_record:
                # updating  the transaction_counter for valid records
                transaction_count += 1
                total_transaction_amount += transaction_amount

                if customer_id not in customer_data:
                    customer_data[customer_id] = {'balance': 0, 'transactions': []}

                if transaction_type == 'deposit':
                    customer_data[customer_id]['balance'] += transaction_amount
                elif transaction_type == 'withdraw':
                    customer_data[customer_id]['balance'] -= transaction_amount
and
 adding rejected records and error massage
    for record, error in rejected_records:
        print("REJECTED RECORD:", record)
        print("ERROR MESSAGE:", error)
testing the data and comparing the code for each transaction value and applying the debug:

    print("PiXELL River Transaction Report\n===============================\n")
    for customer_id, data in customer_data.items():
        balance = data['balance']
        print(f"\nCustomer {customer_id} has a balance of {balance}.")
        print("Transaction History:")
        for transaction in data['transactions']:
            amount, type = transaction
            print(f"\t{type.capitalize()}: {amount}")

    if transaction_count > 0:
        print(f"\nAVERAGE TRANSACTION AMOUNT: ${(total_transaction_amount / transaction_count):,.2f}")
    else:
        print("\nNo valid transactions found.")

