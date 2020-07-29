---
title: Threading (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: e08d25df07ad881c8843953d01d9074c815ddb85
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193071"
---
# <a name="threading-c"></a>threading (C++)

Określa model wątkowości dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parametry

*wzorów*<br/>
Obowiązkowe Jeden z następujących modeli wątkowości:

- `apartment`(wątkowość apartamentu)

- `neutral`(Składniki .NET Framework bez interfejsu użytkownika)

- `single`(prosta wątkowość)

- `free`(bezpłatna wątkowość)

- `both`(Apartment i Free Threading)

Wartość domyślna to `apartment`.

## <a name="remarks"></a>Uwagi

Atrybut **Threading** języka C++ nie jest wyświetlany w wygenerowanym pliku IDL, ale zostanie użyty w implementacji obiektu com.

W projektach ATL, jeśli istnieje również atrybut [klasy coclass](coclass.md) , model wątkowości określony przez *model* jest przenoszona jako parametr szablonu do klasy [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , wstawiany przez `coclass` atrybut.

Atrybut **wątkowości** chroni również dostęp do [event_source](event-source.md).

## <a name="example"></a>Przykład

Zapoznaj się z [licencjonowanym](licensed.md) przykładem użycia **wątku**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutralny apartamentach](/windows/win32/cossdk/neutral-apartments)
