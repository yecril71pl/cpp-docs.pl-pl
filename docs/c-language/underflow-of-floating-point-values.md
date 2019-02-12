---
title: Niedopełnienie wartości zmiennoprzecinkowych
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149935"
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych

**ANSI 4.5.1** ustawionego wyrażenia typu całkowitego funkcje matematyce `errno` wartość makra `ERANGE` na niedopełnienie zakres błędów

Niedopełnienie zmiennoprzecinkowe nie ustawia wyrażenie `errno` do `ERANGE`. Wartość koloru zbliża się zero, a ostatecznie niedopełnienie, wartość jest równa zero.

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
