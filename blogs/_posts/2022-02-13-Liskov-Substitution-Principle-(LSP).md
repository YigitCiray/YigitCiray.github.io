My third post is about LSP, I am on the third post of reverse order of SO-L-ID principles with this blog post.

Please find my other blog post about [Dependency Inversion Principle](https://ihadahamoment.com/Dependency-Inversion-Principe-(DIP)/) and [Interface Segregation Principle](https://ihadahamoment.com/Interface-Segregation-Principle-(ISP)/)

**Background**
Barbara Liskov defined the subtypes as below in [1988, Data Abstraction and Hierarchy](https://www.cs.tufts.edu/~nr/cs257/archive/barbara-liskov/data-abstraction-and-hierarchy.pdf)
_What is unwanted here is something like the following substitution property:
If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T._

Above, complicated to understand, part is taken out from mentioned document by Robert C. Martin, aka Uncle Bob on [Clean Architecrute](https://www.amazon.com/dp/0134494164/ref=redir_mobile_desktop?_encoding=UTF8&aaxitk=8434daf3e487df1e8f2edba3e416eae3&hsa_cr_id=8875635360201&pd_rd_plhdr=t&pd_rd_r=53d11c49-53c5-4f5d-b2c6-b514524c1e6b&pd_rd_w=LGZv0&pd_rd_wg=TCGzk&ref_=sbx_be_s_sparkle_td_asin_1_img) book. To have better understanding I read the 3.3 Type Hierarchy from the paper.

**Why do we need Liskov Substitution Principle?**
By using LSP 
