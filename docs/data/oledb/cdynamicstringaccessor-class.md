---
title: Cdynamicstringaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b8888bdac7d605ce1832ef7074955fab4893b33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor — Klasa
Umożliwia dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (wewnętrzna struktura bazy danych).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|Pobiera dane określonej kolumny jako ciąg.|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|Ustawia dane określonej kolumny jako ciąg.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) żąda danych w formacie native zgłoszone przez dostawcę `CDynamicStringAccessor` żądań, że dostawca pobrać wszystkie dane uzyskiwane ze źródła danych jako dane ciągu. Jest to szczególnie przydatne w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, takie jak wyświetlanie lub drukowanie zawartość magazynu danych.  
  
 Macierzystego typu danych kolumny w magazynie danych nie ma znaczenia; tak długo, jak dostawca może obsługiwać konwersję danych, jej będzie dostarczać dane w formacie ciągu. Jeśli dostawca nie obsługuje konwersji z typu danych natywnych na ciąg (który nie jest często), żądania wywołania zwróci wartość Powodzenie **DB_S_ERRORSOCCURED**, i zostanie stan odpowiadającej mu kolumny wskazywać na problem konwersji z **DBSTATUS_E_CANTCONVERTVALUE**.  
  
 Użyj `CDynamicStringAccessor` metod, aby uzyskać informacje dotyczące kolumn. Informacje te kolumny umożliwia tworzenie akcesor dynamicznie w czasie wykonywania.  
  
 Informacji o kolumnie znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), lub Przechowaj ją przy użyciu buforu [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Omówienie i przykłady przy użyciu klasy dynamicznej metody dostępu, zobacz [przy użyciu dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor — klasa](../../data/oledb/caccessor-class.md)   
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [Cdynamicstringaccessora — klasa](../../data/oledb/cdynamicstringaccessora-class.md)   
 [Cdynamicstringaccessorw — klasa](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor, klasa](../../data/oledb/cxmlaccessor-class.md)