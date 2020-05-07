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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3990d4b15c25cfd6c753c2b1d44c112971ff59af
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918800"
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

*size*<br/>
Ilość pamięci, którą [Nowy operator](../../cpp/new-operator-cpp.md) próbował przydzielić.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|0|Niepowodzenie: nie zainstalowano nowej obsługi lub nie jest ona aktywna.|
|1|Sukces: Nowa procedura obsługi jest zainstalowana i aktywna. Można ponowić próbę alokacji pamięci.|

## <a name="exceptions"></a>Wyjątki

Ta funkcja zgłasza [bad_alloc](../../standard-library/bad-alloc-class.md) , jeśli nie można zlokalizować *nowego programu obsługi* .

## <a name="remarks"></a>Uwagi

*Nowy program obsługi* jest wywoływany, jeśli [Nowy operator](../../cpp/new-operator-cpp.md) nie może pomyślnie przydzielić pamięci. Nowy program obsługi może następnie inicjować pewne odpowiednie działania, takie jak zwalnianie pamięci, aby kolejne przydziały powiodło się.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|_callnewh|wewnętrzny. h|

## <a name="see-also"></a>Zobacz też

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
