---
author: guidedmissile
comments: false
date: 2017-05-22 05:30:35+00:00
layout: page
link: https://inlovewithcode.wordpress.com/words-visz/
slug: words-visz
title: Words Visz
wordpress_id: 2252
---

Seeing is believing. Belief generates faith. Faith is power to move and create.

Here is some code snippet that might be helpful to visualize the text words like a tree. I created so that I can see the regex pattern codes used in a sold product.

``


    
    import pandas as pd
    from treelib import Node, Tree
    from collections import defaultdict
    
    class display_data():
        def __init__(self, data=[]):
            self.data = pd.Series(data)
            self.sam = defaultdict(int)
    
            # create a temporaray fns
            def get_first_charecter(item_number):
                item_number = str(item_number)
                if item_number:
                    return item_number[0]
                return '@'
            
            # PERFORMANCE: SUGGESTION - pass not any self.fns to `map` fns.
            self.all_char_families = sorted(set(map(get_first_charecter, self.data)))
            
            # update N-gram Dict
            self.update_sam()
    
        def reset_sam(self):
            self.sam = defaultdict(int)
    
        def update_sam(self):
            '''Parse each code in N-Grams fashion and update `sam` dict.'''
            if self.sam:
                return
            sam = self.sam
            data = self.data
            def update_code_to_sam(code):
                tmp = ''
                for char in str(code):
                    tmp += char
                    sam[tmp] += 1
            for code in data:
                update_code_to_sam(code)
    
        def get_char_family_data(self, char):
            '''Builds tree data for a Specific Charecter.'''
            sam = self.sam
            tmp = sorted(list(sam.items()), key=lambda x: x[0])
            char_family_data = list(filter(lambda x: x[0].startswith(char), tmp))
            return char_family_data
    
        def charecter_show_tree(self, data):
            '''Builds tree and displays data.'''
            tree = Tree()
            for node_name, count in data:
                title = node_name + '(' + str(count) + ')'
                if len(node_name) == 1:
                    # Narent Node
                    tree.create_node(title, node_name)
                else:
                    if count > 10:
                        tree.create_node(title, node_name, parent=node_name[:-1])
            tree.show()
    
        def show_char_family(self, char):
            '''Main Tree plot to collect data and show as tree.'''
            update_sam = self.update_sam
            if not sam:
                update_sam()
            char_family_data = self.get_char_family_data(char)
            print(char, '- Family Datasize is', len(char_family_data))
            if char_family_data:
                # if data exists
                self.charecter_show_tree(char_family_data)
            return



**TEST DATA VIS**


    
    #  making 10 copies as 10 is min to show in tree
    tmp = display_data(['a', 'aaa', 'a', 'aaa' , 'a',
                        'aaaa123', 'a123', 'a1233', 'adf13',
                        'aabbb123', 'ab123', 'abb1233', 'adbbbf13',
                        'abc', 'abcde', 'abs', 'absol', 'absolute',
                        'ab', 'abo', 'abov', 'above'
                        'ab', 'abe', 'abel',
                        'abraham', 'abe', 'abra'
                        'c', 'c1', 'c2', 'c3',
                        'd', 'd1', 'd2', 'd4',
                       ] * 10 )
    
    
    print(tmp.all_char_families, tmp.show_char_family('a'))



**OUTPUT**


    
    a - Family Datasize is 58
    a(270)
    ├── a1(20)
    │   └── a12(20)
    │       └── a123(20)
    ├── aa(40)
    │   └── aaa(30)
    ├── ab(160)
    │   ├── abc(20)
    │   ├── abe(30)
    │   ├── abo(30)
    │   │   └── abov(20)
    │   ├── abr(20)
    │   │   └── abra(20)
    │   └── abs(30)
    │       └── abso(20)
    │           └── absol(20)
    └── ad(20)
    
    ['a', 'c', 'd'] None
