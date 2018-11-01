---
title: fwide
ms.date: 11/04/2016
apiname:
- fwide
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
apitype: DLLExport
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: d992ebc527744beeb4ef14175e3f10646a77a064
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557852"
---
# <a name="fwide"></a>fwide

Niezaimplementowana.

## <a name="syntax"></a>Składnia

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury (zignorowany).

*Tryb*<br/>
Nową szerokość strumienia: dodatnia dla znaku dwubajtowego, który jest ujemny bajt, zero, aby pozostawić bez zmian. (Ta wartość jest ignorowana).

## <a name="return-value"></a>Wartość zwracana

Ta funkcja jest obecnie po prostu zwraca *tryb*.

## <a name="remarks"></a>Uwagi

Bieżąca wersja tej funkcji jest zgodne ze standardem.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwide**|\<WChar.h >|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).