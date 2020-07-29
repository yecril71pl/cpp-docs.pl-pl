---
title: Błąd kompilatora C2873
ms.date: 11/04/2016
f1_keywords:
- C2873
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
ms.openlocfilehash: b1eabf71c4338a9ede275b58fd12f1be1a25029d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228885"
---
# <a name="compiler-error-c2873"></a>Błąd kompilatora C2873

"symbol": symbol nie może być używany w deklaracji using

W **`using`** dyrektywie brakuje słowa kluczowego [przestrzeni nazw](../../cpp/namespaces-cpp.md) . Powoduje to, że kompilator błędnie interpretuje kod jako [deklarację using](../../cpp/using-declaration.md) zamiast [dyrektywy using](../../cpp/namespaces-cpp.md#using_directives).
