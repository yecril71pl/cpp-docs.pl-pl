---
title: "db_table — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_table
dev_langs: C++
helpviewer_keywords: db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2d8c7efaa23a8d7169ca41b4bfcb78722d73543
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dbtable"></a>db_table
Otwiera tabeli OLE DB.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *db_table —*  
 Ciąg określający nazwę tabeli bazy danych (na przykład "produkty").  
  
 *Nazwa* (opcjonalnie)  
 Nazwa dojście służy do pracy z tabeli. Ten parametr należy określić, aby zwrócić więcej niż jeden wiersz wyników. **db_table —** generuje zmienną z określonym *nazwa* który może służyć do przechodzenia zestawu wierszy lub wykonywać wiele akcji kwerendy.  
  
 *source_name* (opcjonalnie)  
 `CSession` Zmiennej lub wystąpienia klasy, która ma `db_source` atrybut zastosowany do niego, na którym wykonuje polecenie. Zobacz [db_source —](../windows/db-source.md).  
  
 `hresult`(opcjonalnie)  
 Identyfikuje zmienna, która odbierze `HRESULT` tego polecenia bazy danych. Jeśli zmienna nie istnieje, jej zostaną automatycznie dodane przez atrybut.  
  
## <a name="remarks"></a>Uwagi  
 **db_table —** tworzy [CTable](../data/oledb/ctable-class.md) obiektu, który jest używany przez konsumenta OLE DB można otworzyć tabeli. Można użyć tego atrybutu tylko na poziomie klasy; Nie można używać go wbudowanego. Użyj **db_column —** można powiązać kolumny tabeli do zmiennych; użyj **db_param —** ograniczającej (Ustaw dla parametru typu i dlatego na) parametrów.  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje otwarcie tabeli Produkty na potrzeby używania przez `CProducts`.  
  
```  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 Na przykład ten atrybut używany w aplikacji, zobacz przykłady [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) i [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
