---
title: chronione (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317268"
---
# <a name="protected-c"></a>chronione (C++)

## <a name="syntax"></a>Składnia

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Uwagi

**Chronione** słowo kluczowe określa dostęp do członków klasy na *liście elementów członkowskich* do następnego specyfikatora dostępu **(publicznego** lub **prywatnego)** lub końca definicji klasy. Elementy członkowskie klasy **zadeklarowane** jako chronione mogą być używane tylko przez następujące elementy:

- Funkcje składowe klasy, która pierwotnie zadeklarowała te składowe.

- Przyjaciół klasy, która pierwotnie zadeklarowała te składowe.

- Klasy pochodne z publicznym lub chronionym dostępem do klasy, która pierwotnie zadeklarowała te składowe.

- Bezpośrednie klasy pochodne prywatnie, które także mają prywatny dostęp do chronionych składowych.

Poprzedzając nazwę klasy podstawowej, **chronione** słowo kluczowe określa, że publiczne i chronione elementy członkowskie klasy podstawowej są chronionymi członkami jej klas pochodnych.

Chronione elementy członkowskie nie są tak prywatne jak **prywatne** członków, które są dostępne tylko dla członków klasy, w której są zadeklarowane, ale nie są one tak publiczne, jak **członków publicznych,** które są dostępne w dowolnej funkcji.

Chronione elementy członkowskie, które są również zadeklarowane jako **statyczne** są dostępne dla dowolnego znajomego lub elementu członkowskiego funkcji klasy pochodnej. Chronione elementy członkowskie, które nie są zadeklarowane jako **statyczne** są dostępne dla znajomych i funkcji członkowskich w klasie pochodnej tylko za pośrednictwem wskaźnika do, odwołania do lub obiektu klasy pochodnej.

Aby uzyskać powiązane informacje, zobacz [znajomego,](../cpp/friend-cpp.md) [publicznego,](../cpp/public-cpp.md) [prywatnego](../cpp/private-cpp.md)i tabeli dostępu do członków w [obszarze Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR specyfikator dostępu języka C++**(publiczny,** **prywatny**i **chroniony)** może mieć wpływ na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Kontrola dostępu do członków](member-access-control-cpp.md).

> [!NOTE]
> To zachowanie nie ma wpływu na pliki skompilowane za pomocą [/LN.](../build/reference/ln-create-msil-module.md) W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

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

## <a name="see-also"></a>Zobacz też

[Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
