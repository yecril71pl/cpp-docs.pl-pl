---
title: "_Crtisvalidpointer — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs: C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba249bc78b2e6b6aac95bef2c39b0d9526489ec9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer
Sprawdza, czy wskaźnik nie jest zerowa. W wersji biblioteki wykonawcze języka C przed Visual Studio 2010 sprawdza, czy pamięci określony zakres jest nieprawidłowy do odczytu i zapisu (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 adres  
 Wskazuje początek zakresu pamięci, aby sprawdzić poprawność.  
  
 `size`  
 Rozmiar pamięci określony zakres (w bajtach).  
  
 dostęp  
 Ułatwienia dostępu odczytu i zapisu do określenia zakresu pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_CrtIsValidPointer`Zwraca wartość PRAWDA, jeśli określony wskaźnik nie jest zerowa. W wersjach biblioteki CRT przed Visual Studio 2010 zwraca wartość PRAWDA, jeśli zakres pamięci jest nieprawidłowa dla określonej operacji. W przeciwnym razie funkcja zwraca wartość FALSE.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od biblioteki CRT w Visual Studio 2010, rozmiarów i dostępu do parametrów są ignorowane, a `_CrtIsValidPointer` tylko sprawdza, czy określony adres nie jest zerowa. Ponieważ ten test jest łatwe do wykonania samodzielnie, nie zaleca się, że aby użyć tej funkcji. W wersjach przed Visual Studio 2010, funkcja sprawdza, czy zakres pamięci, rozpoczynając od `address` i rozszerzanie dla `size` bajtów jest prawidłowa dla dostępności określonej operacji. Gdy `access` jest ustawiony na wartość TRUE, zakresu pamięci jest weryfikowany na odczytywanie i zapisywanie. Gdy `access` ma wartość FALSE, zakresu pamięci uwierzytelnieniu się tylko do odczytu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtIsValidPointer` są usuwane podczas przetwarzania wstępnego.  
  
 Ponieważ ta funkcja zwraca wartość PRAWDA lub FAŁSZ, mogą być przekazywane do jednego z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli zakres pamięci nie jest prawidłowy dla odczytywanie i zapisywanie operacji:  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 Aby uzyskać więcej informacji o tym, jak `_CrtIsValidPointer` może być używany z innymi funkcje debugowania i makra, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtIsValidPointer`|\<crtdbg.h >|  
  
 `_CrtIsValidPointer`to rozszerzenie firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_crtisvalidheappointer —](../../c-runtime-library/reference/crtisvalidheappointer.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)