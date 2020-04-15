---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: d93de7f963a370810ed3b30af04d6d602abf6313
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333666"
---
# <a name="_callnewh"></a>_callnewh

Wywołuje aktualnie zainstalowany *nowy program obsługi*.

## <a name="syntax"></a>Składnia

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Ilość pamięci, którą [nowy operator](../../cpp/new-operator-cpp.md) próbował przydzielić.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|0|Błąd: Nie zainstalowano żadnego nowego programu obsługi lub nie jest aktywny żaden nowy program obsługi.|
|1|Powodzenie: nowy program obsługi jest zainstalowany i aktywny. Alokacji pamięci można ponowić.|

## <a name="exceptions"></a>Wyjątki

Ta funkcja zgłasza [bad_alloc,](../../standard-library/bad-alloc-class.md) jeśli nie można zlokalizować *nowego programu obsługi.*

## <a name="remarks"></a>Uwagi

*Nowy program obsługi* jest wywoływana, jeśli nowy [operator](../../cpp/new-operator-cpp.md) nie może pomyślnie przydzielić pamięci. Nowy program obsługi może następnie zainicjować niektóre odpowiednie działania, takie jak zwalnianie pamięci, tak aby kolejne alokacje zakończyć się pomyślnie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_callnewh|wewnętrzny.h|

## <a name="see-also"></a>Zobacz też

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
