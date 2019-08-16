---
title: vi_progid (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514871"
---
# <a name="vi_progid"></a>vi_progid

Określa niezależną od wersji identyfikator ProgID.

## <a name="syntax"></a>Składnia

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parametry

*name*<br/>
Niezależny od wersji identyfikator ProgID reprezentujący obiekt.

Identyfikatory ProgID składają się na czytelną dla człowieka wersję identyfikatora klasy (CLSID) służącą do identyfikowania obiektów COM/ActiveX.

## <a name="remarks"></a>Uwagi

Atrybut **vi_progid** C++ umożliwia określenie identyfikatora ProgID niezależnego od wersji dla obiektu com. Identyfikator ProgID ma postać *Name1. NAME2. Version*. Niezależny od wersji ProgID nie ma *wersji*. Można określić zarówno `progid` atrybuty `coclass` **vi_progid** , jak i. Jeśli nie określisz **vi_progid**, program ProgID niezależny od wersji jest wartością określoną przez atrybut [ProgID](progid.md) .

**vi_progid** implikuje `coclass` atrybut, oznacza to, że jeśli określisz **vi_progid**, jest to takie samo, jak określenie `coclass` atrybutów i **vi_progid** .

Atrybut **vi_progid** powoduje, że Klasa jest automatycznie rejestrowana pod określoną nazwą. Wygenerowany plik IDL nie będzie wyświetlał wartości ProgID.

W projektach ATL, jeśli atrybut [klasy coclass](coclass.md) jest również obecny, określony ProgID jest używany przez `GetVersionIndependentProgID` funkcję `coclass` (wstawioną przez atrybut).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [klasy coclass](coclass.md) dla przykładowego użycia **vi_progid**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Klucz ProgID](/windows/win32/com/-progid--key)
