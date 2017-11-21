---
title: _set_app_type | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_app_type
apilocation: api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs: C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86078a8ff66eadc1cdd6b177ba074abfd1683345
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setapptype"></a>_set_app_type
Funkcji wewnętrznej używane przy uruchamianiu CRT stwierdzić, czy aplikacja jest aplikacji konsoli lub graficznego interfejsu użytkownika aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    ); 
```  
  
## <a name="parameters"></a>Parametry  
 `appType`  
 Wartość, która wskazuje typ aplikacji. Możliwe wartości to:  
  
|Wartość|Opis|  
|----------------|-----------------|  
|_crt_unknown_app|Typ nieznanej aplikacji.|  
|_crt_console_app|Aplikacja konsoli (wiersza polecenia).|  
|_crt_gui_app|Aplikacja graficznego interfejsu użytkownika (Windows).|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj wywołanie tej funkcji nie jest konieczne. Jest on częścią kod uruchomienia środowiska uruchomieniowego C, która wykonuje przed `main` jest wywoływana w aplikacji.
 
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|_set_app_type|process.h|

