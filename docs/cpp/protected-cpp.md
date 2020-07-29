---
title: chronione (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 25b25447737a075bcf4f02f1c3049c996fb4c678
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227169"
---
# <a name="protected-c"></a>chronione (C++)

## <a name="syntax"></a>Składnia

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Uwagi

**`protected`** Słowo kluczowe Określa dostęp do elementów członkowskich klasy na *liście składowych* do następnego specyfikatora dostępu ( **`public`** lub **`private`** ) lub końca definicji klasy. Składowe klasy zadeklarowane jako **`protected`** mogą być używane tylko przez następujące:

- Funkcje składowe klasy, która pierwotnie zadeklarowała te składowe.

- Przyjaciół klasy, która pierwotnie zadeklarowała te składowe.

- Klasy pochodne z publicznym lub chronionym dostępem do klasy, która pierwotnie zadeklarowała te składowe.

- Bezpośrednie klasy pochodne prywatnie, które także mają prywatny dostęp do chronionych składowych.

Gdy poprzedzająca nazwę klasy bazowej, **`protected`** słowo kluczowe Określa, że publiczne i chronione składowe klasy bazowej są chronionymi elementami członkowskimi klas pochodnych.

Chronione elementy członkowskie nie są jako **`private`** elementy członkowskie, które są dostępne tylko dla elementów członkowskich klasy, w których są zadeklarowane, ale nie są jako **`public`** elementy publiczne, które są dostępne w dowolnej funkcji.

Chronione elementy członkowskie, które są również zadeklarowane jako **`static`** dostępne dla każdej znajomej lub funkcji członkowskiej klasy pochodnej. Chronione składowe, które nie są zadeklarowane jako **`static`** dostępne dla znajomych i funkcji Członkowskich w klasie pochodnej tylko za pomocą wskaźnika do, odwołania do lub obiektu klasy pochodnej.

Aby uzyskać powiązane informacje, zobacz [zaprzyjaźniona](../cpp/friend-cpp.md), [publiczna](../cpp/public-cpp.md), [prywatna](../cpp/private-cpp.md)i tabela dostępu do elementów członkowskich [kontrolująca dostęp do elementów członkowskich klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR słowa kluczowe specyfikator dostępu języka C++ ( **`public`** , **`private`** , i **`protected`** ) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Access Control elementu członkowskiego](member-access-control-cpp.md).

> [!NOTE]
> Takie zachowanie nie ma wpływ na pliki skompilowane za pomocą [/LN](../build/reference/ln-create-msil-module.md) . W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr

## <a name="example"></a>Przykład

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Zobacz także

[Kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
