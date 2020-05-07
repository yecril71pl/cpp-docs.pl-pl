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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8878bb046a122b545f969dd067c37eeb97126387
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920254"
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

*memblock*<br/>
Wskaźnik do wcześniej przydzielony blok pamięci.

*size*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_expand** zwraca wskaźnik void do ponownie przydzielony blok pamięci. **_expand**, w przeciwieństwie do **realloc**, nie można przenieść bloku, aby zmienić jego rozmiar. W takim przypadku, jeśli dostępna jest wystarczająca ilość pamięci, aby rozwinąć blok bez przechodzenia, parametr *memblock* do **_expand** jest taka sama jak wartość zwracana.

**_expand** zwraca **wartość null** w przypadku wykrycia błędu w trakcie jego działania. Na przykład jeśli **_expand** jest używany do zmniejszania bloku pamięci, może wykryć uszkodzenie w niewielkim stosie bloku lub na nieprawidłowym wskaźniku bloku i zwrócić **wartość null**.

Jeśli jest za mało dostępnej pamięci, aby rozwinąć blok do danego rozmiaru bez przechodzenia, funkcja zwraca **wartość null**. **_expand** nigdy nie zwraca bloku rozwiniętego do rozmiaru mniejszego niż żądana. Jeśli wystąpi awaria, **errno** wskazuje charakter błędu. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wartość zwracana wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby sprawdzić nowy rozmiar elementu, użyj **_msize**. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć rzutowania typu dla zwracanej wartości.

## <a name="remarks"></a>Uwagi

Funkcja **_expand** zmienia rozmiar poprzednio przydzielonego bloku pamięci, próbując rozwijać lub zwijać blok bez przenoszenia jego lokalizacji w stercie. Parametr *memblock* wskazuje początek bloku. Parametr *size* zawiera nowy rozmiar bloku, w bajtach. Zawartość bloku nie zmienia się na krótszy od nowych i starych rozmiarów. *memblock* nie powinien być blokiem, który został zwolniony.

> [!NOTE]
> Na platformach 64-bitowych **_expand** mogą nie kontraktować bloku, jeśli nowy rozmiar jest mniejszy niż bieżący rozmiar; w szczególności, jeśli rozmiar bloku był mniejszy niż 16 KB i dlatego przydzielono go w stercie o niskim fragmentacji, **_expand** pozostawia blok niezmieniony i zwraca *memblock*.

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **_expand** jest rozpoznawana jako [_expand_dbg](expand-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *memblock* jest wskaźnikiem typu null, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**. Jeśli *rozmiar* jest większy niż **_HEAP_MAXREQ**, **errno** jest ustawiona na **ENOMEM** , a funkcja zwraca **wartość null**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_expand**|\<malloc. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[zwolniony](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
