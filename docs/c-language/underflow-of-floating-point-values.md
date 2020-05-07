---
title: Niedopełnienie wartości zmiennoprzecinkowych
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344062"
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych

**ANSI 4.5.1** Czy funkcja matematyki ustawia wyrażenie `errno` liczby całkowitej na wartość makra `ERANGE` w przypadku błędów zakresu niedopełnienia

Niedomiarowa zmiennoprzecinkowa nie ustawia wyrażenia `errno` na. `ERANGE` Gdy wartość zbliża się do zera i ostatecznie podpływa, wartość jest równa zero.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
