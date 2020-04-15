---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347555"
---
# <a name="_expand"></a>_expand

Zmienia rozmiar bloku pamięci.

## <a name="syntax"></a>Składnia

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do wcześniej przydzielonego bloku pamięci.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_expand** zwraca wskaźnik void do ponownie przydzielonego bloku pamięci. **_expand**, w przeciwieństwie do **realokacji,** nie może przenieść bloku, aby zmienić jego rozmiar. W związku z tym jeśli jest dostępna wystarczająca ilość pamięci, aby rozwinąć blok bez przenoszenia go, *parametr memblock* **do _expand** jest taki sam jak wartość zwracana.

**_expand** zwraca **wartość NULL** po wykryciu błędu podczas jego działania. Na przykład jeśli **_expand** jest używany do zmniejszania bloku pamięci, może wykryć uszkodzenie w stercie małego bloku lub nieprawidłowy wskaźnik bloku i zwrócić **wartość NULL**.

Jeśli nie ma wystarczającej ilości pamięci, aby rozwinąć blok do danego rozmiaru bez przenoszenia go, funkcja zwraca **wartość NULL**. **_expand** nigdy nie zwraca bloku rozwiniętego do rozmiaru mniejszego niż żądano. Jeśli wystąpi błąd, **errno** wskazuje charakter błędu. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby sprawdzić nowy rozmiar elementu, użyj **_msize**. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć typu rzutu na wartość zwracaną.

## <a name="remarks"></a>Uwagi

Funkcja **_expand** zmienia rozmiar wcześniej przydzielonego bloku pamięci, próbując rozwinąć lub umowy bloku bez przenoszenia jego lokalizacji w stosie. Parametr *memblock* wskazuje początek bloku. Parametr *size* daje nowy rozmiar bloku w bajtach. Zawartość bloku pozostaje niezmieniona do krótszego rozmiaru nowych i starych. *memblock* nie powinien być blokiem, który został uwolniony.

> [!NOTE]
> Na platformach 64-bitowych **_expand** może nie umowy bloku, jeśli nowy rozmiar jest mniejszy niż bieżący rozmiar; w szczególności, jeśli blok był mniejszy niż 16K wielkości i dlatego przydzielone w niskiej fragmentacji sterty, **_expand** pozostawia blok bez zmian i zwraca *memblock*.

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **_expand** jest _expand_dbg [.](expand-dbg.md) Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *memblock* jest wskaźnikiem null, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**. Jeśli *rozmiar* jest większy niż **_HEAP_MAXREQ,** **errno** jest ustawiona na **ENOMEM,** a funkcja zwraca **wartość NULL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_expand**|\<> malloc.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Wolna](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
