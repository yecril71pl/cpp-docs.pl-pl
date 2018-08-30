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
ms.openlocfilehash: a6131cea7a7684036fd7183a79214c7c6936540b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218751"
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

## <a name="see-also"></a>Zobacz też

[Odwołanie (Biblioteka środowiska uruchomieniowego Windows)](https://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)