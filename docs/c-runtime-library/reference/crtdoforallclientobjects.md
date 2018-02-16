---
title: "_Crtdoforallclientobjects — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1da4ada3286b863444bb567a4fad8cf693f9253
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects
Wywołania funkcji aplikacji dla wszystkich `_CLIENT_BLOCK` typy w stercie (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _CrtDoForAllClientObjects(   
   void ( * pfn )( void *, void * ),  
   void *context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfn`  
 Wskaźnik do funkcji wywołania zwrotnego funkcji aplikacji. Pierwszy parametr do funkcji punktów danych. Drugi parametr jest wskaźnik kontekstu przekazywany do wywołania `_CrtDoForAllClientObjects`.  
  
 `context`  
 Wskaźnik do kontekstu dostarczone przez aplikację do przekazania do funkcji aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtDoForAllClientObjects` Funkcja wyszukuje połączonej listy sterty dla bloków pamięci z `_CLIENT_BLOCK` typu i wywołań znajduje się funkcja dostarczone przez aplikację po bloku tego typu. Znaleziono bloku i `context` parametrów są przekazywane jako argumenty do funkcji aplikacji. Podczas debugowania aplikacji można śledzić określonej grupy alokacji jawnie podczas wywoływania debugowania funkcje sterty przydzielić pamięci i określając, że bloki można przypisać `_CLIENT_BLOCK` zablokować typu. Następnie można osobno i zgłaszanych na inaczej podczas wykrywania przecieków i raportowanie stanu pamięci te bloki.  
  
 Jeśli `_CRTDBG_ALLOC_MEM_DF` pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) flaga nie jest włączona, `_CrtDoForAllClientObjects` natychmiast zwraca. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtDoForAllClientObjects` są usuwane podczas przetwarzania wstępnego.  
  
 Aby uzyskać więcej informacji na temat `_CLIENT_BLOCK` typu i może służyć za inne funkcje debugowania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Jeśli `pfn` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono `EINVAL` i zwraca funkcję.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtDoForAllClientObjects`|\<crtdbg.h>, \<errno.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
 **Biblioteki:** wersja universal C biblioteki wykonawcze tylko debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)   
 [Funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)