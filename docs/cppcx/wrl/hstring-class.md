---
title: HString 类
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 71ebc02dc56b45e8790bfac7b7d4bac80d5f7729
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500488"
---
# <a name="hstring-class"></a>HString 类

一个帮助器类, 用于使用 RAII 模式管理[HSTRING](/windows/win32/WinRT/hstring)的生存期。

## <a name="syntax"></a>语法

```cpp
class HString;
```

## <a name="remarks"></a>备注

Windows 运行时通过[HSTRING](/windows/win32/WinRT/hstring)句柄提供对字符串的访问。 `HString`类提供便利的函数和运算符来简化使用 HSTRING 句柄。 此类可以通过 RAII 模式处理其拥有的 HSTRING 的生存期。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                | 描述
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | 初始化 `HString` 类的新实例。
[HString:: ~ HString](#tilde-hstring) | 销毁`HString`类的当前实例。

### <a name="public-methods"></a>公共方法

名称                                     | 描述
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | 将指定`HString`的对象与当前`HString`的对象相关联。
[HString::CopyTo](#copyto)               | 将当前`HString`对象复制到 HSTRING 对象。
[HString::Detach](#detach)               | 将指定`HString`的对象与其基础值解除对应。
[HString::Get](#get)                     | 检索基础 HSTRING 句柄的值。
[HString::GetAddressOf](#getaddressof)   | 检索指向基础 HSTRING 句柄的指针。
[HString::GetRawBuffer](#getrawbuffer)   | 检索指向基础字符串数据的指针。
[HString::IsValid](#isvalid)             | 指示当前`HString`的对象是否有效。
[HString:: MakeReference](#makereference) | 根据指定的字符串参数创建对象。`HStringReference`
[HString::Release](#release)             | 删除基础字符串值, 并将当前`HString`对象初始化为空值。
[HString::Set](#set)                     | 将当前`HString`对象的值设置为指定的宽字符字符串或`HString`参数。

### <a name="public-operators"></a>公共运算符

名称                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | 将另一个`HString`对象的值移动到当前`HString`对象。
[HString:: operator = =](#operator-equality)    | 指示两个参数是否相等。
[HString::operator!=](#operator-inequality)  | 指示两个参数是否不相等。
[HString:: operator&lt;](#operator-less-than) | 指示第一个参数是否小于第二个参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HString`

## <a name="requirements"></a>要求

**标头:** corewrappers。h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

销毁`HString`类的当前实例。

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

将指定`HString`的对象与当前`HString`的对象相关联。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>参数

*hstr*<br/>
一个现有的 `HString` 对象。

## <a name="copyto"></a>HString::CopyTo

将当前`HString`对象复制到 HSTRING 对象。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*str*<br/>
接收副本的 HSTRING。

### <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)函数。

## <a name="detach"></a>HString::Detach

将指定`HString`的对象与其基础值解除对应。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>返回值

分离操作`HString`开始之前的基础值。

## <a name="get"></a>HString::Get

检索基础 HSTRING 句柄的值。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>返回值

基础 HSTRING 句柄的值

## <a name="getaddressof"></a>HString::GetAddressOf

检索指向基础 HSTRING 句柄的指针。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>返回值

指向基础 HSTRING 句柄的指针。

### <a name="remarks"></a>备注

此操作后，将销毁基础 HSTRING 句柄的字符串值。

## <a name="getrawbuffer"></a>HString::GetRawBuffer

检索指向基础字符串数据的指针。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>参数

*长度*指向接收数据长度的**int**变量的指针。

### <a name="return-value"></a>返回值

指向基础字符串数据的**常量**指针。


## <a name="hstring"></a>HString:: HString

初始化 `HString` 类的新实例。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>参数

*hstr*<br/>
HSTRING 句柄。

*other*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

第一个构造函数初始化一个`HString`空的新对象。

第二个构造函数将`HString`新的对象初始化为现有*其他*参数的值, 然后销毁*其他*参数。

## <a name="isvalid"></a>HString::IsValid

指示当前`HString`对象是否为空。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>参数

如果当前`HString`对象不为空, 则为 true; 否则为**false**。

## <a name="makereference"></a>HString:: MakeReference

根据指定的字符串参数创建对象。`HStringReference`

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>参数

*sizeDest*<br/>
一个模板参数, 指定目标`HStringReference`缓冲区的大小。

*str*<br/>
对宽字符串的引用。

len<br/>
要在此操作中使用的*str*参数缓冲区的最大长度。 如果未指定*len*参数, 则使用整个*str*参数。

### <a name="return-value"></a>返回值

一个`HStringReference`对象, 其值与指定的*str*参数相同。

## <a name="operator-assign"></a>HString:: operator = 运算符

将另一个`HString`对象的值移动到当前`HString`对象。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>参数

*other*<br/>
一个现有的 `HString` 对象。

### <a name="remarks"></a>备注

现有的*其他*对象的值将复制到当前`HString`对象, 然后*其他*对象将被销毁。

## <a name="operator-equality"></a>HString:: operator = = 运算符

指示两个参数是否相等。

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是`HString`或`HStringReference`对象, 也可以是 HSTRING 句柄。

rhs<br/>
要比较的第二个参数。*rhs*可以是`HString` `HStringReference` 、对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数相等, 则**为 true** ;否则**为 false**。

## <a name="operator-inequality"></a>HString:: operator! = 运算符

指示两个参数是否不相等。

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是`HString`或`HStringReference`对象, 也可以是 HSTRING 句柄。

rhs<br/>
要比较的第二个参数。*rhs*可以是`HString` `HStringReference` 、对象或 HSTRING 句柄。

### <a name="return-value"></a>返回值

如果*lhs*和*rhs*参数不相等,**则为 true** ;否则**为 false**。

## <a name="operator-less-than"></a>HString:: operator&lt;运算符

指示第一个参数是否小于第二个参数。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是对的`HString`引用。

rhs<br/>
要比较的第二个参数。 *rhs*可以是对的`HString`引用。

### <a name="return-value"></a>返回值

如果*lhs*参数小于*rhs*参数,**则为 true** ; 否则为 false。否则**为 false**。

## <a name="release"></a>HString::Release

删除基础字符串值, 并将当前`HString`对象初始化为空值。

```cpp
void Release() throw()
```

## <a name="set"></a>HString::Set

将当前`HString`对象的值设置为指定的宽字符字符串或`HString`参数。

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>参数

*str*<br/>
宽字符字符串。

len<br/>
分配给当前`HString`对象的*str*参数的最大长度。

*hstr*<br/>
一个现有的 `HString` 对象。
