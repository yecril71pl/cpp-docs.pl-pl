---
title: dostęp (CRT)
ms.date: 12/16/2019
api_name:
- access
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
- access
helpviewer_keywords:
- access function
ms.assetid: 65197793-bd0a-41c3-9c29-18de2d95d9a6
ms.openlocfilehash: 0f218b8de79ea174d935097c6ecbe4cf303db7a2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300121"
---
# <a name="access-crt"></a>dostęp (CRT)

Nazwa funkcji platformy POSIX wdrożonej przez firmę Microsoft `access` jest przestarzałym aliasem dla funkcji [_access](access-waccess.md) . Domyślnie generuje [Ostrzeżenie kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwa jest przestarzała, ponieważ nie jest zgodna z regułami standard C dla nazw specyficznych dla implementacji. Jednak funkcja jest nadal obsługiwana.

Zalecamy używanie [_access](access-waccess.md) lub funkcji [_access_s](access-s-waccess-s.md) ulepszonych z zabezpieczeniami. Możesz również nadal używać tej nazwy funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
