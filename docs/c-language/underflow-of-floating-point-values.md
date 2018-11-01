---
title: Niedopełnienie wartości zmiennoprzecinkowych
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: cd4aadc5ab006b79a43e31348fa101d40e8ca03a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477366"
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych

**ANSI 4.5.1** ustawionego wyrażenia typu całkowitego funkcje matematyce `errno` wartość makra `ERANGE` na niedopełnienie zakres błędów

Niedopełnienie zmiennoprzecinkowe nie ustawia wyrażenie `errno` do `ERANGE`. Wartość koloru zbliża się zero, a ostatecznie niedopełnienie, wartość jest równa zero.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)