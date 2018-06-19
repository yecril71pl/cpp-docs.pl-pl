---
title: CDynamicAccessor::SetValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9322394f2b72b49afe988c371858d9ee580825ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095680"
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