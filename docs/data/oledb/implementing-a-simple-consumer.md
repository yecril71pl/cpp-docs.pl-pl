---
title: Implementowanie prostego konsumenta | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7dc97c0e64558f066250a54098f7316ac8b33076
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-simple-consumer"></a>Implementowanie prostego konsumenta
W następujących tematach opisano, jak edytować pliki tworzone przez Kreatora aplikacji MFC i ATL OLE DB Kreator konsumenta Tworzenie prostego konsumenta. Ten przykład zawiera następujące części:  
  
-   "Pobieranie danych z klienta" przedstawia sposób implementowania kodu w konsumenta, która odczytuje dane, wiersz po wierszu z tabeli bazy danych.  
  
-   "Dodawanie pozycję obsługuje zakładkę do użytkownika" przedstawiono sposób dodawania Obsługa zakładek do użytkownika.  
  
-   "Dodawanie obsługi XML do użytkownika" pokazuje, jak można zmodyfikować kod klienta do wysyłania danych pobranych wierszy danych XML.  
  
> [!NOTE]
>  Aplikacja konsumenta opisane w tej sekcji służy do testowania dostawców próbki MyProv i dostawcy.  
  
> [!NOTE]
>  Do tworzenia aplikacji klienta, aby przetestować MyProv (tego samego dostawcy opisanego w [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)), należy uwzględnić Obsługa zakładek zgodnie z opisem w "Dodawanie Obsługa zakładek do użytkownika."  
  
> [!NOTE]
>  Do tworzenia aplikacji konsumentów do testowania dostawcy, Opuść Obsługa zakładek opisanego w "Dodawanie zakładki obsługuje do użytkownika" i przejdź do "Dodawanie XML Obsługa klientowi."  
  
## <a name="retrieving-data-with-the-consumer"></a>Pobieranie danych z konsumenta  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Aby zmodyfikować aplikację konsoli konsumenta OLE DB  
  
1.  W MyCons.cpp należy zmienić kod głównego, podając pogrubiony tekst w następujący sposób:  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset   CProducts rs;   hr = rs.OpenAll();   ATLASSERT( SUCCEEDED( hr ) );   hr = rs.MoveFirst();   // Iterate through the rowset   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row      printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",             rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );      hr = rs.MoveNext();   }   rs.Close();   rs.ReleaseCommand();   CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Dodawanie obsługi zakładkę do użytkownika  
 Zakładka jest kolumny, które jednoznacznie identyfikują wiersze w tabeli. Zazwyczaj jest kolumna klucza, ale nie zawsze; jest specyficznych dla dostawcy. W tej sekcji przedstawiono sposób dodawania Obsługa zakładek. Aby to zrobić, należy wykonać następujące czynności w klasie rekord użytkownika:  
  
-   Tworzy zakładki. Są to obiekty typu [CBookmark](../../data/oledb/cbookmark-class.md).  
  
-   Żądanie kolumnę zakładki z dostawcy przez ustawienie **DBPROP_IRowsetLocate** właściwości.  
  
-   Dodaj wpis zakładkę do mapowania kolumn za pomocą [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) makra.  
  
 Poprzednie kroki umożliwiają Obsługa zakładek i obiektu zakładki, z którą chcesz pracować. Ten przykładowy kod przedstawia zakładki w następujący sposób:  
  
-   Otwórz plik do zapisu.  
  
-   Dane zestawu wierszy dane wyjściowe do pliku wiersz po wierszu.  
  
-   Przesuń kursor zestawu wierszy do zakładki przez wywołanie metody [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).  
  
-   Dane wyjściowe wiersza zakładką, dołączenie go do końca pliku.  
  
> [!NOTE]
>  Jeśli używasz tej aplikacji konsumentów do testowania aplikacji dostawcy przykładowej dostawcy Opuść Obsługa zakładek opisane w tej sekcji.  
  
#### <a name="to-instantiate-the-bookmark"></a>Można utworzyć wystąpienia zakładki  
  
1.  Metoda dostępu musi zawierać obiektu typu [CBookmark](../../data/oledb/cbookmark-class.md). `nSize` Parametr określa rozmiar buforu zakładki w bajtach (zazwyczaj 4 dla 32-bitowych platform) i 8 na platformach 64-bitowych. Dodaj następujące oświadczenie do elementów członkowskich danych kolumny w klasie rekord użytkownika:  
  
    ```  
    //////////////////////////////////////////////////////////////////////  
    // Products.h  
    class CProductsAccessor  
    {  
    public:  
       CBookmark<4> m_bookmark;   // Add bookmark declaration  
       LONG m_ProductID;  
       ...  
    ```  
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>Aby zażądać kolumnę zakładki z dostawcy  
  
1.  Dodaj następujący kod w `GetRowsetProperties` metody w klasie rekordu użytkownika:  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Aby dodać wpis zakładkę do mapowania kolumn  
  
1.  Dodaj następujący wpis do mapowania kolumn w klasie rekord użytkownika:  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Aby użyć zakładki w kodzie głównego  
  
1.  W pliku MyCons.cpp z aplikacji konsoli, utworzonych wcześniej zmianę kodu głównego do odczytu w następujący sposób. Aby użyć zakładki, głównego kodu musi wystąpienia obiektu własną zakładki (`myBookmark`); to zakładki innego niż ten, w metodzie dostępu (`m_bookmark`).  
  
    ```  
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
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          nCounter++;  
          if( nCounter == 5 )  
             myBookmark = rs.bookmark;  
          // Output the column information for each row:  
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;  
          hr = rs.MoveNext();  
       }  
  
       // Move cursor to bookmark  
       hr = rs.MoveToBookmark(myBookmark);  
  
       // Iterate through the rowset and output column data to output.txt row by row  
       // In the file, mark the beginning of this set of data:  
       outfile << "row dump starting from bookmarked row" << endl;  
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
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
  
 Aby uzyskać więcej informacji na temat zakładki, zobacz [przy użyciu zakładki](../../data/oledb/using-bookmarks.md). Przykłady zakładek są także wyświetlane w [aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Dodawanie obsługi XML do użytkownika  
 Zgodnie z opisem w [podczas uzyskiwania dostępu do danych XML](../../data/oledb/accessing-xml-data.md), istnieją dwa sposoby można pobrać danych XML źródła danych: za pomocą [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) lub przy użyciu [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). W tym przykładzie użyto `CStreamRowset`, które jest bardziej wydajne, ale wymagane jest uruchomiona na komputerze, na którym będzie wykonanie tej przykładowej aplikacji programu SQL Server 2000.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Aby zmodyfikować dziedziczyć cstreamrowset — klasa polecenia  
  
1.  W aplikacji klienta została wcześniej utworzona, zmień Twoje `CCommand` deklaracji, aby określić `CStreamRowset` jako zestawu wierszy klas w następujący sposób:  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Aby zmodyfikować kod głównego do pobierania i zwracania danych XML  
  
1.  W pliku MyCons.cpp z aplikacji konsoli, utworzonych wcześniej zmianę kodu głównego do odczytu w następujący sposób:  
  
    ```  
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
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
          HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB przy użyciu Kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)