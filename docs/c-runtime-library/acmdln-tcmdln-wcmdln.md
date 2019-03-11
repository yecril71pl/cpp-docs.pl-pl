---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
ms.openlocfilehash: f4cacb512cb9b5bb6ea22f4dc4014ac2a2eeebe6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747024"
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln

Wewnętrzny CRT zmiennej globalnej. Wiersz polecenia.

## <a name="syntax"></a>Składnia

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>Uwagi

Te zmienne wewnętrznego CRT przechowywać cały wiersz polecenia. One są udostępniane w symbolach wyeksportowany do CRT, ale nie są przeznaczone do użycia w kodzie. `_acmdln` przechowuje dane jako ciąg znaków. `_wcmdln` przechowuje dane jako ciąg znaków dwubajtowych. `_tcmdln` można zdefiniować jako `_acmdln` lub `_wcmdln`, w których jest właściwy zależności.

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)
