---
title: Aktualizowanie zestawów wierszy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d2936a65023b32f994ed7260260476bc7b0457c2
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336420"
---
# <a name="updating-rowsets"></a>Aktualizowanie zestawów wierszy
Operacja wykraczającego poza podstawowe bazy danych jest aktualizacji lub zapisywać dane w magazynie danych. W OLE DB, jest prosty mechanizm aktualizacji: aplikacja odbiorcy ustawia wartości składników powiązane dane, a następnie zapisuje te wartości, do zestawu wierszy; następnie konsumenta żądań, czy dostawca zaktualizuj magazyn danych.  
  
 Konsumenci mogą wykonywać następujące rodzaje aktualizacje na zestaw wierszy danych: Ustawianie wartości kolumn w wierszu, wstawienie wiersza i usuwanie wiersza. Wykonywać te operacje klasy szablonów OLE DB [CRowset](../../data/oledb/crowset-class.md) implementuje [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx) interfejs i zastępuje następujące metody interfejsu:  
  
-   [SetData](../../data/oledb/crowset-setdata.md) zmiany kolumny wartości w wierszu zestawu wierszy; jest to równoważne polecenia aktualizacji programu SQL.  
  
-   [Wstaw](../../data/oledb/crowset-insert.md) wstawia wiersz do zestawu wierszy; jest to równoważne polecenia SQL INSERT.  
  
-   [Usuń](../../data/oledb/crowset-delete.md) usuwa wiersze z wierszy; jest to równoważne polecenia SQL DELETE.  
  
## <a name="supporting-update-operations"></a>Obsługa operacje aktualizacji  
 W przypadku utworzenia konsumenta OLE DB Kreator konsumenta ATL, może obsługiwać operacje aktualizacji, wybierając jedną lub więcej z trzech pól wyboru **zmiany**, **Wstaw**, i **Usuń**. Wybranie tych kreatora modyfikuje kod odpowiednio do obsługi typu zmian, które wybierzesz. Jednak jeśli nie używasz kreatora, należy ustawić następujące właściwości zestawu wierszy `VARIANT_TRUE` do obsługi aktualizacji:  
  
-   `DBPROPVAL_UP_CHANGE` Umożliwia zmianę wartości danych w wierszu.  
  
-   `DBPROPVAL_UP_INSERT` Umożliwia wstawianie wiersza.  
  
-   `DBPROPVAL_UP_DELETE` zezwala na usunięcia wiersza.  
  
 Ustaw właściwości w następujący sposób:  
  
```cpp  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 Zmiana, insert nebo operacje usuwania może zakończyć się niepowodzeniem, jeśli co najmniej jedna kolumna nie jest zapisywalna. Zmodyfikuj mapy kursora, aby rozwiązać ten problem.  
  
## <a name="setting-data-in-rows"></a>Ustawienia danych wierszy  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) ustawia wartości danych w co najmniej jedną kolumnę bieżącego wiersza. Poniższy kod ustawia wartości elementów członkowskich danych powiązane z kolumnami "Name" i "Jednostki w Stock" w tabeli Produkty, a następnie wywołuje `SetData` zapisać te wartości do 100 wierszy zestawu wierszy:  
  
```cpp  
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
 [CRowset::Insert](../../data/oledb/crowset-insert.md) tworzy i inicjuje nowego wiersza przy użyciu danych z metody dostępu. `Insert` Tworzy całkowicie nowy wiersz po wierszu bieżącego; należy określić, czy zwiększyć bieżący wiersz do następnego wiersza, lub pozostaw bez zmian. Możesz to zrobić, ustawiając *bGetRow* parametru:  
  
