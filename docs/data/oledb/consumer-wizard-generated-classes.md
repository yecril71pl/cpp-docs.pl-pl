---
title: Klasy konsumentów generowane przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
ms.openlocfilehash: 0d3bd03fb352f2466f0ae48ec0ca99cf66fbb416
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079718"
---
# <a name="consumer-wizard-generated-classes"></a>Klasy konsumentów generowane przez kreatora

::: moniker range="vs-2019"

Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje.

::: moniker-end

::: moniker range="<=vs-2017"

W przypadku wygenerowania konsumenta przy użyciu **kreatora ATL OLE DB Consumer** można korzystać z szablonów OLE DB lub atrybutów OLE DB. W obu przypadkach Kreator generuje klasę poleceń i klasę rekordu użytkownika. Klasa Command zawiera kod umożliwiający otwarcie źródła danych i zestawu wierszy określonego w kreatorze. Klasa rekordu użytkownika zawiera mapę kolumn dla wybranej tabeli bazy danych. Jednak wygenerowany kod różni się w każdym przypadku:

- W przypadku wybrania użytkownika z szablonem Kreator wygeneruje klasę poleceń i klasę rekordu użytkownika. Klasa poleceń będzie miała nazwę, którą wprowadzisz w polu **klasy** kreatora (na przykład `CProducts`), a Klasa rekordu użytkownika będzie miała nazwę formularza "metoda dostępu*ClassName*" (na przykład `CProductsAccessor`). Obie klasy są umieszczane w pliku nagłówkowym użytkownika.

- W przypadku wybrania odbiorcy z atrybutem Klasa rekordu użytkownika będzie miała nazwę formularza "_*ClassName*akcesor" i zostanie wprowadzona. Oznacza to, że będzie można wyświetlić tylko klasę poleceń w edytorze tekstu. można wyświetlić tylko klasę rekordu użytkownika jako wstrzyknięty kod. Aby uzyskać informacje na temat wyświetlania wstrzykniętego kodu, zobacz [debugowanie wstrzykiwanego kodu](/visualstudio/debugger/how-to-debug-injected-code).

W poniższych przykładach użyto klasy Command utworzonej w tabeli `Products` bazy danych `Northwind`, aby przedstawić kod klienta wygenerowany przez kreatora dla klasy poleceń i klasy rekordu użytkownika.

## <a name="templated-user-record-classes"></a>Klasy rekordów użytkowników z szablonami

Jeśli utworzysz klienta OLE DB przy użyciu szablonów OLE DB (zamiast atrybutów OLE DB), Kreator generuje kod zgodnie z opisem w tej sekcji.

### <a name="column-data-members"></a>Elementy członkowskie danych kolumny

