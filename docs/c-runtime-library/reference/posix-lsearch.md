---
title: lsearch
ms.date: 12/16/2019
api_name:
- lsearch
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
- lsearch
helpviewer_keywords:
- lsearch function
ms.assetid: 130da3fc-904a-4375-b0ab-79bfea8a455f
ms.openlocfilehash: a068b6500de8a1a795f5494ac12afa0e5ca08544
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300888"
---
# <a name="lsearch"></a>lsearch

Nazwa funkcji platformy POSIX wdrożonej przez firmę Microsoft `lsearch` jest przestarzałym aliasem dla funkcji [_lsearch](lsearch.md) . Domyślnie generuje [Ostrzeżenie kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwa jest przestarzała, ponieważ nie jest zgodna z regułami standard C dla nazw specyficznych dla implementacji. Jednak funkcja jest nadal obsługiwana.

Zalecamy użycie funkcji _lsearch_s [_lsearch](lsearch.md) lub ulepszonej zabezpieczeniami [](lsearch-s.md) . Możesz również nadal używać tej nazwy funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
