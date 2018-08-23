---
title: EventTargetArray::EventTargetArray, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bbf6cb67973d7538aa7aea0d846cbadf030d585
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590655"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray — Konstruktor

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*godz.*  
Po tej operacji konstruktora parametru *hr* wskazuje, czy przydział tablicy zakończonych powodzeniem lub niepowodzeniem. Poniższa tabela zawiera listę możliwych wartości dla *hr*.

S_OK operacja zakończyła się pomyślnie.

Nie można przydzielić pamięci E_OUTOFMEMORY tablicy.

Parametr S_FALSE *elementów* jest mniejsza niż zero.

*Elementy*  
Liczba elementów tablicy można przydzielić.

## <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy **EventTargetArray** klasy.

**EventTargetArray** jest używany do przechowywania programu obsługi zdarzeń w tablicy `EventSource` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[EventTargetArray, klasa](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)