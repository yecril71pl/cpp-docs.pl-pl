---
title: longjmp | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- longjmp
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
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f80495e9c3e9fa7ce39dac8811e474f68844d196
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="longjmp"></a>longjmp
Przywraca stosu środowiska i ustawień regionalnych wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `env`  
 Zmienna, w której jest przechowywany środowiska.  
  
 *value*  
 Wartość zwracana do `setjmp` wywołania.  
  
## <a name="remarks"></a>Uwagi  
 `longjmp` Środowisku stosu przywraca funkcji i ustawień regionalnych wykonywania wcześniej zapisanych w `env` przez `setjmp`. `setjmp` i `longjmp` umożliwiają wykonanie nielokalne `goto`; zwykle służą one do przekazania Kontrola wykonywania do obsługi błędów lub kod odzyskiwania w wcześniej wywołana procedura bez użycia normalnej wywołanie i zwrócić Konwencji.  
  
 Wywołanie `setjmp` powoduje, że do zapisania w bieżącym środowisku stosu `env`. Kolejne wywołania `longjmp` przywraca zapisanego środowiska i zwraca sterowania do punktu bezpośrednio po odpowiadającego `setjmp` wywołania. Wznawia wykonywanie tak, jakby *wartość* miał właśnie zostały zwrócone przez `setjmp` wywołania. Wartości zmiennych wszystkie (z wyjątkiem zmienne rejestru), które są dostępne dla procedury odbieranie kontroli zawierają wartości podczas obliczania miało `longjmp` została wywołana. Wartości zmiennych rejestru są nieprzewidywalne. Wartość zwrócona przez `setjmp` musi być różna od zera. Jeśli *wartość* jest przekazywany jako 0, wartość 1 zastępuje rzeczywiste powrotu.  
  
 Wywołanie `longjmp` przed funkcją, która wywołuje `setjmp` zwraca; w przeciwnym razie są nieprzewidywalne wyniki.  
  
 Sprawdź następujące ograniczenia, używając `longjmp`:  
  
-   Zakłada się, że wartości zmiennych rejestru jest taka sama. Wartości zmiennych rejestru w wywołaniu procedury `setjmp` nie mogą być przywracane do odpowiednich wartości po `longjmp` jest wykonywana.  
  
-   Nie używaj `longjmp` do przekazywania kontroli procedury obsługi przerwań, chyba że przerwania jest spowodowany przez zmiennoprzecinkowych wyjątków. W takim przypadku program może zwrócić z obsługi przerwań za pośrednictwem `longjmp` jeśli ją najpierw ponownie inicjuje pakietu zmiennoprzecinkowej matematyczny przez wywołanie metody `_fpreset`.  
  
     **Uwaga** należy zachować ostrożność przy użyciu `setjmp` i `longjmp` w programach języka C++. Ponieważ te funkcje nie obsługują semantyki obiektu języka C++, bezpieczniej jest używany mechanizm obsługi wyjątków C++.  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`longjmp`|\<setjmp.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_fpreset —](../../c-runtime-library/reference/fpreset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)