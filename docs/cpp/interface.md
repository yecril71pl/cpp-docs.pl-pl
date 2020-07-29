---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 9ca13ed91601fa3a64071304c14d483e84c314a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233720"
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

[Klasy](../cpp/class-cpp.md) lub [struktury](../cpp/struct-cpp.md) C++ można zaimplementować przy użyciu tych reguł, ale **`__interface`** wymuszają je.

Na przykład poniżej przedstawiono przykładową definicję interfejsu:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Aby uzyskać informacje na temat interfejsów zarządzanych, zobacz [Klasa interfejsu](../extensions/interface-class-cpp-component-extensions.md).

Należy zauważyć, że nie trzeba jawnie wskazywać, że `CommitX` `get_X` funkcje i są czystym wirtualnym. Równoważną deklaracją dla pierwszej funkcji będzie:

```cpp
virtual HRESULT CommitX() = 0;
```

**`__interface`** oznacza modyfikator [notablicę](../cpp/novtable.md) **`__declspec`** .

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

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Atrybuty interfejsu](../windows/attributes/interface-attributes.md)
