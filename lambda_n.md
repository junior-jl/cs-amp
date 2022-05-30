To find the value of $\lambda_n$, we use the lambda_n.spice file. Here we check the influence of W and L on $\lambda$.

Let's fix L = 1u and see what happens when W increases.

For W = 1u
![image](https://user-images.githubusercontent.com/69206952/171067656-eb72b8c9-85ef-4df1-b776-82ba5a802685.png)

For W = 10u
![image](https://user-images.githubusercontent.com/69206952/171067718-71422a0a-fe83-412b-88e5-2f0b08c4ea8c.png)

For W = 100u
![image](https://user-images.githubusercontent.com/69206952/171067748-d4e9cc86-b7c8-4606-99ce-0940ece7334a.png)

For W = 1000u
![image](https://user-images.githubusercontent.com/69206952/171067808-04697e4b-a5ca-4dab-b9d8-d9bf71077069.png)

As expected, W doesn't affect the channel modulation parameter.
Now, let's fix W = 100u and vary L to see what happens.

For L = 1u
![image](https://user-images.githubusercontent.com/69206952/171067748-d4e9cc86-b7c8-4606-99ce-0940ece7334a.png)

For L = 10u
![image](https://user-images.githubusercontent.com/69206952/171067943-9c2c7260-4e58-4f36-ae4b-61cbb161f098.png)

For L = 100u
![image](https://user-images.githubusercontent.com/69206952/171067964-afa1e881-5081-4b2d-bb0c-8f7edc1287f0.png)

For L = 1000u
![image](https://user-images.githubusercontent.com/69206952/171067989-9a06be9b-3aa7-4a4a-a5bf-75d2e19c3ccd.png)

Although not so big, changes in L affect $\lambda$ in an inversely proportional way.

Since we are going to fix L = 1u in the project, we'll use $\lambda_n = 3.8052 \cdot 10^{⁻2}$.
