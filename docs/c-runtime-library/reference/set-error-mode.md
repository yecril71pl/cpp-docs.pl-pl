---
title: "_set_error_mode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_error_mode
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
- set_error_mode
- _set_error_mode
dev_langs: C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 12152137e899fbc5e8d73679bcda57fce5ff5f72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="seterrormode"></a>_set_error_mode
Modyfikuje `__error_mode` do określenia lokalizacji innych niż domyślne, gdzie C runtime zapisuje komunikat o błędzie dla błędu, który może zakończyć program.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `modeval`  
 Miejsce docelowe komunikaty o błędach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca stare ustawienia lub wartość -1, jeśli wystąpi błąd.  
  
## <a name="remarks"></a>Uwagi  
 Określa ujście danych wyjściowych błędu, ustawiając wartość `__error_mode`. Na przykład Przekieruj dane wyjściowe do standardowego błędu lub użyj `MessageBox` interfejsu API.  
  
 `modeval` Parametr może należeć do jednej z następujących wartości.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_OUT_TO_DEFAULT`|Błąd zbiornika jest określany przez `__app_type`.|  
|`_OUT_TO_STDERR`|Błąd zbiornika jest błąd standardowy.|  
|`_OUT_TO_MSGBOX`|Błąd zbiornika jest okno komunikatu.|  
|`_REPORT_ERRMODE`|Bieżący raport `__error_mode` wartość.|  
  
 Jeśli przekazano wartość inną niż wymienione program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `_set_error_mode` ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
 Gdy jest używana z [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md), `_set_error_mode` wyświetla instrukcji nie powiodło się w oknie dialogowym i umożliwia wybór `Ignore` przycisk Tak, aby można kontynuować do uruchomienia programu.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_set_error_mode`|\<stdlib.h >|  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
```Output  
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Assert — makro, _assert, _wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)