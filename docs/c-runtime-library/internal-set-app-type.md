---
title: __set_app_type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __set_app_type
- _set_app_type
apilocation:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __set_app_type
dev_langs:
- C++
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854873987cd83b89efc5c9006c1e091023c91226
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389065"
---
# <a name="setapptype"></a>__set_app_type
Ustawia bieżący typ aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __set_app_type (  
   int at  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `at`  
 Wartość, która wskazuje typ aplikacji. Możliwe wartości to:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|_UNKNOWN_APP|Typ nieznanej aplikacji.|  
|_CONSOLE_APP|Aplikacja konsoli (wiersza polecenia).|  
|_GUI_APP|Aplikacja graficznego interfejsu użytkownika (Windows).|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__set_app_type|internal.h|