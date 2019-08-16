---
title: wątkowość (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: db2940ec3536ae8ea29ba40db84ea869ecb3d0ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513932"
---
# <a name="threading-c"></a>threading (C++)

Określa model wątkowości dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parametry

*model*<br/>
Obowiązkowe Jeden z następujących modeli wątkowości:

- `apartment`(wątkowość apartamentu)

- `neutral`(Składniki .NET Framework bez interfejsu użytkownika)

- `single`(prosta wątkowość)

- `free`(bezpłatna wątkowość)

- `both`(Apartment i Free Threading)

Wartość domyślna to `apartment`.

## <a name="remarks"></a>Uwagi

Atrybut Threading nie jest wyświetlany w wygenerowanym pliku IDL, ale zostanie użyty w implementacji obiektu com. C++

W projektach ATL, jeśli istnieje również atrybut [klasy coclass](coclass.md) , model wątkowości określony przez *model* jest przenoszona jako parametr szablonu do `coclass` klasy [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , wstawiany przez atrybut.

Atrybut **wątkowości** chroni również dostęp do [event_source](event-source.md).

## <a name="example"></a>Przykład

Zapoznaj [](licensed.md) się z licencjonowanym przykładem użycia **wątku**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutralny apartamentach](/windows/win32/cossdk/neutral-apartments)