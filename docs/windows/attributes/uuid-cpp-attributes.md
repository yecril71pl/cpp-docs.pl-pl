---
title: uuid (Atrybuty C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: 72d18eb50f8d85fb10d5af3ffce08c5b74947531
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222098"
---
# <a name="uuid-c-attributes"></a>uuid (Atrybuty C++)

Określa unikatowy identyfikator klasy lub interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ uuid( "uuid" ) ]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
128-bitowy, unikatowy identyfikator.

## <a name="remarks"></a>Uwagi

Jeśli definicja interfejsu lub klasy nie określa `uuid` atrybutu C++, zostanie on podany w kompilatorze języka Microsoft C++. Po określeniu należy `uuid` uwzględnić cudzysłowy.

Jeśli nie określisz `uuid` , kompilator generuje ten sam identyfikator GUID dla interfejsów lub klas o tej samej nazwie w różnych projektach atrybutów na komputerze.

Możesz użyć Uuidgen.exe lub Guidgen.exe do wygenerowania własnych unikatowych identyfikatorów. (Aby uruchomić dowolne z tych narzędzi, kliknij przycisk **Start** , a następnie kliknij pozycję **Uruchom** w menu. Następnie wprowadź nazwę wymaganego narzędzia.

Gdy jest używany w projekcie, który nie używa także ATL, określenie `uuid` atrybutu jest taka sama jak określenie modyfikatora [UUID](../../cpp/uuid-cpp.md) **`__declspec`** . Aby pobrać `uuid` klasę, można użyć [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Przykład

Zobacz przykładowy [przykład użycia](bindable.md) `uuid` .

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|`class`, `struct`, `interface`, `union`, `enum`|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty typedef, enum, Union i struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
