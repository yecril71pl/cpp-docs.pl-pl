---
title: CDynamicAccessor::GetValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e43707d4697fbbeece5475f71b7e2f93e731772
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
Pobiera dane dla określonej kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 [in] Parametr szablonu, który obsługuje dowolny typ danych, z wyjątkiem typu ciąg (**CHAR\***, **WCHAR\***), które wymagają specjalnej obsługi. `GetValue` używa odpowiedni typ danych oparte na tutaj Określ.  
  
 `nColumn`  
 [in] Numer kolumny. Numery kolumn rozpoczynać 1. Wartość 0 odwołuje się do kolumny zakładki, jeśli istnieją.  
  
 `pColumnName`  
 [in] Nazwa kolumny.  
  
 `pData`  
 [out] Wskaźnik do zawartości określonej kolumny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli chcesz przekazać ciąg danych, użyj wersji nontemplated `GetValue`. Wersje nontemplated tej metody zwrócić **void\***, który wskazuje część buforu, który zawiera dane określonej kolumny. Zwraca **NULL** Jeśli kolumna nie zostanie znaleziony.  
  
 Dla wszystkich innych typów danych jest prostsze opartego na szablonie wersjach programu `GetValue`. Zwraca opartego na szablonie wersji **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
## <a name="remarks"></a>Uwagi  
 Użyj wersji nontemplated, aby zwrócić kolumny zawierające ciągi i szablonem wersji dla kolumny, które zawierają inne typy danych.  
  
 W trybie debugowania, zostanie wyświetlony potwierdzenia, jeśli rozmiar `pData` jest nierówne rozmiar kolumny, na którą wskazuje.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)