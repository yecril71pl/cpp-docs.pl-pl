---
title: support_error_info (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: cf02af793b97c55de4c52280ad2795a460a98d9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832181"
---
# <a name="support_error_info"></a>support_error_info

Implementuje obsługę zwracania szczegółowych błędów.

## <a name="syntax"></a>Składnia

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametry

*error_interface*<br/>
Identyfikator implementujący interfejs `IErrorInfo` .

## <a name="remarks"></a>Uwagi

Atrybut **support_error_info** języka C++ implementuje obsługę zwracania szczegółowych, kontekstowych błędów, które są napotkane przez obiekt docelowy dla klienta. Aby obiekt mógł obsłużyć błędy, metody `IErrorInfo` interfejsu muszą być implementowane przez obiekt. Aby uzyskać więcej informacji, zobacz [Obsługa IDispatch i IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Ten atrybut dodaje klasę [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) jako klasę bazową do obiektu docelowego. Powoduje to wykonanie domyślnej implementacji `ISupportErrorInfo` i może być używane, gdy pojedynczy interfejs generuje błędy w obiekcie.

## <a name="example"></a>Przykład

Poniższy kod dodaje domyślną obsługę `ISupportErrorInfo` interfejsu do `CMyClass` obiektu.

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**|
|**Powtarzalne**|Tak|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
