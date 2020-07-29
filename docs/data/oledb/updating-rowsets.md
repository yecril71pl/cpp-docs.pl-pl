---
title: Aktualizowanie zestawów wierszy
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: 22e362170d645574b40070c6db39c2576d3ae9c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212946"
---
# <a name="updating-rowsets"></a>Aktualizowanie zestawów wierszy

Podstawową operacją bazy danych jest aktualizowanie lub zapisywanie danych w magazynie danych. W OLE DB mechanizm aktualizacji jest prosty: aplikacja konsumenta ustawia wartości powiązanych elementów członkowskich danych, a następnie zapisuje te wartości w zestawie wierszy. następnie konsument żąda aktualizacji magazynu danych przez dostawcę.

Konsumenci mogą wykonywać następujące rodzaje aktualizacji dla danych zestawu wierszy: Ustawianie wartości kolumn w wierszu, Wstawianie wiersza i usuwanie wiersza. Aby wykonać te operacje, Klasa szablonu OLE DB [CRowset](../../data/oledb/crowset-class.md) implementuje interfejs [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) i zastępuje następujące metody interfejsu:

- [SetData](../../data/oledb/crowset-setdata.md) zmienia wartości kolumn w wierszu zestawu wierszy; jest ono równe poleceniem SQL UPDATE.

- [Wstaw](../../data/oledb/crowset-insert.md) wstawia wiersz do zestawu wierszy; jest ono równe poleceniem INSERT języka SQL.

- [Delete](../../data/oledb/crowset-delete.md) usuwa wiersze z zestawu wierszy; jest ono równe poleceniem DELETE języka SQL.

## <a name="supporting-update-operations"></a>Obsługa operacji aktualizacji

> [!NOTE]
> Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

Podczas tworzenia odbiorcy za pomocą **kreatora ATL OLE DB klienta**można obsługiwać operacje aktualizacji, zaznaczając co najmniej jedno z trzech pól wyboru **zmieni**, **Wstaw**i **Usuń**. W przypadku wybrania tych opcji Kreator odpowiednio modyfikuje kod w celu obsługi wybranego typu zmian. Jeśli jednak Kreator nie jest używany, należy ustawić następujące właściwości zestawu wierszy, aby `VARIANT_TRUE` obsługiwały aktualizacje:

- `DBPROPVAL_UP_CHANGE`umożliwia zmianę wartości danych w wierszu.

- `DBPROPVAL_UP_INSERT`umożliwia wstawienie wiersza.

- `DBPROPVAL_UP_DELETE`pozwala na usunięcie wiersza.

Właściwości należy ustawić w następujący sposób:

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

Operacje zmiany, wstawiania lub usuwania mogą zakończyć się niepowodzeniem, jeśli co najmniej jedna kolumna nie jest zapisywalna. Zmodyfikuj mapę kursorów, aby rozwiązać ten problem.

## <a name="setting-data-in-rows"></a>Ustawianie danych w wierszach

[CRowset:: SetData](../../data/oledb/crowset-setdata.md) ustawia wartości danych w co najmniej jednej kolumnie bieżącego wiersza. Poniższy kod ustawia wartości elementów członkowskich danych powiązanych z kolumnami `Name` i `Units in Stock` tabeli `Products` , a następnie wywołuje `SetData` do zapisania tych wartości w wierszu ewentualna szczytowa zestawu wierszy:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>Wstawianie wierszy do zestawów wierszy

[CRowset:: INSERT](../../data/oledb/crowset-insert.md) tworzy i inicjuje nowy wiersz przy użyciu danych z metody dostępu. `Insert`tworzy zupełnie nowy wiersz po bieżącym wierszu; należy określić, czy chcesz zwiększyć bieżący wiersz do następnego wiersza, czy pozostać bez zmian. W tym celu należy ustawić parametr *bGetRow* :

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **`false`**(wartość domyślna) określa, że bieżący wiersz jest zwiększany do następnego wiersza (w tym przypadku wskazuje wstawiony wiersz).

- **`true`** Określa, że bieżący wiersz pozostaje tam, gdzie jest.

Poniższy kod ustawia wartości elementów członkowskich danych powiązanych z kolumnami tabeli `Products` , a następnie wywołuje, `Insert` Aby wstawić nowy wiersz z tymi wartościami po wierszu ewentualna szczytowa zestawu wierszy. Zaleca się, aby ustawić wszystkie wartości kolumn, aby uniknąć niezdefiniowanych danych w nowym wierszu:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

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

