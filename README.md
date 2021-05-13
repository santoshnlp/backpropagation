# backpropagation

Forward pass
-------------

Inputs  

   i1
   
   i2

First layer

    h1=w1*i1+w2*i2   # w1, w2, w3, and w4  weights

    h2=w3*i1+w4*i2
    
    Activation 

    a_h1= sigmoid(h1) =  1/(1+exp(-h1))

    a_h2= sigmoid(h2) =  1/(1+exp(-h2))
    
Second layer/ output layer

      o1= w5*a_h1+w6*a_h2   # w5, w6, w7, and w8  weights

      o2= w7*a_h1+w8*a_h2


      Activation
      
         a_o1= sigmoid(o1) =  1/(1+exp(-o1))

         a_o2= sigmoid(o2) =  1/(1+exp(-o2))
         
 L2 Error Computation
 
        E1=1/2*(t1-a_o1)^2
        
        E2=1/2*(t2-a_o2)^2
        
        ET= E1+E2  # Total error
        
        
 Gradients computation
 ================================
          
           We want to know  how ET changes wrt weights w1,2...8
           
           i.e  dET/dw1 , dET/dw2   similarly for all weights
           
           ET =  E1+E2  
           
           dET/da_o1  = dE1/da_o1  + dE2/da_o2 = (a_o1-t1)  + 0
           
           #          a_o1= sigmoid(o1) =  1/(1+exp(-o1))


           da_o1/do1  =  a_o1*(1-a_o1)  #  sigmoing differentiation
           
           do1/dw5 = a_h1
           
           
           chain rule
           
           dET/dw5=(dE1/dwa_o1)*(dao_1/do1)*(do1/dw5)  =  (a_o1-t1)*a_o1*(1-a_o1)*a_h1
           
           similarly dET/dw6, dET/dw7 and dET/dw8 could be computed
           
           
           Now let's find dET/dw1
           
           dET/da_h1 = d(E1+E2)/da_h1 
           
           dE1/da_h1 = (dE1/da_o1)*(da_o1/do1)*(do1/da_h1) = (a_o1-t1)*a_o1*(1-a_o1)*w5
           
           dE2/da_h1 = (dE2/da_o2)*(da_o2/do2)*(do2/da_h1) = (a_o2-t2)*a_o2*(1-a_o2)*w7

           
           dET/dw1 = (dE1/da_h1)*(da_h1/dh1)*(dh1/dw1)
           
           
      Weights update
      ================
      
      w =  w - learning rate* dET/dw
           
