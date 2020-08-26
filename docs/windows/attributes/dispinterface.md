---
title: dispinterface (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: dd2a0883418ff79af53285d3cf51dba7601a363c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845396"
---
# <a name="dispinterface"></a>dispinterface

Umieszcza interfejs w pliku. idl jako interfejs wysyłania.

## <a name="syntax"></a>Składnia

```cpp
[dispinterface]
```

## <a name="remarks"></a>Uwagi

Gdy atrybut **dispinterface** C++ poprzedza interfejs, powoduje, że interfejs należy umieścić wewnątrz bloku biblioteki w wygenerowanym pliku IDL.

Chyba że określisz klasę bazową, będzie on pochodzić od `IDispatch` . Należy określić [Identyfikator](id.md) dla elementów członkowskich interfejsu wysyłania.

Przykład użycia [dispinterface](/windows/win32/Midl/dispinterface) w dokumentacji MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

nie jest prawidłowy dla atrybutu **dispinterface** .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [powiązania](bindable.md) z przykładem użycia **dispinterface**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**interfejsu**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty według użycia](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[celnej](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
