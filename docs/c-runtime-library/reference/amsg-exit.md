---
title: _amsg_exit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _amsg_exit
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
f1_keywords: _amsg_exit
dev_langs: C++
helpviewer_keywords: _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7ce90e59ba20f81b8737c5f53c99b7cbc0ff3fdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="amsgexit"></a>_amsg_exit
Emituje komunikat o błędzie wykonawcze i kończy działanie aplikacji z kodem błędu 255.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void _amsg_exit (  
   int rterrnum  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `rterrnum`  
 Numer identyfikacyjny runtime zdefiniowanym przez system komunikatu o błędzie.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja emituje środowiska uruchomieniowego komunikat o błędzie **stderr** dla aplikacji konsoli lub wyświetlanie pola komunikatu do wiadomości dla aplikacji systemu Windows. W trybie debugowania można wywołać debugera przed zakończeniem.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|_amsg_exit|internal.h|