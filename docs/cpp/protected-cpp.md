---
title: chronione (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: protected_cpp
dev_langs: C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1996ce93be7fc5f722936dee0f04923cafa5d767
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="protected-c"></a>chronione (C++)
## <a name="syntax"></a>Składnia  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Uwagi  
 `protected` — Słowo kluczowe określa dostęp do elementów członkowskich klasy w *listy członków* do następnego specyfikator dostępu (**publicznego** lub `private`) lub na końcu definicji klasy. Elementy członkowskie klasy zadeklarowani jako `protected` mogą być używani tylko przez następujące:  
  
-   Funkcje członkowskie klasy, która pierwotnie zadeklarowała tych elementów członkowskich.  
  
-   Przyjaciół klasy, która pierwotnie zadeklarowała tych elementów członkowskich.  
  
-   Klasy pochodne z publicznym lub chronionym dostępem do klasy, która pierwotnie zadeklarowała te elementy członkowskie.  
  
-   Bezpośrednie klasy pochodne prywatnie, które także mają prywatny dostęp do chronionych elementów członkowskich.  
  
 Gdy nazwę klasy podstawowej poprzedza słowo kluczowe `protected`, określa ono, że publiczne i chronione elementy członkowskie klasy podstawowej są chronionymi elementami członkowskimi klas pochodnych.  
  
 Chronione elementy członkowskie nie są jako prywatny jako `private` elementów członkowskich, które są dostępne tylko dla elementów członkowskich klasy, w której zostały zgłoszone, ale nie są one jako publiczną jako **publicznego** elementów członkowskich, które są dostępne w żadnych funkcji.  
  
 Elementy członkowskie, które także są deklarowane jako chronione **statycznych** są dostępne dla dowolnej funkcji friend lub elementu członkowskiego klasy pochodnej. Elementy członkowskie, które nie są deklarowane jako chronione **statycznych** są dostępne dla znajomych i funkcje Członkowskie w klasie pochodnej tylko za pośrednictwem wskaźnik do odwołania do, lub obiekt klasy pochodnej.  
  
 Powiązane informacje, zobacz [friend](../cpp/friend-cpp.md), [publicznego](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), a tabelą dostęp do elementu członkowskiego w [kontrolowanie dostępu do członków klasy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specyficzne dla /clr  
 W typach CLR C++ dostępu specyfikator słowa kluczowe (**publicznego**, `private`, i `protected`) mogą wpłynąć na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontroli dostępu elementu członkowskiego](member-access-control-cpp.md).  
  
> [!NOTE]
>  Skompilowane pliki z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).  
  
## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr  
  
## <a name="example"></a>Przykład  
  
```  
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
 [Kontrolowanie dostępu do członków klasy](member-access-control-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)