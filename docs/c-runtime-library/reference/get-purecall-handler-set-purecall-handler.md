---
title: "_get_purecall_handler, _set_purecall_handler — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
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
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs:
- C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 918fbe6c27333c705dbb2768ccd903c64e0fd687
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler
Pobiera lub ustawia program obsługi błędów wywołanie czystej funkcji wirtualnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void (__cdecl* _purecall_handler)(void);  
  
_purecall_handler __cdecl _get_purecall_handler(void);  
  
_purecall_handler __cdecl _set_purecall_handler(   
   _purecall_handler function  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `function`  
 Funkcja wywoływana, gdy jest wywoływana czystej funkcji wirtualnej. A `_purecall_handler` funkcji muszą być zwrócony typ void.  
  
## <a name="return-value"></a>Wartość zwracana  
 Poprzedni `_purecall_handler`. Zwraca `nullptr` Jeśli nie było żadnych poprzednią procedurę obsługi.  
  
## <a name="remarks"></a>Uwagi  
 `_get_purecall_handler` i `_set_purecall_handler` funkcje są specyficzne dla firmy Microsoft i mają zastosowanie tylko do kod w języku C++.  
  
 Wywołanie czystej funkcji wirtualnej występuje błąd, ponieważ ma ona żadnej implementacji. Domyślnie kompilator generuje kod, aby wywołać funkcję obsługi błędu wywołanego czystej funkcji wirtualnej, która kończy program. Można zainstalować własnych funkcji obsługi błędu dla wywołań czystej funkcji wirtualnej, aby wykryć je do debugowania lub celów raportowania. Aby korzystać z własnych program obsługi błędów, tworzy funkcję, która ma `_purecall_handler` podpisu, następnie użyć `_set_purecall_handler` dokonanie bieżący program obsługi.  
  
 Ponieważ istnieje tylko jeden `_purecall_handler` dla każdego procesu podczas wywoływania `_set_purecall_handler` bezpośrednio wpływa wszystkie wątki. Ostatni obiekt wywołujący w którymkolwiek wątku Ustawia program obsługi.  
  
 Aby przywrócić domyślne zachowanie, należy wywołać `_set_purecall_handler` przy użyciu `nullptr` argumentu.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_purecall_handler`, `_set_purecall_handler`|\<cstdlib — > lub \<stdlib.h >|  
  
 Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// _set_purecall_handler.cpp  
// compile with: /W1  
#include <tchar.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
class CDerived;  
class CBase  
{  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function(void) = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase  
{  
public:  
   CDerived() : CBase(this) {};   // C4355  
   virtual void function(void) {};  
};  
  
CBase::~CBase()  
{  
   m_pDerived -> function();  
}  
  
void myPurecallHandler(void)  
{  
   printf("In _purecall_handler.");  
   exit(0);  
}  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
   _set_purecall_handler(myPurecallHandler);  
   CDerived myDerived;  
}  
```  
  
```Output  
In _purecall_handler.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów](../../c-runtime-library/error-handling-crt.md)   
 [_purecall](../../c-runtime-library/reference/purecall.md)