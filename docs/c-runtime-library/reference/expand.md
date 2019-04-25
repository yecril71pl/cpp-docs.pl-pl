---
title: _expand
ms.date: 11/04/2016
apiname:
- _expand
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c1606bedbb1264bddb7674c829fe456f506d6584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335207"
---
# <a name="expand"></a>_expand

Zmienia rozmiar bloku pamięci.

## <a name="syntax"></a>Składnia

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_rozwiń** zwraca pusty wskaźnik do bloku pamięci ponownie przydzielona. **_rozwiń**, w przeciwieństwie do **realloc**, nie można przenieść bloku, aby zmienić jego rozmiar. Dlatego, jeśli istnieje wystarczająca ilość pamięci rozwinąć blok bez przenoszenia, *memblock* parametr **_rozwiń** jest taka sama jak wartość zwracaną.

**_rozwiń** zwraca **NULL** gdy zostanie wykryty błąd podczas jego działania. Na przykład jeśli **_rozwiń** jest używany, aby zmniejszyć bloku pamięci, jego może wykrywać uszkodzenia sterty małych blokach lub wskaźnik nieprawidłowy blok i powrócić **NULL**.

Jeśli jest za mało pamięci rozwinąć blok na dany rozmiar bez przenoszenia go, funkcja zwraca **NULL**. **_rozwiń** nigdy nie zwraca blok rozwinięty rozmiar mniej niż żądana. Jeśli wystąpi błąd, **errno** wskazuje naturę niepowodzenia. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Zwracana wartość wskazuje miejsce do magazynowania, który gwarantuje bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby sprawdzić nowy rozmiar elementu, użyj **_msize —**. Aby uzyskać wskaźnik do typu innego niż **void**, użyj typu rzutowanego na wartość zwracaną.

## <a name="remarks"></a>Uwagi

**_Rozwiń** funkcja zmienia rozmiar bloku pamięci uprzednio przydzielony spowodowany próbą rozwiń lub Zwiń blok bez przenoszenia jego lokalizację w stosie. *Memblock* parametr wskazuje na początku bloku. *Rozmiar* parametru zapewnia nowy rozmiar bloku, w bajtach. Zawartość bloku nie uległy zmianie maksymalnie krótszy z nowym i starym rozmiarów. *memblock* nie powinny być blok, który ma zostać zwolniony.

> [!NOTE]
> Na platformach 64-bitowych **_rozwiń** nie może być kontraktu bloku, jeśli nowy rozmiar jest mniejszy niż bieżący rozmiar; w szczególności, jeśli blok został mniej niż 16 KB, rozmiar i w związku z tym jest przydzielonych w niską fragmentację sterty **_rozwiń**  opuszcza blok bez zmian i zwraca *memblock*.

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **_rozwiń** jest rozpoznawana jako [_expand_dbg —](expand-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *memblock* jest pustym wskaźnikiem, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**. Jeśli *rozmiar* jest większa niż **_heap_maxreq —**, **errno** ustawiono **ENOMEM** a funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
