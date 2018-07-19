---
title: publiczne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- public_cpp
dev_langs:
- C++
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa6d4abf9423df29d59f375b825a815404a3c76c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947911"
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
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)