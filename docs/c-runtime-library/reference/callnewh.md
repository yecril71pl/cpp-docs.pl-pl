---
title: _callnewh
ms.date: 11/04/2016
api_name:
- _callnewh
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3e14450538807b164897c335f7e37d82d8562314
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939381"
---
# <a name="_callnewh"></a>_callnewh

Wywołuje aktualnie zainstalowaną *nową procedurę obsługi*.

## <a name="syntax"></a>Składnia

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Ilość pamięci, którą [Nowy operator](../../cpp/new-operator-cpp.md) próbował przydzielić.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|0|Spraw Nie zainstalowano żadnego nowego programu obsługi lub nie jest on aktywny.|
|1|Prawnego Nowa procedura obsługi jest zainstalowana i aktywna. Można ponowić próbę alokacji pamięci.|

## <a name="exceptions"></a>Wyjątki

Ta funkcja zgłasza [bad_alloc](../../standard-library/bad-alloc-class.md) , jeśli nie można zlokalizować *nowego programu obsługi* .

## <a name="remarks"></a>Uwagi

*Nowy program obsługi* jest wywoływany, jeśli [Nowy operator](../../cpp/new-operator-cpp.md) nie może pomyślnie przydzielić pamięci. Nowy program obsługi może następnie inicjować pewne odpowiednie działania, takie jak zwalnianie pamięci, aby kolejne przydziały powiodło się.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Zobacz także

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
