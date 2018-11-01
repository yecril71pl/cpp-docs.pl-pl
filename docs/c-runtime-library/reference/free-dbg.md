---
title: _free_dbg
ms.date: 11/04/2016
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 5a0024101e4f5a74f1573b271d444b27738db8e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442253"
---
# <a name="freedbg"></a>_free_dbg

Zwalnia blok pamięci w stercie (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parametry

*danych użytkownika*<br/>
Wskaźnik do bloku ilość przydzielonej pamięci, który ma zostać zwolniony.

*blockType*<br/>
Typ bloku ilość przydzielonej pamięci, która będzie zwolniona: **_CLIENT_BLOCK**, **_NORMAL_BLOCK**, lub **_IGNORE_BLOCK**.

## <a name="remarks"></a>Uwagi

**_Free_dbg —** funkcja jest wersją debugowania [bezpłatne](free.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_free_dbg —** jest ograniczone do wywołania **bezpłatne**. Zarówno **bezpłatne** i **_free_dbg —** zwolnieniu bloku pamięci na stosie podstawowym, ale **_free_dbg —** obsługuje dwie funkcje debugowania: możliwość przechowywania zwolnione bloki na stercie połączonej listy symulowanie warunków małej ilości pamięci i parametr typu blok, aby zwolnić określonych typów alokacji.

**_free_dbg —** wykonuje sprawdzanie poprawności dla wszystkich określonych plików i lokalizacje bloku przed wykonaniem tej operacji bezpłatne. Nie oczekiwano aplikacji może przekazać tę informację. Gdy blok pamięci jest zwalniana, Menedżer stosu debugowania automatycznie sprawdza spójność buforów po obu stronach części użytkownika i generuje raport o błędach, jeżeli zastąpienie wystąpiło. Jeśli **_CRTDBG_DELAY_FREE_MEM_DF** pola bitowego [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) flaga jest ustawiona, zwolnione blok zostanie wypełnione wartością 0xDD, przypisane **_FREE_BLOCK** typ, bloku i trzymane w połączonej liście stosu, bloków pamięci.

W przypadku wystąpienia błędu w zwalnianie pamięci, **errno** została ustawiona za pomocą informacji z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Przykład sposobu użycia **_free_dbg —**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
