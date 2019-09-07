---
title: _callnewh
ms.date: 11/04/2016
apiname:
- _callnewh
apilocation:
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
apitype: DLLExport
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 98526f6c8c40b71104345563db71ef098b6cfb8d
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739820"
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
