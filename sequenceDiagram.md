```mermaid
sequenceDiagram
	participant json
	participant jackson
	participant shipment
	participant micronaut_data
	participant DB


	json->>shipment: デシリアライズ
	Note right of jackson: TrackingNumberDeserializer
	Note right of jackson: EncryptPropertyDeserializer

	shipment->>DB: データ登録・更新
	Note right of micronaut_data: EncyprtPropertyConverter
	DB->>shipment: データ取得
	Note left of micronaut_data: EncyprtPropertyConverter

	shipment->>json: シリアライズ
	Note left of jackson: TrackingNumberSerializer
	Note left of jackson: EncryptPropertySerializer
  ```
