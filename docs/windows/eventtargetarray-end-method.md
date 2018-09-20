---
title: EventTargetArray::End, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17f79830cf50d83058ee2f2665b94f86a53acd78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428983"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
ComPtr<IUnknown>* End();
```

## <a name="return-value"></a>Wartość zwracana

Adres do ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="remarks"></a>Uwagi

Pobiera adres ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[EventTargetArray, klasa](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)