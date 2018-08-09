# Mutabilit vs Immutability

Source: [Medium](https://medium.com/@meghamohan/mutable-and-immutable-side-of-python-c2145cf72747)

* Everything in Python is an object.
* A mutable object can be changed after it is created, and an immutable object can’t.
* Objects of built-in types like (int, float, bool, str, tuple, unicode) are immutable.
* Objects of built-in types like (list, set, dict) are mutable.
* **To simulate immutability in a class, one should override attribute setting and deletion to raise exceptions.**

## Exception

    t = ('hello', [1, 2, 3])

* t is immutable
* t[0] is immutable
* t[1] is mutable

## Immutable
 * passed by value


      def updateList(list1):
          list1 += [10]

      n = [5, 6]
      print(id(n))                  # 140312184155336

      updateList(n)
      print(n)                      # [5, 6, 10]
      print(id(n))                  # 140312184155336



## Mutable
 * Passed by reference
    (why reference?because its value can always change)

      def updateNumber(n):
          print(id(n))
          n += 10

      b = 5
      print(id(b))                   # 10055680
      updateNumber(b)                # 10055680
      print(b)                       # 5

