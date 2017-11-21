---
title: "db_accessor — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_accessor
dev_langs: C++
helpviewer_keywords: db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5293712990685ff63bcafa8e5c9d5a0e8592a25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dbaccessor"></a>db_accessor
Grupy **db_column —** atrybuty, które uczestniczą w `IAccessor`— na podstawie powiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *NUM*  
 Określa liczbę metody dostępu (indeks całkowitą liczony od zera). Należy określić numery dostępu w rosnącej przy użyciu liczb całkowitych lub wartości określone.  
  
 *Automatycznie*  
 Wartość logiczna określająca, czy akcesor jest automatycznie pobierany (**TRUE**) lub nie pobrać (**FALSE**).  
  
## <a name="remarks"></a>Uwagi  
 **db_accessor —** definiuje podstawowej akcesora OLE DB dla kolejnych **db_column —** i **db_param —** atrybutów w tej samej klasy lub funkcji. **db_accessor —** jest użyteczne na poziomie elementu członkowskiego do grupy **db_column —** atrybuty, które uczestniczą w bazie danych OLE DB `IAccessor`— na podstawie powiązania. Jest on używany w połączeniu z albo **db_table —** lub **db_command —** atrybutów. Wywołanie tego atrybutu jest podobny do wywoływania [begin_accessor —](../data/oledb/begin-accessor.md) i [END_ACCESSOR](../data/oledb/end-accessor.md) makra.  
  
 **db_accessor —** generuje zestawu wierszy i wiąże go do odpowiedniego mapowania dostępu. Jeśli nie zostanie wywołana **db_accessor —**akcesor 0 będą automatycznie generowane i wszystkie powiązania kolumny zostanie zamapowane do tego bloku metody dostępu.  
  
 **db_accessor —** powiązania kolumny do jednego lub więcej metod dostępu do bazy danych grupy. Omówienie scenariuszy, w których należy użyć wielu metod dostępu, zobacz [przy użyciu wielu metod dostępu w zestawie wierszy](../data/oledb/using-multiple-accessors-on-a-rowset.md). Zobacz też "Użytkownika rekordu pomocy technicznej dla wielu metod dostępu" w [rekordów użytkowników](../data/oledb/user-records.md).  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto **db_accessor —** do grupy kolumn w tabeli poleceń z bazy danych Northwind do dwóch metod dostępu. Akcesor 0 jest automatyczne dostępu, a akcesor 1 jest.  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Bloki atrybutów|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
