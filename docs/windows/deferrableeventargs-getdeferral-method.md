---
title: DeferrableEventArgs::GetDeferral, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47376a055da1625f718b7b2a8b6dbf4fe703e533
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601808"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral — metoda

Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, który reprezentuje odroczonego zdarzenie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>Parametry

*wynik*  
Wskaźnik, który będzie odwoływać się [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu po zakończeniu wywołanie.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Dla przykładu kodu zobacz [DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md)