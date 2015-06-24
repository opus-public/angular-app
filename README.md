# Realex Remote Java SDK

You can sign up for a Realex account at https://www.realexpayments.com.

## Requirements
Java 1.6 and later.

## Installation

### Maven users

Add this dependency to your project's POM:

```xml
<dependency>
  <groupId>com.realexpayments</groupId>
  <artifactId>rxp-remote-java</artifactId>
  <version>1.0</version>
</dependency>
```

Usage
=====

RealexRemote.java

```java

import com.realexpayments.*;

public class RealexRemote {

    public static void main(String[] args) {
        Card card = new Card()
            .addExpiryDate(1, 19)
            .addNumber("420000000000000000")
            .addType(CardType.VISA)
            .addCardHolderName("Joe Smith")
            .addCvn(123)
            .addCvnPresenceIndicator(PresenceIndicator.CVN_PRESENT);

        PaymentRequest request = new PaymentRequest()
            .addAccount("yourAccount")
            .addMerchantId("yourMerchantId")
            .addType(PaymentType.AUTH)
            .addAmount(100)
            .addCurrency("EUR")
            .addCard(card)
            .addAutoSettle(new AutoSettle().addFlag(AutoSettleFlag.TRUE)); 
    }
}
```

See [StripeTest.java](https://github.com/stripe/stripe-java/blob/master/src/test/java/com/stripe/StripeTest.java) for more examples.

Testing
=======

You must have Maven installed. To run the tests, simply run `mvn test`. You can run particular tests by passing `-D test=Class#method` -- for example, `-D test=StripeTest#testPlanCreate`.
