---
title: Metody konsumenta generowane przez kreatora
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: ce2442909fd318187a1508300a75ff4f634b3410
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211513"
---
# <a name="consumer-wizard-generated-methods"></a>Metody konsumenta generowane przez kreatora

::: moniker range="vs-2019"

Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje.

::: moniker-end

::: moniker range="<=vs-2017"

**Kreator użytkownika ATL OLE DB** i **Kreator aplikacji MFC** generują pewne funkcje, których należy wiedzieć. Niektóre metody są implementowane inaczej w projektach z atrybutami, więc istnieją pewne zastrzeżenia: Każdy przypadek jest objęty poniżej. Aby uzyskać informacje na temat wyświetlania wstrzykniętego kodu, zobacz [debugowanie wstrzykiwanego kodu](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` otwiera źródło danych, zestawy wierszy i włącza zakładki, jeśli są dostępne.

- `CloseAll` zamyka wszystkie otwarte zestawy wierszy i zwalnia wszystkie wykonania poleceń.

- `OpenRowset` jest wywoływana przez `OpenAll`, aby otworzyć zestaw wierszy lub zestawy wierszy konsumenta.

- `GetRowsetProperties` Pobiera wskaźnik do zbioru właściwości zestawu wierszy, dla którego można ustawić właściwości.

- `OpenDataSource` otwiera źródło danych przy użyciu ciągu inicjującego określonego w oknie dialogowym **Właściwości łącza danych** .

- `CloseDataSource` zamyka źródło danych w odpowiedni sposób.

## <a name="openall-and-closeall"></a>Metody OpenAll i CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

Poniższy przykład pokazuje, jak można wywołać `OpenAll` i `CloseAll`, gdy wielokrotnie wykonujesz to samo polecenie. Porównaj przykład kodu w [CCommand:: Close](../../data/oledb/ccommand-close.md), który pokazuje odmianę, która wywołuje `Close` i `ReleaseCommand` zamiast `CloseAll`.

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

W przypadku zdefiniowania metody `HasBookmark`, kod `OpenAll` ustawia właściwość `DBPROP_IRowsetLocate`; Upewnij się, że jest to możliwe tylko wtedy, gdy dostawca obsługuje tę właściwość.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` wywołuje tę metodę, aby otworzyć zestaw wierszy lub zestawy wierszy w odbiorcy. Zazwyczaj nie trzeba wywoływać `OpenRowset`, chyba że chcesz współpracować z wieloma źródłami danych/sesjami/zestawami wierszy. `OpenRowset` jest zadeklarowana w pliku nagłówkowym polecenia lub klasy tabeli:

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

Atrybuty implementują tę metodę inaczej. Ta wersja pobiera obiekt sesji i ciąg polecenia, który domyślnie jest ciągiem poleceń określonym w db_command, chociaż można przekazać inny. W przypadku zdefiniowania metody `HasBookmark`, kod `OpenRowset` ustawia właściwość `DBPROP_IRowsetLocate`; Upewnij się, że jest to możliwe tylko wtedy, gdy dostawca obsługuje tę właściwość.

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

Ta metoda pobiera wskaźnik do zestawu właściwości zestawu wierszy; Możesz użyć tego wskaźnika, aby ustawić właściwości, takie jak `DBPROP_IRowsetChange`. `GetRowsetProperties` jest używany w klasie rekordu użytkownika w następujący sposób. Możesz zmodyfikować ten kod, aby ustawić dodatkowe właściwości zestawu wierszy:

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

Nie należy definiować globalnej metody `GetRowsetProperties`, ponieważ może ona powodować konflikt z elementem zdefiniowanym przez kreatora. Jest to metoda wygenerowana przez kreatora, którą można uzyskać z szablonem i projektami z atrybutami. atrybuty nie wstrzyknąć tego kodu.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource i CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Uwagi

Kreator definiuje metody `OpenDataSource` i `CloseDataSource`; wywołania `OpenDataSource` [CDataSource:: OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
