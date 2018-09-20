---
title: EventTargetArray::Begin, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs:
- C++
helpviewer_keywords:
- Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b818595d8ad32295dbce1498161898b215e1885f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433777"
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
ComPtr<IUnknown>* Begin();
```

## <a name="return-value"></a>Wartość zwracana

Adres do pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="remarks"></a>Uwagi

Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[EventTargetArray, klasa](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)