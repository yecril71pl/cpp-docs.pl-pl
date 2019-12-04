---
title: Błąd kompilatora C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 95d6385cea95f22bbb9bbb9197dace22bd1a3adf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755255"
---
# <a name="compiler-error-c2811"></a>Błąd kompilatora C2811

"type1": nie można dziedziczyć po elemencie "type2", Klasa referencyjna może dziedziczyć tylko z klasy referencyjnej lub klasy interfejsu

Podjęto próbę użycia niezarządzanej klasy jako klasy bazowej dla zarządzanej klasy.

Poniższy przykład generuje C2811:

```cpp
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```
