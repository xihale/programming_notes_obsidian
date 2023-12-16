#draft #tech 

>[!tip] ref: https://en.cppreference.com/w/cpp/language/user_literal

>[!note] 必须以 `_` 作为开头

>[!note] 具体细节
>
>>[!tip] 忽略了 `deprecated` 的 `identifier` 方式
>
>`literal` 主要指 `number` `chars` `char`
>e.g `(wchar_t)` `(char32_t*, size_t)`

```cpp
long double operator ""_w(long double);
std::string operator ""_w(const char16_t*, size_t);
unsigned    operator ""_w(const char*);
 
int main()
{
    1.2_w;    // calls operator ""_w(1.2L)
    u"one"_w; // calls operator ""_w(u"one", 3)
    12_w;     // calls operator ""_w("12")
    "two"_w;  // error: no applicable literal operator
						  // unsigned operator ""_w(const char*, size_t);
}
```

> c++20 `non-type` `template`
> 
```cpp
struct A { constexpr A(const char*); };
 
template<A a>
A operator ""_a();
```

```cpp
template<std::size_t N>
struct DoubleString
{
    char p[N + N - 1]{};
 
    constexpr DoubleString(char const(&pp)[N])
    {
        std::ranges::copy(pp, p);
        std::ranges::copy(pp, p + N - 1);
    }
};
 
template<DoubleString A>
constexpr auto operator""_x2()
{
    return A.p;
}

"abc"_x2; // "abcabc" (char*)
```