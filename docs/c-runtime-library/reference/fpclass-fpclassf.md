---
title: _fpclass, _fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: a6591d9348739d27831785a05f4a602aacdd4d0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914844"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

Zwraca wartość wskazującą klasyfikację zmiennoprzecinkową argumentu.

## <a name="syntax"></a>Składnia

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Parametry

*y*<br/>
Wartość zmiennoprzecinkowa do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Funkcje **_fpclass** i **_fpclassf** zwracają liczbę całkowitą, która wskazuje na klasyfikację zmiennoprzecinkową argumentu *x*. Klasyfikacja może mieć jedną z następujących wartości zdefiniowanych w \<> float. h.

|Wartość|Opis|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Sygnalizowanie NaN|
|**_FPCLASS_QNAN**|Cichy NaN|
|**_FPCLASS_NINF**|Nieskończoność ujemna (-INF)|
|**_FPCLASS_NN**|Ujemna znormalizowana wartość niezerowa|
|**_FPCLASS_ND**|Nieznormalizowana wartość ujemna|
|**_FPCLASS_NZ**|Ujemna zero (-0)|
|**_FPCLASS_PZ**|Dodatnia 0 (+ 0)|
|**_FPCLASS_PD**|Nieznormalizowana wartość dodatnia|
|**_FPCLASS_PN**|Dodatnia znormalizowana wartość niezerowa|
|**_FPCLASS_PINF**|Nieskończoność dodatnia (+ INF)|

## <a name="remarks"></a>Uwagi

**_Fpclass** i **_fpclassf** funkcje są specyficzne dla firmy Microsoft. Są one podobne do [fpclassify —](fpclassify.md), ale zwracają więcej szczegółowych informacji na temat argumentu. Funkcja **_fpclassf** jest dostępna tylko po skompilowaniu dla platformy x64.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<Floating. h>|

Aby uzyskać bardziej zgodność i informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
