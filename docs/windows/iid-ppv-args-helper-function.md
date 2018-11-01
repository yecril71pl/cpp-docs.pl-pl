---
title: IID_PPV_ARGS_Helper — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: cae29c70c551701a351cdcf404342ed1634a0e3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467421"
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

*T*<br/>
Typ argumentu *pp*.

*strony*<br/>
Wskaźnik podwójnie pośrednich.

## <a name="return-value"></a>Wartość zwracana

Argument *pp* rzutowany na wskaźnik do a-wskaźnik do **void**.

## <a name="remarks"></a>Uwagi

Błąd kompilacji jest generowany, gdy wartość parametru szablonu *T* nie pochodzi od `IUnknown`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

