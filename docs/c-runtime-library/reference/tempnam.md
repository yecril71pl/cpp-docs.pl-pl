---
title: tempnam
ms.date: 12/16/2019
api_name:
- tempnam
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
- tempnam
helpviewer_keywords:
- tempnam function
ms.assetid: 42446733-f131-470f-b4d0-96918becab11
ms.openlocfilehash: d4c7945b68a0cd8dd99fcf15e7484aad877c401d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300329"
---
# <a name="tempnam"></a>tempnam

Nazwa funkcji platformy POSIX wdrożonej przez firmę Microsoft `tempnam` jest przestarzałym aliasem dla funkcji [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) . Domyślnie generuje [Ostrzeżenie kompilatora (poziom 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Nazwa jest przestarzała, ponieważ nie jest zgodna z regułami standard C dla nazw specyficznych dla implementacji. Jednak funkcja jest nadal obsługiwana.

Zalecamy używanie [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) . Możesz również nadal używać tej nazwy funkcji i wyłączyć ostrzeżenie. Aby uzyskać więcej informacji, zobacz Wyłączanie [nazw funkcji](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names) [Warning](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) i POSIX.
