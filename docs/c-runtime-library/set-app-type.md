---
title: _set_app_type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs:
- C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9b3901cb031a1cc08d911889dc97818cfb5a44
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410184"
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

