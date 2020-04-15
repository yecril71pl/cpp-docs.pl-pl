---
title: publiczne (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376049"
---
# <a name="public-c"></a>publiczne (C++)

## <a name="syntax"></a>Składnia

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Uwagi

Poprzedzając listę członków klasy, **publiczne** słowo kluczowe określa, że te elementy członkowskie są dostępne z dowolnej funkcji. Dotyczy to wszystkich członków zadeklarowanych do następnego specyfikatora dostępu lub na końcu klasy.

Poprzedzając nazwę klasy podstawowej, **public** — słowo kluczowe określa, że publiczne i chronione elementy członkowskie klasy podstawowej są odpowiednio publicznymi i chronionymi członkami klasy pochodnej.

Domyślny dostęp członków w klasie jest prywatny. Domyślny dostęp członków w strukturze lub związku jest publiczny.

Domyślny dostęp do klasy podstawowej jest prywatny dla klas i publiczny dla struktur. Związki zawodowe nie mogą mieć klas podstawowych.

Aby uzyskać więcej informacji, zobacz [prywatne,](../cpp/private-cpp.md) [chronione,](../cpp/protected-cpp.md) [przyjaciel](../cpp/friend-cpp.md)i tabela dostępu do członków w [obszarze Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR specyfikator dostępu języka C++**(publiczny,** **prywatny**i **chroniony)** może mieć wpływ na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Kontrola dostępu do członków](member-access-control-cpp.md).

> [!NOTE]
> To zachowanie nie ma wpływu na pliki skompilowane za pomocą [/LN.](../build/reference/ln-create-msil-module.md) W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

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

## <a name="see-also"></a>Zobacz też

[Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
