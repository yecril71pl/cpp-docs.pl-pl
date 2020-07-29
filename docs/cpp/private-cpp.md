---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 3b9df2ee2abcaca1c7c11c08ef73ae795a84310d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232251"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Składnia

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Uwagi

Po powyższym liście elementów członkowskich klasy, **`private`** słowo kluczowe Określa, że te składowe są dostępne tylko z funkcji składowych i przyjaciół klasy. Dotyczy to wszystkich członków zadeklarowanych do następnego specyfikatora dostępu lub końca klasy.

Gdy poprzedzająca nazwę klasy bazowej, **`private`** słowo kluczowe Określa, że publiczne i chronione składowe klasy bazowej są prywatnymi elementami członkowskimi klasy pochodnej.

Domyślny dostęp do elementów członkowskich w klasie jest prywatny. Domyślny dostęp do elementów członkowskich w strukturze lub Unii jest publiczny.

Domyślny dostęp klasy bazowej jest prywatny dla klas i publicznych dla struktur. Unia nie może mieć klas bazowych.

Aby uzyskać powiązane informacje, zobacz [zaprzyjaźniona](../cpp/friend-cpp.md), [publiczna](../cpp/public-cpp.md), [chroniona](../cpp/protected-cpp.md)i tabela dostępu do elementów członkowskich w celu [kontrolowania dostępu do składowych klasy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specyficzne dla /clr

W typach CLR słowa kluczowe specyfikator dostępu języka C++ ( **`public`** , **`private`** , i **`protected`** ) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [Access Control elementu członkowskiego](member-access-control-cpp.md).

> [!NOTE]
> Takie zachowanie nie ma wpływ na pliki skompilowane za pomocą [/LN](../build/reference/ln-create-msil-module.md) . W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).

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
