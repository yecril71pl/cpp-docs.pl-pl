---
title: memicmp
ms.date: 12/16/2019
api_name:
- memicmp
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
- memicmp
helpviewer_keywords:
- memicmp function
ms.assetid: 45362e9c-7c64-41e9-92bb-7d4999a8635b
ms.openlocfilehash: 82edf102239a6f345b22d25fbab0cd3cfdd8c40d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301031"
---
# <a name="memicmp"></a>memicmp

Nazwa funkcji specyficznej dla firmy Microsoft `memicmp` jest przestarzałym aliasem dla funkcji [_memicmp](memicmp-memicmp-l.md) . Domyślnie generuje [Ostrzeżenie kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwa jest przestarzała, ponieważ nie jest zgodna z regułami standard C dla nazw specyficznych dla implementacji. Jednak funkcja jest nadal obsługiwana.

Zalecamy używanie [_memicmp](memicmp-memicmp-l.md) . Możesz również nadal używać tej nazwy funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
