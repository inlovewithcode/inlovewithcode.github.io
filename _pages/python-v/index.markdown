---
author: guidedmissile
comments: false
date: 2017-04-01 09:42:28+00:00
layout: page
link: https://inlovewithcode.wordpress.com/python-v/
slug: python-v
title: Python V Static(Fns/Var), Exception
wordpress_id: 1940
---

## Static Methods & Static Variables



Class Sum:


    
    <code># static variable
    num_of_sum_ops = 0
    
    @staticmethod
    def getSum(*args):
        sum = 0
        for i in args:
            sum += int(i)
        Sum.num_of_sum_ops += 1
    return sum
    </code>



Note:
    * static variables are assigned in class but not in **init**
    * static methods have `@staticmethod` keyword.


    
    <code>* static methods/variables are shared like Global functions and variables
    </code>





# Exception Handling







  * When an Error Occurs


  * When something out of ordinary like close a file



try:
    aList = [1, 2, 3]
    print(aList[3])
except IndexError:
    print(‘yep, we had index error’)

except KeyError:
    print(‘ ooh, we had KeyError’)

except:
    print(‘ oh yea, you are screwed, we don’t what caused it’)



## Custom Exception







  * kwargs -> keyword args



Defining Custom exception


    
    <code>class DogNameError(Excepton):
    
        def __init__(self, *args, **kwargs):
            Exception.__init__(self, *args, **kwargs)
    </code>



Example


    
    <code>try:
        dogName = input(“what is your dog name:”)
        if any(char.isdigit() for char in dogName):
            raise DogNameError ## our custom Error fns
    except: DogNameError:
        print(“cool man, you got your exception”)
    
    else:
        # if exception does not occur
        print(“no errors occured”)
    finally:
        # does not matter if excetion happened
        print(“Inputs are ….”)
    </code>



Note:
* `kwargs` mean keyword arguments
* created a custom exception(class)
* custom exception class is supposed to be a inheritance of `Exception` class
* we used keyword `raise` to raise exception
* use `else` for cases like if read a file then print you were able to read. and the content in it.





  * use `finally` key word to do actions which much happened like closing a file and so

try:
    myFile = open(“helloworld”, encoding=“utf-8”)

except FileNotFoundError as ex:
    print(“that file was not found”)
    print(ex.args)

else:
    print(“File:“, myFile.read())
    myFile.close()
finally:
    print(“tried working with file”)






Note:
* we are catching error as `ex` using key word `as`

Source: [Static methods, Exceptions](https://www.youtube.com/watch?v=7vbgD-3s-w4)
