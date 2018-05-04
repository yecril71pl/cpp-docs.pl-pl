---
title: _except_handler3 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
dev_langs:
- C++
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8253db3ce5a1ec60001bb32b241bfebe000502
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="excepthandler3"></a>_except_handler3
Funkcji CRT wewnętrznej. Użyć przez platformę w celu znalezienia odpowiednich wyjątków program obsługi przetwarzał bieżącego wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _except_handler3(  
   PEXCEPTION_RECORD exception_record,  
   PEXCEPTION_REGISTRATION registration,  
   PCONTEXT context,  
   PEXCEPTION_REGISTRATION dispatcher  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `exception_record`  
 Informacje dotyczące określonego wyjątku.  
  
 [in] `registration`  
 Rekord, który wskazuje tabelę, z której zakres powinien być używany do znalezienia obsługi wyjątków.  
  
 [in] `context`  
 Zastrzeżone.  
  
 [in] `dispatcher`  
 Zastrzeżone.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli wyjątek powinien być ukryty, zwraca `DISPOSITION_DISMISS`. Jeśli wyjątek powinien zostać przekazany wyższy poziom do hermetyzowany programy obsługi wyjątków, zwraca `DISPOSITION_CONTINUE_SEARCH`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda umożliwia znalezienie obsługi wyjątków odpowiednie, przekazuje wyjątek do programu obsługi. W takim przypadku ta metoda nie powróci do kodu, który wywołał go i wartości zwracanej nie ma znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)