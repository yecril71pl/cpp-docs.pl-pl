---
title: Implementowanie prostego konsumenta
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 9e93b40313a215dfe5872b33dc7d41641204a2f1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508974"
---
# <a name="implementing-a-simple-consumer"></a>Implementowanie prostego konsumenta

::: moniker range="vs-2019"

Kreator użytkownika ATL OLE DB nie jest dostępny w programie Visual Studio 2019 i nowszych. Można nadal ręcznie dodawać funkcje. Aby uzyskać więcej informacji, zobacz [Tworzenie klienta bez korzystania z Kreatora](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

W poniższych tematach przedstawiono sposób edytowania plików utworzonych przez **Kreatora aplikacji MFC** i Kreatora programu **ATL OLE DB użytkownika** w celu utworzenia prostego konsumenta. Ten przykład zawiera następujące części:

- [Pobieranie danych z konsumenta](#retrieve) pokazuje, jak zaimplementować kod w odbiorcy, który odczytuje wszystkie dane, wiersz po wierszu, z tabeli bazy danych.

- [Dodanie obsługi zakładki do konsumenta](#bookmark) pokazuje, jak dodać obsługę zakładki do konsumenta.

> [!NOTE]
> Możesz użyć aplikacji konsumenta opisanej w tej sekcji, aby przetestować `MyProv` `Provider` przykładowo dostawców i.

> [!NOTE]
> Aby skompilować aplikację konsumenta do testowania `MyProv` (ten sam dostawca opisany w temacie [ulepszanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)), musisz dołączyć obsługę zakładki zgodnie z opisem w temacie [Dodawanie obsługi zakładki do konsumenta](#bookmark).

## <a name="retrieving-data-with-the-consumer"></a><a name="retrieve" ></a> Pobieranie danych z konsumenta

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Aby zmodyfikować aplikację konsolową tak, aby korzystała z klienta OLE DB

1. W programie `MyCons.cpp` Zmień kod główny, wstawiając tekst pogrubiony w następujący sposób:

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="adding-bookmark-support-to-the-consumer"></a><a name="bookmark" ></a> Dodawanie obsługi zakładki do konsumenta

Zakładka to kolumna, która jednoznacznie identyfikuje wiersze w tabeli. Zwykle jest to kolumna klucza, ale nie zawsze; jest on specyficzny dla dostawcy. W tej sekcji przedstawiono sposób dodawania obsługi zakładki. W tym celu należy wykonać następujące kroki w klasie rekordu użytkownika:

- Tworzenie wystąpienia zakładek. Są to obiekty typu [CBookmark](../../data/oledb/cbookmark-class.md).

- Zażądaj kolumny zakładki od dostawcy, ustawiając `DBPROP_IRowsetLocate` Właściwość.

- Dodaj wpis zakładki do mapy kolumn za pomocą makra [BOOKMARK_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#bookmark_entry) .

Poprzednie kroki zapewniają obsługę zakładek i obiekt zakładek, z którymi należy korzystać. Ten przykład kodu demonstruje zakładkę w następujący sposób:

- Otwórz plik do zapisu.

- Dane wyjściowe zestawu wierszy do wiersza pliku według wiersza.

- Przenieś kursor zestawu wierszy do zakładki, wywołując [MoveToBookmark](./crowset-class.md#movetobookmark).

- Wyprowadza wiersz z zakładką, dołączając go na końcu pliku.

> [!NOTE]
> W przypadku korzystania z tej aplikacji konsumenta do testowania `Provider` przykładowej aplikacji dostawcy należy skorzystać z pomocy technicznej zakładki opisanej w tej sekcji.

### <a name="to-instantiate-the-bookmark"></a>Aby utworzyć wystąpienie zakładki

1. Metoda dostępu musi przechowywać obiekt typu [CBookmark](../../data/oledb/cbookmark-class.md). Parametr *nSize* określa rozmiar buforu zakładki w bajtach (zwykle 4 dla platform 32-bitowych i 8 dla platform 64-bitowych). Dodaj następującą deklarację do elementów członkowskich danych w klasie rekordu użytkownika:

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>Aby zażądać kolumny zakładki od dostawcy

1. Dodaj następujący kod w `GetRowsetProperties` metodzie w klasie rekordu użytkownika:

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Aby dodać wpis zakładki do mapy kolumn

1. Dodaj następujący wpis do mapy kolumn w klasie rekordu użytkownika:

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>Aby użyć zakładki w kodzie głównym

1. W `MyCons.cpp` pliku z wcześniej utworzonej aplikacji konsolowej Zmień kod główny, tak aby był odczytywany w następujący sposób. Aby można było używać zakładek, główny kod musi utworzyć wystąpienie własnego obiektu zakładki ( `myBookmark` ); jest to inna zakładka z jednej w metodzie dostępu ( `m_bookmark` ).

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

Aby uzyskać więcej informacji na temat zakładek, zobacz [using zakładki](../../data/oledb/using-bookmarks.md). Przykłady zakładek są również wyświetlane w temacie [Aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
