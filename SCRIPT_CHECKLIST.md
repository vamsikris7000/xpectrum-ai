# 📋 Script Checklist for New Pages

## 🚨 CRITICAL: Always include these scripts in new pages

### 1. **jQuery Library** (Required for dropdown functionality)
```html
<!-- jQuery -->
<script src="assets/js/jquery-3.5.1.min.dc5e7f18c8.js" type="text/javascript" crossorigin="anonymous"></script>
```

### 2. **Webflow Scripts** (Handles dropdown and other interactions)
```html
<!-- Webflow Scripts -->
<script src="assets/js/webflow.c91af5672.js" type="text/javascript"></script>
```

### 3. **Custom Dropdown Functionality** (Our custom code)
```html
<!-- Dropdown Functionality -->
<script>
    $(document).ready(function() {
        // Remove Webflow badge
        function removeWebflowBadge() {
            $('.w-webflow-badge, [data-wf-badge], .w-webflow-badge-container, [class*="webflow"][class*="badge"]').remove();
            $('body').find('[class*="webflow"][class*="badge"]').remove();
        }
        
        // Remove badge immediately
        removeWebflowBadge();
        
        // Remove badge periodically in case it gets added back
        setInterval(removeWebflowBadge, 1000);
        
        // Initialize dropdown functionality
        $('.w-dropdown-toggle').on('click', function(e) {
            e.preventDefault();
            e.stopPropagation();
            var dropdown = $(this).closest('.w-dropdown');
            var dropdownList = dropdown.find('.w-dropdown-list');
            
            console.log('Dropdown clicked:', dropdown.length, dropdownList.length);
            
            // Toggle dropdown
            if (dropdown.hasClass('w--open')) {
                dropdown.removeClass('w--open');
                dropdownList.hide();
            } else {
                // Close other dropdowns
                $('.w-dropdown').removeClass('w--open');
                $('.w-dropdown-list').hide();
                
                // Open this dropdown
                dropdown.addClass('w--open');
                dropdownList.show();
            }
        });
        
        // Close dropdown when clicking outside
        $(document).on('click', function(e) {
            if (!$(e.target).closest('.w-dropdown').length) {
                $('.w-dropdown').removeClass('w--open');
                $('.w-dropdown-list').hide();
            }
        });
    });
</script>
```

## 📝 **Complete Script Section Template**
```html
    <!-- jQuery -->
    <script src="assets/js/jquery-3.5.1.min.dc5e7f18c8.js" type="text/javascript" crossorigin="anonymous"></script>
    
    <!-- Webflow Scripts -->
    <script src="assets/js/webflow.c91af5672.js" type="text/javascript"></script>
    
    <!-- Dropdown Functionality -->
    <script>
        $(document).ready(function() {
            // Remove Webflow badge
            function removeWebflowBadge() {
                $('.w-webflow-badge, [data-wf-badge], .w-webflow-badge-container, [class*="webflow"][class*="badge"]').remove();
                $('body').find('[class*="webflow"][class*="badge"]').remove();
            }
            
            // Remove badge immediately
            removeWebflowBadge();
            
            // Remove badge periodically in case it gets added back
            setInterval(removeWebflowBadge, 1000);
            
            // Initialize dropdown functionality
            $('.w-dropdown-toggle').on('click', function(e) {
                e.preventDefault();
                e.stopPropagation();
                var dropdown = $(this).closest('.w-dropdown');
                var dropdownList = dropdown.find('.w-dropdown-list');
                
                console.log('Dropdown clicked:', dropdown.length, dropdownList.length);
                
                // Toggle dropdown
                if (dropdown.hasClass('w--open')) {
                    dropdown.removeClass('w--open');
                    dropdownList.hide();
                } else {
                    // Close other dropdowns
                    $('.w-dropdown').removeClass('w--open');
                    $('.w-dropdown-list').hide();
                    
                    // Open this dropdown
                    dropdown.addClass('w--open');
                    dropdownList.show();
                }
            });
            
            // Close dropdown when clicking outside
            $(document).on('click', function(e) {
                if (!$(e.target).closest('.w-dropdown').length) {
                    $('.w-dropdown').removeClass('w--open');
                    $('.w-dropdown-list').hide();
                }
            });
        });
    </script>
```

## ✅ **Pre-Creation Checklist**
Before creating a new page, ensure you have:

1. **✅ jQuery script** included
2. **✅ Webflow script** included  
3. **✅ Custom dropdown code** included
4. **✅ Proper script order** (jQuery first, then Webflow, then custom)
5. **✅ Scripts placed before closing `</body>` tag**

## 🐛 **Troubleshooting**
If dropdown doesn't work:
1. **Check browser console** for JavaScript errors
2. **Verify jQuery is loaded** - type `$` in console
3. **Verify Webflow script is loaded** - check network tab
4. **Check script order** - jQuery must load before custom code

## 📁 **Working Examples**
- ✅ `index.html` - Working dropdown
- ✅ `contact.html` - Working dropdown  
- ✅ `pricing.html` - Now fixed with proper scripts

## 🚀 **Quick Copy-Paste Method**
When creating new pages, copy the entire script section from a working page (like `index.html`) and paste it into your new page.

## 📋 **Company Dropdown Structure**
The Company dropdown should include these 4 options:

1. **About** - "Discover our mission to revolutionize business with AI agents."
2. **Developers** - "Meet the experts behind our AI innovation."
3. **Products** - "AI agents that work like real employees."
4. **API** - "Access our AI agent APIs and documentation." (Links to https://testapi-liard.vercel.app/)

### **API Link Template:**
```html
<a href="https://testapi-liard.vercel.app/" target="_blank" class="service-card dropdown-service w-inline-block" tabindex="0">
    <div class="g-stack-xl fill-100 md-inline">
        <img alt="api icon" loading="lazy" src="assets/images/6544f2728f0eed98d9944652_About%20icon.svg" class="navigation-dropdown-icon">
        <div class="g-stack-l fill-100">
            <h3 class="headline xxs">API</h3>
            <p class="body-text-s display-lg">Access our AI agent APIs and documentation.</p>
        </div>
    </div>
</a>
```
