---
title: EventSource::Remove, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00f3275095648a41eb25d10bac1f34637b2ac242
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604575"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove — Metoda

Usuwa program obsługi zdarzeń, reprezentowane przez tokenu rejestracji określonego zdarzenia z zestawu programów obsługi zdarzeń skojarzonych z bieżącym **EventSource** obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*Token*  
Uchwyt, który reprezentuje program obsługi zdarzeń. Token ten został zwrócony podczas obsługi zdarzeń było zarejestrowane przez [Add()](../windows/eventsource-add-method.md) metody.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat `EventRegistrationToken` struktury, zobacz **struktury typem Windows::Foundation:: eventregistrationtoken** tematu w **Windows Runtime** dokumentację referencyjną.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[EventSource, klasa](../windows/eventsource-class.md)