---
title: wątkowość (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: 0feb258941993ff9776bb9f94f61a556d7d4caec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449845"
---
# <a name="threading-c"></a>threading (C++)

Określa model wątkowości dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parametry

*Model*<br/>
(Opcjonalnie) Jeden z następujących Modele wątkowości:

- `apartment` (wątkowości typu apartment)

- `neutral` (Składników .NET framework bez interfejsu użytkownika)

- `single` (wątki proste)

- `free` (bezpłatnie, wątki)

- `both` (apartamentu i wolnych wątków)

Wartość domyślna to `apartment`.

## <a name="remarks"></a>Uwagi

**Wątkowości** atrybut C++ nie ma pliku .idl wygenerowane, ale będą stosowane w implementacji obiektu COM.

W projektach ATL Jeśli [coclass](coclass.md) również jest obecny, atrybut modelu wątku określonego przez *modelu* jest przekazywany jako parametr szablonu [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) klasy , wstawione przez `coclass` atrybutu.

**Wątkowości** atrybut chroni także dostęp do [event_source](event-source.md).

## <a name="example"></a>Przykład

Zobacz [licencjonowane](licensed.md) przykład użycie próbki **wątkowości**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutralne Apartamentach](/windows/desktop/cossdk/neutral-apartments)