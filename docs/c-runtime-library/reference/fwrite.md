---
title: "fwrite — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fwrite
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords: fwrite
dev_langs: C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 98d965b6a8e12e2f27d1544bec07357c28c3b7ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fwrite"></a>fwrite
Zapisuje dane do strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t fwrite(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Wskaźnik do zapisania danych.  
  
 `size`  
 Rozmiar elementu w bajtach.  
  
 `count`  
 Maksymalna liczba elementów do zapisania.  
  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fwrite`Zwraca liczbę pełnych elementów zapisana, co może być mniejsza niż `count` w przypadku wystąpienia błędu. Ponadto jeśli wystąpi błąd, nie można ustalić wskaźnika położenia pliku. Jeśli dowolny `stream` lub `buffer` jest wskaźnika o wartości null, lub jeśli nieparzystą liczbę bajtów do zapisania określono w trybie Unicode, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 `fwrite` Funkcja zapisuje do `count` elementów, z `size` długość, z `buffer` z danymi wyjściowymi `stream`. Wskaźnika pliku skojarzone z `stream` (jeśli istnieje) jest zwiększany o liczba bajtów zapisanych w rzeczywistości. Jeśli `stream` jest otwarty w trybie tekstowym każdego wysuwu wiersza jest zastępowany znak powrotu karetki - pary wysuwu wiersza. Zastąpienie nie ma wpływu na wartość zwracaną.  
  
 Gdy `stream` jest otwarty w trybie translacji Unicode — na przykład, jeśli `stream` jest otwarty przez wywołanie metody `fopen` i przy użyciu trybu parametru, który zawiera `ccs=UNICODE`, `ccs=UTF-16LE`, lub `ccs=UTF-8`, lub jeśli tryb jest zmieniana na Unicode Tryb tłumaczenia przy użyciu `_setmode` i parametr tryb, który obejmuje `_O_WTEXT`, `_O_U16TEXT`, lub `_O_U8TEXT`—`buffer` jest interpretowany jako wskaźnik do tablicy `wchar_t` zawierający dane UTF-16. Próba zapisu nieparzystą liczbę bajtów w tym trybie powoduje błąd sprawdzania poprawności parametru.  
  
 Ponieważ ta funkcja umożliwia zablokowanie wątek wywołujący, jest bezpieczne wątkowo. Wersja — blokowanie dla `_fwrite_nolock`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fwrite`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [fread —](../../c-runtime-library/reference/fread.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_setmode —](../../c-runtime-library/reference/setmode.md)   
 [fread —](../../c-runtime-library/reference/fread.md)   
 [_fwrite_nolock —](../../c-runtime-library/reference/fwrite-nolock.md)   
 [_Write](../../c-runtime-library/reference/write.md)