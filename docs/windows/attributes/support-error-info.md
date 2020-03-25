---
title: support_error_info (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: e61ef2efbdc4039f496d7ffbcccc37cc8d111935
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166149"
---
# <a name="support_error_info"></a>support_error_info

Implementuje obsługę zwracania szczegółowych błędów.

## <a name="syntax"></a>Składnia

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametry

*error_interface*<br/>
Identyfikator interfejsu implementującego `IErrorInfo`.

## <a name="remarks"></a>Uwagi

Atrybut **support_error_info** C++ implementuje obsługę zwracania szczegółowych błędów kontekstowych napotkanych przez obiekt docelowy dla klienta. Aby obiekt mógł obsłużyć błędy, metody interfejsu `IErrorInfo` muszą być implementowane przez obiekt. Aby uzyskać więcej informacji, zobacz [Obsługa IDispatch i IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Ten atrybut dodaje klasę [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) jako klasę bazową do obiektu docelowego. Powoduje to wykonanie domyślnej implementacji `ISupportErrorInfo` i może być używane, gdy pojedynczy interfejs generuje błędy w obiekcie.

## <a name="example"></a>Przykład

Poniższy kod dodaje domyślną obsługę interfejsu `ISupportErrorInfo` do obiektu `CMyClass`.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**class**|
|**Powtarzalne**|Yes|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
