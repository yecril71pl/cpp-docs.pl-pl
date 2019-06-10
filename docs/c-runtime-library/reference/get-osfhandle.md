---
title: _get_osfhandle
ms.date: 05/29/2018
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
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: cc3b50e3d3f65bee83b8df83aa0adb5c8694e35a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821659"
---
# <a name="getosfhandle"></a>_get_osfhandle

Pobiera dojście do pliku systemu operacyjnego, który jest skojarzony z deskryptorem określonego pliku.

## <a name="syntax"></a>Składnia

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Istniejące deskryptor pliku.

## <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt pliku systemu operacyjnego, jeśli *fd* jest prawidłowy. W przeciwnym razie program obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **INVALID_HANDLE_VALUE** (-1). Ustawia również **errno** do **EBADF**, wskazując nieprawidłowe dojście do pliku. Aby uniknąć ostrzeżenia, gdy zostanie użyty wynik jako uchwyt pliku systemu Win32, należy rzutować go na **obsługi** typu.

> [!NOTE]
> Gdy **stdin**, **stdout**, i **stderr** nie są skojarzone z usługą stream (na przykład w aplikacji Windows bez okna konsoli), wartości deskryptora pliku te strumienie są zwracane z [_fileno](fileno.md) jako specjalnych wartości -2. Podobnie jeśli używasz parametru deskryptora pliku zamiast wyniku wywołania wartość 0, 1 lub 2 **_fileno**, **_get_osfhandle —** również zwraca specjalna wartość -2, jeśli deskryptor pliku nie jest skojarzony za pomocą strumienia, a nie ustawia **errno**. Jednak nie jest to wartość uchwyt prawidłowego pliku, a kolejne wywołania, które próbują używać go będzie prawdopodobnie nie powiedzie się.

Aby uzyskać więcej informacji na temat **EBADF** i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Można zamknąć pliku, w których uchwyt pliku systemu operacyjnego (OS) można uzyskać przez **_get_osfhandle —** , wywołaj [_zamknij](close.md) na deskryptor pliku *fd*. Nigdy nie wywołują metody **funkcja CloseHandle** na wartość zwracana przez tę funkcję. Dojście do pliku podstawowego systemu operacyjnego jest własnością *fd* deskryptor pliku i jest zamknięte, kiedy [_zamknij](close.md) jest wywoływana w *fd*. Jeżeli deskryptor pliku jest własnością `FILE *` strumienia, następnie wywoływania [fclose —](fclose-fcloseall.md) na tym `FILE *` strumień zostanie zamknięty, deskryptor pliku i dojście do pliku podstawowego systemu operacyjnego. W tym przypadku nie wywołuj [_zamknij](close.md) na deskryptor pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
