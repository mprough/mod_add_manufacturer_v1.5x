==== Zen Cart Add Manufacturer Admin Column ====


=== Tested on Zen Cart 1.5.X & PHP 5.3.21 ===


== License GNU GENERAL PUBLIC LICENSE ==
=== YOUR MAY NOT REDISTRIBUTE THIS MODULE ===


= This module is an intermediate installation. =

###########################################################################################
#                                                                                         #
# Module release 05/29/2013 http://pro-webs.net/                                          #
#                                                                                         #
# Please REPORT bugs to support@pro-webs.net                             #
#                                                                                         #
# This module can be installed for you by checking the link below:                        #
# http://pro-webs.net/store/index.php?main_page=product_info&cPath=10_11&products_id=429  #
#                                                                                         #
###########################################################################################

This module simply adds the manufacturers name in several place in the admin to
assist stores with multiple vendors in more quickly identifying the inventory
locations. Optional addition pages included are:
--single admin order screen
--pop up admin invoice
--pop up admin packing slip


===Database Changes===
There are no database changes.


===Core File Edits===
/admin/includes/languages/english.php
/admin/orders.php
/admin/invoice.php
/admin/packingslip.php


+++++++++++===Basic Installation===+++++++++++


1. !!!! Backup your database and affected files !!!!

 
================================================================  
   
   
2. Edit /admin/includes/languages/english.php

####ADD
//Edit for manufacturers column
define('TABLE_HEADING_PRODUCTS_MANUFACTURER', 'Manufacturer');


================================================================


3. To add the manufacturer to the admin order screen you will need to edit
/admin/orders.php

####FIND
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MODEL; ?></td>

####ADD the following after
<!--edit add manufacturer column-->
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MANUFACTURER; ?></td>




####FIND
'            <td class="dataTableContent" valign="top">' . $order->products[$i]['model'] . '</td>' . "\n" .

####ADD the following after
//edit add manufacturer column
'            <td class="dataTableContent" valign="top">' . zen_get_products_manufacturers_name($order->products[$i]['id']) . '</td>' . "\n" .



###FIND
          <tr>
            <td align="right" colspan="8"><table border="0" cellspacing="0" cellpadding="2">
<?php
    for ($i = 0, $n = sizeof($order->totals); $i < $n; $i++) {
    
###CHANGE TO
          <tr>
            <td align="right" colspan="10"><table border="0" cellspacing="0" cellpadding="2">
<?php
    for ($i = 0, $n = sizeof($order->totals); $i < $n; $i++) {


================================================================


4. To add the manufacturer column to the pop up admin invoice edit the following:
/admin/invoice.php

####FIND
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MODEL; ?></td>

####ADD the following after
<!--edit add manufacturer column-->
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MANUFACTURER; ?></td>



####FIND
'            <td class="dataTableContent" valign="top">' . $order->products[$i]['model'] . '</td>' . "\n" .

####ADD the following after
//edit add manufacturer column
echo '        <td class="dataTableContent" valign="right">' . zen_get_products_manufacturers_name($order->products[$i]['id']) . '</td>' . "\n" ;




####FIND
        <td align="right" colspan="8"><table border="0" cellspacing="0" cellpadding="2">
<?php
  for ($i = 0, $n = sizeof($order->totals); $i < $n; $i++) {
  
####CHANGE TO
        <td align="right" colspan="10"><table border="0" cellspacing="0" cellpadding="2">
<?php
  for ($i = 0, $n = sizeof($order->totals); $i < $n; $i++) {


================================================================


5. To add the manufacturer column to the pop up admin packing slip edit the following:
/admin/packingslip.php

####FIND
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MODEL; ?></td>

####ADD the following after
<!--edit add manufacturer column-->
<td class="dataTableHeadingContent"><?php echo TABLE_HEADING_PRODUCTS_MANUFACTURER; ?></td>


####FIND
'        <td class="dataTableContent" valign="top">' . $order->products[$i]['model'] . '</td>' . "\n" .
 
####ADD the following after
//edit add manufacturer column
'            <td class="dataTableContent" valign="top">' . zen_get_products_manufacturers_name($order->products[$i]['id']) . '</td>' . "\n" .          


++++++++++===EOF Basic Installation===++++++++++			
       
       
===Change History===

Date       Version  Who             Why
===============================================================================
05/29/2013  1.1	  PRO-Webs.net	Initial Release 
				
				