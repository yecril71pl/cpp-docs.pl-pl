---
title: publiczne (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 24cc4dd3cd7e0c893664339e7ad83383839b0b11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244479"
---
# <a name="public-c"></a>publiczne (C++)

## <a name="syntax"></a>Składnia

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Uwagi

Gdy poprzedzającej listę elementów członkowskich klasy **publicznych** — słowo kluczowe Określa, że te elementy członkowskie są dostępne z dowolnej funkcji. Dotyczy to wszystkich elementów członkowskich zadeklarowana aż do następnego specyfikatora dostępu lub na końcu tej klasy.

Gdy nazwę klasy podstawowej poprzedza **publicznych** — słowo kluczowe Określa, że publiczne i chronione składowe klasy podstawowej są publiczne i chronione składowe, odpowiednio, klasy pochodnej.

Domyślny dostęp do elementów składowych w klasie jest prywatny. Dostęp do domyślnej elementów członkowskich struktury lub Unii jest publiczny.

Dostęp do domyślnej klasy bazowej są prywatne dla klas i publiczne dla struktur. Unie nie może mieć klas bazowych.

Aby uzyskać więcej informacji, zobacz [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)i tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md) .

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR, kluczowe specyfikatorów dostępu C++ (**publicznych**, **prywatnej**, i **chronione**) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontrola dostępu do składowych](member-access-control-cpp.md).

> [!NOTE]
>  Pliki skompilowane z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

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