Aby zapoznać się z bardziej szczegółowym przykładem, zobacz [CRowset:: INSERT](../../data/oledb/crowset-insert.md).

Aby uzyskać więcej informacji na temat ustawiania stanu i liczby elementów członkowskich danych, zobacz sekcję [stan pola elementy członkowskie danych w przystawce metod dostępu generowanych przez kreatora](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

## <a name="deleting-rows-from-rowsets"></a>Usuwanie wierszy z zestawów wierszy

[CRowset::D suń](../../data/oledb/crowset-delete.md) usuwa bieżący wiersz z zestawu wierszy. Poniższy kod wywołuje, `Delete` Aby usunąć wiersz ewentualna szczytowa zestawu wierszy:

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

## <a name="immediate-and-deferred-updates"></a>Aktualizacje natychmiastowe i odroczone

O ile nie określono inaczej, wywołania `SetData` metod, `Insert` i `Delete` natychmiast zaktualizują magazyn danych. Można jednak odroczyć aktualizacje, aby konsument przechowywał wszystkie zmiany w lokalnej pamięci podręcznej, a następnie przetransferować je do magazynu danych po wywołaniu jednej z następujących metod aktualizacji:

- [CRowset:: Update](../../data/oledb/crowset-update.md) przenosi wszystkie oczekujące zmiany w bieżącym wierszu od momentu ostatniego pobrania lub `Update` wywołania.

- [CRowset:: UPDATEALL](../../data/oledb/crowset-updateall.md) przenosi wszystkie oczekujące zmiany wprowadzone do wszystkich wierszy od momentu ostatniego pobrania lub `Update` wywołania.

Aktualizacja, która jest używana przez metody aktualizacji, ma szczególne znaczenie dla wprowadzania zmian w poleceniu i nie należy mylić z poleceniem SQL **Update** ( `SetData` jest równoważne z poleceniem SQL **Update** ).

Aktualizacje odroczone są przydatne, na przykład w sytuacjach, takich jak seria transakcji bankowych; Jeśli jedna transakcja została anulowana, można cofnąć zmiany, ponieważ seria zmian nie jest wysyłana do czasu zatwierdzenia. Ponadto dostawca może powiązać zmiany w jedno wywołanie sieciowe, co jest bardziej wydajne.

Aby zapewnić obsługę aktualizacji odroczonych, należy ustawić `DBPROP_IRowsetChange` Właściwość wraz z właściwościami opisanymi w temacie **Obsługa operacji aktualizacji**:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

Po wywołaniu `Update` metody lub `UpdateAll` metoda transferu zmian z lokalnej pamięci podręcznej do magazynu danych, a następnie wyczyszczenia lokalnej pamięci podręcznej. Ponieważ aktualizacja transferuje zmiany tylko dla bieżącego wiersza, ważne jest, aby aplikacja śledzi zakres aktualizacji i czas ich aktualizacji. Poniższy przykład pokazuje, jak zaktualizować dwa kolejne wiersze:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

Aby upewnić się, że oczekujące zmiany są transferowane, należy wywołać `Update` przed przechodzeniem do innego wiersza. Jednak jeśli jest to żmudnym lub niewydajne, na przykład gdy aplikacja wymaga aktualizacji setek wierszy, można użyć `UpdateAll` programu, aby zaktualizować wszystkie wiersze jednocześnie.

Na przykład jeśli w `Update` powyższym kodzie brakuje pierwszego wywołania, wiersz 100 pozostanie niezmieniony, podczas gdy wiersz 101 zostanie zmieniony. Po tym momencie aplikacja będzie musiała wywołać `UpdateAll` lub przejść z powrotem do wiersza 100 i wywoływać `Update` dla tego wiersza do zaktualizowania.

Wreszcie jednym z głównych przyczyn odroczenia zmian jest możliwość ich cofnięcia. Wywołanie [CRowset:: Undo](../../data/oledb/crowset-undo.md) przywraca stan lokalnej pamięci podręcznej zmian do stanu magazynu danych przed wprowadzeniem oczekujących zmian. Należy pamiętać, że `Undo` nie Wycofaj stanu lokalnej pamięci podręcznej o jeden krok (stan przed ostatnią zmianą); spowoduje to wyczyszczenie lokalnej pamięci podręcznej dla tego wiersza. Ma także `Undo` wpływ tylko na bieżący wiersz.

## <a name="see-also"></a>Zobacz także

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[Klasa CRowset](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
