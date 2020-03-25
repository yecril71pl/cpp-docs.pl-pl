---
title: dispinterface (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 66567b0a1b043136e0a754e3a52bbdd7c463e178
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168242"
---
# <a name="dispinterface"></a>dispinterface

Umieszcza interfejs w pliku. idl jako interfejs wysyłania.

## <a name="syntax"></a>Składnia

```cpp
[dispinterface]
```

## <a name="remarks"></a>Uwagi

Gdy atrybut **dispinterface** C++ poprzedza interfejs, powoduje, że interfejs należy umieścić wewnątrz bloku biblioteki w wygenerowanym pliku IDL.

O ile nie zostanie określona klasa bazowa, interfejs wysyłania będzie pochodzić od `IDispatch`. Należy określić [Identyfikator](id.md) dla elementów członkowskich interfejsu wysyłania.

Przykład użycia [dispinterface](/windows/win32/Midl/dispinterface) w dokumentacji MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

nie jest prawidłowy dla atrybutu **dispinterface** .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [powiązania](bindable.md) z przykładem użycia **dispinterface**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty w zależności od zastosowania](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
