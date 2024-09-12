##     `Optional<T>`  与 `T` 的区别

> Optional<T> 与 T 之间的区别主要在于 Optional<T> 是一个容器对象，专门用于表示值可能存在也可能不存在.
> 
>提供了一种优雅的方式来处理可能为 null 的对象，避免显式的 null 检查和潜在的空指针异常（NullPointerException）。
> 
> Optional<T> 是 Java 8 引入的一个容器类，用于表示一个可能为空（null）的值
>


### 主要区别：

 -  存在性表示：
	•	T：表示某个具体的数据类型，如果值不存在时，可能会返回 null，因此代码中需要手动检查 null。
	•	Optional<T>：封装了一个 T 类型的对象，表示值可能存在也可能不存在。如果值不存在，Optional 本身不是 null，而是一个空的 Optional 对象。
 - 	空值处理：
	•	T：需要通过显式的 null 检查避免 NullPointerException。
	•	Optional<T>：不必直接处理 null，如可通过 isPresent()、orElse()、orElseGet() 等方法。
 -  API 支持：
	•	Optional<T>：提供了丰富的 API 来简化空值的处理，如：
	    •	isPresent(): 检查是否包含值。
	    •	ifPresent(Consumer<? super T> action): 如果值存在，执行指定的操作。
	    •	orElse(T other): 值不存在时返回默认值。
	    •	orElseGet(Supplier<? extends T> other): 值不存在时，执行一个 Supplier 方法返回默认值。
	    •	orElseThrow(): 值不存在时抛出异常。
### 示例代码
 **使用T表示**
```java
public Customer getCustomer(String openid) {
    Customer customer = customerRepository.findByOpenid(openid);
    if (customer != null) {
        // 值存在，继续处理
        return customer;
    } else {
        // 处理值不存在的情况
        return createCustomer();
    }
}
```

**使用Option<T>表示**

```java
public Customer getCustomer(String openid) {
    return customerRepository.findByOpenid(openid)
        .orElseGet(() -> createCustomer());  // 如果值不存在，调用 createCustomer 方法
}
```
    

