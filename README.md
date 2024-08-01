# cold-walletfrom bit import Key
from bit.network import NetworkAPI

# Create a new private key
private_key = Key()

# Print the private key (keep this safe and secure)
print(f"Private key: {private_key.to_wif()}")

# Print the public key (address)
print(f"Address: {private_key.address}")

# Function to create and sign a transaction offline
def create_and_sign_transaction(private_key, to_address, amount):
    # Create a new transaction
    tx = private_key.create_transaction([(to_address, amount, 'btc')], fee=100)

    # Sign the transaction
    signed_tx = private_key.sign_transaction(tx)

    return signed_tx

# Example usage:
if __name__ == "__main__":
    # Generate new private key and address
    private_key = Key()
    address = private_key.address

    print("Your new cold wallet has been generated.")
    print(f"Address: {address}")
    print(f"Private key (WIF): {private_key.to_wif()}")

    # To create and sign a transaction (do this offline)
    # Replace 'to_address' with the recipient's Bitcoin address
    # Replace 'amount' with the amount to send in BTC
    to_address = "recipient_bitcoin_address_here"
    amount = 0.001  # Amount in BTC

    # Create and sign the transaction
    signed_tx = create_and_sign_transaction(private_key, to_address, amount)
    print(f"Signed transaction: {signed_tx}")

    # To broadcast the transaction (do this online)
    # NetworkAPI.broadcast_tx(signed_tx)
