---
title: "_recalloc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _recalloc
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
dev_langs: C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 007f174b3cbdb7e8ca53af19b6f9764200ff690a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recalloc"></a>_recalloc
Kombinację `realloc` i `calloc`. Przydziela ponownie tablicy w pamięci i inicjuje swoich elementów na 0.  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Wskaźnik do bloku wcześniej alokacji pamięci.  
  
 `num`  
 Liczba elementów.  
  
 `size`  
 Długość w bajtach każdego elementu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_recalloc`Zwraca `void` wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia).  
  
 Jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar, oryginalnego bloku pozostanie niezmieniona, i `NULL` jest zwracany.  
  
 Jeśli żądany rozmiar wynosi zero, a następnie bloku wskazywana przez `memblock` zostanie zwolniona; jest zwracana wartość `NULL`, i `memblock` pozostanie wskazującego zwolnionych blok.  
  
 Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby otrzymywać wskaźnik do typu innego niż `void`, użyj typu rzutowania wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `_recalloc` Funkcja zmienia rozmiar bloku alokacji pamięci. `memblock` Argument wskazuje na początku bloku pamięci. Jeśli `memblock` jest `NULL`, `_recalloc` działa tak samo jak [calloc —](../../c-runtime-library/reference/calloc.md) i przydziela nowy blok `num`  *  `size` bajtów. Każdy element jest ustawiana na 0. Jeśli `memblock` nie jest `NULL`, należy go wskaźnik zwrócony przez poprzednie wywołanie `calloc`, [— funkcja malloc](../../c-runtime-library/reference/malloc.md), lub [realloc](../../c-runtime-library/reference/realloc.md).  
  
 Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwrócony przez `_recalloc` nie musi być wskaźnikiem przekazywane `memblock` argumentu.  
  
 `_recalloc`Ustawia `errno` do `ENOMEM` czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza `_HEAP_MAXREQ`. Aby uzyskać informacje na ten temat oraz innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `recalloc`wywołania `realloc` aby można było używać języka C++ [_set_new_mode —](../../c-runtime-library/reference/set-new-mode.md) funkcji, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, `realloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `realloc` nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy `_recalloc` nie może przydzielić pamięci, `realloc` wywołuje nowe procedury obsługi tak samo jak robi `new` operator nie w przypadku niepowodzenia tego samego powodu. Aby zastąpić domyślną, należy wywołać  
  
```  
_set_new_mode(1)  
```  
  
 wczesne w programie lub Połącz z biblioteką NEWMODE.OBJ.  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `_recalloc` jest rozpoznawana jako [_recalloc_dbg —](../../c-runtime-library/reference/recalloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_recalloc`jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i czy zwrócony wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_recalloc`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [_recalloc_dbg —](../../c-runtime-library/reference/recalloc-dbg.md)   
 [_aligned_recalloc —](../../c-runtime-library/reference/aligned-recalloc.md)   
 [_aligned_offset_recalloc —](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [w warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [Opcje łącz](../../c-runtime-library/link-options.md)