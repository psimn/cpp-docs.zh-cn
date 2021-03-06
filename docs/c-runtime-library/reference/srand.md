---
title: srand
ms.date: 01/02/2018
api_name:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: 03e2b87a37d1b520b6e2b32c2f756fea625eb9a2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958000"
---
# <a name="srand"></a>srand

设置**rand**函数使用的伪随机数生成器的起始种子值。

## <a name="syntax"></a>语法

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>参数

*seed*<br/>
伪随机数生成的种子

## <a name="remarks"></a>备注

**Srand**函数设置在当前线程中生成一系列伪随机整数的起点。 若要重新初始化生成器以创建相同的结果序列，请调用**srand**函数并再次使用同一*种子*参数。 *种子*的任何其他值将生成器设置为伪随机序列中的另一个起点。 **rand**检索生成的伪随机数。 在调用**srand**之前调用**rand**会生成与调用**srand**时的序列相同的序列，并将*seed*作为1传递。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [rand](rand.md) 的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
