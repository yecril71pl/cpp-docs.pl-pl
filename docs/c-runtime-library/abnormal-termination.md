---
title: _abnormal_termination | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords: _abnormal_termination
dev_langs: C++
helpviewer_keywords: _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 17dbe8079972626439f2706061258265303f5226
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="abnormaltermination"></a>_abnormal_termination
Wskazuje, czy `__finally` zablokować z [try-finally — instrukcja](../cpp/try-finally-statement.md) jest wprowadzana, gdy system wykonuje wewnętrzną listę programy obsługi zakończenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli system jest *odwijaniem* stosu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jest używany do zarządzania odwijaniem wyjątków funkcji wewnętrznej i nie jest przeznaczona do wywoływania z kodu użytkownika.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|_abnormal_termination|excpt.h|  
  
## <a name="see-also"></a>Zobacz też  
 [try-finally — instrukcja](../cpp/try-finally-statement.md)