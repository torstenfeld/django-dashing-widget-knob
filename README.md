django-dashing-widget-knob
==========================

Simple Django Dashing widget to display a knob chart. Using jQuery Knob

![Knob Widget](http://i.imgur.com/Xbr9G0h.png)

## Usage

Add **knob** to [``INSTALLED_WIDGETS``](http://django-dashing.readthedocs.org/en/latest/getting-started.html#django-settings) and finally add the following code to your dashing [javascript configuration file](http://django-dashing.readthedocs.org/en/latest/getting-started.html#config-file).

    <dashboard>.addWidget('knob_widget', 'Knob', {
        data: {
            title: 'Twitter followers',
            more_info: 'for @thisisjustaplaceholder',
            value: 0
        },
        interval: 5000, // 30 min
    
        getData: function () {
            var self = this;
    
            $.extend(self.data, {
                value: 23,
                data: {
                    angleArc: 250,
                    fgColor: '#90ee90',
                    angleOffset: -125,
                    displayInput: true,
                    displayPrevious: false,
                    step: 1,
                    min: 0,
                    max: 10000,
                    readOnly: true
                }
            });
            self.data.value = Math.floor((Math.random() * 10000) + 1);;
            self.data.updated_at = lastUpdate();
    
            home.publish('knob/render');
            $('.dashing-knob').trigger('change');
        }
    });

Replacing ``<dashboard>`` for your dashboard name.