---
title: "Aktualizowanie zestawów wierszy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a06cd7d4f9e62bb40c24be67eb7b356906b4069
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="updating-rowsets"></a>Aktualizowanie zestawów wierszy
Operacja bardzo podstawowe bazy danych jest aktualizacji lub zapisać danych w magazynie danych. W OLE DB, mechanizmu aktualizacji jest prosty: aplikacja klienta ustawia wartości składników powiązana z danymi, a następnie zapisuje te wartości na wierszy; następnie konsumenta żądania, czy dostawca aktualizacji do magazynu danych.  
  
 Konsumenci mogą wykonywać następujące rodzaje aktualizacje na wierszy danych: Ustawianie wartości kolumn w wierszu, wstawiania wiersza i usuwanie wiersza. Do wykonania tych operacji klasy szablonów OLE DB [CRowset](../../data/oledb/crowset-class.md) implementuje [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interfejsu i zastępuje następujące metody interfejsu:  
  
-   [SetData](../../data/oledb/crowset-setdata.md) wartości kolumny zmiany w wierszu zestawu wierszy; jest odpowiednikiem polecenia SQL UPDATE.  
  
-   [Wstaw](../../data/oledb/crowset-insert.md) wstawia wiersza do zestawu wierszy; jest odpowiednikiem polecenia SQL INSERT.  
  
-   [Usuń](../../data/oledb/crowset-delete.md) usuwa wiersze z zestawu wierszy; jest odpowiednikiem polecenia SQL DELETE.  
  
## <a name="supporting-update-operations"></a>Obsługa operacje aktualizacji  
 Po utworzeniu konsumenta OLE DB Kreator konsumenta ATL należy może obsługiwać operacje aktualizacji, wybierając jedną lub więcej z trzech pól wyboru **zmiany**, **Wstaw**, i **usunąć**. W przypadku wybrania te kreatora modyfikuje kod odpowiednio do obsługi rodzaju zmiany, którą wybierzesz. Jednak jeśli nie używasz kreatora, należy określić następujące właściwości zestawu wierszy `VARIANT_TRUE` do obsługi aktualizacji:  
  
-   **DBPROPVAL_UP_CHANGE** umożliwia zmianę wartości danych w wierszu.  
  
-   **DBPROPVAL_UP_INSERT** służy do wstawienia wiersza.  
  
-   **DBPROPVAL_UP_DELETE** służy do usunięcia wiersza.  
  
 Ustaw właściwości w następujący sposób:  
  
```  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 Zmiany, wstawiania lub usuwania mogą wystąpić błędy, jeśli co najmniej jedna kolumna nie jest zapisywalny. Zmodyfikuj mapy kursora, aby rozwiązać ten problem.  
  
## <a name="setting-data-in-rows"></a>Ustawienia danych wierszy  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) ustawia wartości danych w co najmniej jedną kolumnę bieżącego wiersza. Poniższy kod ustawia wartości powiązane z kolumnami "Name" i "Jednostki w magazynie" w tabeli Produkty elementy członkowskie danych, a następnie wywołuje `SetData` można zapisać tych wartości do 100 wierszy zestawu wierszy:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_UnitsInStock = 10000;  
  
// Set the data  
HRESULT hr = product.SetData();  
```  
  
## <a name="inserting-rows-into-rowsets"></a>Wstawianie wierszy do zestawów wierszy  
 [CRowset::Insert](../../data/oledb/crowset-insert.md) tworzy i inicjuje nowy wiersz przy użyciu danych z metody dostępu. **Wstaw** tworzy całkowicie nowy wiersz po wierszu bieżącego; należy określić, czy mają być zwiększane bieżący wiersz do następnego wiersza lub pozostaw bez zmian. Możesz to zrobić przez ustawienie *bGetRow* parametru:  
  
```  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **FALSE** (wartość domyślna) określa, czy bieżący wiersz zwiększyć do następnego wiersza (w takim przypadku wskazuje wstawionego wiersza).  
  
-   **wartość true,** Określa, czy bieżący wiersz pozostają, gdzie jest.  
  
 Poniższy kod ustawia wartości powiązane z kolumnami tabeli Produkty elementy członkowskie danych, a następnie wywołuje **Wstaw** Aby wstawić nowy wiersz z tych wartości po 100 wierszu zestawu wierszy. Zaleca się, że ustawisz wszystkie wartości w kolumnach to uniknąć Niezdefiniowany danych do nowego wiersza:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  

product.m_UnitPrice = 20;  
product.m_UnitsInStock = 10000;  
product.m_UnitsOnOrder = 5201;  
product.m_ReorderLevel = 5000;  
product.m_Discontinued = false;  
  
// You must also initialize the status and length fields before setting/inserting data  
// Set the column status values  
m_dwProductIDStatus = DBSTATUS_S_OK;  
m_dwProductNameStatus = DBSTATUS_S_OK;  
m_dwSupplierIDStatus = DBSTATUS_S_OK;  
m_dwCategoryIDStatus = DBSTATUS_S_OK;  
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;  
m_dwUnitPriceStatus = DBSTATUS_S_OK;  
m_dwUnitsInStockStatus = DBSTATUS_S_OK;  
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;  
m_dwReorderLevelStatus = DBSTATUS_S_OK;  
m_dwDiscontinuedStatus = DBSTATUS_S_OK;  
  
// Set the column length value for column data members that are not fixed-length types.  
// The value should be the length of the string that you are setting.  
m_dwProductNameLength = 6;             // "Candle" has 6 characters  
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters  
  
// Insert the data  
HRESULT hr = product.Insert();  
```  
  
 Aby uzyskać bardziej szczegółowy przykład zobacz [CRowset::Insert](../../data/oledb/crowset-insert.md).  
  
 Aby uzyskać więcej informacji na temat ustawiania stanu i długość elementy członkowskie danych, zobacz [elementy członkowskie dotyczących stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
## <a name="deleting-rows-from-rowsets"></a>Usuwanie wierszy z zestawów wierszy  
 [CRowset::Delete](../../data/oledb/crowset-delete.md) usuwa bieżący wiersz z zestawu wierszy. Poniższy kod wywołania **usunąć** usunąć 100 wierszy zestawu wierszy:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Delete the row  
HRESULT hr = product.Delete();  
```  
  
## <a name="immediate-and-deferred-updates"></a>Natychmiastowe i odroczone aktualizacje  
 O ile nie określono inaczej, wywołań `SetData`, **Wstaw**, i **usunąć** metody natychmiast zaktualizować źródła danych. Można jednak odroczenie aktualizacji, dzięki czemu klient przechowuje wszystkie zmiany w lokalnej pamięci podręcznej i przesyła je do magazynu danych podczas wywoływania jednej z następujących metod aktualizacji:  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) przenosi wszystkie oczekujące zmiany do bieżącego wiersza od czasu ostatniego pobrania lub **aktualizacji** wywoływać w nim.  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) przenosi wszystkie oczekujące zmiany do wszystkich wierszy od czasu ostatniego pobrania lub **aktualizacji** wywoływać w nim.  
  
 Tę aktualizację, należy pamiętać, jako metody aktualizacji, ma szczególne znaczenie wprowadzanie zmian na polecenia i nie należy mylić z poleceniem instrukcji SQL UPDATE (`SetData` jest odpowiednikiem polecenia instrukcji SQL UPDATE).  
  
 Odroczone aktualizacje są przydatne, na przykład w sytuacji, szereg transakcji bankowych; Jeśli jedna transakcja została anulowana, ponieważ nie wysyłaj serii zmiany dopiero po dba ostatnią można cofnąć zmiany. Ponadto dostawca może pakietu zmiany w jednej sieci wywołanie, które jest bardziej wydajny.  
  
 Aby obsługiwać odroczone aktualizacje, musisz ustawić **DBPROP_IRowsetChange** właściwość oprócz właściwości opisane w "Obsługujące operacje aktualizacji":  
  
```  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 Podczas wywoływania **aktualizacji** lub `UpdateAll`, metody przetransferować zmiany wprowadzone w lokalnej pamięci podręcznej w magazynie danych, a następnie zniszczyć lokalnej pamięci podręcznej. Ponieważ aktualizacji przesyła zmiany tylko dla bieżącego wiersza, należy zachować informacje o którym wiersz do aktualizacji i kiedy należy zaktualizować je aplikacji. Poniższy przykład pokazuje, jak zaktualizować dwóch kolejnych wierszy:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  

product.m_UnitsInStock = 10000;  

HRESULT hr = product.SetData();  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext();  

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  

product.m_UnitsInStock = 500;  

HRESULT hr = product.SetData();  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
 Aby upewnić się, że oczekujące zmiany są przesyłane, należy wywołać **aktualizacji** przed przejściem do kolejnego wiersza. Jednak gdy jest to niewygodny lub nieskuteczne, na przykład, gdy aplikacja musi zaktualizować setki wierszy, można `UpdateAll` jednocześnie zaktualizować wszystkie wiersze.  
  
 Na przykład jeśli pierwszy **aktualizacji** wywołania brakowało kodu powyżej, wiersza 100 pozostanie bez zmian, gdy wiersz 101 zostałaby zmieniona. Od tego momentu aplikacja musi wywołać `UpdateAll` lub powrót do wiersza 100 i wywołanie **aktualizacji** dla danego wiersza do zaktualizowania.  
  
 Na koniec głównym powodem odroczenie zmiany ma być można cofnąć je. Wywoływanie [CRowset::Undo](../../data/oledb/crowset-undo.md) przywraca stan zmiany w lokalnej pamięci podręcznej do stanu magazynu danych przed wszystkie oczekujące zmiany zostały wprowadzone. Należy zauważyć, że **Cofnij** nie Przywróć kopię stan lokalnej pamięci podręcznej w jednym kroku (stan przed tylko najnowsze zmiany); zamiast tego czyści lokalnej pamięci podręcznej dla tego wiersza. Ponadto **Cofnij** dotyczy tylko bieżącego wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)