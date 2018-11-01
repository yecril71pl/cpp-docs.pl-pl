---
title: support_error_info — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: 8aed647677b8c8d26fdca522c10ec9ecee9f87c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626013"
---
# <a name="supporterrorinfo"></a>support_error_info

Implementuje obsługę zwracania szczegółowe informacje o błędach.

## <a name="syntax"></a>Składnia

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametry

*error_interface*<br/>
Identyfikator implementującego interfejs `IErrorInfo`.

## <a name="remarks"></a>Uwagi

**Support_error_info —** atrybut C++ zapewnia obsługę zwraca szczegółowe, kontekstowe błędy napotykane przez obiekt docelowy do klienta. Dla obiektu do obsługi błędów, metody `IErrorInfo` interfejsu muszą być zaimplementowane przez obiekt. Aby uzyskać więcej informacji, zobacz [obsługi IDispatch i IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Ten atrybut dodaje [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) klasy jako klasę bazową do obiektu docelowego. Skutkuje to domyślna Implementacja klasy `ISupportErrorInfo` i mogą być używane, gdy jeden interfejs generuje błędy na obiekcie.

## <a name="example"></a>Przykład

Poniższy kod dodaje domyślną obsługę `ISupportErrorInfo` współpracować w celu `CMyClass` obiektu.

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
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)