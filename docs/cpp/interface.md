---
title: __interface | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __interface_cpp
dev_langs:
- C++
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34b861ade07070f296c3fb03a9eef441998b7af7
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789179"
---
# <a name="interface"></a>__interface

**Microsoft Specific**

Interfejs Visual C++ można zdefiniować w następujący sposób:

- Może dziedziczyć z zero lub więcej podstawowych interfejsów.

- Nie można dziedziczyć z klasy bazowej.

- Może zawierać tylko publiczne, czystych metod wirtualnych.

- Nie może zawierać konstruktory, destruktory lub operatorów.

- Nie może zawierać metod statycznych.

- Nie może zawierać elementy członkowskie danych; właściwości są dozwolone.

## <a name="syntax"></a>Składnia

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Uwagi

C++ [klasy](../cpp/class-cpp.md) lub [struktury](../cpp/struct-cpp.md) implementacji przy użyciu tych zasad, ale **__interface** je egzekwuje.

Na przykład Oto przykładowa definicja interfejsu:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Aby uzyskać informacji na temat interfejsów zarządzanych, zobacz [interfejsu klasy](../windows/interface-class-cpp-component-extensions.md).

Zwróć uwagę, że nie trzeba jawnie wskazać, że `CommitX` i `get_X` są czyste funkcje wirtualne. Równoważną deklarację dla pierwszej funkcji mogą być następujące:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** oznacza [novtable](../cpp/novtable.md) **__declspec** modyfikator.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia właściwości zadeklarowanych w interfejsie.

```cpp
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Atrybuty interfejsu](../windows/attributes/interface-attributes.md)