---
title: Błąd kompilatora C2873 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf0cc5663d81d6c1e7ad6a9f1a5f7ca167f12909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049907"
---
# <a name="compiler-error-c2873"></a>Błąd kompilatora C2873

'symbol': symbol nie może zostać użyty w deklaracji using

A `using` brakuje dyrektywy [przestrzeni nazw](../../cpp/namespaces-cpp.md) — słowo kluczowe. To powoduje, że kompilator błędnie interpretuje kod jako [użycie — deklaracja](../../cpp/using-declaration.md) zamiast [użycie dyrektywy](../../cpp/namespaces-cpp.md#using_directives).