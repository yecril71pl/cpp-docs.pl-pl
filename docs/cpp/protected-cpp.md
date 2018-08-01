---
title: chronione (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68cf69cd0c14d56c75a2c67d4369264e7a2ee440
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406175"
---
# <a name="protected-c"></a>chronione (C++)
## <a name="syntax"></a>Składnia  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Uwagi  
 **Chronione** — słowo kluczowe określa dostęp do składowych klasy w *listę elementów członkowskich* aż do następnego specyfikatora dostępu (**publicznych** lub **prywatne**) lub na końcu definicji klasy. Składowe klasy zadeklarowane jako **chronione** mogą być używane tylko przez następujące czynności:  
  
-   Funkcje składowe klasy, która pierwotnie zadeklarowała te składowe.  
  
-   Przyjaciół klasy, która pierwotnie zadeklarowała te składowe.  
  
-   Klasy pochodne z publicznym lub chronionym dostępem do klasy, która pierwotnie zadeklarowała te składowe.  
  
-   Bezpośrednie klasy pochodne prywatnie, które także mają prywatny dostęp do chronionych składowych.  
  
 Gdy nazwę klasy podstawowej poprzedza **chronione** — słowo kluczowe Określa, że publiczne i chronione składowe klasy podstawowej są chronionymi składowymi jej klas pochodnych.  
  
 Chronione składowe nie są tak prywatne jak **prywatnej** elementów członkowskich, które są dostępne tylko dla składowych klasy, w którym są one zadeklarowane, ale nie są tak publiczne jak **publicznych** elementów członkowskich, które są dostępne w żadnej funkcji.  
  
 Chronione składowe, które są również deklarowane jako **statyczne** są dostępne dla dowolnego friend lub funkcji składowej klasy pochodnej. Chronione składowe, które nie są deklarowane jako **statyczne** są dostępne dla funkcji zaprzyjaźnionych i funkcji składowych w klasie pochodnej tylko przez wskaźnik, odwołanie lub obiekt klasy pochodnej.  
  
 Aby uzyskać powiązane informacje, zobacz [friend](../cpp/friend-cpp.md), [publicznych](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md)i tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specyficzne dla /clr  
 W typach CLR, kluczowe specyfikatorów dostępu C++ (**publicznych**, **prywatnej**, i **chronione**) mogą wpływać na widoczność typów i metod w odniesieniu do zestawów. Aby uzyskać więcej informacji, zobacz [kontrola dostępu do składowych](member-access-control-cpp.md).  
  
> [!NOTE]
>  Pliki skompilowane z [/LN](../build/reference/ln-create-msil-module.md) nie dotyczy to zachowanie. W tym przypadku, widoczne będą wszystkie klasy zarządzane (publiczne lub prywatne).  
  
## <a name="end-clr-specific"></a>KONIEC specyficzne dla /clr  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [Kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)