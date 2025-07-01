# Stocks platform 
- We want to design a stock broker platform - GROWW, UPSTOCK
- APIs for stock exchange is already given- We don't create about order matching and fulfillment.
- Users should be able to place orders (Buy, Sell) on the platform and the plaform forwards it to exchange.
- Support both LIMIT and MARKET Order type.
- Users should be able to see stock price on in real time.
- Good to have price charts .

## Non-Functional Requirements
- Users should be able to see the stock prices. YOur data may be a bit older , however the data needs to be present all the times. (High Availability)
- Buying and Selling of stock should be constent . Once you are enaging in Buying a stock , your data should be consistent .
- 100 M DAU .
- New data can be poured into the stock prices in 200- 500 ms

## Back of the envelope calculation 
100 MDAU 
10 M - Users do check the stock - 

## API 

### Purchase
POST /stocks {

    type: MARKET
    stock: <ticker>,
    
}
POST /stocks {

    type: LIMIT
    stock: <ticker>,
    price: ?
    time: ?
}
### View
GET /stocks/TICKER?range=startTime&endTime

## High Level Components. 
- Stock (



