---
title: publiczne (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 0f6b58896cbcb11901721125f9b1a32a99acb357
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227143"
---
# <a name="public-c"></a>publiczne (C++)

## <a name="syntax"></a>Składnia

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Uwagi

Po powyższym liście elementów członkowskich klasy, **`public`** słowo kluczowe Określa, że te elementy członkowskie są dostępne z dowolnej funkcji. Dotyczy to wszystkich członków zadeklarowanych do następnego specyfikatora dostępu lub końca klasy.

Gdy poprzedzająca nazwę klasy bazowej, **`public`** słowo kluczowe Określa, że publiczne i chronione składowe klasy bazowej są odpowiednio publicznymi i chronionymi elementami członkowskimi klasy pochodnej.

Domyślny dostęp do elementów członkowskich w klasie jest prywatny. Domyślny dostęp do elementów członkowskich w strukturze lub Unii jest publiczny.

Domyślny dostęp klasy bazowej jest prywatny dla klas i publicznych dla struktur. Unia nie może mieć klas bazowych.

Aby uzyskać więcej informacji, zobacz sekcję [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md), [Friend](../cpp/friend-cpp.md)i dostęp do elementów członkowskich w celu [kontrolowania dostępu do elementów członkowskich klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR słowa kluczowe specyfikator dostępu języka C++ ( **`public`** , **`private`** , i **`protected`** ) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Access Control elementu członkowskiego](member-access-control-cpp.md).

> [!NOTE]
> Takie zachowanie nie ma wpływ na pliki skompilowane za pomocą [/LN](../build/reference/ln-create-msil-module.md) . W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr

## <a name="example"></a>Przykład

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>Zobacz także

[Kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
