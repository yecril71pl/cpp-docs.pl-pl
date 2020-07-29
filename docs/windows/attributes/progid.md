---
title: ProgID (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 3092111236afe1e1360a2814c3091ab0de4ff6ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213856"
---
# <a name="progid"></a>progid

Określa identyfikator ProgID dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametry

*Nazwij*<br/>
Identyfikator ProgID reprezentujący obiekt.

Identyfikatory ProgID składają się na czytelną dla człowieka wersję identyfikatora klasy (CLSID) służącą do identyfikowania obiektów COM/ActiveX.

## <a name="remarks"></a>Uwagi

`progid`Atrybut C++ umożliwia określenie identyfikatora ProgID dla obiektu com. Identyfikator ProgID ma postać *Name1. NAME2. Version*. Jeśli nie określisz *wersji* identyfikatora ProgID, domyślna wersja to 1. Jeśli nie określisz *Name1. NAME2*, nazwa domyślna to *ClassName. ClassName*. Jeśli nie określisz `progid` i określisz `vi_progid` , *Name1. NAME2* są pobierane z i zostanie `vi_progid` dołączona (Następna kolejna liczba) wersja.

Jeśli blok atrybutu, który używa `progid` nie jest również używany `uuid` , kompilator sprawdzi rejestr, aby zobaczyć, czy `uuid` istnieje dla określonego `progid` . Jeśli `progid` nie jest określony, zostanie użyta wersja (i nazwa klasy coclass, jeśli tworzysz klasę coclass) `progid` .

`progid`Określa `coclass` atrybut, który oznacza, że jeśli określisz `progid` , jest to takie samo, jak określenie `coclass` `progid` atrybutów i.

Ten `progid` atrybut powoduje automatyczne zarejestrowanie klasy pod określoną nazwą. Wygenerowany plik IDL nie będzie wyświetlał `progid` wartości.

Gdy ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie atrybutu zostanie zmienione. Oprócz powyższych zachowań informacje określone przy użyciu tego atrybutu są używane w `GetProgID` funkcji, wstrzykiwane przez `coclass` atrybut. Aby uzyskać więcej informacji, zobacz atrybut [coclass](coclass.md) .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [klasy coclass](coclass.md) dla przykładowego użycia `progid` .

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|`class`, `struct`|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klucz ProgID](/windows/win32/com/-progid--key)
