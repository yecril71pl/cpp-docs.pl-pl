---
title: lfind
ms.date: 12/16/2019
api_name:
- lfind
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
- lfind
helpviewer_keywords:
- lfind function
ms.assetid: 2528e787-94b6-4740-8a8d-6efc276d1f42
ms.openlocfilehash: 7a1ac69bbebfea45345c7dae17b18f02b84228cd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300915"
---
# <a name="lfind"></a>lfind

Nazwa funkcji platformy POSIX wdrożonej przez firmę Microsoft `lfind` jest przestarzałym aliasem dla funkcji [_lfind](lfind.md) . Domyślnie generuje [Ostrzeżenie kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwa jest przestarzała, ponieważ nie jest zgodna z regułami standard C dla nazw specyficznych dla implementacji. Jednak funkcja jest nadal obsługiwana.

Zalecamy użycie funkcji _lfind_s [_lfind](lfind.md) lub ulepszonej zabezpieczeniami [](lfind-s.md) . Możesz również nadal używać tej nazwy funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
