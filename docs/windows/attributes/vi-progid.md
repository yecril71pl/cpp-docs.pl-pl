---
title: vi_progid — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b5c5dcadc1715384684062f203ae9179ef044
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789789"
---
# <a name="viprogid"></a>vi_progid

Określa formularza niezależny od wersji identyfikatora ProgID.

## <a name="syntax"></a>Składnia

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Identyfikator ProgID niezależny od wersji reprezentujący obiekt.

ProgID przedstawiają czytelny dla człowieka wersję identyfikator klasy (CLSID) używany do identyfikowania obiektów COM/ActiveX.

## <a name="remarks"></a>Uwagi

**Vi_progid —** atrybut C++ pozwala określić identyfikator ProgID niezależny od wersji dla obiektu COM. Identyfikator ProgID ma formę *name1.name2.version*. Identyfikator ProgID niezależny od wersji nie ma *wersji*. Można określić zarówno `progid` i **vi_progid —** atrybuty na `coclass`. Jeśli nie określisz **vi_progid —**, niezależnie od wersji ProgID jest wartość określoną przez [progid](progid.md) atrybutu.

**vi_progid —** oznacza `coclass` atrybutu, oznacza to, jeśli określisz **vi_progid —**, jest tak samo jak określanie `coclass` i **vi_progid —** atrybutów.

**Vi_progid —** atrybutu powoduje, że klasy do zarejestrowania się automatycznie w ramach określonej nazwy. Pliku .idl wygenerowanego identyfikatora ProgID wartości nie są wyświetlane.

W projektach ATL Jeśli [coclass](coclass.md) atrybut również występuje, określony identyfikator ProgID jest używany przez `GetVersionIndependentProgID` — funkcja (wstawione przez `coclass` atrybutu).

## <a name="example"></a>Przykład

Zobacz [coclass](coclass.md) przykład użycie próbki **vi_progid —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Klucz identyfikatora progID](/windows/desktop/com/-progid--key)  