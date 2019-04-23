---
title: Błąd kompilatora C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: e29e536bf89aef887dc043327e4b4596703d0538
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778881"
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