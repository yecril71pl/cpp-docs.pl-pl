---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345027"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Pobiera dojście do pliku systemu operacyjnego skojarzone z określonym deskryptorem pliku.

## <a name="syntax"></a>Składnia

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Istniejący deskryptor pliku.

## <a name="return-value"></a>Wartość zwracana

Zwraca dojście do pliku systemu operacyjnego, jeśli *fd* jest prawidłowy. W przeciwnym razie wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, zwraca **INVALID_HANDLE_VALUE** (-1). Ustawia również **errno** na **EBADF,** wskazując nieprawidłowy uchwyt pliku. Aby uniknąć ostrzeżenia, gdy wynik jest używany jako dojście do pliku Win32, przerzuć go na typ **HANDLE.**

> [!NOTE]
> Gdy **stdin**, **stdout**i **stderr** nie są skojarzone ze strumieniem (na przykład w aplikacji systemu Windows bez okna konsoli), wartości deskryptora plików dla tych strumieni są zwracane z [_fileno](fileno.md) jako wartość specjalna -2. Podobnie, jeśli używasz 0, 1 lub 2 jako parametr deskryptora pliku zamiast wyniku wywołania **_fileno**, **_get_osfhandle** zwraca również wartość specjalną -2, gdy deskryptor pliku nie jest skojarzony ze strumieniem i nie ustawia **errno**. Jednak nie jest to prawidłowa wartość dojścia do pliku, a kolejne wywołania, które próbują go użyć, mogą zakończyć się niepowodzeniem.

Aby uzyskać więcej informacji na temat **EBADF** i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Aby zamknąć plik, którego dojście do pliku systemu operacyjnego (OS) jest uzyskiwane przez **_get_osfhandle,** wywołaj [_close](close.md) na deskryptorze pliku *fd*. Nigdy nie należy wywoływać **CloseHandle** na wartość zwracaną tej funkcji. Podstawowy uchwyt pliku systemu operacyjnego jest własnością deskryptora pliku *fd* i jest zamykany, gdy [_close](close.md) jest wywoływana na *fd*. Jeśli deskryptor pliku jest `FILE *` własnością strumienia, [wywołanie fclose](fclose-fcloseall.md) w tym `FILE *` strumieniu zamyka zarówno deskryptor pliku, jak i dojście do podstawowego pliku systemu operacyjnego. W takim przypadku nie wywołuj [_close](close.md) na deskryptorze plików.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_osfhandle**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
