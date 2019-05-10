---
title: Metody konsumenta generowane przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 409d339acb37bd09ae10eabba16e19d5df0aae63
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525028"
---
# <a name="consumer-wizard-generated-methods"></a>Metody konsumenta generowane przez kreatora

::: moniker range="vs-2019"

Kreator OLE DB konsumenta ATL nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach. Można nadal ręcznie dodawać funkcje.

::: moniker-end

::: moniker range="vs-2017"

**OLE DB Kreator konsumenta ATL** i **Kreator aplikacji MFC** generować pewne funkcje, których należy wiedzieć. Niektóre metody są implementowane w inny sposób w projektach atrybutami, więc istnieje kilka zastrzeżenia; Każdy przypadek jest opisane poniżej. Aby uzyskać informacje o wyświetlaniu wprowadzonego kodu, zobacz [debugowania kodu wprowadzony](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` Otwiera źródło danych, zestawy wierszy i powoduje włączenie zakładki, jeśli są one dostępne.

- `CloseAll` Zamyka wszystkie otwarte zestawów wierszy i wersje wszystkich wykonań poleceń.

- `OpenRowset` jest wywoływana przez `OpenAll` otworzyć konsumenta lub zbiory wierszy.

- `GetRowsetProperties` pobiera wskaźnik do za pomocą właściwości, które można ustawić właściwość zestawu wierszy.

- `OpenDataSource` Otwiera źródło danych przy użyciu parametrów inicjacji określone w **właściwości Linku danych** okno dialogowe.

- `CloseDataSource` Zamyka źródła danych w odpowiedni sposób.

## <a name="openall-and-closeall"></a>Openall — i closeall —

```cpp
HRESULT OpenAll();

void CloseAll();
```

W poniższym przykładzie pokazano, jak można wywołać `OpenAll` i `CloseAll` podczas wykonywania tego samego polecenia wielokrotnie. Porównaj przykładowy kod z [CCommand::Close](../../data/oledb/ccommand-close.md), który wskazuje odmiany, który wywołuje `Close` i `ReleaseCommand` zamiast `CloseAll`.

```cpp
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

### <a name="remarks"></a>Uwagi

Jeśli zdefiniujesz `HasBookmark` metody `OpenAll` kod ustawia `DBPROP_IRowsetLocate` właściwości; upewnij się, możesz to zrobić tylko jeśli Twój dostawca obsługuje tej właściwości.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` wywołuje tę metodę, aby otworzyć wierszy lub zestawy wierszy w konsumenta. Zazwyczaj nie trzeba wywoływać `OpenRowset` , chyba że chcesz pracować z wieloma danych źródła/sesje/zestawów wierszy. `OpenRowset` jest zadeklarowana w pliku nagłówkowym klasę polecenia lub tabeli:

```cpp
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

Atrybuty zaimplementować tę metodę w różny sposób. Ta wersja przyjmuje obiekt sesji i ciąg polecenia, który domyślnie przyjmuje wartość ciągu polecenia określony w db_command —, mimo że można przekazać inny. Jeśli zdefiniujesz `HasBookmark` metody `OpenRowset` kod ustawia `DBPROP_IRowsetLocate` właściwości; upewnij się, możesz to zrobić tylko jeśli Twój dostawca obsługuje tej właściwości.

```cpp
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

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

Ta metoda pobiera wskaźnik do zestawu właściwości zestawu wierszy; można użyć tego wskaźnika można ustawić właściwości, takie jak `DBPROP_IRowsetChange`. `GetRowsetProperties` jest używany w następujący sposób w klasie rekordu użytkownika. Można zmodyfikować ten kod, aby ustawić właściwości dodatkowych wierszy:

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Uwagi

Nie należy zdefiniować globalną `GetRowsetProperties` metoda, ponieważ może ona konflikt z wersją zdefiniowana przez kreatora. Jest to metoda generowane przez kreatora, której można korzystać z projektów oparte na szablonach i opartego na atrybutach; atrybuty nie wstrzyknąć tego kodu.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource i closedatasource —

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Uwagi

Kreator definiuje metody `OpenDataSource` i `CloseDataSource`; `OpenDataSource` wywołania [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)