---
title: _open_osfhandle — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3783420389dc008e39c818c39406f0b2af8af5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569839"
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

**_Open_osfhandle —** funkcja przydziela deskryptora pliku wykonawcze języka C i kojarzy ją z określonego przez dojście do pliku systemu operacyjnego *osfhandle*. Aby uniknąć ostrzeżenia kompilatora, *osfhandle* argumentów **obsługi** do **intptr_t —**. *Flagi* argumentu wyrażeniem liczby całkowitej z jedną lub więcej z manifestu stałe zdefiniowane w \<fcntl.h >. Gdy dwa lub więcej manifestu stałe są używane do formularza *flagi* argumentu, stałe są łączone z operator Alternatywy ( **&#124;** ).

Te manifestu stałe są zdefiniowane w \<fcntl.h >:

|||
|-|-|
**\_O\_DOŁĄCZANIA**|Określa położenie pliku wskaźnik na koniec pliku przed każdej operacji zapisu.
**\_O\_RDONLY**|Otwiera plik tylko odczytywanie.
**\_O\_TEXT**|Otwiera plik w trybie tekstowym (translacji).
**\_O\_WTEXT**|Otwiera plik w trybie Unicode (przetłumaczonego UTF-16).

**_Open_osfhandle —** wywołania przesyła własność dojście do pliku Win32 do deskryptorów plików. Można zamknąć pliku, która została otwarta z **_open_osfhandle —**, wywołaj [ \_zamknąć](close.md). Dojście do pliku podstawowego systemu operacyjnego jest również zamknięte przez wywołanie do **_zamknij**, więc nie jest konieczne do wywołania funkcji Win32 **CloseHandle** w dojściu do oryginalnego. Jeśli właścicielem jest deskryptorów plików **pliku &#42;**  strumienia, wywołując [fclose —](fclose-fcloseall.md) na tej **pliku &#42;**  strumienia powoduje zamknięcie deskryptorów plików i dojście do podstawowej. W takim przypadku nie wywołuj **_zamknij** na deskryptorów plików.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
