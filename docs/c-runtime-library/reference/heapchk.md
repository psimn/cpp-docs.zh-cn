---
title: _heapchk
ms.date: 11/04/2016
api_name:
- _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 857feb66d89d5dc406042478156483ecb86a2474
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954812"
---
# <a name="_heapchk"></a>_heapchk

在堆上运行一致性检查。

## <a name="syntax"></a>语法

```C
int _heapchk( void );
```

## <a name="return-value"></a>返回值

**_heapchk**返回在 Malloc. h 中定义的以下整数清单常量之一。

|返回值|条件|
|-|-|
| **_HEAPBADBEGIN** | 初始头信息已损坏，或找不到。 |
| **_HEAPBADNODE** | 找到错误节点，或堆已损坏。 |
| **_HEAPBADPTR** | 指向堆的指针无效。 |
| **_HEAPEMPTY** | 尚未初始化堆。 |
| **_HEAPOK** | 堆看起来一致。 |

此外，如果发生错误， **_heapchk**会将**Errno**设置为**ENOSYS**。

## <a name="remarks"></a>备注

**_Heapchk**函数通过检查堆的最小一致性来帮助调试堆相关的问题。 如果操作系统不支持 **_heapchk**（例如，Windows 98），该函数将返回 **_HEAPOK**并将**errno**设置为**ENOSYS**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
