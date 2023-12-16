```md
> [!(neckname)](+/-)
```

> `neckname` 在下方有
> `+`: 自动展开
> `-`: 自动收缩

> [!note] 

> [!abstract] 

> [!summary] 

> [!tldr] 

> [!info] 

> [!todo] 

> [!tip] 

> [!hint] 

> [!important] 

> [!success] 

> [!check] 

> [!done] 

> [!question] 

> [!help] 

> [!faq] 

> [!warning] 

> [!caution] 

> [!attention] 

> [!failure] 

> [!fail] 

> [!missing] 

> [!danger] 

> [!error] 

> [!bug] 

> [!example] 

> [!quote] 

> [!cite]

```ts
const c=`- note
- abstract, summary, tldr
- info, todo
- tip, hint, important
- success, check, done
- question, help, faq
- warning, caution, attention
- failure, fail, missing
- danger, error
- bug
- example
- quote, cite`;

// 获取 c 中的所有单词

const tags = c.match(/\w+/g)

console.log(tags)

// 以 `> [word]` 格式输出

console.log(tags?.map(t => `> [!${t}]`).join('\n'))
```