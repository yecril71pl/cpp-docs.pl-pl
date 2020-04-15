---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338122"
---
# <a name="_recalloc"></a>_recalloc

Połączenie **realloc** i **calloc**. Ponownie przydziela tablicę w pamięci i inicjuje jej elementy do 0.

## <a name="syntax"></a>Składnia

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do wcześniej przydzielonego bloku pamięci.

*numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**_recalloc** zwraca wskaźnik **void** do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci.

Jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru, oryginalny blok pozostaje niezmieniony, a **null** jest zwracany.

Jeśli żądany rozmiar wynosi zero, blok wskazywał *przez blok memblock* jest zwalniany; zwracana wartość **null**, a *memblock* jest pozostawiony wskazujący na zwolniony blok.

Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć typu rzutu na wartość zwracaną.

## <a name="remarks"></a>Uwagi

Funkcja **_recalloc** zmienia rozmiar przydzielonego bloku pamięci. Argument *memblock* wskazuje na początek bloku pamięci. Jeśli *memblock* ma **wartość NULL**, **_recalloc** zachowuje się tak samo jak [calloc](calloc.md) i przydziela nowy blok*bajtów rozmiaru* *liczb.* *  Każdy element jest inicjowany do 0. Jeśli *memblock* nie ma **wartości NULL**, powinien to być wskaźnik zwrócony przez poprzednie wywołanie **calloc**, [malloc](malloc.md)lub [realloc](realloc.md).

Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwrócony przez **_recalloc** nie jest gwarantowana jako wskaźnik przeszedł przez argument *memblock.*

**_recalloc** ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiedzie się lub jeśli ilość żądanej pamięci przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** wywołuje **realloc** w celu użycia funkcji [_set_new_mode](set-new-mode.md) C++ do ustawiania nowego trybu obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii **realloc** jest wywołanie nowej procedury obsługi zgodnie z [_set_new_handler](set-new-handler.md). Domyślnie **realloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to zachowanie domyślne, tak aby, gdy **_recalloc** nie można przydzielić pamięci, **realloc** wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną,

```C
_set_new_mode(1);
```

na początku programu, lub link z NEWMODE.OBJ.

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **_recalloc** jest _recalloc_dbg [.](recalloc-dbg.md) Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** jest oznaczony `__declspec(noalias)` `__declspec(restrict)`i , co oznacza, że funkcja jest gwarantowana nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_recalloc**|\<> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[Wolna](free.md)<br/>
[Opcje łącza](../../c-runtime-library/link-options.md)<br/>
