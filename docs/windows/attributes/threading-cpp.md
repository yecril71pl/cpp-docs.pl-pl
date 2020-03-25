---
title: wątkowość (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: b249eaf61266ed9964e44f6f0ad1c2f12a1b1067
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214503"
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

- `apartment` (wątkowość apartamentu)

- `neutral` (składniki .NET Framework bez interfejsu użytkownika)

- `single` (prosta wątkowość)

- `free` (bezpłatna wątkowość)

- `both` (Apartment i Free Threading)

Wartością domyślną jest `apartment`.

## <a name="remarks"></a>Uwagi

C++ Atrybut **Threading** nie jest wyświetlany w wygenerowanym pliku IDL, ale zostanie użyty w implementacji obiektu com.

W projektach ATL, jeśli istnieje również atrybut [klasy coclass](coclass.md) , model wątkowości określony przez *model* jest przenoszona jako parametr szablonu do klasy [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , wstawiany przez atrybut `coclass`.

Atrybut **wątkowości** chroni również dostęp do [event_source](event-source.md).

## <a name="example"></a>Przykład

Zapoznaj się z [licencjonowanym](licensed.md) przykładem użycia **wątku**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutralny apartamentach](/windows/win32/cossdk/neutral-apartments)
