---
title: Błąd kompilatora C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: e29e536bf89aef887dc043327e4b4596703d0538
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775195"
---
# <a name="compiler-error-c3675"></a>Błąd kompilatora C3675

'Funkcja': jest zarezerwowana, ponieważ "właściwość" jest zdefiniowana.

Kiedy Deklarujesz właściwości prostej, kompilator generuje get i metody dostępu set, a te nazwy są obecne w zakresie programu.  Nazwy generowane przez kompilator są tworzone przez dołączenie rzeczoznawcy i Pobierz nazwę właściwości.  W związku z tym nie można zadeklarować funkcji z taką samą nazwę jak metodach dostępu generowanych przez kompilator.

Zobacz [właściwość](../../extensions/property-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3675.

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```