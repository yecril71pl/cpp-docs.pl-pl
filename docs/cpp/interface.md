---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 9b265dcbaca9f8fa836795cca990804371813647
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178214"
---
# <a name="__interface"></a>__interface

**Specyficzne dla firmy Microsoft**

Interfejs Microsoft C++ można zdefiniować w następujący sposób:

- Może dziedziczyć z zero lub więcej interfejsów podstawowych.

- Nie można dziedziczyć z klasy bazowej.

- Może zawierać tylko publiczne, czyste metody wirtualne.

- Nie może zawierać konstruktorów, destruktorów ani operatorów.

- Nie mogą zawierać metod statycznych.

- Nie może zawierać składowych danych; właściwości są dozwolone.

## <a name="syntax"></a>Składnia

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Uwagi

C++ [Klasę](../cpp/class-cpp.md) lub [strukturę](../cpp/struct-cpp.md) można zaimplementować przy użyciu tych reguł, ale **__interface** wymuszają te reguły.

Na przykład poniżej przedstawiono przykładową definicję interfejsu:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Aby uzyskać informacje na temat interfejsów zarządzanych, zobacz [Klasa interfejsu](../extensions/interface-class-cpp-component-extensions.md).

Należy zauważyć, że nie trzeba jawnie wskazywać, że `CommitX` i `get_X` funkcje są czystymi wirtualnymi. Równoważną deklaracją dla pierwszej funkcji będzie:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** sugeruje modyfikator __declspec [notablicę](../cpp/novtable.md) **__declspec** .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać właściwości zadeklarowanych w interfejsie.

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Atrybuty interfejsu](../windows/attributes/interface-attributes.md)
