# 0.2.1
* Fake refunds via `Braintree::Transaction.refund` and
  `Braintree::CreditCard.refund`.
* Create credit cards via `Braintree::CreditCard.create(:token => token,
  :number => TEST_CC_NUMBER)`
* Depend on Thin instead of Mongrel (fixes NotImplementedError).

# 0.2.0
* Generated transactions (from `FakeBraintree.generate_transaction`) now include
  the amount.
* `Braintree::Customer.update` will reject updates that contain credit cards that
  have been marked as a failure in the registry.

# 0.1.1
* `Braintree::CreditCard.update` now works

# 0.1.0
* `FakeBraintree.{customers, transactions, failures, subscriptions, redirects}`
  are now accessed via `FakeBraintree.registry`. For example,
  `FakeBraintree.customers` is now `FakeBraintree.registry.customers`
* `FakeBraintree.credit_card_from_token` is now `FakeBraintree.registry.credit_card_from_token`
* The server code (it intercepts calls to Braintree) now lives in FakeBraintree::Server
* `Braintree::Customer.create` will use the provided customer ID instead of
  overwriting it (#15).
* `Braintree::Subscription.cancel` now works

# 0.0.6
* Flesh out the README
* Add support for transparent redirect
* Add basic support for adding add-ons
* Add basic support for adding discounts
* Add support for `Braintree::Customer.update`
* Add support for `Braintree::Customer.delete`
* Add support for `Braintree::Subscription.delete`
* Lots of internal refactorings

# 0.0.5
* Add support for `Braintree::Customer.find`

# 0.0.4
* Allow for very basic card verification

# 0.0.3
* Ensure `FakeBraintree.log_file_path` directory exists
* The `FakeBraintree.log_file_path` attribute can now be read (it could only be set before)
* Clear log when `FakeBraintree.clear!` is called
* Correctly handle nonexistent subscriptions when using
  `Braintree::Subscription.find`
