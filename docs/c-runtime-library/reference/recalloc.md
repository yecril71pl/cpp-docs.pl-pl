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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 45f483bcaa397969a81097768ebbd1ed4cda288b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226193"
---
# <a name="_recalloc"></a>_recalloc

Kombinacja elementów **realloc** i **calloc**. Ponownie przydziela tablicę w pamięci i inicjuje jej elementy w wartości 0.

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
Wskaźnik do wcześniej przydzielony blok pamięci.

*liczba*<br/>
Liczba elementów.

*zmienia*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**_recalloc** zwraca **`void`** wskaźnik do ponownie przydzielony blok pamięci (i prawdopodobnie został przeniesiony).

Jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozszerzyć blok do danego rozmiaru, oryginalny blok pozostaje niezmieniony i zwracana jest **wartość null** .

Jeśli żądany rozmiar wynosi zero, zostanie zwolniony blok wskazywany przez *memblock* . zwracana wartość ma wartość **null**, a *memblock* pozostawia w bloku zwolnionym.

Wartość zwracana wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **`void`** , należy użyć rzutowania typu dla zwracanej wartości.

## <a name="remarks"></a>Uwagi

Funkcja **_recalloc** zmienia rozmiar przydzielony blok pamięci. Argument *memblock* wskazuje początek bloku pamięci. Jeśli *memblock* ma **wartość null**, **_recalloc** zachowuje się tak samo jak [calloc](calloc.md) i przydziela nowy *blok o*  *  *rozmiarze* bajtów. Każdy element jest inicjowany do wartości 0. Jeśli *memblock* nie ma **wartości null**, powinien być wskaźnikiem zwróconym przez poprzednie wywołanie metody **calloc**, [malloc](malloc.md)lub [realloc](realloc.md).

Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez **_recalloc** nie gwarantuje, że wskaźnik przeszedł przez argument *memblock* .

**_recalloc** ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiedzie się lub jeśli żądana ilość pamięci przekroczy **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** wywołuje zmianę **alokacji** , aby użyć funkcji [_set_new_mode](set-new-mode.md) języka C++ do ustawienia nowego trybu obsługi. Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **realloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie **realloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. To zachowanie domyślne można przesłonić, aby w przypadku niepowodzenia przydzielenia pamięci przez **_recalloc** funkcja **realloc** wywołuje nową procedurę obsługi w taki sam sposób, w jaki **`new`** operator wykonuje, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, Połącz

```C
_set_new_mode(1);
```

Wczesne w programie lub Połącz z NEWMODE. OBJ.

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **_recalloc** jest rozpoznawana jako [_recalloc_dbg](recalloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)` , co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[zwolniony](free.md)<br/>
[Opcje łącza](../../c-runtime-library/link-options.md)<br/>
