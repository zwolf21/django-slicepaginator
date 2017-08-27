# django-slicepaginator

Slice page range of default django paginator

Tested on python3.4, django==1.6.5

Installation

    pip install django-slicepaginator

Usage

    # views.py
    from django.views.generic import ListView
    from djangoslicer import SlicePaginatorMixin

    
    class SomeListView(SlicePaginatorMixin, ListView):
        model = somemodel
        paginate_by = 10
        slice_count = 10  #optional, default is 10
        
        ...
    
    
    # somemodel_list.html
    ...
    {% for i in page_obj.paginator.page_range %} 
        {% if page_obj.has_next %}	
            {% if request.get_full_path %}
            <li {% if i == page_obj.number %}class="active"{% endif %}><a href="{{ request.get_full_path }}&page={{i}}">{{i}}</a></li>
            {% else %}
            <li {% if i == page_obj.number %}class="active"{% endif %}><a href="?page={{i}}">{{i}}</a></li>	
            {% endif %}
        {% endif %}
    {% endfor %} 
    ...
