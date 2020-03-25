---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 652aee03bfb5504a51d74efb326cc7a3d7c28649
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171206"
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

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** (ignorowany).

*wyst*<br/>
Nowa szerokość strumienia: wartość dodatnia dla znaku dwubajtowego, wartość ujemna dla Byte, zero, aby opuścić niezmieniony. (Ta wartość jest ignorowana).

## <a name="return-value"></a>Wartość zwracana

Ta funkcja właśnie zwraca *tryb*.

## <a name="remarks"></a>Uwagi

Bieżąca wersja tej funkcji jest niezgodna ze standardem.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwide**|\<WCHAR. h >|

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).
