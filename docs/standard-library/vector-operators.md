---
title: '&lt;vector&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: f6717add93c489f536bd0c0b0f82b74bbd915985
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240983"
---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt; 运算符

## <a name="op_neq"></a> 运算符 ！ =

测试运算符左侧的对象是否不等于右侧的对象。

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果 vector 不相等，则为 **true**；如果 vector 相等，则为 **false**。

### <a name="remarks"></a>备注

如果两个 vector 具有的元素数目相等且对应元素具有相同的值，则两个 vector 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="op_lt"></a> 运算符&lt;

测试运算符左侧的对象是否小于右侧的对象。

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 vector 小于运算符右侧的 vector，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="op_lt_eq"></a> 运算符&lt;=

测试运算符左侧的对象是否小于或等于右侧的对象。

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 vector 小于或等于运算符右侧的 vector，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="op_eq_eq"></a> 运算符 = =

测试运算符左侧的对象是否等于右侧的对象。

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 vector 等于运算符右侧的 vector，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

如果两个 vector 具有的元素数目相等且对应元素具有相同的值，则两个 vector 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="op_gt"></a> 运算符&gt;

测试运算符左侧的对象是否大于右侧的对象。

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 vector 大于运算符右侧的 vector，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="op_gt_eq"></a> 运算符&gt;=

测试运算符左侧的对象是否大于或等于右侧的对象。

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*左侧*\
一个 `vector` 类型的对象。

*右侧*\
一个 `vector` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 vector 大于或等于运算符右侧的 vector，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```
