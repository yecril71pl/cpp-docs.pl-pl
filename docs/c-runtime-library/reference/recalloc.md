---
title: _recalloc
ms.date: 11/04/2016
apiname:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 3bcc238dcb950a8e30af16efc557e99d933efe92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357725"
---
# <a name="recalloc"></a>_recalloc

Kombinacji **realloc** i **calloc**. Przydzieli tablicy w pamięci i inicjuje jego elementy na 0.

## <a name="syntax"></a>Składnia

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**_recalloc —** zwraca **void** wskaźnik do bloku pamięci ponownie przydzielane (i ewentualnie przenoszenia).

Jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar, oryginalnym bloku pozostanie niezmieniona, a **NULL** jest zwracana.

Jeśli żądany rozmiar jest równy zero, a następnie blok wskazywany przez *memblock* jest zwalniana; wartość zwracana jest **NULL**, i *memblock* pozostanie wskazującego zwolnione blok.

Zwracana wartość wskazuje miejsce do magazynowania, który gwarantuje bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, użyj typu rzutowanego na wartość zwracaną.

## <a name="remarks"></a>Uwagi

**_Recalloc —** funkcja zmieni rozmiar bloku ilość przydzielonej pamięci. *Memblock* argument wskazuje na początku bloku pamięci. Jeśli *memblock* jest **NULL**, **_recalloc —** działa tak samo jak [calloc](calloc.md) i przydziela blok nowe *numer*  *  *rozmiar* bajtów. Każdy element jest inicjowana wartością 0. Jeśli *memblock* nie jest **NULL**, wskaźnik zwracany przez poprzednie wywołanie powinno być **calloc**, [— funkcja malloc](malloc.md), lub [realloc ](realloc.md).

Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez **_recalloc —** nie musi zostać przekazany przez wskaźnik myszy *memblock* argumentu.

**_recalloc —** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub Jeśli żądana ilość pamięci, przekracza **_heap_maxreq —**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc —** wywołania **realloc** aby można było używać C++ [_set_new_mode](set-new-mode.md) funkcję, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **realloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **realloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **_recalloc —** nie może przydzielić pamięci, **realloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** — operator Nie, gdy zakończy się niepowodzeniem z tego samego powodu. Aby zastąpić domyślne, należy wywołać

```C
_set_new_mode(1);
```

wcześniej program, lub Połącz z NEWMODE.OBJ.

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **_recalloc —** jest rozpoznawana jako [_recalloc_dbg —](recalloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc —** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> and \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[Opcje łącz](../../c-runtime-library/link-options.md)<br/>