```cpp  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **FALSE** (wartość domyślna) określa, czy bieżący wiersz zwiększyć do następnego wiersza (w którym to przypadku wskazuje wstawionego wiersza).  
  
-   **wartość true,** Określa, że bieżący wiersz pozostaje, gdzie jest.  
  
 Poniższy kod ustawia wartości elementów członkowskich danych powiązane z kolumnami tabeli Produkty, a następnie wywołuje `Insert` Aby wstawić nowy wiersz, w którym te wartości po 100 wierszy zestawu wierszy. Zaleca się, że ustawisz wszystkie wartości kolumny, aby uniknąć niezdefiniowane danych w nowym wierszu:  
  
```cpp  
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
  
 Aby uzyskać bardziej szczegółowym przykładem, zobacz [CRowset::Insert](../../data/oledb/crowset-insert.md).  
  
 Aby uzyskać więcej informacji na temat ustawiania stanu i długość składowych danych, zobacz [elementy członkowskie danych stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
## <a name="deleting-rows-from-rowsets"></a>Usuwanie wierszy z zestawów wierszy  
 [CRowset::Delete](../../data/oledb/crowset-delete.md) usuwa bieżący wiersz z zestawu wierszy. Poniższy kod wywoła `Delete` do usunięcia 100 wierszy zestawu wierszy:  
  
```cpp  
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
 O ile nie określono inaczej, wywołania `SetData`, `Insert`, i `Delete` metody natychmiast zaktualizować magazynu danych. Można jednak odroczenie aktualizacji, dzięki czemu odbiorcy przechowuje wszystkie zmiany w lokalnej pamięci podręcznej i przesyła je do magazynu danych podczas wywoływania jednej z następujących metod aktualizacji:  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) przesyła wszystkie oczekujące zmiany wprowadzone do bieżącego wiersza od czasu ostatniego pobrania lub `Update` wywołania.  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) przesyła wszystkie oczekujące zmiany wprowadzone do wszystkich wierszy od czasu ostatniego pobrania lub `Update` wywołania.  
  
 Należy pamiętać tej aktualizacji, ponieważ używane przez metody aktualizacji, ma szczególne znaczenie wprowadzanie zmian na polecenia i nie należy mylić za pomocą polecenia instrukcji SQL UPDATE (`SetData` jest odpowiednikiem polecenia instrukcji SQL UPDATE).  
  
 Odroczone aktualizacje są przydatne, na przykład w sytuacjach, takich jak serie transakcji bankowych; Jeśli jedna transakcja została anulowana, możesz cofnąć zmiany, ponieważ nie wysyłaj serię zmian, aż po ostatnim jest zatwierdzona. Ponadto dostawca może pakietu zmiany do wywołania jednej sieci, co jest bardziej wydajne.  
  
 Obsługują odroczone aktualizacje, należy ustawić `DBPROP_IRowsetChange` właściwość oprócz właściwości opisane w "Obsługujące operacje aktualizacji":  
  
```cpp  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 Gdy wywołujesz `Update` lub `UpdateAll`, metody przetransferować zmiany wprowadzone z lokalnej pamięci podręcznej w magazynie danych, a następnie zniszczyć lokalnej pamięci podręcznej. Ponieważ aktualizacja przesyła zmiany tylko w przypadku bieżącego wiersza, należy zachować informacje o wiersz do zaktualizowania oraz kiedy należy go zaktualizować aplikację. Poniższy przykład pokazuje, jak zaktualizować dwóch następujących po sobie wierszy:  
  
```cpp  
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
  
 Aby upewnić się, że oczekujące zmiany są przesyłane, należy wywołać `Update` przed przejściem do kolejnego wiersza. Jednak gdy jest to uciążliwe lub nieskuteczne, na przykład, gdy Twoja aplikacja musi zaktualizować setki wierszy, służy `UpdateAll` można jednocześnie uaktualnić wszystkie wiersze.  
  
 Na przykład jeśli pierwszy `Update` wywołań brakuje powyższy kod, wiersza 100 pozostaje bez zmian, gdy zostaną zmienione wiersz 101. Od tego momentu aplikacja musi wywoływać `UpdateAll` lub przenieść z powrotem do wiersza 100 i wywołanie `Update` dla tego wiersza do zaktualizowania.  
  
 Na koniec głównym celem Odrocz zmian jest aby można było cofnąć ich. Wywoływanie [CRowset::Undo](../../data/oledb/crowset-undo.md) wycofanie stan zmiany w lokalnej pamięci podręcznej do stanu magazynu danych przed wszelkie oczekujące zmiany zostały wprowadzone. Ważne jest, aby pamiętać, że `Undo` nieoperacyjnym kopii stanu lokalnej pamięci podręcznej w jednym kroku (stan przed ostatnią zmianę); zamiast tego powoduje wyczyszczenie lokalnej pamięci podręcznej dla tego wiersza. Ponadto `Undo` dotyczy tylko bieżącego wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [Klasa CRowset](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)