---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 4626df0db1956efd26ee267cb8cacf8ea4a4570c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942528"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Wywołuje funkcję dostarczoną przez aplikację dla wszystkich typów **_CLIENT_BLOCK** w stercie (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*PFN*<br/>
Wskaźnik do funkcji wywołania zwrotnego funkcji dostarczonej przez aplikację. Pierwszy parametr tej funkcji wskazuje na dane. Drugi parametr jest wskaźnikiem kontekstu, który jest przesyłany do wywołania **_CrtDoForAllClientObjects**.

*Context*<br/>
Wskaźnik do kontekstu dostarczonego przez aplikację, który ma zostać przekazany do funkcji dostarczonej przez aplikację.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtDoForAllClientObjects** przeszukuje połączoną listę sterty dla bloków pamięci z typem **_CLIENT_BLOCK** i wywołuje funkcję dostarczoną przez aplikację po znalezieniu bloku tego typu. Znaleziony blok i parametr *kontekstowy* są przekazane jako argumenty do funkcji dostarczonej przez aplikację. Podczas debugowania aplikacja może śledzić określoną grupę alokacji, jawnie wywołując funkcje sterty debugowania w celu przydzielenia pamięci i określając, że bloki mają przypisany typ bloku **_CLIENT_BLOCK** . Te bloki mogą być następnie śledzone oddzielnie i raportowane w różny sposób podczas wykrywania przecieków i raportowania stanu pamięci.

Jeśli pole bitowe **_CRTDBG_ALLOC_MEM_DF** flagi [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) nie jest włączone, **_CrtDoForAllClientObjects** natychmiast zwraca wartość. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtDoForAllClientObjects** są usuwane podczas przetwarzania wstępnego.

Aby uzyskać więcej informacji o typie **_CLIENT_BLOCK** i sposobach ich użycia przez inne funkcje debugowania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Jeśli *PFN* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ma wartość **EINVAL** , a funkcja zwraca.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Bibliotece** Debuguj tylko wersje uniwersalnych bibliotek uruchomieniowych języka C.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
