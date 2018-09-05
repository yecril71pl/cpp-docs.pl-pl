---
title: Iid_ppv_args_helper — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32970c9d30e1804071190ee5a57c42fd4b6334af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677254"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper — Funkcja

Sprawdza, czy typ określony argument jest pochodną `IUnknown` interfejsu.

> [!IMPORTANT]
> Ta specjalizacja szablonu obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie. Użyj [IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) zamiast tego.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parametry

*T*  
Typ argumentu *pp*.

*strony*  
Wskaźnik podwójnie pośrednich.

## <a name="return-value"></a>Wartość zwracana

Argument *pp* rzutowany na wskaźnik do a-wskaźnik do **void**.

## <a name="remarks"></a>Uwagi

Błąd kompilacji jest generowany, gdy wartość parametru szablonu *T* nie pochodzi od `IUnknown`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

