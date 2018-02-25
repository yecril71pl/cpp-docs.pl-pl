---
title: Metody konsumenta generowane przez kreatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b9ee0a1a044a7e1f87b6da4bec9418c42e6b6ba1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="consumer-wizard-generated-methods"></a>Metody konsumenta generowane przez kreatora
Generowanie niektórych funkcji, które należy zwrócić uwagę, OLE DB Kreator konsumenta ATL i Kreator aplikacji MFC. Należy pamiętać, że niektóre metody są implementowane inaczej w przypisanych projektów, więc istnieje kilka ostrzeżenia; każdej sprawy zostało opisane poniżej. Aby uzyskać informacje o wyświetlaniu wprowadzony kod, zobacz [debugowania wstrzyknięcie kodu](/visualstudio/debugger/how-to-debug-injected-code).  
  
-   `OpenAll` Otwiera ze źródłem danych, zestawy wierszy i włącza zakładki, jeśli są dostępne.  
  
-   `CloseAll` powoduje zamknięcie wszystkich otwartych zestawów wierszy i zwalnia wszystkie wykonania polecenia.  
  
-   `OpenRowset` wywołuje OpenAll, aby otworzyć konsumenta lub zbiory wierszy.  
  
-   `GetRowsetProperties` pobiera wskaźnik do ustawiony za pomocą właściwości, które można ustawić właściwość zestawu wierszy.  
  
-   `OpenDataSource` Otwiera źródła danych, używając określonego w ciągu inicjowania **właściwości Linku danych** okno dialogowe.  
  
-   `CloseDataSource` Zamyka źródła danych w odpowiedni sposób.  
  
## <a name="openall-and-closeall"></a>OpenAll i CloseAll  
  
```  
HRESULT OpenAll();   

void CloseAll();  
```  
  
 W poniższym przykładzie pokazano, jak można wywołać `OpenAll` i `CloseAll` podczas wykonywania tego samego polecenia wielokrotnie. Porównanie przykładowy kod z [CCommand::Close](../../data/oledb/ccommand-close.md), który zawiera zmiany, która wywołuje **Zamknij** i `ReleaseCommand` zamiast `CloseAll`.  
  
```  
int main(int argc, char* argv[])  
{  
   HRESULT hr;  
  
   hr = CoInitialize(NULL);  
  
   CCustOrdersDetail rs;      // Your CCommand-derived class  
   rs.m_OrderID = 10248;      // Open order 10248  
   hr = rs.OpenAll();         // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the first command execution  
   rs.Close();  
  
   rs.m_OrderID = 10249;      // Open order 10249 (a new order)  
   hr = rs.Open();            // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the second command execution;  
   // Instead of rs.CloseAll() you could call  
   // rs.Close() and rs.ReleaseCommand():  
   rs.CloseAll();  
  
   CoUninitialize();  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Należy pamiętać, że w przypadku definiowania `HasBookmark` metody `OpenAll` kod ustawia właściwość DBPROP_IRowsetLocate; upewnij się, że tylko w tym przypadku dostawca obsługuje tej właściwości.  
  
## <a name="openrowset"></a>OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** wywołuje tę metodę, aby otworzyć wierszy lub zestawy wierszy w konsumenta. Zazwyczaj nie trzeba wywołać `OpenRowset` chyba że chcesz pracować z wieloma danych źródeł/sesje/zestawów wierszy. `OpenRowset` jest zadeklarowany w pliku nagłówka klasy poleceń lub tabeli:  
  
```  
// OLE DB Template version:  
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
{  
   HRESULT hr = Open(m_session, NULL, pPropSet);  
   #ifdef _DEBUG  
   if(FAILED(hr))  
      AtlTraceErrorRecords(hr);  
   #endif  
   return hr;  
}  
```  
  
 Atrybuty inaczej zaimplementować tę metodę. Ta wersja ma obiekt sesji i ciąg polecenia, który domyślnie ciąg polecenia określony w db_command —, mimo że można przekazać inny. Należy pamiętać, że w przypadku definiowania `HasBookmark` metody `OpenRowset` kod ustawia właściwość DBPROP_IRowsetLocate; upewnij się, że tylko w tym przypadku dostawca obsługuje tej właściwości.  
  
```  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)  
{  
  
   DBPROPSET *pPropSet = NULL;  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   __if_exists(HasBookmark)  
  
   {  
      propset.AddProperty(DBPROP_IRowsetLocate, true);  
      pPropSet= &propset;  
      }  
...  
}  
```  
  
## <a name="getrowsetproperties"></a>GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 Ta metoda pobiera wskaźnik do zestawu właściwości zestawu wierszy; this, wskaźnik służy do ustawiania właściwości, takie jak DBPROP_IRowsetChange. `GetRowsetProperties` jest używany w następujący sposób w klasie rekordu użytkownika. Można zmodyfikować ten kod, aby ustawić właściwości dodatkowych wierszy:  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Nie powinna definiować globalnym `GetRowsetProperties` — metoda, ponieważ może ona konflikt z jednym zdefiniowany przez kreatora. Należy pamiętać, że jest to metoda generowane przez kreatora, który można pobrać z szablonem i atrybutami projektów; atrybuty nie wstrzyknąć tego kodu.  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource i CloseDataSource  
  
```  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>Uwagi  
 Kreator definiuje metody `OpenDataSource` i `CloseDataSource`; `OpenDataSource` wywołania [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)