---
title: Błąd kompilatora C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 8dfc462cc0eedfff1661ae38f79bbb79c5c1a8fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281758"
---
# <a name="compiler-error-c2811"></a>Błąd kompilatora C2811

'Typ1': nie może dziedziczyć po "type2" ref klasy mogą dziedziczyć tylko z klasy interfejsu lub klasy referencyjnej

Próbowano użyć niezarządzane klasy jako klasę bazową dla klasy zarządzanej.

Poniższy przykład spowoduje wygenerowanie C2811:

```
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```