To find the value of $\lambda_p$, we use the lambda_n.spice file. Here we check the influence of W and L on $\lambda$.

Let's fix L = 1u and see what happens when W increases.

For W = 1u
![image](https://user-images.githubusercontent.com/69206952/171070209-64dad661-6d73-450b-bd59-c7a86f30a48e.png)

For W = 10u
![image](https://user-images.githubusercontent.com/69206952/171070290-e02e43f2-ed08-40d8-bd00-714d029f9a70.png)

For W = 100u
![image](https://user-images.githubusercontent.com/69206952/171070326-c388d7f5-0614-45bb-9072-d32297e2644b.png)

For W = 1000u
![image](https://user-images.githubusercontent.com/69206952/171070352-e5327094-e5e2-4346-86c9-0d00848773fa.png)

Now, let's fix W = 100u and vary L to see what happens.

For L = 1u
![image](https://user-images.githubusercontent.com/69206952/171070326-c388d7f5-0614-45bb-9072-d32297e2644b.png)

For L = 10u
![image](https://user-images.githubusercontent.com/69206952/171070400-d4adb616-b374-446f-a1fe-a7c51d0f8854.png)

For L = 100u
![image](https://user-images.githubusercontent.com/69206952/171070409-ce76a57b-32bc-4ea6-89a2-a661cb4d9282.png)

For L = 1000u
![image](https://user-images.githubusercontent.com/69206952/171070466-43bb2994-1ac2-4ed4-854a-53e96e47feaf.png)

Although not so big, changes in L affect $\lambda$ in an inversely proportional way and in W affect $\lambda$ in a proportional way.

Since we are going to fix L = 1u in the project, we'll use $\lambda_p = 6.9696 \cdot 10^{⁻2}$.
