---
title: "set_unexpected — (CRT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_unexpected
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
- set_unexpected
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edc1d3b96ee5b52d349b30434932d2c9770267b4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)
Instaluje własnej funkcji zakończenia ma zostać wywołana przez `unexpected`.  
  
## <a name="syntax"></a>Składnia  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `unexpFunction`  
 Wskaźnik do funkcji, która zapisu zastąpić `unexpected` funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do funkcji zakończenia poprzedniej zarejestrowany przez `_set_unexpected` tak, aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.  
  
## <a name="remarks"></a>Uwagi  
 `set_unexpected` Funkcji instaluje `unexpFunction` jako funkcja wywoływana przez `unexpected`. `unexpected` nie jest używany w obecnej obsługi wyjątków C++. `unexpected_function` Typ jest zdefiniowany w EH. H jako wskaźnik do zdefiniowanych przez użytkownika funkcji nieoczekiwany, `unexpFunction` zwracającą `void`. Niestandardowe `unexpFunction` funkcja nie może zwracać do swojego obiektu wywołującego.  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 Domyślnie `unexpected` wywołania `terminate`. To zachowanie domyślne można zmienić, pisanie funkcji zakończenia i wywołanie `set_unexpected` z nazwą funkcji jako jej argument. `unexpected` wywołuje ostatniej podany jako argument do funkcji `set_unexpected`.  
  
 W odróżnieniu od funkcji niestandardowych zakończenia zainstalowane przez wywołanie do `set_terminate`, może zostać wygenerowany wyjątek z poziomu `unexpFunction`.  
  
 W środowisku wielowątkowym nieoczekiwany funkcje są obsługiwane osobno dla każdego wątku. Każdym nowym wątku, należy zainstalować nieoczekiwany funkcji. W związku z tym każdy wątek jest odpowiedzialny za własną nieoczekiwany obsługi.  
  
 Bieżący implementacji Microsoft C++, obsługa wyjątków `unexpected` wywołania `terminate` domyślnie i nigdy nie jest wywoływany przez biblioteki wykonawczej obsługi wyjątków. Nie ma żadnych dodatkowych zalet określonego wywołania `unexpected` zamiast `terminate`.  
  
 Istnieje jeden `set_unexpected` obsługę wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy jest wywoływana `set_unexpected` programu obsługi może być zastąpiony innym lub użytkownik zastępuje obsługi ustawiony przez inny plik DLL lub EXE.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`set_unexpected`|\<eh.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)   
 [Przerwania](../../c-runtime-library/reference/abort.md)   
 [_get_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set_terminate —](../../c-runtime-library/reference/set-terminate-crt.md)   
 [Zakończenie](../../c-runtime-library/reference/terminate-crt.md)   
 [Nieoczekiwany](../../c-runtime-library/reference/unexpected-crt.md)