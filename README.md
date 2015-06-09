cd wheel-selection.github.io
~$echo "Wheel0selection" > index.html

# wheel-selection
Select a tractor manufacturer from the list below:
<div id="navigation-pagination">
  <ul>
    <li>John Deere</li>
    <li>Fendt</li>
    <li>New Holland</li>
    <li>Claas</li>
  </ul>
</div>

Some aditional css needed to show/hide select or list
*/

( function( $ ) {
    jQuery(document).ready(function(){
        var totalElements = jQuery('#navigation-pagination ul li').size();

        jQuery("<select />").appendTo("#navigation-pagination");

        jQuery("#navigation-pagination a").each(function() {
            var oneElement = jQuery(this);
            jQuery("<option />", {
                "value"   : oneElement.attr("href"),
                "text"    : "Seite "+oneElement.text()+" von "+totalElements
            }).appendTo("#navigation-pagination select");
        });

        jQuery("#navigation-pagination select").on('change', function(e) {
            e.preventDefault();
            jQuery('#go_to_page').val(jQuery(this).val());
            jQuery('.apply-button-enrolled').click();
        });
    })
} )( jQuery );
