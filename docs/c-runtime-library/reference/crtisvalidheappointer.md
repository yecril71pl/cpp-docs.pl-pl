---
title: "_Crtisvalidheappointer — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f888466e0b1625f93c4e1cf66fab0bb85678094
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer
Sprawdza, czy określony wskaźnik jest w stercie przydzielone przez niektóre biblioteki wykonawczej języka C, ale niekoniecznie Biblioteka CRT obiektu wywołującego. W wersjach CRT przed Visual Studio 2010 sprawdza, czy określony wskaźnik znajduje się w lokalnej sterty (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int _CrtIsValidHeapPointer(   
   const void *userData   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Wskaźnik do początku blok pamięci przydzielony.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_CrtIsValidHeapPointer` Zwraca wartość PRAWDA, jeśli określony wskaźnik jest w stercie współużytkowane przez wszystkie wystąpienia biblioteki CRT. W wersjach CRT przed Visual Studio 2010 to zwraca wartość TRUE, jeśli określony wskaźnik znajduje się w lokalnej sterty. W przeciwnym razie funkcja zwraca wartość FALSE.  
  
## <a name="remarks"></a>Uwagi  
 Nie zaleca się użycie tej funkcji. Począwszy od programu Visual Studio 2010 CRT biblioteki wszystkich bibliotek CRT udostępniania jednego sterty systemu operacyjnego, *sterty procesu*. `_CrtIsValidHeapPointer` Funkcji raportów, czy wskaźnik została przydzielona w stosie CRT, ale nie alokowanej Biblioteka CRT obiektu wywołującego. Rozważmy na przykład przydzielony przy użyciu programu Visual Studio 2010 biblioteki CRT bloku. Jeśli `_CrtIsValidHeapPointer` funkcji wyeksportowanej przez wersję programu Visual Studio 2012 biblioteki CRT testy wskaźnika, zwraca wartość TRUE. To nie jest już przydatne testu. W wersjach biblioteki CRT przed Visual Studio 2010 funkcja służy do upewnij się, że adres pamięci mieści się w lokalnej sterty. Lokalnej sterty odwołuje się do stosu tworzony i zarządzany przez konkretnego wystąpienia biblioteki wykonawczej języka C. Jeśli biblioteki dołączanej (dynamicznie DLL) zawiera statyczne łącze do biblioteki wykonawczej, ma własne wystąpienie sterty środowiska wykonawczego i dlatego jego własnej sterty, niezależnie od lokalnego stosu aplikacji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtIsValidHeapPointer` są usuwane podczas przetwarzania wstępnego.  
  
 Ponieważ ta funkcja zwraca wartość PRAWDA lub FAŁSZ, mogą być przekazywane do jednego z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli określony adres nie znajduje się w lokalnej sterty:  
  
```  
_ASSERTE( _CrtIsValidHeapPointer( userData ) );  
```  
  
 Aby uzyskać więcej informacji o tym, jak `_CrtIsValidHeapPointer` może być używany z innymi funkcje debugowania i makra, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtIsValidHeapPointer`|\<crtdbg.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób sprawdzić, czy pamięć jest prawidłowa, gdy jest używany z biblioteki wykonawcze języka C przed Visual Studio 2010. W tym przykładzie jest dostępna dla użytkowników kod biblioteki CRT starszej wersji.  
  
```  
// crt_isvalid.c  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then tests the validity of this memory by calling   
 * _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
#define  TRUE   1  
#define  FALSE  0  
  
int main( void )  
{  
        char *my_pointer;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header information  
         */  
        my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,   
        _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
        // Ensure that the memory got allocated correctly  
        _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,   
        NULL, NULL, NULL );  
  
         // Test for read/write accessibility  
        if (_CrtIsValidPointer((const void *)my_pointer,   
        sizeof(char) * 10, TRUE))  
                printf("my_pointer has read and write accessibility.\n");  
        else  
                printf("my_pointer only has read access.\n");  
  
        // Make sure my_pointer is within the local heap  
        if (_CrtIsValidHeapPointer((const void *)my_pointer))  
                printf("my_pointer is within the local heap.\n");  
        else  
                printf("my_pointer is not located within the local"  
                       " heap.\n");  
  
        free(my_pointer);  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
my_pointer has read and write accessibility.  
my_pointer is within the local heap.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)