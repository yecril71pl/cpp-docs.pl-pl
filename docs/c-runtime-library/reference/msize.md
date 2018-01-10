---
title: "_msize — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _msize
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
- msize
- _msize
dev_langs: C++
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ebc066e9ad01ff08014ed9174d0ca4915ea1868f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="msize"></a>_msize
Zwraca rozmiar bloku pamięci przydzielić w stercie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      size_t _msize(  
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Wskaźnik do bloku pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_msize`Zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.  
  
## <a name="remarks"></a>Uwagi  
 `_msize` Funkcja zwraca rozmiar w bajtach blok pamięci przydzielonej przez wywołanie `calloc`, `malloc`, lub `realloc`.  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `_msize` jest rozpoznawana jako [_msize_dbg —](../../c-runtime-library/reference/msize-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Ta funkcja weryfikuje jej parametr. Jeśli `memblock` wskaźnika o wartości null, jest `_msize` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli ten błąd jest obsługiwane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_msize`|\<malloc.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [realloc](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [_rozszerz lokację](../../c-runtime-library/reference/expand.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)