---
title: _rozszerz lokację | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f709df131ded856881dc171c2e1549d3d5d378e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402354"
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
Wskaźnik do bloku wcześniej alokacji pamięci.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_rozszerz lokację** zwraca typ void wskaźnik do bloku przydzielić pamięci. **_rozszerz lokację**, w przeciwieństwie do **realloc**, nie można przenieść bloku, aby zmienić jego rozmiaru. W związku z tym, jeśli istnieje wystarczająca ilość pamięci rozwinąć blok bez przenoszenia go, *memblock* parametr **_rozszerz lokację** jest taka sama jak wartość zwracaną.

**_rozszerz lokację** zwraca **NULL** gdy zostaje wykryty błąd podczas jego działania. Na przykład jeśli **_rozszerz lokację** jest używany do zmniejszania blok pamięci, go może wykrywać uszkodzenia w stercie niewielki blok lub bloku nieprawidłowy wskaźnik i zwracać **NULL**.

Jeśli jest za mało pamięci rozwinąć blok na dany rozmiar bez przenoszenia go, funkcja zwraca **NULL**. **_rozszerz lokację** nigdy nie zwraca blok rozszerzonej na rozmiar mniej niż żądana. Jeśli wystąpi błąd, **errno** wskazuje naturę niepowodzenia. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby sprawdzić nowy rozmiar elementu, użyj **_msize —**. Aby otrzymywać wskaźnik do typu innego niż **void**, użyj typu rzutowania wartości zwracanej.

## <a name="remarks"></a>Uwagi

**_Rozszerz lokację** funkcja zmienia rozmiar bloku wcześniej alokacji pamięci próbując rozwiń lub Zwiń bloku bez przenoszenia jego lokalizacji w stosie. *Memblock* parametr wskazuje na początku bloku. *Rozmiar* parametru zapewnia nowy rozmiar bloku, w bajtach. Treść bloku nie uległy zmianie do krótszej z nowym i starym rozmiary. *memblock* nie może być blokiem został zwolniony.

> [!NOTE]
> Na platformach 64-bitowych **_rozszerz lokację** nie może być kontraktu bloku, jeśli nowy rozmiar jest mniejszy niż bieżący rozmiar; w szczególności, jeśli blok był mniejszy niż 16 KB, rozmiar i w związku z tym przydzielić w stercie fragmentacji małej **_rozszerz lokację**  opuszcza blok bez zmian i zwraca *memblock*.

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **_rozszerz lokację** jest rozpoznawana jako [_expand_dbg —](expand-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja weryfikuje jego parametrów. Jeśli *memblock* jest wskaźnika o wartości null, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**. Jeśli *rozmiar* jest większa niż **_heap_maxreq —**, **errno** ustawiono **enomem —** i funkcja zwraca **NULL**.

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
