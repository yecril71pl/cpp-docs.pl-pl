---
title: prywatne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d064a1154126878ce75d9dd08d88fa9d65f83c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028561"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Składnia

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Uwagi

Gdy poprzedzającej listę elementów członkowskich klasy **prywatnej** — słowo kluczowe Określa, że te elementy członkowskie są dostępne tylko z funkcji elementów członkowskich i przyjaciół klasy. Dotyczy to wszystkich elementów członkowskich zadeklarowana aż do następnego specyfikatora dostępu lub na końcu tej klasy.

Gdy nazwę klasy podstawowej poprzedza **prywatnej** — słowo kluczowe Określa, że publiczne i chronione składowe klasy podstawowej są prywatne składowe klasy pochodnej.

Domyślny dostęp do elementów składowych w klasie jest prywatny. Dostęp do domyślnej elementów członkowskich struktury lub Unii jest publiczny.

Dostęp do domyślnej klasy bazowej są prywatne dla klas i publiczne dla struktur. Unie nie może mieć klas bazowych.

Aby uzyskać powiązane informacje, zobacz [friend](../cpp/friend-cpp.md), [publicznych](../cpp/public-cpp.md), [chronione](../cpp/protected-cpp.md)i tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR, kluczowe specyfikatorów dostępu C++ (**publicznych**, **prywatnej**, i **chronione**) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontrola dostępu do składowych](member-access-control-cpp.md).

> [!NOTE]
>  Pliki skompilowane z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

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

## <a name="see-also"></a>Zobacz także

[Kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)