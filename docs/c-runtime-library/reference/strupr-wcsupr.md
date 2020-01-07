---
title: strupr, wcsupr
ms.date: 12/16/2019
api_name:
- strupr
- wcsupr
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
- strupr
- wcsupr
helpviewer_keywords:
- strupr function
- wcsupr function
ms.assetid: 17dfe1cd-3b09-4702-9f89-2207f44953e6
ms.openlocfilehash: ce51eb4f7eeb80766e19cfdb4a39a3a7dd50d85a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300459"
---
# <a name="strupr-wcsupr"></a>strupr, wcsupr

Nazwy funkcji specyficznych dla firmy Microsoft `strupr` i `wcsupr` są przestarzałe aliasy dla funkcji [_strupr i _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) . Domyślnie generują [ostrzeżenia kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwy są przestarzałe, ponieważ nie przestrzegają standardowych reguł języka C dla nazw specyficznych dla implementacji. Jednak funkcje są nadal obsługiwane.

Zalecamy używanie [_strupr i _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) lub [_strupr_s oraz funkcji _wcsupr_s](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md) ulepszonych z zabezpieczeniami. Możesz również nadal używać tych nazw funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
