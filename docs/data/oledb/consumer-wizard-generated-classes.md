---
title: "Klasy konsumentów generowane przez kreatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ebd53b8b39fb94e4275f5052a74f77bf71bd790
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="consumer-wizard-generated-classes"></a>Klasy konsumentów generowane przez kreatora
Gdy używasz OLE DB Kreator konsumenta ATL do wygenerowania z klientem, użytkownik może przy użyciu atrybutów szablony OLE DB lub OLE DB. W obu przypadkach kreator generuje klasę polecenie i klasy rekordu użytkownika. Klasa polecenia zawiera kod, aby otworzyć źródła danych i zestawu wierszy określone w kreatorze. Klasa rekordu użytkownika zawiera mapy kolumny dla wybranej tabeli bazy danych. Jednak wygenerowany kod różni się w każdym przypadku:  
  
-   W przypadku wybrania szablonu konsumenta, Kreator generuje klasę polecenie i klasy rekordu użytkownika. Klasy poleceń ma nazwę, która zostanie wprowadzona w polu klasy w Kreatorze (na przykład `CProducts`), i klasy rekordów użytkowników mają nazwy w postaci "*ClassName*metody dostępu" (na przykład `CProductsAccessor`). Obie klasy znajdują się w pliku nagłówka konsumenta.  
  
-   W przypadku wybrania konsumenta oparte na atrybutach klasy rekordów użytkowników mają nazwy w postaci "_*ClassName*metody dostępu" i zostaną dodane. Oznacza to, że będzie mogła wyświetlać tylko klasy poleceń w edytorze tekstu; klasy rekordów użytkowników można przeglądać tylko jako wprowadzony kod. Aby uzyskać informacje o wyświetlaniu wprowadzony kod, zobacz [debugowania wstrzyknięcie kodu](/visualstudio/debugger/how-to-debug-injected-code).  
  
 W poniższych przykładach użyto klasy poleceń utworzyć dla tabeli Produkty bazy danych Northwind, aby zademonstrować generowane przez kreatora konsumenta kod klasy polecenie i klasy rekordu użytkownika.  
  
## <a name="templated-user-record-classes"></a>Klasy rekordów użytkowników opartego na szablonie  
 Jeśli tworzysz konsumenta OLE DB przy użyciu szablonów OLE DB (zamiast atrybuty OLE DB), Kreator generuje kod, zgodnie z opisem w tej sekcji.  
  
### <a name="column-data-members"></a>Elementy członkowskie kolumny danych  
 Pierwsza część klasy rekordu użytkownika zawiera deklaracji elementu członkowskiego danych i elementy członkowskie danych stanu i długość dla każdej kolumny powiązane z danymi. Informacje o tych elementów członkowskich danych znajdują się w temacie [elementy członkowskie dotyczących stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
> [!NOTE]
>  Modyfikowanie klasy rekordów użytkowników lub napisać własny konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.  
  
> [!NOTE]
>  OLE DB Kreator konsumenta ATL używa **DB_NUMERIC** typu powiązać liczbowych typów danych. Wcześniej używana przez nią **DBTYPE_VARNUMERIC** (format jest opisane przez **DB_VARNUMERIC** typ; Zobacz Oledb.h). Jeśli Kreator nie umożliwiają utworzenie konsumentów, zalecane jest użycie **DB_NUMERIC**.  
  
```  
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
 Następnie Kreator ustawia właściwości zestawu wierszy. W przypadku wybrania **zmiany**, **Wstaw**, lub **usunąć** w OLE DB Kreator konsumenta ATL, odpowiednie właściwości są ustawiane w tym miejscu (DBPROP_IRowsetChange jest zawsze ustawiona, następnie co co najmniej DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT i/lub DBPROPVAL_UP_DELETE, odpowiednio).  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
### <a name="command-or-table-class"></a>Polecenie lub klasy tabeli  
 Jeśli określisz klasy poleceń, Kreator deklaruje klasy poleceń; dla kodu opartego na szablonie polecenie wygląda następująco:  
  
```  
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
  
### <a name="column-map"></a>Mapowania kolumn  
 Kreator generuje następnie powiązania kolumny lub mapowania kolumn. Aby rozwiązać pewne problemy z niektórymi dostawcami, poniższy kod może powiązać kolumny w innym porządku niż zgłoszony przez dostawcę.  
  
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
 Ponadto Kreator generuje deklaracji klasy polecenia, takie jak następujące:  
  
```  
class CProducts : public CCommand<CAccessor<CProductsAccessor> >  
```  
  
## <a name="attribute-injected-user-record-classes"></a>Klasy rekordów użytkowników z wprowadzonym atrybutem  
 Jeśli tworzenie konsumenta OLE DB za pomocą atrybutów bazy danych ([db_command —](../../windows/db-command.md) lub [db_table —](../../windows/db-table.md)), atrybutów wstrzyknąć klasy rekordu użytkownika o nazwie w postaci "_*ClassName*Akcesor. " Na przykład, jeśli nazwę klasy polecenia `COrders`, klasy rekordów użytkowników będzie `_COrdersAccessor`. Chociaż klasa rekordu użytkownika znajduje się w widoku klas, kliknij go dwukrotnie przechodzi do polecenia lub tabeli klasy w pliku nagłówka zamiast tego. W takich przypadkach możesz jedynie wyświetlić rzeczywista deklaracja klasy rekordów użytkowników przez wyświetlanie wprowadzonym atrybutem kodu.  
  
 Potencjalne komplikacji może istnieć, jeśli Dodawanie lub zastąpienie metody użytkowników oparte na atrybutach. Na przykład można dodać `_COrdersAccessor` konstruktora `COrders` deklaracji, ale należy pamiętać, że w rzeczywistości spowoduje to dodanie konstruktora do wprowadzony `COrdersAccessor` klasy. Takie Konstruktor może zainicjować kolumny/parametrów, ale nie można utworzyć konstruktora kopiującego temu, ponieważ nie można bezpośrednio wystąpienia `COrdersAccessor` obiektu. Jeśli potrzebujesz konstruktora (lub innej metody) bezpośrednio na `COrders` klasy, zalecane jest, aby zdefiniować nowej klasy wywodzące się z `COrders` i Dodaj te metody niezbędne.  
  
 W poniższym przykładzie, Kreator generuje deklaracji klasy `COrders`, ale klasa rekordu użytkownika `COrdersAccessor` nie jest wyświetlana, ponieważ atrybuty wstrzyknąć go.  
  
```  
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
class CProducts : public CCommand<CAccessor<_CProductsAccessor> >  
```  
  
 Większość wprowadzony kod jest taka sama jak lub podobne do wersji szablonem. Główne różnice są wprowadzony metod, które zostały opisane w [metody Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-methods.md).  
  
 Aby uzyskać informacje o wyświetlaniu wprowadzony kod, zobacz [debugowania wstrzyknięcie kodu](/visualstudio/debugger/how-to-debug-injected-code).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)