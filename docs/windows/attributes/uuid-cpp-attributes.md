---
title: uuid (Atrybuty C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514952"
---
# <a name="uuid-c-attributes"></a>uuid (Atrybuty C++)

Określa unikatowy identyfikator klasy lub interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
128-bitowy, unikatowy identyfikator.

## <a name="remarks"></a>Uwagi

Jeśli definicja interfejsu lub klasy nie określa atrybutu **UUID** C++ , zostanie on podany w kompilatorze firmy Microsoft C++ . Po określeniu **identyfikatora UUID**należy uwzględnić cudzysłowy.

Jeśli nie określisz **identyfikatora UUID**, kompilator generuje ten sam identyfikator GUID dla interfejsów lub klas o tej samej nazwie w różnych projektach atrybutów na komputerze.

Aby wygenerować własne unikatowe identyfikatory, można użyć uuidgen. exe lub Guidgen. exe. (Aby uruchomić dowolne z tych narzędzi, kliknij przycisk **Start** , a następnie kliknij pozycję **Uruchom** w menu. Następnie wprowadź nazwę wymaganego narzędzia.

W przypadku użycia w projekcie, który nie używa także ATL, określenie atrybutu **UUID** jest takie samo jak określenie modyfikatora [UUID](../../cpp/uuid-cpp.md) **__declspec** . Aby pobrać **identyfikator UUID** klasy, można użyć [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Przykład

Zobacz przykład [powiązania](bindable.md) dla przykładowego zastosowania **identyfikatora UUID**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Class**, **struct**, **Interface**, **Union**, **enum**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)