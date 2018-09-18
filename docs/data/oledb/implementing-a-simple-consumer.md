---
title: Implementowanie prostego konsumenta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 681aa3ef5a1434ab191854f23a9e7bc908b65728
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082420"
---
# <a name="implementing-a-simple-consumer"></a>Implementowanie prostego konsumenta

Poniższe tematy przedstawiają sposób edytowania plików utworzonych przez Kreatora aplikacji MFC i ATL OLE DB Kreator konsumenta Tworzenie prostego konsumenta. W tym przykładzie ma następujące elementy:  
  
- "Pobieranie danych z konsumentem" pokazuje, jak zaimplementować kod u odbiorcy, która odczytuje dane, wiersz po wierszu z tabeli bazy danych.  
  
- "Dodawanie pozycję obsługują zakładki do odbiorcy" pokazuje, jak dodać obsługę zakładki do konsumenta.  
  
- "Dodawanie obsługi XML do odbiorcy" pokazuje, jak zmodyfikować kod klienta do wysyłania danych odzyskanych wierszy danych XML.  
  
> [!NOTE]
>  Aplikacji konsumentów, opisane w tej sekcji służy do testowania dostawcy próbki MyProv i dostawcy.  
  
> [!NOTE]
>  Aby skompilować aplikację konsumenta, aby przetestować MyProv (tego samego dostawcy opisanego w [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)), musi zawierać Obsługa zakładek, zgodnie z opisem w "Dodawanie Obsługa zakładek do użytkownika."  
  
> [!NOTE]
>  Aby skompilować aplikację klienta, aby przetestować dostawcy, opuszczenie Obsługa zakładek, opisane w "Dodawanie zakładki pomocy technicznej do odbiorcy", a następnie przejdź do "Dodawanie XML Support konsumenta."  
  
## <a name="retrieving-data-with-the-consumer"></a>Trwa pobieranie danych z konsumentem  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Aby zmodyfikować aplikację konsolową używać konsumenta OLE DB  
  
1. W MyCons.cpp Zmień głównego kodu, wstawiając pogrubioną czcionką w następujący sposób:  
  
    ```cpp  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
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
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Dodawanie obsługi zakładki do konsumenta  

Zakładka jest kolumna, która unikatowo identyfikuje wierszy w tabeli. Zazwyczaj jest kolumna klucza, ale nie zawsze; jest specyficzny dla dostawcy. W tej sekcji dowiesz się, jak dodać obsługę zakładki. Aby to zrobić, należy wykonać następujące czynności w klasie rekord użytkownika:  
  
- Tworzy zakładki. Są to obiekty typu [CBookmark](../../data/oledb/cbookmark-class.md).  
  
- Żądanie kolumnę zakładki z dostawcy, ustawiając `DBPROP_IRowsetLocate` właściwości.  
  
- Dodaj wpis zakładki do mapy kolumny przy użyciu [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) makra.  
  
Poprzednie kroki umożliwiają Obsługa zakładek i obiekt zakładki, z którą chcesz pracować. Ten przykład kodu pokazuje zakładki w następujący sposób:  
  
- Otwórz plik do zapisu.  
  
- Zestaw wierszy dane wyjściowe do pliku wiersz po wierszu.  
  
- Przesunięcie kursora wierszy do zakładki, wywołując [movetobookmark —](../../data/oledb/crowset-movetobookmark.md).  
  
- Dane wyjściowe wiersza zakładką, dołączenie jej do końca pliku.  
  
> [!NOTE]
>  Jeśli używasz tej aplikacji klienta do testowania Przykładowa aplikacja dostawcy dostawcy Opuść Obsługa zakładek, opisane w tej sekcji.  
  
#### <a name="to-instantiate-the-bookmark"></a>Aby utworzyć wystąpienie zakładki  
  
1. Metoda dostępu musi zawierać obiektu typu [CBookmark](../../data/oledb/cbookmark-class.md). *NSize* parametr określa rozmiar buforu zakładki w bajtach (zwykle 4 dla platform 32-bitowe) i 8 na platformach 64-bitowych. Do elementów członkowskich danych kolumny w klasie rekord użytkownika, należy dodać następującą deklarację:  
  
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
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>Żądanie kolumnę zakładki z dostawcy  
  
1. Dodaj następujący kod w `GetRowsetProperties` metody w klasie rekordu użytkownika:  
  
    ```cpp  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Aby dodać wpis zakładki do mapy kolumny  
  
1. Dodaj następujący wpis do mapy kolumny w klasie rekord użytkownika:  
  
    ```cpp  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Aby użyć zakładki w kodzie głównego  
  
1. W pliku MyCons.cpp z aplikacji konsoli, który został wcześniej utworzony Zmień głównego kodu do odczytu w następujący sposób. Aby użyć zakładek, trzeba utworzyć swój własny obiektu zakładki głównego kodu (`myBookmark`); jest to zakładki innego niż ten, w metodzie dostępu (`m_bookmark`).  
  
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
  
Aby uzyskać więcej informacji na temat zakładek, zobacz [przy użyciu zakładki](../../data/oledb/using-bookmarks.md). Przykłady zakładki są także wyświetlane w [aktualizowanie zestawów wierszy](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Dodawanie obsługi XML do konsumenta  

Zgodnie z opisem w [uzyskiwania dostępu do danych XML](../../data/oledb/accessing-xml-data.md), istnieją dwa sposoby, aby pobrać dane XML ze źródła danych: za pomocą [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) lub za pomocą [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). W tym przykładzie użyto `CStreamRowset`, który jest bardziej wydajne, ale wymagane jest posiadanie programu SQL Server 2000 uruchomionej na komputerze, w którym są wykonywane tej przykładowej aplikacji.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Aby zmodyfikować klasy polecenia, aby dziedziczyć cstreamrowset —  
  
1. W aplikacji konsumentów, została wcześniej utworzona, należy zmienić swoje `CCommand` deklaracji, aby określić `CStreamRowset` jako zestaw wierszy klasy w następujący sposób:  
  
    ```cpp  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Aby zmodyfikować głównego kodu do pobierania i zwracania danych XML  
  
1. W pliku MyCons.cpp z aplikacji konsoli, który został wcześniej utworzony Zmień głównego kodu do odczytu w następujący sposób:  
  
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

[Tworzenie konsumenta OLE DB przy użyciu kreatora](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)