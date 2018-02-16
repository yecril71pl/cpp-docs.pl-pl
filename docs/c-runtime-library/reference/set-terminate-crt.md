---
title: "set_terminate — (CRT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eba062bd1b791f055b2ae1c74c2a0107a4039d23
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)
Instaluje własnego procedury zakończenia ma zostać wywołana przez `terminate`.  
  
## <a name="syntax"></a>Składnia  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `termFunction`  
 Wskaźnik do funkcji przerwania, który można zapisać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do funkcji poprzednie zarejestrowane przez `set_terminate` tak, aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.  
  
## <a name="remarks"></a>Uwagi  
 `set_terminate` Funkcji instaluje `termFunction` jako funkcja wywoływana przez `terminate`. `set_terminate` jest używany z C++, obsługa wyjątków i może być wywoływana w dowolnym momencie w programie przed wyjątku. `terminate` wywołania `abort` domyślnie. To ustawienie domyślne można zmienić, pisanie funkcji zakończenia i wywołanie `set_terminate` z nazwą funkcji jako jej argument. `terminate` wywołuje ostatniej podany jako argument do funkcji `set_terminate`. Po wykonywania żądanego zadania oczyszczania `termFunction` powinno zakończyć program. Jeśli nie zostanie zamknięta (jeśli wraca do swojego obiektu wywołującego), `abort` jest wywoływana.  
  
 W środowisku wielowątkowym, należy zakończyć funkcje są obsługiwane osobno dla każdego wątku. Każdym nowym wątku, należy zainstalować ma własną funkcję przerwania. W związku z tym każdy wątek jest odpowiedzialny za własną obsługi zakończenia.  
  
 `terminate_function` Typ jest zdefiniowany w EH. H jako wskaźnik do funkcji zdefiniowanej przez użytkownika zakończenia `termFunction` zwracającą `void`. Niestandardowej funkcji `termFunction` może nie przyjmują argumentów i nie może zwracać do swojego obiektu wywołującego. Jeśli tak, `abort` jest wywoływana. Wyjątek nie może zostać zgłoszony z poziomu `termFunction`.  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  `set_terminate` Funkcja działa tylko poza debugerem.  
  
 Istnieje jeden `set_terminate` obsługę wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy jest wywoływana `set_terminate` programu obsługi mogą być zastąpione przez inny lub może być zastępowania obsługi ustawione przez innego pliku DLL lub EXE.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`set_terminate`|\<eh.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [przerwanie](../../c-runtime-library/reference/terminate-crt.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)   
 [Przerwania](../../c-runtime-library/reference/abort.md)   
 [_get_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [Zakończenie](../../c-runtime-library/reference/terminate-crt.md)   
 [Nieoczekiwany](../../c-runtime-library/reference/unexpected-crt.md)