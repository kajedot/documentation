=====================
Print shipping labels
=====================

Integrate Odoo with :doc:`third-party shipping carriers
<../setup_configuration/third_party_shipper>` to automatically generate shipping labels that
includes real prices, destination addresses, tracking numbers, and barcodes.

Configuration
=============

To generate labels for a third-party shipping carrier, install the shipping connector, configure and
activate the delivery method, and provide the company's source address and product weights.

For detailed instructions and context on configuring these options, refer to :doc:`this document
<../setup_configuration/third_party_shipper>`.

Install shipping connector
--------------------------

Install the shipping connector's module in Odoo to integrate Odoo with the third party shipping
carrier. To do so, navigate to :menuselection:`Inventory app --> Configuration --> Settings`.

Under the :guilabel:`Shipping Connectors` heading, select the third-party shipping carrier's
checkbox to install it.

.. image:: ../setup_configuration/third_party_shipper/shipping-connectors.png
   :align: center
   :alt: Options of available shipping connectors in Odoo.

Then, click :guilabel:`Save`.

Delivery method
---------------

Next, add the carrier details by going to :menuselection:`Inventory app --> Configuration -->
Shipping Methods`.

On the :guilabel:`Shipping Methods` page, choose the desired delivery method. For details on
configuring shipping method fields, such as :guilabel:`Delivery Product`, :guilabel:`Invoicing
Policy`, or :guilabel:`Margin on Rate`, refer to the :doc:`../setup_configuration/delivery_method`
document.

Next, enter the API key, password, and other API credentials. For specific details about each
shipping method, refer to the following documents:

.. seealso::
   - :doc:`DHL credentials <../setup_configuration/dhl_credentials>`
   - :doc:`Sendcloud credentials <../setup_configuration/sendcloud_shipping>`
   - :doc:`UPS credentials <../setup_configuration/ups_credentials>`


Publish
~~~~~~~

With the delivery method details configured, click the :guilabel:`Test Environment` smart button to
activate it.

.. warning::
   Setting the delivery method to :guilabel:`Production` charges customers for shipping. Verify all
   configurations before launching to production.

.. image:: ../setup_configuration/third_party_shipper/production.png
   :align: center
   :alt: Show the "Test Environment" smart button.

Source address
--------------

Configure the source address for package shipments by going to :menuselection:`Inventory app -->
Configuration --> Warehouses` and selecting the desired warehouse.

On the warehouse configuration page, hover over the :guilabel:`Address` field and select the
:guilabel:`➡️ (right arrow)` icon. Doing so opens the warehouse's contact page.

.. image:: ../setup_configuration/third_party_shipper/internal-link.png
   :align: center
   :alt: Show the internal link icon that appears when hovering over "Address".

Input the warehouse's :guilabel:`Address` and :guilabel:`Phone` number, as they are used to
calculate cost of shipping.

.. image:: ../setup_configuration/third_party_shipper/company.png
   :align: center
   :alt: Show company address and phone number.

Product weight
--------------

To calculate the price of shipping, specify the weight of products by going to
:menuselection:`Inventory app --> Products --> Products`, and selecting the desired product.

Then, switch to the :guilabel:`Inventory` tab, define the :guilabel:`Weight` of the product, in
kilograms.

.. image:: ../setup_configuration/third_party_shipper/product-weight.png
   :align: center
   :alt: Display the "Weight" field in the Inventory tab of the product form.

.. tip::
   Make sure to convert weights into kilograms for the calculations to work properly.

Print tracking labels
=====================

Add shipping on quotation
-------------------------

To generate a tracking label for an order, begin by creating a quotation in :menuselection:`Sales
app --> Orders --> Quotations`. Then, click the :guilabel:`Add Shipping` button in the bottom-right
corner.

.. image:: labels/add-shipping-button.png
   :align: center
   :alt: Show the "Add Shipping" button on the quotation.

In the resulting pop-up window, select the intended carrier from the :guilabel:`Shipping Method`
drop-down menu. After clicking :guilabel:`Get Rate`, the :guilabel:`Cost` of shipping the customer
through the third-party shipping carrier is displayed in the :guilabel:`Cost` field.

Click :guilabel:`Add` to add the cost to the quotation, which is listed as the :ref:`configured
delivery product <inventory/shipping_receiving/delivery-product>`. Finally, click
:guilabel:`Confirm` on the quotation, and click the :guilabel:`Delivery` smart button to access the
delivery order.

.. image:: labels/get-rate.png
   :align: center
   :alt: Show "Get rate" pop-up window.

.. tip::
   For users who do not have the *Sales* app installed, the shipping carrier is specified in a
   delivery order's :guilabel:`Carrier` field of the :guilabel:`Additional Info` tab of

   .. image:: labels/additional-info-tab.png
      :align: center
      :alt: Show the "Additional Info" tab of a delivery order.

Validate delivery order
-----------------------

On the delivery order, after the items in the order have been packed, click
:guilabel:`Validate` to get the shipping carrier's tracking number and generate the shipping label.

The :guilabel:`Tracking Reference` number is generated in the :guilabel:`Additional Info` tab of the
delivery order. Click the :guilabel:`Tracking` smart button to access the tracking link from the
shipping carrier's website.

The tracking label is found in PDF format in the chatter.

.. image:: labels/shipping-label.png
   :align: center
   :alt: Show generated shipping label in the chatter.

.. note::
   For multi-package shipping, one label is generated per package. Each label appears in the
   delivery history.

.. seealso::
   - :doc:`invoicing`
   - :doc:`multipack`
