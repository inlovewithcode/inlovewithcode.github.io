Q!. Python - 2.7 Reference pages

[http://rgruet.free.fr/#QuickRef](http://rgruet.free.fr/#QuickRef)

Q. How to compare two float?

use `math.isclose` function to compare them.

Q. Is there a equivalent to java static main in Python?

Guido's best practices for writing [**Main** method](https://www.artima.com/weblogs/viewpost.jsp?thread=4829)

Q. A Speed Comparison Of C, Julia, Python, Numba, and Cython on LU Factorization

[Link](https://www.ibm.com/developerworks/community/blogs/jfp/entry/A_Comparison_Of_C_Julia_Python_Numba_Cython_Scipy_and_BLAS_on_LU_Factorization?lang=en)

Q. python-new-style-classes-and-subclasses-function

[https://stackoverflow.com/questions/2877110/python-new-style-classes-and-subclasses-function](https://stackoverflow.com/questions/2877110/python-new-style-classes-and-subclasses-function)



# Python 3 Templates

Part of string module

    from string import Template
    
    def main():
      cart = []
      cart.append(dict(item='Coke', price=8, qty=2))
      cart.append(dict(item='Cake', price=12, qty=1))
      cart.append(dict(item='Fish', price=32, qty=4))
      
      t = Template("$qty x $item = $price")
      total = 0
      print("Cart:")
      
      for data in cart:
        print(t.substiture(data))
        total += data['price']
      print("Total: " + str(total))


    if __name__ == "__main__":
      main()
      
# python kubernetes

    import kubernetes, pprint
    from kubernetes import client, config
    from kubernetes.client.rest import ApiException


    k = kubernetes.config.incluster_config.Configuration()

    api_instance = kubernetes.client.CoreV1Api()
    pprint.pprint([ns.metadata.name for ns in api_instance.list_pod_for_all_namespaces().items])


    load_incluster_config()

    kubernetes.config.incluster_config

    /opt/conda/lib/python2.7/site-packages/kubernetes/config/incluster_config.py



# kubernetes creating a node with read_wite access

    gcloud container node-pools create mynewapp1node \
       --cluster myclustername \
       --zone us-central1-b \
       --machine-type=n1-standard-16 \
       --enable-autoscaling \
       --max-nodes=11 \
       --min-nodes=0 \
       --scopes https://www.googleapis.com/auth/devstorage.read_write \
       --node-labels=deploy=newapp1node

    gcloud container node-pools describe mynodepoolname --cluster mycluster --zone us-central1-b

