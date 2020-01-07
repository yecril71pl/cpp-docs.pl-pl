---
title: y0, y1, yn
ms.date: 12/16/2019
api_name:
- y1
- yn
- y0
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- yn
- y1
- y0
helpviewer_keywords:
- y0 function
- y1 function
- yn function
ms.assetid: e14215f3-53d4-4ae8-816e-4c1ec2019316
ms.openlocfilehash: ade2978d9a052b481c8250933257cfa33493860f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301720"
---
# <a name="y0-y1-yn"></a>y0, y1, yn

Zaimplementowana przez firmę Microsoft nazwa funkcji POSIX `y0`, `y1`i `yn` są przestarzałe aliasy dla funkcji [_y0, _y1 i _yn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Domyślnie generują [ostrzeżenia kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwy są przestarzałe, ponieważ nie przestrzegają standardowych reguł języka C dla nazw specyficznych dla implementacji. Jednak funkcje są nadal obsługiwane.

Zalecamy używanie [_y0, _y1 i _yn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Możesz również nadal używać tych nazw funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
