---

---

Base Parameters:

- **Number of transactions**: `100`
- **Basket value per transaction**: `$100`
- **DiscoPay processing fee**: 3% of the customer's final price
- **Merchant always receives**: `$100` (full price guaranteed)
- **DiscoPay covers**: Any discount directly — merchant is unaffected
- **Overpayments**: Given back to the customer as **store credit**
- **DiscoPay does not take a cut** of the store credit
- **Fee application: **applied to total (original price + store credit)


[[Test #1: Control]]

[[Test #2: 5% + $0.30 ]]

[[Test #3: 6% + $0.30, fee applied to original amount]]

problems:

1. Who holds the extra store credit? 
2. Discopay fees are being taken from total amount (original +overpayment) 


Point of contention:

 Who pays the difference assuming DP takes a fee from the full amount when DP issues the store credit?
Example:

- A customer overpays by $20 (total $120)
- DP takes 5% + $0.30 on total transaction cost ($6.30)
- total owed to customer: $20
- total available at DP: 

---

10,000 transaction simulation summary:

- Total profit: **$27,830.00**
- Profit per transaction: **$2.78**
- Total store credit generated: **$39,460.00** (about **$3.95** per transaction)

Outcome distribution:

- Discounts: **2,545** (**25.4%**)
- Full price: **4,517** (**45.2%**)
- Store credit: **2,938** (**29.4%**)









