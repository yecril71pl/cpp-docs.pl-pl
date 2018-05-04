---
title: _get_osfhandle — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/12/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b58bbeb7c0b52950509dc8005551ad706577fcf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="getosfhandle"></a>_get_osfhandle

Pobiera dojście do pliku systemu operacyjnego skojarzonego z deskryptorem określonego pliku.

## <a name="syntax"></a>Składnia

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Istniejące deskryptorów plików.

## <a name="return-value"></a>Wartość zwracana

Zwraca dojście do pliku systemu operacyjnego, jeśli *fd* jest nieprawidłowy. W przeciwnym razie program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **INVALID_HANDLE_VALUE** (-1) i ustawia **errno** do **ebadf —**, wskazując nieprawidłowe dojście do pliku.

## <a name="remarks"></a>Uwagi

Aby zamknąć plik, którego dojście do pliku systemu operacyjnego (OS) są uzyskiwane przez **_get_osfhandle —**, wywołaj [_zamknij](close.md) na deskryptorów plików *fd*. Nie wywołuj **CloseHandle** wartości zwracanej tej funkcji. Dojście do pliku podstawowego systemu operacyjnego jest własnością *fd* pliku deskryptora i zostanie zamknięty kiedy [_zamknij](close.md) jest wywoływana na *fd*. Jeśli właścicielem jest deskryptorów plików **pliku \***  strumienia, wywołując [fclose —](fclose-fcloseall.md) na tej **pliku \***  strumienia zamyka deskryptorów plików i podstawowy system operacyjny dojście do pliku. W takim przypadku nie wywołuj [_zamknij](close.md) na deskryptorów plików.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
