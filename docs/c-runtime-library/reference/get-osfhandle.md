---
title: _get_osfhandle
ms.date: 05/29/2018
api_name:
- _get_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: 65060689e0a7fc72b67da8fc3bf7ce0af75fd645
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955774"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Pobiera dojście do pliku systemu operacyjnego, które jest skojarzone z określonym deskryptorem pliku.

## <a name="syntax"></a>Składnia

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Istniejący deskryptor pliku.

## <a name="return-value"></a>Wartość zwracana

Zwraca dojście do pliku systemu operacyjnego, jeśli *FD* jest prawidłowy. W przeciwnym razie procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwraca **INVALID_HANDLE_VALUE** (-1). Ustawia również **errno** na **EBADF**, wskazując nieprawidłowe dojście do pliku. Aby uniknąć ostrzeżenia, gdy wynik jest używany jako uchwyt plików Win32, należy rzutować go na typ **dojścia** .

> [!NOTE]
> Gdy **stdin**, **stdout**i **stderr** nie są skojarzone ze strumieniem (na przykład w aplikacji systemu Windows bez okna konsoli), wartości deskryptora pliku dla tych strumieni są zwracane z [_fileno](fileno.md) jako wartość Specjalna-2. Podobnie, jeśli jako parametr deskryptora pliku jest używana wartość 0, 1 lub 2, a nie wynik wywołania funkcji **_fileno**, **_get_osfhandle** również zwraca wartość specjalną-2, gdy deskryptor pliku nie jest skojarzony ze strumieniem i nie ustawi **errno**. Nie jest to jednak prawidłowa wartość dojścia do pliku, a kolejne wywołania, które próbują użyć, prawdopodobnie zakończą się niepowodzeniem.

Aby uzyskać więcej informacji na temat **EBADF** i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Aby zamknąć plik, którego dojście do pliku systemu operacyjnego jest uzyskiwane przez **_get_osfhandle**, wywołaj [_close](close.md) w deskryptorze pliku *FD*. Nigdy nie wywołuj metody **CloseHandle** dla wartości zwracanej przez tę funkcję. Dojście do pliku bazowego systemu operacyjnego jest własnością deskryptora pliku *FD* i jest zamknięte, gdy [_close](close.md) jest wywoływana na *FD*. Jeśli deskryptor pliku jest własnością `FILE *` strumienia, wywołanie [fclose](fclose-fcloseall.md) w tym `FILE *` strumieniu spowoduje zamknięcie zarówno deskryptora pliku, jak i bazowego uchwytu pliku systemu operacyjnego. W tym przypadku nie należy wywoływać [_close](close.md) z deskryptora pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
