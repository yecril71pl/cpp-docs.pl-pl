---
title: Kompilator ostrzeżenie (poziom 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 9357088106a45026eae543f8627ea59988e73995
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818508"
---
# <a name="compiler-warning-level-3-c4641"></a>Kompilator ostrzeżenie (poziom 3) C4641

Komentarz dokumentu XML ma niejednoznaczne odwołanie

Kompilator nie może jednoznacznie rozpoznać odwołania. Aby rozwiązać tego ostrzeżenia, należy określić informacje o parametrach, trzeba przywołać jednoznaczne.

Aby uzyskać więcej informacji, zobacz [dokumentacji XML](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4641.

```
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```