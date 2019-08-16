---
title: dispinterface (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 6360c5e97eae19d7b2d74b3b43d4feae07d4b091
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501624"
---
# <a name="dispinterface"></a>dispinterface

Umieszcza interfejs w pliku. idl jako interfejs wysyłania.

## <a name="syntax"></a>Składnia

```cpp
[dispinterface]
```

## <a name="remarks"></a>Uwagi

Gdy atrybut **dispinterface** C++ poprzedza interfejs, powoduje, że interfejs należy umieścić wewnątrz bloku biblioteki w wygenerowanym pliku IDL.

Chyba że określisz klasę bazową, będzie on pochodzić od `IDispatch`. Należy określić [Identyfikator](id.md) dla elementów członkowskich interfejsu wysyłania.

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
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty w zależności od zastosowania](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)