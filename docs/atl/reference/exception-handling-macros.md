---
title: Obsługa makra wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05ee381aa792c252fc9b80107d25e15e7d1ecfca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exception-handling-macros"></a>Makra Obsługa wyjątków
Makra te zapewniają obsługę wyjątków.  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|Instrukcji do obsługi błędów występujących w skojarzonym `_ATLTRY`.|  
|[_ATLCATCHALL](#_atlcatchall)|Instrukcji do obsługi błędów występujących w skojarzonym `_ATLTRY`.|  
|[_ATLTRY](#_atltry)|Oznacza sekcji kodu ochroną, gdzie prawdopodobnie może wystąpić błąd.|  
  
## <a name="requirements"></a>Wymagania:
**Nagłówek:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH  
 Instrukcji do obsługi błędów występujących w skojarzonym `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Wyjątek do catch.  
  
### <a name="remarks"></a>Uwagi  
 Używane w połączeniu z `_ATLTRY`. Jest rozpoznawana jako C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) obsługi danego typu wyjątków C++.  
  
##  <a name="_atlcatchall"></a>  _ATLCATCHALL  
 Instrukcji do obsługi błędów występujących w skojarzonym `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Uwagi  
 Używane w połączeniu z `_ATLTRY`. Jest rozpoznawana jako C++ [instrukcji catch(...) została ](../../cpp/try-throw-and-catch-statements-cpp.md) obsługę wszystkich typów wyjątków C++.  
  
##  <a name="_atltry"></a>  _ATLTRY  
 Oznacza sekcji kodu ochroną, gdzie prawdopodobnie może wystąpić błąd.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Uwagi  
 Używane w połączeniu z [_ATLCATCH](#_atlcatch) lub [_ATLCATCHALL](#_atlcatchall). Jest rozpoznawana jako C++ symbol [spróbuj](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
