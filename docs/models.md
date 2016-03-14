# Estructura de los modelos
---
* **Pedido**
    * Datos del Cliente (salen de la relación)
	    - Nombre
		- Apellido
		- Direccion Particular
		- DNI
		- Telefonos
	* Direccion del evento
	* Direccion de entrega
	* Direccion de retiro
	* Producto/s
		- Nombre
		- Precio
	* Subtotal (solo precio productos)
	* Precio flete
	* Deposito (seguro)
	* Total $
	* Seña
	* Resto (total - seña)
	* Reposiciones

* **Producto**
	* Nombre
	* Foto
	* Descripcion
	* Categoria/Tipo (plato/cubierto)
	* Precio
	* Precio reposicion
	* Stock_Total

* **Cliente**
	* Nombre
	* Apellido
	* DNI
	* Direccion
	* Observaciones
	* Contacto
		- Telefono/s
		- Mail/s

---

* **User**
  * belongs_to *Client* (1)   :references
  * type                      :string
  * username                  :string
  * password                  :string

* **Client**
  * has_many *Contacts* (0-N) :references
  * has_many *Orders* (0-N)   :references
  * has_one *User* (0-1)      :references
  * name                      :string
  * last_name                 :string
  * document                  :string
  * address                   :string
  * observation               :text

* **Contact**
  * type                      :string
  * value                     :string

* **Order**
  * belongs_to *Client* (1)   :references
  * has_many *Products* (0-N) :references
  * event_address             :string
  * delivery_address          :string
  * withdrawal_address        :string
  * shipping_fee              :decimal
  * deposit_fee               :decimal
  * sign_fee                  :decimal
  * replacement_fee           :decimal
  * subtotal                  :decimal
  * total                     (calculado)
  * rest                      (calculado)

* **Product**
  * belongs_to *Category* (1) :references
  * name                      :string
  * image                     :attachment (paperclip gem)
  * description               :text
  * price                     :decimal
  * replacement_price         :decimal
  * stock                     :integer

* **Category**
  * name                      :string 
