---
title: "_Crtismemoryblock — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
dev_langs: C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec6bea115ba509c7275a2d220cf4b10c6faecae9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock
Sprawdza, czy blok pamięci określony w lokalnej sterty i ma identyfikator typu bloku sterty debugowania prawidłowe (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`userData`  
 Wskaźnik na początku bloku pamięci, aby sprawdzić.  
  
 [in]`size`  
 Rozmiar określonego bloku (w bajtach).  
  
 [out]`requestNumber`  
 Wskaźnik do numer alokacji bloku lub `NULL`.  
  
 [out]`filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanego bloku lub `NULL`.  
  
 [out]`linenumber`  
 Wskaźnik do numeru wiersza w pliku źródłowym lub `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_CrtIsMemoryBlock`Zwraca `TRUE` Jeśli blok pamięci określony znajduje się w lokalnej sterty i ma identyfikator typu bloku sterty debugowania prawidłowe; w przeciwnym razie funkcja zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtIsMemoryBlock` Funkcja weryfikuje, czy blok pamięci określony znajduje się w lokalnej pamięci oraz ma identyfikator typu bloku prawidłowe. Tej funkcji można również uzyskać numer zamówienia obiekt alokacji i numer Nazwa/wiersza pliku źródłowego których alokacji blok pamięci był pierwotnie żądany. Przekazywanie wartości innej niż NULL dla `requestNumber`, `filename`, lub `linenumber` powoduje, że parametry `_CrtIsMemoryBlock` można ustawić parametry te wartości w nagłówku debugowania blok pamięci, w przypadku odnalezienia bloku w lokalnej sterty. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtIsMemoryBlock` są usuwane podczas przetwarzania wstępnego.  
  
 Jeśli `_CrtIsMemoryBlock` nie powiedzie się, zwraca `FALSE` i parametry wyjściowe są inicjowane wartości domyślne: `requestNumber` i `lineNumber` są ustawione na 0 i `filename` ma ustawioną wartość `NULL`.  
  
 Ponieważ ta funkcja zwraca `TRUE` lub `FALSE`, mogą być przekazywane do jednego z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli określony adres nie znajduje się w lokalnej sterty:  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 Aby uzyskać więcej informacji o tym, jak `_CrtIsMemoryBlock` może być używany z innymi funkcje debugowania i makra, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_crtisvalidheappointer —](../../c-runtime-library/reference/crtisvalidheappointer.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)