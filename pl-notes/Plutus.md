Check error:
```haskell
import qualified Plutus.Prelude

validator' :: PaymentPubKeyHash -> Validator
validator' key =  mkValidatorScript $ $$(compile [|| wrapValidator ||]) `applyCode` liftCode key

validator :: Validator
validator = Prelude.error $ show $  PaymentPubKeyHash "a8bc76574af70dd8784a78b753a342b2a57bd302578f6fb827aacaed"
```
