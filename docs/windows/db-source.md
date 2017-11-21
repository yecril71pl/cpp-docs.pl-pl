---
title: "db_source — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_source
dev_langs: C++
helpviewer_keywords: db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89f07745d2a9f0f832f42c512e0671b4114a80c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dbsource"></a>db_source
Tworzy połączenie ze źródłem danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *db_source —*  
 Parametry połączenia używane do nawiązania połączenia ze źródłem danych. Format ciągu połączenia dla [parametry połączenia i łącza danych](https://msdn.microsoft.com/en-us/library/ms718376.aspx) w Microsoft Data Access Components (MDAC) zestawu SDK.  
  
 *Nazwa* (opcjonalnie)  
 Jeśli używasz `db_source` w klasie, *nazwa* jest wystąpieniem obiektu źródła danych, która ma `db_source` atrybut (Zobacz przykład 1). Jeśli używasz `db_source` wbudowany w implementacji metody, *nazwa* jest zmienna (lokalny do metody), która może służyć do uzyskiwania dostępu do danych źródła (Zobacz przykład 2). Przekaż to *nazwa* do `source_name` parametr **db_command —** do skojarzenia ze źródłem danych za pomocą polecenia.  
  
 `hresult`(opcjonalnie)  
 Identyfikuje zmienna, która odbierze `HRESULT` tego polecenia bazy danych. Jeśli zmienna nie istnieje, jej zostaną automatycznie dodane przez atrybut.  
  
## <a name="remarks"></a>Uwagi  
 `db_source`Tworzy [CDataSource](../data/oledb/cdatasource-class.md) i [CSession](../data/oledb/csession-class.md) obiektu, który łącznie stanowią połączenie ze źródłem danych konsumentów OLE DB.  
  
 Jeśli używasz `db_source` w klasie, `CSession` obiektu stanie się członkiem tej klasy.  
  
 Jeśli używasz `db_source` w metodzie, wprowadzony kod zostanie wykonany w zakresie — metoda i `CSession` obiekt jest tworzony jako zmiennej lokalnej.  
  
 `db_source`dodaje właściwości źródła danych do klasy lub w metodzie. Jest on używany w połączeniu z **db_command —** (który bierze `db_source` *nazwa* parametr jako jego `source_name` parametru).  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
 Na przykład ten atrybut używany w aplikacji, zobacz przykłady [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) i [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wywołuje `db_source` dla klasy, aby utworzyć połączenie ze źródłem danych `ds` przy użyciu bazy danych Northwind. `ds`jest dojścia dla źródła danych, która jest używana wewnętrznie do `CMyCommand` klasy.  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, elementu członkowskiego, metoda, lokalnego|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
