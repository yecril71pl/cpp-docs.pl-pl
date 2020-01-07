---
title: strdup, wcsdup
ms.date: 12/16/2019
api_name:
- wcsdup
- strdup
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
- wcsdup
- strdup
helpviewer_keywords:
- wcsdup function
- strdup function
ms.assetid: c9ac0935-b525-4e95-8a64-396fc7e34ee9
ms.openlocfilehash: e381a1933a6b657108a66053bad1c7ff795c1a29
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300524"
---
# <a name="strdup-wcsdup"></a>strdup, wcsdup

Zaimplementowana przez firmę Microsoft nazwa funkcji POSIX `strdup` i `wcsdup` są przestarzałe aliasy dla funkcji [_strdup i _wcsdup](strdup-wcsdup-mbsdup.md) . Domyślnie generują [ostrzeżenia kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwy są przestarzałe, ponieważ nie przestrzegają standardowych reguł języka C dla nazw specyficznych dla implementacji. Jednak funkcje są nadal obsługiwane.

Zalecamy używanie [_strdup i _wcsdup](strdup-wcsdup-mbsdup.md) . Możesz również nadal używać tych nazw funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
