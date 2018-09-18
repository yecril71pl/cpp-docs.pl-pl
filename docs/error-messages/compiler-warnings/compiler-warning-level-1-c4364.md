---
title: Kompilator ostrzeżenie (poziom 1) C4364 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e37c7f37e1b51296bd5c3ae2cbdb85a93326f027
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087256"
---
# <a name="compiler-warning-level-1-c4364"></a>Kompilator ostrzeżenie (poziom 1) C4364

\##using dla zestawu 'Plik' poprzednio widziano w location(line_number) bez atrybutu as_friend; nie zastosowano as_friend

A `#using` dyrektywa została powtórzona pliku określonych metadanych, ale `as_friend` kwalifikatora nie jest używany w pierwszym wystąpieniu; Kompilator zignoruje drugi `as_friend`.

Aby uzyskać więcej informacji, zobacz [przyjazne zestawy (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4364.

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```