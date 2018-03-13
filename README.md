POPUPS AFTER SUBMISION


Create contact form.

Install plugin:
Popups – WordPress Popup - https://wordpress.org/plugins/popups/

Create popup.
In popup options, Change RULES to Page Type - is not equal to - All Pages
Trigger Action - Manual Triggering

Add code to functions.php:

add_action( 'wp_footer', 'mycustom_wp_footer' );
function mycustom_wp_footer() {
?>
<script type="text/javascript">
document.addEventListener( 'wpcf7mailsent', function( event ) {
    if ( '123' == event.detail.contactFormId ) { // Change 123 to the ID of the form 
        
       SPU.show( 143 ); // change 143 to the ID of the popup
       SPU.hide( 120 ); // hide another popup 
       SPU.track( 143, false );//track an impression , if you set to true you track a conversion
    }
}, false );
</script>
<?php
}

// Change 123 to the ID of the form 
// change 143 to the ID of the popup

Test.

CUSTOM CSS

Find unique ID of contact form and add custom CSS to hide "Sender's message was sent successfully".


#wpcf7-f1586-p2156-o1 //Add unique form ID .wpcf7-mail-sent-ok {
	display:none !important;
}

GIF ATTACHMENT DISPLAY SETTINGS
Alignment:Right
Size:Full Size
