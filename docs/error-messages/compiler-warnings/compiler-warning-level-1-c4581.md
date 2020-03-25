---
title: Ostrzeżenie kompilatora (poziom 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 491121bc236c54ce5b74c76abfa6a650ff7a99ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162169"
---
# <a name="compiler-warning-level-1-c4581"></a>Ostrzeżenie kompilatora (poziom 1) C4581

przestarzałe zachowanie: element "" ciąg1 "" został zastąpiony przez "ciąg2" atrybutem procesu

Ten błąd może być wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio 2005: sprawdzanie parametrów wizualizacji C++ .

W poprzednich wersjach wartości atrybutów zostały zaakceptowane niezależnie od tego, czy zostały ujęte w cudzysłów. Jeśli wartość jest wyliczeniem, nie może być ujęta w cudzysłów.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4581.

```cpp
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
