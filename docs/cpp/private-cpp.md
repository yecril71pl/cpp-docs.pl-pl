---
title: prywatne (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baa3a23eacc8428bcbeb6ee5a88a835ff193ee02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>Składnia  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy poprzedzającym listę elementów członkowskich klasy `private` — słowo kluczowe Określa, że te elementy członkowskie są dostępne tylko z funkcji Członkowskich i znajomych klasy. Dotyczy to wszystkich elementów członkowskich zadeklarowanych do następnego specyfikator dostępu lub na końcu tej klasy.  
  
 Gdy poprzedzającej nazwę klasy podstawowej, `private` — słowo kluczowe Określa, że publiczne i chronione elementy członkowskie klasy podstawowej są prywatne elementy członkowskie klasy pochodnej.  
  
 Domyślny dostęp do elementów członkowskich w klasie jest prywatny. Dostęp do domyślnej elementów członkowskich struktury lub Unii jest publiczny.  
  
 Dostęp do domyślnej klasy podstawowej jest prywatne dla klas i publiczne dla struktury. Unie nie może mieć klas podstawowych.  
  
 Powiązane informacje, zobacz [friend](../cpp/friend-cpp.md), [publicznego](../cpp/public-cpp.md), [chronione](../cpp/protected-cpp.md), a tabelą dostęp do elementu członkowskiego w [kontrolowanie dostępu do członków klasy](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>Specyficzne dla /clr  
 W typach CLR C++ dostępu specyfikator słowa kluczowe (**publicznego**, `private`, i `protected`) mogą wpłynąć na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontroli dostępu elementu członkowskiego](member-access-control-cpp.md).  
  
> [!NOTE]
>  Skompilowane pliki z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).  
  
## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr  
  
## <a name="example"></a>Przykład  
  
```  
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
 [Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)