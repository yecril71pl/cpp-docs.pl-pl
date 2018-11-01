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
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643667"
---
# <a name="callnewh"></a>_callnewh

Wywołuje obecnie zainstalowanej *nowy program obsługi*.

## <a name="syntax"></a>Składnia

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Ilość pamięci, który [operatora new](../../cpp/new-operator-cpp.md) próbował przydzielić.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|0|Błąd: Albo nie nowy program obsługi jest zainstalowany lub nie nowy program obsługi jest aktywny.|
|1|Powodzenie: Nowy program obsługi jest zainstalowaną i aktywną. Mogą być ponawiane alokacji pamięci.|

## <a name="exceptions"></a>Wyjątki

Ta funkcja zgłosi [bad_alloc —](../../standard-library/bad-alloc-class.md) Jeśli *nowy program obsługi* nie można odnaleźć.

## <a name="remarks"></a>Uwagi

*Nowy program obsługi* jest wywoływana, gdy [operatora new](../../cpp/new-operator-cpp.md) zakończy się niepowodzeniem, można przydzielić pamięci na pomyślnie. Nowy program obsługi może następnie zainicjuj odpowiednich działań, taką jak zwalnianie pamięci, aby pomyślnie kolejnych alokacji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Zobacz także

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
