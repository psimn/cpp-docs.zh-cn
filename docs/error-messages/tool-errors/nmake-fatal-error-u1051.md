---
title: NMAKE 错误 U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367195"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 错误 U1051

内存不足

NMAKE 用尽了内存中，由于生成文件太大或太复杂，包括虚拟内存。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 释放一些磁盘空间。

1. 增加 Windows NT 分页文件或 Windows 交换文件的大小。

1. 如果仅使用生成文件的一部分，则将生成文件划分为单独的文件或使用 **！如果**预处理指令以限制 NMAKE 必须处理量。 **！如果**指令包含 **！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！其他** `IFDEF`，和 **！其他** `IFNDEF`。