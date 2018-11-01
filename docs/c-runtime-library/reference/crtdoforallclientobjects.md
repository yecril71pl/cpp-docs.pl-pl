---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 86268bd9ac49c8ea27f715404236bcb9291f5d8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521193"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Wywołuje funkcję dostarczone przez aplikację dla wszystkich **_CLIENT_BLOCK** typy w stercie (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parametry

*nazwy pfn*<br/>
Wskaźnik do funkcji wywołania zwrotnego dostarczonej przez aplikację funkcji. Pierwszy parametr do tej funkcji punktów danych. Drugi parametr jest wskaźnik kontekstu, który jest przekazywany do wywołania **_CrtDoForAllClientObjects**.

*Kontekst*<br/>
Wskaźnik do kontekstu dostarczone przez aplikację do przekazania do funkcji dostarczonych aplikacji.

## <a name="remarks"></a>Uwagi

**_CrtDoForAllClientObjects** Funkcja przeszukuje połączonej liście stosu, bloków pamięci za pomocą **_CLIENT_BLOCK** typu i wywołań, znajduje się funkcja dostarczone przez aplikację, gdy blok tego typu. Znaleziono bloku i *kontekstu* parametru są przekazywane jako argumenty do funkcji dostarczonych aplikacji. Podczas debugowania aplikacji można śledzić określonej grupy alokacji przez jawne wywołanie funkcji sterty w celu przydzielenia pamięci debugowania i określenie, że można przypisać te bloki **_CLIENT_BLOCK** typ bloku. Te bloki, następnie można osobno i inaczej zgłoszone podczas wykrywania przecieków i raportowania stanu pamięci.

Jeśli **_CRTDBG_ALLOC_MEM_DF** pola bitowego [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) flaga nie jest włączona, **_CrtDoForAllClientObjects** natychmiast powraca. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtDoForAllClientObjects** są usuwane podczas przetwarzania wstępnego.

Aby uzyskać więcej informacji na temat **_CLIENT_BLOCK** wpisz i może służyć przez inne funkcje debugowania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Jeśli *pfn* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono **EINVAL** a funkcja zwraca.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** universal C biblioteki wykonawczej tylko wersja debugowania.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funkcje raportowania stanu stosu](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
