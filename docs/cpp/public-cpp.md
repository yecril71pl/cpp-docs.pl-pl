---
title: publiczne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- public_cpp
dev_langs:
- C++
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff41d2b12f43deabd82538a3e2fb10eb35ead16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="public-c"></a>publiczne (C++)
## <a name="syntax"></a>Składnia  
  
```  
public:  
   [member-list]  
public base-class  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy poprzedzającym listę elementów członkowskich klasy, **publicznego** — słowo kluczowe Określa, że te elementy członkowskie są dostępne z dowolnej funkcji. Dotyczy to wszystkich elementów członkowskich zadeklarowanych do następnego specyfikator dostępu lub na końcu tej klasy.  
  
 Gdy poprzedzającej nazwę klasy podstawowej, **publicznego** — słowo kluczowe Określa, czy publiczne i chronione elementy członkowskie klasy podstawowej są publiczne i chronione elementy członkowskie, odpowiednio klasy pochodnej.  
  
 Domyślny dostęp do elementów członkowskich w klasie jest prywatny. Dostęp do domyślnej elementów członkowskich struktury lub Unii jest publiczny.  
  
 Dostęp do domyślnej klasy podstawowej jest prywatne dla klas i publiczne dla struktury. Unie nie może mieć klas podstawowych.  
  
 Aby uzyskać więcej informacji, zobacz [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md), a tabelą dostęp do elementu członkowskiego w [kontrolowanie dostępu do członków klasy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specyficzne dla /clr  
 W typach CLR C++ dostępu specyfikator słowa kluczowe (**publicznego**, `private`, i `protected`) mogą wpłynąć na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontroli dostępu elementu członkowskiego](member-access-control-cpp.md).  
  
> [!NOTE]
>  Skompilowane pliki z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).  
  
## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr  
  
## <a name="example"></a>Przykład  
  
```  
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
 [Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)