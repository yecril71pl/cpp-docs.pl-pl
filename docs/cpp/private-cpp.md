---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: d6dc1ca309c096a4f5e857ade3d7550749991f3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366206"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Składnia

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Uwagi

Poprzedzając listę członków klasy, **prywatne** słowo kluczowe określa, że te elementy członkowskie są dostępne tylko z funkcji członkowskich i znajomych klasy. Dotyczy to wszystkich członków zadeklarowanych do następnego specyfikatora dostępu lub na końcu klasy.

Poprzedzając nazwę klasy podstawowej, **prywatne** słowo kluczowe określa, że publiczne i chronione elementy członkowskie klasy podstawowej są członkami prywatnymi klasy pochodnej.

Domyślny dostęp członków w klasie jest prywatny. Domyślny dostęp członków w strukturze lub związku jest publiczny.

Domyślny dostęp do klasy podstawowej jest prywatny dla klas i publiczny dla struktur. Związki zawodowe nie mogą mieć klas podstawowych.

Aby uzyskać powiązane informacje, zobacz [znajomego,](../cpp/friend-cpp.md) [publiczne,](../cpp/public-cpp.md) [chronione](../cpp/protected-cpp.md)i tabela dostępu do członków w [obszarze Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR specyfikator dostępu języka C++**(publiczny,** **prywatny**i **chroniony)** może mieć wpływ na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Kontrola dostępu do członków](member-access-control-cpp.md).

> [!NOTE]
> To zachowanie nie ma wpływu na pliki skompilowane za pomocą [/LN.](../build/reference/ln-create-msil-module.md) W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr

## <a name="example"></a>Przykład

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>Zobacz też

[Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
