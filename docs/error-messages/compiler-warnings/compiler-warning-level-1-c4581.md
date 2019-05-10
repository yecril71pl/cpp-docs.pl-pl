---
title: Kompilator ostrzeżenie (poziom 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 9868d33538a1f56906455f2b1772b53eb3a7734d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447101"
---
# <a name="compiler-warning-level-1-c4581"></a>Kompilator ostrzeżenie (poziom 1) C4581

zachowanie przestarzałe: "ciąg1" zastąpione "ciąg2", aby przetwarzać atrybut

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual Studio 2005: Sprawdzanie parametrów dla wizualizacji C++ atrybutów.

W poprzednich wersjach wartości atrybutów zostały zaakceptowane, czy zostały one ujęta w znaki cudzysłowu. Jeśli wartość jest wyliczeniem, nie muszą być ujęte w znaki cudzysłowu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4581.

```
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```