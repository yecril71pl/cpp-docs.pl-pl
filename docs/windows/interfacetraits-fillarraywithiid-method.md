---
title: InterfaceTraits::FillArrayWithIid, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fc4679d9e6d3a4fdfc112d8a8b471ceb2646ecc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583731"
---
# <a name="interfacetraitsfillarraywithiid-method"></a>InterfaceTraits::FillArrayWithIid — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*  
Wskaźnik do pola, które zawiera wartość indeksu zaczynającego się od zera.

*IID*  
Tablica identyfikatorów interfejsu.

## <a name="remarks"></a>Uwagi

Przypisuje identyfikator interfejsu `Base` do elementu tablicy, określonego przez argument indeksu.

Sprzecznie nazwę tego interfejsu API tylko jedna tablica element zostanie zmodyfikowany; nie macierz w całości.

Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publiczne definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[InterfaceTraits, struktura](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)