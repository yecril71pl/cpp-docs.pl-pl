---
title: "_Crtmemcheckpoint — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
dev_langs: C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4abb20ba85407e12c71ca83af7dce96eb0f9d751
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint
Pobiera bieżący stan sterty debugowania i zapisuje w dostarczonych aplikacji `_CrtMemState` struktury (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 Wskaźnik do `_CrtMemState` struktury umożliwia wypełnienie pamięci punktu kontrolnego.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtMemCheckpoint` Funkcja tworzy migawkę bieżącego stanu sterty debugowania w danym momencie. Ta migawka mogą być używane przez inne funkcje stanu sterty takich jak [_crtmemdifference —](../../c-runtime-library/reference/crtmemdifference.md) ułatwia wykrywanie przecieków pamięci i innych problemów. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtMemState` są usuwane podczas przetwarzania wstępnego.  
  
 Aplikacja musi przekazać wskaźnik do wcześniej alokowanego wystąpienia elementu `_CrtMemState` struktury zdefiniowane w Crtdbg.h, w `state` parametru. Jeśli `_CrtMemCheckpoint` napotka błąd podczas tworzenia punktu kontrolnego, funkcja generuje `_CRT_WARN` debugowania raport opisujący problem.  
  
 Aby uzyskać więcej informacji na temat funkcji stanu sterty i `_CrtMemState` struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Jeśli `state` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono `EINVAL` i zwraca funkcję.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtMemCheckpoint`|\<crtdbg.h >, \<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
 **Biblioteki:** wersja biblioteka UCRT tylko debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_Crtmemdifference —](../../c-runtime-library/reference/crtmemdifference.md)