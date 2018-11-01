---
title: Kompilator ostrzeżenie (poziom 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643602"
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