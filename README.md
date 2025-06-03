Description	Method	Endpoint	Parameters	Response Codes & Descriptions
				
Shopper Profile				
Register as a shopper	POST	/shoppers	zoneId (query, optional, string)	201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 405: Method not supported, 409: Conflict
Find shopper data by shopperId	GET	/shoppers/{shopperId}	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Update shopper details	PATCH	/shoppers/{shopperId}	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported, 409: Conflict
Generate URL for forgot password	POST	/users/forgot-password	Headers: email (required, string), role (required, string), verifyUrl (optional, string)	200: Password reset mail sent, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Shopper login	POST	/users/login	None	200: OK, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Reset password	POST	/users/reset-password	Header: token (required, string)	200: Password reset successful, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Set user password after verification	POST	/users/verify-account	Header: password (required, string), Query: token (required, string)	200: Password created, 401: Not authorised, 403: Access forbidden, 405: Method not supported
				
Product View Action				
Returns all the products	GET	/products	zoneId (query, required, string)	200: Products data is returned, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Returns all the default products	GET	/products/alpha	zoneId (query, optional, string, default = ALPHA)	200: OK, 401: Not authorised, 403: Access forbidden, 405: Method not supported
				
Shopper Address				
Get all the addresses of specified user	GET	/shoppers/{shopperId}/address	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Add a new address for specified user	POST	/shoppers/{shopperId}/address	shopperId (path, required, integer), address (body, required)	201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Get a particular address by addressId	GET	/shoppers/{shopperId}/address/{addressId}	shopperId (path, required, integer), addressId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Update an added address	PUT	/shoppers/{shopperId}/address/{addressId}	shopperId (path, required, integer), addressId (path, required, integer), address (body)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Delete an address for specified user	DELETE	/shoppers/{shopperId}/address/{addressId}	shopperId (path, required, integer), addressId (path, required, integer)	204: No Content, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Wishlist				
Get all products from the wishlist	GET	/shoppers/{shopperId}/wishlist	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Add a product to the wishlist	POST	/shoppers/{shopperId}/wishlist	shopperId (path, required, integer), item (body, required)	201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Delete a product from the wishlist	DELETE	/shoppers/{shopperId}/wishlist/{productId}	shopperId (path, required, integer), productId (path, required, integer)	204: No Content, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Cart				
Get all products from the cart	GET	/shoppers/{shopperId}/carts	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Add a product to the cart	POST	/shoppers/{shopperId}/carts	shopperId (path, required, integer), item (body, required)	201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Update a product in the cart	PUT	/shoppers/{shopperId}/carts/{itemId}	shopperId (path, required, integer), itemId (path, required, integer), item (body, required)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Delete a product from the cart	DELETE	/shoppers/{shopperId}/carts/{productId}	shopperId (path, required, integer), productId (path, required, integer)	200: OK, 204: Successfully deleted, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Order				
Display order history	GET	/shoppers/{shopperId}/orders	shopperId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Place order from cart	POST	/shoppers/{shopperId}/orders	shopperId (path, required, integer), shopperOrderRequest (body, required, JSON)	201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Update order status	PATCH	/shoppers/{shopperId}/orders/{orderId}	shopperId (path, required, integer), orderId (path, required, integer), status (query, string)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Generate Invoice copy	GET	/shoppers/{shopperId}/orders/{orderId}/invoice	shopperId (path, required, integer), orderId (path, required, integer)	200: OK (PDF), 400: User order info not retrieved
				
Shopper Product Review				
Add a review to delivered product	POST	/reviews	productId (query, required, integer), review (body, required, XML)	200: OK, 201: Created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Get all reviews of a product	GET	/reviews/{productId}	productId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Update an added review	PUT	/reviews/{reviewId}	productId (query, required, integer), review (body, required, XML), reviewId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Delete an added review	DELETE	/reviews/{reviewId}	productId (query, required, integer), reviewId (path, required, integer)	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Bank Cards				
Creates a new card for a given bank	GET	/cards	"bankName(string, required, query),
cardType
(string, required, query, values: DEBIT, CREDIT),
email
(string, required, query),
name
(string, required, query),
shopperId
(int64, required, query)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Bank not found, 405: Method not supported, 409: Conflict
Update card balance	PATCH	/cards	"amount(double, required, query),
cardNumber
(string, required, query)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
Validate bank card with amount	POST	/cards/transaction	"amount(double, required, query),
card
(body, required, XML)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
Validate bank card	POST	/cards/verify	card(body, required, XML)	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
				
Shopper Profile Cards				
Save the card data	POST	/cards	shopperCard(body, required, XML): cvv, expiryDate, id, nameOnCard, number, type, userId	200: OK, 201: Successfully created, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Delete card data based on id	DELETE	/cards/{cardId}	cardId(path, required, integer)	200: OK, 201: Successfully returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Get card data based on type	GET	/cards/{shopperId}	"shopperId(path, required, integer),
type
(query, required, string)"	200: OK, 201: Successfully returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
Returns all shopper’s cards	GET	/shoppers/cards	"cardType(query, string, values: DEBIT, CREDIT),
shopperId
(query, integer)"	200: Shoppers cards data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Bank Account				
Get all bank accounts of shopper	GET	/bankaccounts	shopperId(int64, required, query)	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
Create bank account	POST	/bankaccounts	"bankName(string, required, query),
email
(string, required, query),
shopperId
(int64, required, query)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
Update bank account balance	PATCH	/bankaccounts	"action(string, required, query),
amount
(double, required, query),
number
(string, required, query)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
Validate bank account credential	POST	/bankaccounts/login	"bankName(string, required, query),
login
(body, required, XML with email, password, role)"	200: Users data returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Card not found, 405: Method not supported
				
