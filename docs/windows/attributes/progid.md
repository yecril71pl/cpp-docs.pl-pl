---
title: Identyfikator ProgID (C++ COM atrybut) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5e499a6faabda20450a7af76d97664b90464b36
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789586"
---
# <a name="progid"></a>progid

Określa identyfikator ProgID dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Identyfikator ProgID reprezentujący obiekt.

ProgID przedstawiają czytelny dla człowieka wersję identyfikator klasy (CLSID) używany do identyfikowania obiektów COM/ActiveX.

## <a name="remarks"></a>Uwagi

**Progid** atrybut C++ pozwala na określenie identyfikatora dla obiektów COM. Identyfikator ProgID ma formę *name1.name2.version*. Jeśli nie określisz *wersji* dla ProgID, wersja domyślna to 1. Jeśli nie określisz *name1.name2*, domyślną nazwą jest *classname.classname*. Jeśli nie określisz **progid** i określ `vi_progid`, *name1.name2* są pobierane z `vi_progid` (dalej numer sekwencyjny) i jest dołączany wersji.

Jeśli blok atrybutu, który używa **progid** również nie używa **uuid**, kompilator będzie sprawdzać rejestru, aby sprawdzić, czy **uuid** istnieje w określonym **progid** . Jeśli **progid** nie zostanie określony, wersja (i nazwa klasy coclass, w przypadku tworzenia klasy coclass) będzie służyć do generowania **progid**.

**Identyfikator ProgID** oznacza `coclass` atrybutu, oznacza to, jeśli określisz **progid**, jest tak samo jak określanie `coclass` i **progid** atrybutów.

**Progid** atrybutu powoduje, że klasy do zarejestrowania się automatycznie w ramach określonej nazwy. Nie zawiera pliku .idl wygenerowanego **progid** wartość.

Jeśli ten atrybut jest używany w projekcie, który korzysta z biblioteki ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowania, informacji o określony za pomocą tego atrybutu jest używana w `GetProgID` funkcji wstrzyknięte przez `coclass` atrybutu. Aby uzyskać więcej informacji, zobacz [coclass](coclass.md) atrybutu.

## <a name="example"></a>Przykład

Zobacz przykład [coclass](coclass.md) do użytku przykładowe **progid**.

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
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klucz identyfikatora progID](/windows/desktop/com/-progid--key)  