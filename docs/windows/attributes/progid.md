---
title: ProgID (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514246"
---
# <a name="progid"></a>progid

Określa identyfikator ProgID dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametry

*name*<br/>
Identyfikator ProgID reprezentujący obiekt.

Identyfikatory ProgID składają się na czytelną dla człowieka wersję identyfikatora klasy (CLSID) służącą do identyfikowania obiektów COM/ActiveX.

## <a name="remarks"></a>Uwagi

Atrybut **ProgID** C++ umożliwia określenie identyfikatora ProgID dla obiektu com. Identyfikator ProgID ma postać *Name1. NAME2. Version*. Jeśli nie określisz *wersji* identyfikatora ProgID, domyślna wersja to 1. Jeśli nie określisz *Name1. NAME2*, nazwa domyślna to *ClassName. ClassName*. Jeśli nie określisz **identyfikatora ProgID** i określisz `vi_progid`, *Name1. NAME2* są pobierane z `vi_progid` i zostanie dołączona (Następna kolejna liczba) wersja.

Jeśli blok atrybutu, który używa **identyfikatora ProgID** , nie używa również **identyfikatora UUID**, kompilator sprawdzi rejestr, aby sprawdzić, czy istnieje **identyfikator UUID** dla określonego **identyfikatora ProgID**. Jeśli nie określono **identyfikatora ProgID** , do wygenerowania **identyfikatora ProgID**zostanie użyta wersja (i nazwa klasy coclass, jeśli zostanie utworzona Klasa coclass).

**Identyfikator ProgID** oznacza `coclass` atrybut, oznacza to, że jeśli określisz **ProgID**, jest to takie samo jak określenie `coclass` atrybutów i **ProgID** .

Atrybut **ProgID** powoduje, że Klasa jest automatycznie rejestrowana pod określoną nazwą. Wygenerowany plik IDL nie będzie wyświetlał wartości **ProgID** .

Gdy ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie atrybutu zostanie zmienione. Oprócz powyższych zachowań informacje określone przy użyciu tego atrybutu są używane w `GetProgID` funkcji, wstrzykiwane `coclass` przez atrybut. Aby uzyskać więcej informacji, zobacz atrybut [coclass](coclass.md) .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [klasy coclass](coclass.md) dla przykładowego zastosowania **identyfikatora ProgID**.

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
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klucz ProgID](/windows/win32/com/-progid--key)
