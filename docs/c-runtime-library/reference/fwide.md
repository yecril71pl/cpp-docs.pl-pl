---
title: fwide — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd52c450e2eb34c40d44d00a76550c401abcb6c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397272"
---
# <a name="fwide"></a>fwide

Niezaimplementowane.

## <a name="syntax"></a>Składnia

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury (zignorowany).

*Tryb*<br/>
Nową szerokość strumienia: dodatnią dla znaku dwubajtowego ujemny bajt, zero, aby pozostawić bez zmian. (Ta wartość zostanie zignorowana).

## <a name="return-value"></a>Wartość zwracana

Ta funkcja jest obecnie tylko zwraca *tryb*.

## <a name="remarks"></a>Uwagi

Bieżąca wersja ta funkcja nie jest zgodne ze standardem.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwide**|\<WChar.h >|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).