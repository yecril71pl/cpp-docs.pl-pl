---
title: __interface | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __interface_cpp
dev_langs: C++
helpviewer_keywords: __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fc53310c492c424c3d97aecec965ba03553dd8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interface"></a>__interface
**Dotyczące firmy Microsoft**  
  
 Interfejs Visual C++ można zdefiniować w następujący sposób:  
  
-   Może dziedziczyć od zera lub większej interfejsach podstawowych.  
  
-   Nie można dziedziczyć po klasie podstawowej.  
  
-   Może zawierać tylko publiczne, czystych metod wirtualnych.  
  
-   Nie może zawierać konstruktorów, destruktory lub Operatorzy.  
  
-   Nie może zawierać metod statycznych.  
  
-   Nie może zawierać elementy członkowskie danych; właściwości są dozwolone.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
modifier  
 __interface interface-name {interface-definition};  
```  
  
## <a name="remarks"></a>Uwagi  
 C++ [klasy](../cpp/class-cpp.md) lub [struktury](../cpp/struct-cpp.md) może być realizowane za pomocą tych zasad, ale `__interface` wymusza je.  
  
 Na przykład Oto przykład definicji interfejsu:  
  
```  
__interface IMyInterface {  
   HRESULT CommitX();  
   HRESULT get_X(BSTR* pbstrName);  
};  
```  
  
 Uzyskać informacji o zarządzanych interfejsów, temacie [interfejsu klasy](../windows/interface-class-cpp-component-extensions.md).  
  
 Powiadomienie, że nie trzeba jawnie wskazać, że `CommitX` i `get_X` są czystych funkcji wirtualnych. Odpowiednik deklaracji dla pierwszej funkcji mogą być następujące:  
  
```  
virtual HRESULT CommitX() = 0;  
```  
  
 `__interface`oznacza [novtable](../cpp/novtable.md) `__declspec` modyfikator.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia właściwości zadeklarowany w interfejsie.  
  
```  
// deriv_interface.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <string.h>  
#include <comdef.h>  
#include <stdio.h>  
  
[module(name="test")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]  
__interface IFace {  
   [ id(0) ] int int_data;  
   [ id(5) ] BSTR bstr_data;  
};  
  
[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]  
class MyClass : public IFace {  
private:  
    int m_i;  
    BSTR m_bstr;   
  
public:  
    MyClass()  
    {  
        m_i = 0;  
        m_bstr = 0;  
    }  
  
    ~MyClass()  
    {  
        if (m_bstr)   
            ::SysFreeString(m_bstr);  
    }  
  
    int get_int_data()  
    {  
        return m_i;  
    }  
  
    void put_int_data(int _i)   
    {  
        m_i = _i;  
    }  
  
    BSTR get_bstr_data()  
    {   
        BSTR bstr = ::SysAllocString(m_bstr);  
        return bstr;   
    }  
  
    void put_bstr_data(BSTR bstr)   
    {   
        if (m_bstr)   
            ::SysFreeString(m_bstr);  
        m_bstr = ::SysAllocString(bstr);  
    }  
};  
  
int main()  
{  
    _bstr_t bstr("Testing");  
    CoInitialize(NULL);  
    CComObject<MyClass>* p;  
    CComObject<MyClass>::CreateInstance(&p);  
    p->int_data = 100;  
    printf_s("p->int_data = %d\n", p->int_data);                
    p->bstr_data = bstr;  
    printf_s("bstr_data = %S\n", p->bstr_data);  
}  
```  
  
```Output  
p->int_data = 100  
bstr_data = Testing  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)