Pierwsza część klasy rekordu użytkownika zawiera deklaracje elementu członkowskiego danych oraz dane o stanie i długości dla każdej kolumny powiązanej z danymi. Informacje o tych elementach członkowskich danych znajdują się [w temacie elementy członkowskie danych o stanie pola w przystawce metod dostępu generowanych przez kreatora](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

> [!NOTE]
> W przypadku modyfikacji klasy rekordu użytkownika lub napisania własnego odbiorcy zmienne danych muszą występować przed zmiennymi stan i długość.

> [!NOTE]
> Kreator OLE DB użytkownika ATL używa typu `DB_NUMERIC` do powiązania typów danych liczbowych. Wcześniej użył `DBTYPE_VARNUMERIC` (format, który jest opisywany przez typ `DB_VARNUMERIC`; Zobacz OLEDB. h). Jeśli nie używasz Kreatora do tworzenia odbiorców, zalecamy korzystanie z `DB_NUMERIC`.

```cpp
// Products.H : Declaration of the CProducts class

class CProductsAccessor
{
public:
   // Column data members:
   LONG m_ProductID;
   TCHAR m_ProductName[41];
   LONG m_SupplierID;
   LONG m_CategoryID;
   TCHAR m_QuantityPerUnit[21];
   CURRENCY m_UnitPrice;
   SHORT m_UnitsInStock;
   SHORT m_UnitsOnOrder;
   SHORT m_ReorderLevel;
   VARIANT_BOOL m_Discontinued;

   // Column status data members:
   DBSTATUS m_dwProductIDStatus;
   DBSTATUS m_dwProductNameStatus;
   DBSTATUS m_dwSupplierIDStatus;
   DBSTATUS m_dwCategoryIDStatus;
   DBSTATUS m_dwQuantityPerUnitStatus;
   DBSTATUS m_dwUnitPriceStatus;
   DBSTATUS m_dwUnitsInStockStatus;
   DBSTATUS m_dwUnitsOnOrderStatus;
   DBSTATUS m_dwReorderLevelStatus;
   DBSTATUS m_dwDiscontinuedStatus;

   // Column length data members:
   DBLENGTH m_dwProductIDLength;
   DBLENGTH m_dwProductNameLength;
   DBLENGTH m_dwSupplierIDLength;
   DBLENGTH m_dwCategoryIDLength;
   DBLENGTH m_dwQuantityPerUnitLength;
   DBLENGTH m_dwUnitPriceLength;
   DBLENGTH m_dwUnitsInStockLength;
   DBLENGTH m_dwUnitsOnOrderLength;
   DBLENGTH m_dwReorderLevelLength;
   DBLENGTH m_dwDiscontinuedLength;
```

### <a name="rowset-properties"></a>Właściwości zestawu wierszy

Następnie Kreator ustawia właściwości zestawu wierszy. W przypadku wybrania opcji **Zmień**, **Wstaw**lub **Usuń** w Kreatorze OLE DB użytkownika ATL, odpowiednie właściwości są ustawione w tym miejscu (DBPROP_IRowsetChange jest zawsze ustawiona, a następnie co najmniej jeden DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT i/lub DBPROPVAL_UP_DELETE).

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>Klasa polecenia lub tabeli

W przypadku określenia klasy poleceń Kreator deklaruje klasę poleceń; w przypadku kodu z szablonem polecenie wygląda następująco:

```cpp
DEFINE_COMMAND_EX(CProductsAccessor, L" \
SELECT \
   ProductID, \
   ProductName, \
   SupplierID, \
   CategoryID, \
   QuantityPerUnit, \
   UnitPrice, \
   UnitsInStock, \
   UnitsOnOrder, \
   ReorderLevel, \
   Discontinued \
   FROM dbo.Products")
```

### <a name="column-map"></a>Mapa kolumn

Następnie Kreator generuje powiązania kolumn lub mapę kolumn. Aby rozwiązać kilka problemów z niektórymi dostawcami, poniższy kod może powiązać kolumny w innej kolejności niż zgłoszone przez dostawcę.

```cpp
   BEGIN_COLUMN_MAP(CProductsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))
   END_COLUMN_MAP()
};
```

### <a name="class-declaration"></a>Deklaracja klasy

Na koniec Kreator generuje deklarację klasy polecenia, taką jak:

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>Klasy rekordów użytkowników z Wstrzykiwanymi atrybutami

Jeśli utworzysz klienta OLE DB przy użyciu atrybutów bazy danych ([db_command](../../windows/db-command.md) lub [DB_Table](../../windows/db-table.md)), atrybuty iniekcji klasy rekordu użytkownika z nazwą formularza "_*ClassName*akcesor". Na przykład jeśli nazwa klasy poleceń `COrders`, Klasa rekordu użytkownika zostanie `_COrdersAccessor`a. Mimo że Klasa rekordu użytkownika pojawia się w **Widok klasy**, dwukrotnie klikając ją w pliku nagłówkowym, można w tym celu przejść do klasy polecenia lub tabeli. W takich przypadkach można wyświetlić tylko rzeczywistą deklarację klasy rekordu użytkownika, wyświetlając kod wstrzykiwanego atrybutu.

Mogą istnieć potencjalne komplikacje w przypadku dodawania lub zastępowania metod w przypadku użytkowników z atrybutami. Na przykład można dodać konstruktora `_COrdersAccessor` do deklaracji `COrders`, ale należy pamiętać, że w rzeczywistości dodaje konstruktora do klasy wstrzykiwanej `COrdersAccessor`. Taki Konstruktor może inicjować kolumny/parametry, ale nie można utworzyć konstruktora kopiującego w ten sposób, ponieważ nie może on bezpośrednio utworzyć wystąpienia obiektu `COrdersAccessor`. Jeśli potrzebujesz konstruktora (lub innej metody) bezpośrednio w klasie `COrders`, zalecamy zdefiniowanie nowej klasy pochodnej z `COrders` i dodanie niezbędnych metod.

W poniższym przykładzie Kreator generuje deklarację dla klasy `COrders`, ale Klasa rekordu użytkownika `COrdersAccessor` nie jest wyświetlona, ponieważ atrybuty iniekcji.

```cpp
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>
[
   db_source(L"your connection string"),
   db_command(L"Select ShipName from Orders;")
]
class COrders
{
public:

   // COrders()            // incorrect constructor name
   _COrdersAccessor()      // correct constructor name
   {
   }
      [db_column(1) ] TCHAR m_ShipName[41];
   };
```

Deklaracja klasy wstrzykiwanych poleceń wygląda następująco:

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

Większość iniekcji kodu jest taka sama jak lub podobna do wersji z szablonami. Główne różnice znajdują się w metodach wstrzykiwanych, które są opisane w [metodach generowanych przez kreatora klienta](../../data/oledb/consumer-wizard-generated-methods.md).

Aby uzyskać informacje na temat wyświetlania wstrzykniętego kodu, zobacz [debugowanie wstrzykiwanego kodu](/visualstudio/debugger/how-to-debug-injected-code).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)