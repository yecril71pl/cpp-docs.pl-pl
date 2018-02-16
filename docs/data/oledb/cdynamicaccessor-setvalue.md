---
title: CDynamicAccessor::SetValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2227564d321ca3c5c590c11fca52b906ebc911ca
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
Zapisuje dane do określonej kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 [in] Parametr szablonu, który obsługuje dowolny typ danych, z wyjątkiem typu ciąg (**CHAR\***, **WCHAR\***), które wymagają specjalnej obsługi. `GetValue` używa odpowiedni typ danych oparte na tutaj Określ.  
  
 `pColumnName`  
 [in] Wskaźnik na ciąg znaków zawierający nazwę kolumny.  
  
 `data`  
 [in] Wskaźnik do pamięci zawierający dane.  
  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Można ustawić dane ciągu, należy użyć wersji nontemplated `GetValue`. Wersje nontemplated tej metody zwrócić **void\***, który wskazuje część buforu, który zawiera dane określonej kolumny. Zwraca **NULL** Jeśli kolumna nie zostanie znaleziony.  
  
 Dla wszystkich innych typów danych jest prostsze opartego na szablonie wersjach programu `GetValue`. Zwraca opartego na szablonie wersji **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)