---
title: Klasy konsumentów generowane przez kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b63713dd57695a54a58ce3d57b295cd57cdf393d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338746"
---
# <a name="consumer-wizard-generated-classes"></a>Klasy konsumentów generowane przez kreatora
Gdy możesz generować za pomocą biblioteki ATL OLE DB konsumenta kreatora konsumenta, użytkownik może przy użyciu atrybutów szablony OLE DB lub OLE DB. W obu przypadkach kreator generuje klasę polecenie i klasy rekordu użytkownika. Klasa polecenia zawiera kod, aby otworzyć źródła danych i wierszy, które określiłeś w kreatorze. Klasa rekordu użytkownika zawiera mapę kolumny dla wybranej tabeli bazy danych. Jednak wygenerowanego kodu różni się w każdym przypadku:  
  
-   Jeśli wybierzesz oparte na szablonach konsumenta, Kreator generuje klasę polecenie i klasy rekordu użytkownika. Klasy poleceń będzie mieć nazwę, która zostanie wprowadzona w polu klasy w Kreatorze (na przykład `CProducts`), a klasa rekordu użytkownika będzie zawierał nazwę w postaci "*ClassName*metody dostępu" (na przykład `CProductsAccessor`). Obie klasy są umieszczane w pliku nagłówkowym konsumenta.  
  
-   Jeśli wybierzesz konsumenta atrybutami, klasy rekordów użytkowników mają nazwy w postaci "_*ClassName*metody dostępu" i zostanie dodany. Oznacza to, że będzie mogła wyświetlać tylko klasy poleceń w edytorze tekstów; Klasa rekordu użytkownika mogą wyświetlać tylko jako wprowadzonego kodu. Aby uzyskać informacje o wyświetlaniu wprowadzonego kodu, zobacz [debugowania kodu wprowadzony](/visualstudio/debugger/how-to-debug-injected-code).  
  
 W poniższych przykładach używane polecenia klasy utworzone w tabeli Produkty bazy danych Northwind, aby zademonstrować kod generowane przez kreatora konsumenta klasy polecenia i klasa rekordu użytkownika.  
  
## <a name="templated-user-record-classes"></a>Klasy rekordów użytkowników oparte na szablonach  
 Jeśli tworzysz konsumenta OLE DB przy użyciu szablonów OLE DB (zamiast atrybuty OLE DB), Kreator generuje kod, zgodnie z opisem w tej sekcji.  
  
### <a name="column-data-members"></a>Elementy członkowskie danych kolumny  
 Pierwsza część klasy rekordu użytkownika zawiera deklaracji elementu członkowskiego danych i elementy członkowskie danych stanu i długość dla każdej kolumny powiązane z danymi. Aby uzyskać informacji na temat tych elementów członkowskich danych, zobacz [elementy członkowskie danych stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
> [!NOTE]
>  Jeśli modyfikujesz klasy rekordu użytkownika lub napisać własny konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.  
  
> [!NOTE]
>  ATL OLE DB konsumenta kreator używa `DB_NUMERIC` typu, aby powiązać liczbowych typów danych. On wcześniej użyty `DBTYPE_VARNUMERIC` (format jest opisana przez `DB_VARNUMERIC` typu; Zobacz Oledb.h). Jeśli nie używasz kreatora do tworzenia użytkowników, zalecane jest użycie `DB_NUMERIC`.  
  
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
 Następnie Kreator ustawia właściwości zestawu wierszy. W przypadku wybrania **zmiany**, **Wstaw**, lub **Usuń** w OLE DB Kreator konsumenta ATL, odpowiednie właściwości są ustawione w tym miejscu (DBPROP_IRowsetChange zawsze ustawiono, następnie jednym co najmniej DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT i/lub DBPROPVAL_UP_DELETE, odpowiednio).  
  
```cpp  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
### <a name="command-or-table-class"></a>Polecenie lub klasy tabeli  
 Jeśli określisz klasy polecenia, Kreator deklaruje klasy polecenia; Kod, oparte na szablonach polecenie wygląda następująco:  
  
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
  
### <a name="column-map"></a>Mapa kolumny  
 Kreator generuje następnie powiązania kolumny lub mapie kolumny. Aby rozwiązać pewne problemy z niektórymi dostawcami, poniższy kod może powiązać kolumny w innym porządku niż zgłoszony przez dostawcę.  
  
```  
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
 Na koniec Kreator generuje deklarację klasy polecenia, takie jak następujące:  
  
```cpp  
class CProducts : public CCommand<CAccessor<CProductsAccessor>>  
```  
  
## <a name="attribute-injected-user-record-classes"></a>Klasy rekordów użytkowników z wprowadzonym atrybutem  
 Jeśli utworzysz konsumenta OLE DB przy użyciu atrybutów bazy danych ([db_command —](../../windows/db-command.md) lub [db_table —](../../windows/db-table.md)), atrybuty wstawić klasy do rekordu użytkownika o nazwie w postaci "_*ClassName*Akcesor. " Na przykład, jeśli nazwę klasy polecenia `COrders`, klasa rekordu użytkownika będzie `_COrdersAccessor`. Chociaż klasa rekordu użytkownika jest wyświetlany w widoku klas, kliknij go dwukrotnie powoduje przejście do klasy polecenia lub tabeli w pliku nagłówkowym zamiast tego. W takich przypadkach rzeczywista deklaracja klasy rekordu użytkownika mogą wyświetlać tylko przeglądając kod wprowadzonym atrybutem.  
  
 Może być potencjalne kompilacji w przypadku dodania lub zastąpienia metody w opartego na atrybutach konsumentów. Na przykład można dodać `_COrdersAccessor` Konstruktor `COrders` deklaracji, ale należy pamiętać, że w rzeczywistości spowoduje to dodanie konstruktora do wprowadzonego `COrdersAccessor` klasy. Taki Konstruktor może zainicjować kolumny/parametrów, ale nie można utworzyć konstruktora kopiującego w ten sposób, ponieważ on nie można bezpośrednio utworzyć wystąpienia `COrdersAccessor` obiektu. Jeśli potrzebujesz konstruktora (lub innej metody) bezpośrednio na `COrders` klasy, zalecane jest, że zdefiniujesz Nowa Klasa pochodząca od `COrders` i Dodawanie metody niezbędne.  
  
 W poniższym przykładzie, Kreator generuje deklarację klasy `COrders`, ale klasa rekordu użytkownika `COrdersAccessor` jest niewidoczny, ponieważ atrybutów wstrzyknięcia go.  
  
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
  
 Deklaracja klasy wprowadzonego polecenia wygląda następująco:  
  
```  
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>  
```  
  
 Większość wprowadzonego kodu jest taka sama jak lub podobne do wersji z szablonem. Główne różnice znajdują się w wprowadzonego kodu metody, które są opisane w [metody Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-methods.md).  
  
 Aby uzyskać informacje o wyświetlaniu wprowadzonego kodu, zobacz [debugowania kodu wprowadzony](/visualstudio/debugger/how-to-debug-injected-code).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)