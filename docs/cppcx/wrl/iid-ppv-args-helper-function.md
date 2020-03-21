---
title: IID_PPV_ARGS_Helper — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 68dbd0b5b2e9d4fc04821a7e7e0193840b55e312
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077127"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper — Funkcja

Sprawdza, czy typ określonego argumentu pochodzi z interfejsu `IUnknown`.

> [!IMPORTANT]
> Ta specjalizacja szablonu obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie. Zamiast tego użyj [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ argumentu *PP*.

*miesięcznie*<br/>
Wskaźnik pośrednika.

## <a name="return-value"></a>Wartość zwracana

Argument *PP* rzutowania na wskaźnik do wskaźnika do typu **void**.

## <a name="remarks"></a>Uwagi

Generowany jest błąd czasu kompilacji, jeśli parametr szablonu *T* nie pochodzi od `IUnknown`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h