Shopper Wallet Action				
Get all wallet transactions	GET	/shoppers/{shopperId}/wallets	shopperId(int64, required, path)	200: Successful, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: Given ID not found, 405: Method not supported
				
Shopper Likes Action				
Returns all the likes of shopper	GET	/shoppers/likes	shopperId(int64, required, query)	200: Shoppers likes data is returned, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported
Delete the shopper's like list	DELETE	/shoppers/likes	"category(string, required, query),
shopperId
(int64, required, query)"	200: Shopper like list is deleted, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported
Update the shopper's like list	PATCH	/shoppers/likes	"likes(body, required, JSON),
shopperId
(int64, required, query)"	200: Shopper like list is updated, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported
				
Admin Profile				
Register as Admin	POST	/admin	"user(body, required, XML),
verifyUrl
(string, required, header)"	201: Created, 400: Bad requests, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported, 409: Conflict
Get Admin Details by Id	GET	/admin/{adminId}	adminId(int32, required, path)	200: OK, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported
Update Admin Details by Id	PUT	/admin/{adminId}	"adminId(int32, required, path),
user
(body, required, XML)"	200: OK, 400: Bad request, 401: Not authorised, 403: Access forbidden, 404: ID not found, 405: Method not supported
				
Admin Action				
Returns all merchant data of a specific zone	GET	/merchants	zoneId(string, required, query)	200: Merchants data returned, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Update merchant status (Blocked ↔ Approved)	PATCH	/merchants/{merchantId}/status	"merchantId(int32, required, path),
status
(string, required, query)"	200: Updated merchant data returned, 401: Not authorised, 403: Access forbidden, 405: Method not supported
Get merchants by status and zone	GET	/merchants/status/zoneId	"zoneId(string, required, query),
status
(string, optional, query, default: ACTIVE)"	200: Merchants data returned, 401: Not authorised, 403: Access forbidden, 405: Method not supported
				
Merchant Profile				
Save a new merchant	POST	/merchants	"Body:merchant
(application/xml)"	200: OK, 201: Created, 400: Bad request, 401: Not authorised, 403: Forbidden, 405: Method not supported, 409: Conflict, 415: Unsupported media
Get a merchant by ID	GET	/merchants/{merchantId}	"Path:merchantId
(int32, required)"	200: Merchant data returned, 401: Not authorised, 403: Forbidden, 404: ID not found, 405: Method not supported
Update an existing merchant	PUT	/merchants/{merchantId}	"Path:merchantId
(int32, required)Body:
merchant
(application/xml)"	200: OK, 204: Updated, 400: Bad request, 401: Not authorised, 403: Forbidden, 404: ID not found, 405: Method not supported, 409: Conflict, 415: Unsupported media
				
Merchant Product Review				
Get all reviews for a product	GET	/reviews/{productId}	"Path:productId
(int32, required)"	200: OK (returns list of reviews), 400: Bad request, 401: Not authorised, 403: Forbidden, 404: ID not found, 405: Not supported
Delete a specific review	DELETE	/reviews/{reviewId}	"Path:reviewId
(int32, required)Query:
productId
(int32, required)"	200: OK (review deleted), 400: Bad request, 401: Not authorised, 403: Forbidden, 404: ID not found, 405: Not supported
				
Merchant Product Action				
Returns all products in a zone	GET	/products	zoneId(query, string)	200: Success with product list401: Not Authorized403: Forbidden405: Not Supported
Save new product	POST	/products	"merchantId(query, int32)
product
(body, XML)"	200/201: Product created400: Bad Request401: Not Authorized403: Forbidden405: Not Supported415: Unsupported Content Type
Update an existing product	PUT	/products	"productId(query, int32)
product
(body, XML)"	200/204: Updated successfully400: Bad Request401: Not Authorized403: Forbidden404: ID Not Found405/415: Not Supported / Content Type
Get a single product by ID	GET	/products/{productId}	productId(path, int32)	200: Product found401: Not Authorized403: Forbidden404: Not Found405: Not Supported
Delete a product by ID	DELETE	/products/{productId}	productId(path, int32)	200/204: Deleted401: Not Authorized403: Forbidden404: Not Found405: Not Supported
Get all products by a merchant	GET	/products/merchant/{merchantId}	merchantId(path, int32)	200: Products returned400: Bad Request401: Not Authorized403: Forbidden404: Not Found405/415: Not Supported / Content Type
				
Bank Action				
Returns all the available banks	GET	/banks	None	200: List of bank names400: Bad Request401: Not Authorized403: Forbidden404: Not Found405: Method Not Supported
