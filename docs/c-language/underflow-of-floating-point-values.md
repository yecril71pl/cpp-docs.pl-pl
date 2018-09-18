---
title: Niedopełnienie wartości zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 980000932c8cc4a6be3798976d273dae8608324f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089167"
---
# <a name="underflow-of-floating-point-values"></a>Niedopełnienie wartości zmiennoprzecinkowych

**ANSI 4.5.1** ustawionego wyrażenia typu całkowitego funkcje matematyce `errno` wartość makra `ERANGE` na niedopełnienie zakres błędów

Niedopełnienie zmiennoprzecinkowe nie ustawia wyrażenie `errno` do `ERANGE`. Wartość koloru zbliża się zero, a ostatecznie niedopełnienie, wartość jest równa zero.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)