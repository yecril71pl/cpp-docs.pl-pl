---
title: _open_osfhandle — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 270b17ce72ece85687c23678908e10bc1dcc3764
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="openosfhandle"></a>_open_osfhandle

Powoduje skojarzenie deskryptora pliku wykonawcze języka C z istniejących dojście do pliku systemu operacyjnego.

## <a name="syntax"></a>Składnia

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parametry

*osfhandle*<br/>
Dojście do pliku systemu operacyjnego.

*Flagi*<br/>
Typy operacji dozwolone.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_open_osfhandle —** zwraca deskryptor pliku wykonawcze języka C. W przeciwnym razie zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**_Open_osfhandle —** funkcja przydziela deskryptora pliku wykonawcze języka C i kojarzy ją z określonego przez dojście do pliku systemu operacyjnego *osfhandle*. *Flagi* argument jest wyrażeniem liczby całkowitej z co najmniej jednego z manifestu stałe zdefiniowane w Fcntl.h. Gdy dwa lub więcej manifestu stałe są używane do formularza *flagi* argumentu, stałe są łączone z operator Alternatywy ( **&#124;** ).

Fcntl.h definiuje następujące stałe manifestu:

**\_O\_APPEND** umieszcza wskaźnik pliku na koniec pliku przed każdej operacji zapisu.

**\_O\_RDONLY** otwiera plik do odczytu tylko.

**\_O\_tekst** otwiera plik w trybie tekstowym (translacji).

**\_O\_WTEXT** otwiera plik w trybie Unicode (przetłumaczonego UTF-16).

Można zamknąć pliku, która została otwarta z **_open_osfhandle —**, wywołaj [ \_zamknąć](close.md). Dojście do pliku podstawowego systemu operacyjnego jest również zamknięte przez wywołanie do **_zamknij**, więc nie jest konieczne do wywołania funkcji Win32 **CloseHandle** w dojściu do oryginalnego. Jeśli właścicielem jest deskryptorów plików **pliku &#42;**  strumienia, wywołując [fclose —](fclose-fcloseall.md) na tej **pliku &#42;**  strumienia powoduje zamknięcie deskryptorów plików i dojście do podstawowej. W takim przypadku nie wywołuj **_zamknij** na deskryptorów plików.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
