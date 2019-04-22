---
title: lokalne (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 678968bb7b0f2e7af94124bea5b0967df27e43f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033073"
---
# <a name="local-c"></a>local (C++)

W przypadku użycia w nagłówku interfejsu, umożliwia kompilatorowi MIDL jako generator nagłówka. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.

## <a name="syntax"></a>Składnia

```cpp
[local]
```

## <a name="remarks"></a>Uwagi

**Lokalnego** atrybut C++ ma taką samą funkcjonalność jak [lokalnego](/windows/desktop/Midl/local) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [call_as](call-as.md) przykład sposobu użycia **lokalnego**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, interfejs — metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`dispinterface`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[call_as](call-as.md)