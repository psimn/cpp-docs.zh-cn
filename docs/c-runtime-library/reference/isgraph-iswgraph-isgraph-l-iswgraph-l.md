---
title: isgraph、iswgraph、_isgraph_l、_iswgraph_l
ms.date: 11/04/2016
api_name:
- isgraph
- iswgraph
- _iswgraph_l
- _isgraph_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isgraph_l
- _iswgraph_l
- _ismbcgraph_l
- Isgraph
- _istgraph_l
- _istgraph
- iswgraph
helpviewer_keywords:
- isgraph function
- _istgraph_l function
- istgraph function
- _isgraph_l function
- iswgraph function
- _iswgraph_l function
- _istgraph function
- _ismbcgraph_l function
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
ms.openlocfilehash: 88219ca6dc4218fc13f7d7c0b5f2ba399c07d501
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954868"
---
# <a name="isgraph-iswgraph-_isgraph_l-_iswgraph_l"></a>isgraph、iswgraph、_isgraph_l、_iswgraph_l

确定整数是否表示图形字符。

## <a name="syntax"></a>语法

```C
int isgraph(
   int c
);
int iswgraph(
   wint_t c
);
int _isgraph_l(
   int c,
   _locale_t locale
);
int _iswgraph_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果*c*是可打印字符而非空格的特定表示形式，则每个例程将返回非零值。 如果*c*是一个除空格之外的可打印字符，则**isgraph**将返回一个非零值。 如果*c*是一个非宽字符空间的可打印宽字符，则**iswgraph**将返回一个非零值。 如果*c*不满足测试条件，则这些例程都将返回0。

具有 **_l**后缀的这些函数的版本使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*不是 EOF 或介于0到0xff （含0和0xff），则**isgraph**和 **_isgraph_l**的行为是不确定的。 当使用调试 CRT 库并且*c*不是这些值之一时，函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istgraph**|**isgraph**|[_ismbcgraph](ismbcgraph-functions.md)|**iswgraph**|
|**_istgraph_l**|**_isgraph_l**|[_ismbcgraph_l](ismbcgraph-functions.md)|**_iswgraph_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**isgraph**|\<ctype.h>|
|**iswgraph**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isgraph_l**|\<ctype.h>|
|**_iswgraph_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
