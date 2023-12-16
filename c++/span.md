#tech

## preface

span 翻译过来是 `连续` 的意思, 正如其名, 这是一个用来存储连续的东西的东西

>[!tip] 我想说
>这是革命性的! 

## Definition

```cpp
template <typename T, std::size_t Extent = std::dynamic_extent>
class span;
```

简单来说, 的确是 `span`, 其存储一个 `指针(T)` 和 `长度(Extent)`

>[!note]- 为什么
>
>```cpp
>void func(char a[]);
>```
>在 `c` 中, 这是很平常的操作
>但是, 当你传入一个 `array`, 自然地, 它退化成了一个指针, 我们无法识别它的长度!
>
>这是我在写 xsocket 的时候实在地遇到的问题: [[xsocket/草案#domain_resolver]]
 
## usage

#### `Extent` 可以 `static` 也可以 `dynamic`

1. `dynamic` 可以 `隐性` 转换为 `static` 
2. 设定 `static` 之后不可以重新赋值(`operator =`)

```cpp
std::span<T> _span={...};
std::span<T, 5> _span={...};
```

### samples

```c++
int main() {
	std::vector myVec{1,2,3};
	std::span mySpan1{myVec};
	std::span mySpan2{myVec.data(), myVec.size()};
}
```


>[!note] 省略了 `template<...>` 参数
>![[Class Template Argument Deduction]]

