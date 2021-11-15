# Mock plugin for Python Dia 
A mocking module for writing and testing Python plugins for [Dia](https://wiki.gnome.org/action/show/Apps/Dia).
Now plugin of [python-dia](https://sosie-js.github.io/python-dia/)

## Mocking Sample: ##

```python
#
#   diamock.py ..  bunnyfied by SoSie on 03 nov 2021
#
# 


from dumpObj import dumpObj #here is the golden carot

import inspect
def onDiaLaunched():
    stack=inspect.stack()
    return ("python-startup.py" in stack[-1][1])


if __name__ == '__main__' or not onDiaLaunched():
    
    
    #dia is the mocked version of lib pydia library.
    # it is now python2-3 compatible
    #available here: https://github.com/sosie-js/dia-test
    #installable with the scripts helpers install*.sh
    
    import dia 

else:

    import dia

    """
    import dill
    d=dill.dumps(dia)
    file_path="dill"+__name__+"-dia.dump"
      
    with open(file_path, "wb") as w:
        w.write(d)
    """

#Now set your dia playground
active_display = dia.active_display()
d = active_display.diagram
data = d.data
layer = data.active_layer


objects = layer.objects
#len(objects) is zero here which is normal for an empty diagram

#otypes=dia.registered_types()  is not supported by dia-test.
#As this is the core of creating objects to be added to layer
#we can play only here unless Chris Daley original 
#dia-test accept I merge his project in mine called [pythondia](https://github.com/sosie-js/python-dia) -- SoSie


#enjoy the doc
dumpObj(dia)
dumpObj(layer)
```
