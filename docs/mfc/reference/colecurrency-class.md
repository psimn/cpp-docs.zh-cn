---
title: COleCurrency 类
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: fc7c64ada1100b0fc0a51670de3e8ec04b141b04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741648"
---
# <a name="colecurrency-class"></a>COleCurrency 类

封装 OLE 自动化的 `CURRENCY` 数据类型。

## <a name="syntax"></a>语法

```
class COleCurrency
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|构造 `COleCurrency` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleCurrency::Format](#format)|生成`COleCurrency`对象的格式化字符串表示形式。|
|[COleCurrency::GetStatus](#getstatus)|获取此`COleCurrency`对象的状态（有效性）。|
|[COleCurrency::ParseCurrency](#parsecurrency)|从字符串中读取货币值并设置的值`COleCurrency`。|
|[COleCurrency::SetCurrency](#setcurrency)|设置此`COleCurrency`对象的值。|
|[COleCurrency::SetStatus](#setstatus)|设置此`COleCurrency`对象的状态（有效性）。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator =](#operator_eq)|`COleCurrency`复制值。|
|[operator +、-](#operator_plus_minus)|添加、减去和更改值的`COleCurrency`符号。|
|[operator +=, -=](#operator_plus_minus_eq)|从此对象中添加`COleCurrency`和减去值。 `COleCurrency`|
|[运算符 */](#operator_star)|按整数值缩放值。`COleCurrency`|
|[operator *=, /=](#operator_star_div_eq)|按整数`COleCurrency`值缩放此值。|
|[操作员 < <](#operator_stream)|将值输出到`CArchive`或`CDumpContext`。 `COleCurrency`|
|[operator >>](#operator_stream)|输入中`COleCurrency` `CArchive`的对象。|
|[运算符货币](#operator_currency)|`COleCurrency`将值转换为货币。|
|[operator = =、<、< = 等。](#colecurrency_relational_operators)|比较两`COleCurrency`个值。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|包含此`COleCurrency`对象的基础货币。|
|[COleCurrency::m_status](#m_status)|包含此`COleCurrency`对象的状态。|

## <a name="remarks"></a>备注

`COleCurrency`没有基类。

货币作为8字节、2的补码整数值（由10000缩放）来实现。 这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。 货币数据类型对于涉及 money 的计算非常有用，对于精确度非常重要的任何固定点计算都非常有用。 它是 OLE 自动化的`VARIANT`数据类型的可能类型之一。

`COleCurrency`还实现此定点类型的一些基本算术运算。 已选择支持的操作，以控制在固定点计算期间发生的舍入误差。

## <a name="inheritance-hierarchy"></a>继承层次结构

`COleCurrency`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="colecurrency"></a>COleCurrency：： COleCurrency

构造 `COleCurrency` 对象。

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>参数

*cySrc*<br/>
要复制到新`COleCurrency`对象中的货币值。

*curSrc*<br/>
要复制`COleCurrency`到新`COleCurrency`对象的现有对象。

*varSrc*<br/>
要转换`VARIANT`为货币值（VT_CY `COleVariant` ）并复制到新`COleCurrency`对象中的现有数据结构（可能为对象）。

*nUnits*， *nFractionalUnits*指示要复制到新`COleCurrency`对象中的值的单位和小数部分（1/10000 的部分）。

### <a name="remarks"></a>备注

所有这些构造函数将创建`COleCurrency`初始化为指定值的新对象。 下面是每个构造函数的简要说明。 除非另有说明，否则新`COleCurrency`项的状态将设置为 "有效"。

- COleCurrency （）构造一个`COleCurrency`初始化为0（零）的对象。

- COleCurrency (`cySrc`) 从[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)`COleCurrency`值构造对象。

- COleCurrency （`curSrc`）从现有`COleCurrency` `COleCurrency`对象构造对象。 新对象具有与源对象相同的状态。

- COleCurrency （`varSrc`） `COleCurrency`构造对象。 尝试将[变体](/windows/win32/api/oaidl/ns-oaidl-variant)或`COleVariant`对象转换为货币（VT_CY）值。 如果此转换成功，转换后的值将复制到新`COleCurrency`的对象。 如果不是，则将`COleCurrency`对象的值设置为零（0），并将其状态设置为 "无效"。

- `COleCurrency(`指定`, `数值`) Constructs a `分量中的 nUnits nFractionalUnits COleCurrency ' 对象。 如果小数部分的绝对值大于10000，则对单位进行适当的调整。 请注意，单位和小数部分由有符号的长值指定。

有关详细信息，请参阅 Windows SDK 中的[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[变体](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

### <a name="example"></a>示例

下面的示例演示零参数和双参数构造函数的影响：

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>COleCurrency：： Format

调用此成员函数可创建货币值的格式化表示形式。

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
指示区域设置的标志。 只有以下标志与货币相关：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

*lcid*<br/>
指示用于转换的区域设置 ID。

### <a name="return-value"></a>返回值

一个`CString`包含格式化货币值的。

### <a name="remarks"></a>备注

它使用本地语言规范（区域设置 Id）设置值的格式。 返回的值中不包含货币符号。 如果此`COleCurrency`对象的状态为 null，则返回值为空字符串。 如果状态无效，则返回字符串由字符串资源 IDS_INVALID_CURRENCY 指定。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>COleCurrency：： GetStatus

调用此成员函数以获取给定`COleCurrency`对象的状态（有效性）。

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>返回值

返回此`COleCurrency`值的状态。

### <a name="remarks"></a>备注

返回值由`CurrencyStatus` `COleCurrency`类中定义的枚举类型定义。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有关这些状态值的简要说明，请参阅以下列表：

  - `COleCurrency::valid`指示此`COleCurrency`对象有效。

  - `COleCurrency::invalid`指示此`COleCurrency`对象无效; 也就是说，它的值可能不正确。

  - `COleCurrency::null`指示此`COleCurrency`对象为 null，即没有为此对象提供值。 （在数据库意义上，这是 "null"，而不是C++ null。）

`COleCurrency`对象的状态在下列情况下无效：

- 如果其值是从无法转换为货币`COleVariant`值的变量或值设置的，则为。

- 如果此对象已溢出或下溢在过程中遇到算术赋值运算，例如`+=`或 **\*=** 。

- 如果分配给此对象的值无效。

- 如果使用[SetStatus](#setstatus)将此对象的状态显式设置为无效，则为。

有关可能将状态设置为 "无效" 的操作的详细信息，请参阅以下成员函数：

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +-](#operator_plus_minus)

- [operator + = 和-=](#operator_plus_minus_eq)

- [operator * /](#operator_star)

- [运算符 * = 和/=](#operator_star_div_eq)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>  COleCurrency::m_cur

此`COleCurrency`对象的基础[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)结构。

### <a name="remarks"></a>备注

> [!CAUTION]
>  更改此函数所返回`CURRENCY`的指针所访问的结构中的值将更改此`COleCurrency`对象的值。 它不会更改此`COleCurrency`对象的状态。

有关详细信息，请参阅 Windows SDK 中的[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)项。

##  <a name="m_status"></a>COleCurrency：： m_status

此数据成员的类型是在`CurrencyStatus` `COleCurrency`类中定义的枚举类型。

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>备注

有关这些状态值的简要说明，请参阅以下列表：

- `COleCurrency::valid`指示此`COleCurrency`对象有效。

- `COleCurrency::invalid`指示此`COleCurrency`对象无效; 也就是说，它的值可能不正确。

- `COleCurrency::null`指示此`COleCurrency`对象为 null，即没有为此对象提供值。 （在数据库意义上，这是 "null"，而不是C++ null。）

`COleCurrency`对象的状态在下列情况下无效：

- 如果其值是从无法转换为货币`COleVariant`值的变量或值设置的，则为。

- 如果此对象已溢出或下溢在过程中遇到算术赋值运算，例如`+=`或 **\*=** 。

- 如果分配给此对象的值无效。

- 如果使用[SetStatus](#setstatus)将此对象的状态显式设置为无效，则为。

有关可能将状态设置为 "无效" 的操作的详细信息，请参阅以下成员函数：

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +、-](#operator_plus_minus)

- [operator +=, -=](#operator_plus_minus_eq)

- [运算符 */](#operator_star)

- [operator *=, /=](#operator_star_div_eq)

> [!CAUTION]
>  此数据成员适用于高级编程情况。 应使用内联成员函数[GetStatus](#getstatus)和[SetStatus](#setstatus)。 有关`SetStatus`显式设置此数据成员的其他注意事项，请参阅。

##  <a name="operator_eq"></a>COleCurrency：： operator =

这些重载赋值运算符将源货币值复制到此`COleCurrency`对象中。

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>备注

下面是每个运算符的简要说明：

- **operator = （** `cySrc` **）** 将`CURRENCY`该值复制到对象中`COleCurrency` ，并将其状态设置为 "有效"。

- **operator = （** `curSrc` `COleCurrency` **）** 操作数`COleCurrency`的值和状态将复制到此对象中。

- **operator = （** *varSrc* **）** 如果将`VARIANT`值（或[COleVariant](../../mfc/reference/colevariant-class.md)对象）转换为货币（ `VT_CY`）成功，则会将转换后的值复制到此`COleCurrency`对象中，并将其状态设置为 "有效"。 如果转换不成功，则将`COleCurrency`对象的值设置为0，并将其状态设置为 "无效"。

有关详细信息，请参阅 Windows SDK 中的[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[变体](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>COleCurrency：： operator +，-

通过这些运算符，可以在两`COleCurrency`个值之间增加和向彼此进行减法运算，还可以更改`COleCurrency`值的符号。

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>备注

如果任一操作数为 null，则结果`COleCurrency`值的状态为 null。

如果算术运算溢出，则生成`COleCurrency`的值无效。

如果操作数无效，而另一个不为 null，则结果`COleCurrency`值的状态将无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>COleCurrency：： operator + =，-=

允许您在此`COleCurrency` `COleCurrency`对象中添加和减去值。

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>备注

如果任一操作数为 null，则此`COleCurrency`对象的状态将设置为 null。

如果算术运算溢出，此`COleCurrency`对象的状态将设置为 "无效"。

如果其中一个操作数无效，而另一个不为 null，则此`COleCurrency`对象的状态将设置为 "无效"。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>COleCurrency：： operator \*和/

允许通过整数值缩放`COleCurrency`值。

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>备注

如果操作数为 null，则结果`COleCurrency`值的状态为 null。 `COleCurrency`

如果算术运算溢出或下溢，则结果`COleCurrency`值的状态将无效。

如果操作数无效，则结果`COleCurrency`值的状态将无效。 `COleCurrency`

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>COleCurrency：： operator \*=，/=

允许使用整数值缩放`COleCurrency`此值。

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>备注

如果操作数为 null，则此`COleCurrency`对象的状态将设置为 null。 `COleCurrency`

如果算术运算溢出，此`COleCurrency`对象的状态将设置为 "无效"。

如果操作数无效，则此`COleCurrency`对象的状态将设置为 "无效"。 `COleCurrency`

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>COleCurrency：： operator &lt;， &lt;&gt;&gt;

支持诊断转储并存储到存档。

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>备注

提取（ **>>** ）运算符支持从存档中加载。

##  <a name="operator_currency"></a>COleCurrency：： operator CURRENCY

返回一个`CURRENCY`结构，它的值`COleCurrency`从此对象复制。

```
operator CURRENCY() const;
```

### <a name="remarks"></a>备注

##  <a name="parsecurrency"></a>COleCurrency：:P arseCurrency

调用此成员函数可分析字符串，以读取货币值。

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>参数

*lpszCurrency*<br/>
指向要分析的以 null 结尾的字符串的指针。

*dwFlags*<br/>
指示区域设置的标志，可能为以下标志：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

*lcid*<br/>
指示用于转换的区域设置 ID。

### <a name="return-value"></a>返回值

如果字符串成功转换为货币值，则为非零值; 否则为0。

### <a name="remarks"></a>备注

它使用本地语言规范（区域设置 Id）来表示源字符串中的非数字字符。

有关区域设置 ID 值的讨论，请参阅[支持多种语言](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)。

如果字符串已成功转换为货币值，则将此`COleCurrency`对象的值设置为该值，并将其状态设置为 "有效"。

如果字符串无法转换为货币值，或如果存在数值溢出，则此`COleCurrency`对象的状态无效。

如果由于内存分配错误，字符串转换失败，此函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。 在任何其他错误状态中，此函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>COleCurrency 关系运算符

比较两个货币值，如果条件为 true，则返回非零值;否则为0。

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  如果任一操作数的状态为 null 或 **<** 无效，则 **>=** 排序操作的返回值（、 **\< =** 、 **>** ）是不确定的。 相等运算符（ `==`， `!=`）考虑操作数的状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>COleCurrency：： SetCurrency

调用此成员函数以设置此`COleCurrency`对象的单位和小数部分。

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>参数

*nUnits*， *nFractionalUnits*指示要复制到此`COleCurrency`对象中的值的单位和小数部分（1/10000 的部分）。

### <a name="remarks"></a>备注

如果小数部分的绝对值大于10000，则对单位进行适当的调整，如下面的第三个示例所示。

请注意，单位和小数部分由有符号的长值指定。 下面的第四个示例演示当参数具有不同的符号时会发生的情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>  COleCurrency::SetStatus

调用此成员函数以设置此`COleCurrency`对象的状态（有效性）。

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>参数

*status*<br/>
此`COleCurrency`对象的新状态。

### <a name="remarks"></a>备注

*状态*参数值由`CurrencyStatus`枚举类型定义，该类型`COleCurrency`是在类中定义的。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleCurrency::valid`指示此`COleCurrency`对象有效。

- `COleCurrency::invalid`指示此`COleCurrency`对象无效; 也就是说，它的值可能不正确。

- `COleCurrency::null`指示此`COleCurrency`对象为 null，即没有为此对象提供值。 （在数据库意义上，这是 "null"，而不是C++ null。）

> [!CAUTION]
>  此函数适用于高级编程情况。 此函数不会更改此对象中的数据。 通常用于将状态设置为 null 或无效。 请注意，赋值运算符（ [operator =](#operator_eq)）和[SetCurrency](#setcurrency)根据源值将对象的状态设置为。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 类](../../mfc/reference/colevariant-class.md)
