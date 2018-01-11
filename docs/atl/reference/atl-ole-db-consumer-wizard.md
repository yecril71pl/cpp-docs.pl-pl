---
title: Kreator konsumenta OLE DB ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.consumer.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d12020b6adfca2c23dc610b5e596ff883bb9e7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-ole-db-consumer-wizard"></a>Kreator konsumenta OLE DB ATL
Ten kreator konfiguruje klasę konsumenta OLE DB z powiązaniami danych niezbędnych do uzyskania dostępu z określonego źródła danych za pomocą określonego dostawcy OLE DB.  
  
> [!NOTE]
>  Ten kreator wymaga, aby **źródła danych** przycisk, aby wybrać źródło danych przed wprowadzeniem nazwy w `Class` i **pliku .h** pola.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Źródło danych**  
 **Źródła danych** przycisk umożliwia konfigurowanie określonego źródła danych przy użyciu określonego dostawcy OLE DB. Po kliknięciu tego przycisku **właściwości Linku danych** zostanie wyświetlone okno dialogowe. Aby uzyskać więcej informacji na temat budowania parametry połączenia i **właściwości Linku danych** okno dialogowe, zobacz [omówienie interfejsu API łącza danych](https://msdn.microsoft.com/library/ms718102.aspx) w dokumentacji zestawu SDK systemu Windows.  
  
> [!NOTE]
>  W poprzednich wersjach, klikając przycisk Shift **źródła danych** przycisk otworzyć okno dialogowe Otwieranie pliku pozwala wybrać pliku połączenia danych (udl). Ta funkcja nie jest już obsługiwana.  
  
 Okno dialogowe zawiera cztery karty:  
  
- **Dostawca** kartę  
  
- **Połączenie** kartę  
  
- **Zaawansowane** kartę  
  
- **Wszystkie** kartę  
  
     Następujące dodatkowe informacje w tym artykule opisano kart **właściwości Linku danych** okno dialogowe.  
  
     Kliknij przycisk **OK** aby zakończyć. **Obiektu bazy danych wybierz** zostanie wyświetlone okno dialogowe. To okno dialogowe Wybieranie tabeli, widoku lub procedury składowanej, który będzie używany przez klienta.  
  
 **Dostawcy**  
     Wybierz odpowiedniego dostawcę, aby zarządzać połączenia ze źródłem danych. Typ dostawcy jest zazwyczaj określana przez typ bazy danych, z którym chcesz się połączyć. Kliknij przycisk `Next` przycisk lub kliknij przycisk **połączenia** kartę.  
  
 **Połączenia**  
     Zawartość na tej karcie zależą od wybranego dostawcy. Mimo że istnieje wiele typów dostawców, w tej sekcji omówiono połączeń dla dwóch typowych: danych SQL i ODBC. Inne są podobne zmiany w polach opisanych tutaj.  
  
     W przypadku danych SQL:  
  
    1. **Wybierz lub wprowadź nazwę serwera:** kliknij menu listy rozwijanej, aby wyświetlić wszystkie serwery zarejestrowanych danych w sieci, a następnie wybierz jeden.  
  
    2. **Wprowadź informacje o logowaniu do serwera:** wprowadź nazwę użytkownika i hasło do logowania się do serwera danych.  
  
    3. **Wybierz bazę danych na serwerze:** kliknij menu rozwijanego do wyświetlenia wszystkich zarejestrowanych baz danych na serwerze danych, a następnie wybierz jeden.  
  
         —lub—  
  
 **Dołącz plik bazy danych jako nazwę bazy danych:** Określ plik do użycia jako baza danych; wprowadź jawna nazwa ścieżki.  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **Użyj zabezpieczenia zintegrowane systemu Windows NT**  
  
 **Użyj określonej nazwy użytkownika i hasła**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **Użyj nazwy źródła danych:** tej listy rozwijanej wyświetla źródła danych zarejestrowane na tym komputerze. Możesz skonfigurować źródła danych wcześniejsze przy użyciu Administrator źródła danych ODBC- lub -**Użyj parametrów połączenia:** albo wprowadź ciąg połączenia, już uzyskały, lub kliknij przycisk **kompilacji** przycisk; **Wybierz źródło danych** zostanie wyświetlone okno dialogowe. Wybierz źródło danych pliku lub komputera, a następnie kliknij przycisk **OK**.  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **Zaawansowane**  
 **Ustawień sieciowych:** określ **poziom personifikacji** (poziom personifikacji, serwer może używać w przypadku personifikowania klienta; odpowiada bezpośrednio do poziomu personifikacji RPC) i  **Poziom ochrony** (poziom ochrony danych przesyłanych między klientem i serwerem; odpowiada bezpośrednio poziomów ochrony RPC).  
  
 **Inne:** w **limit czasu połączenia**, określ czas w sekundach czas bezczynności przed zostanie przekroczony limit czasu. W **uprawnień dostępu**, określić uprawnienia dostępu dla połączenia danych.  
  
     Aby uzyskać więcej informacji na temat zaawansowanych właściwości inicjujących można znaleźć w dokumentacji dostarczonej z każdego dostawcy OLE DB.  
  
 **Wszystkie**  
     Ta karta przedstawia podsumowanie właściwości inicjowania dla źródła danych i połączenia, który został określony. Te wartości można edytować.  
  
     Kliknij przycisk **OK** aby zakończyć. **Obiektu bazy danych wybierz** zostanie wyświetlone okno dialogowe. To okno dialogowe Wybieranie tabeli, widoku lub procedury składowanej, który będzie używany przez klienta.  
  
 `Class`  
 Po wybraniu źródła danych, to pole jest wypełniane przy użyciu domyślną nazwę klasy na podstawie tabeli lub procedury składowanej, które wybrano (zobacz **wybierz źródło danych** poniżej). Można edytować nazwy klasy.  
  
 **w pliku .h**  
 Po wybraniu źródła danych, to pole jest wypełniane przy użyciu domyślną nazwę klasy nagłówka na podstawie tabeli lub procedury składowanej, które wybrano (zobacz **wybierz źródło danych** poniżej). Można zmienić nazwę pliku nagłówka, lub wybierz istniejący plik nagłówka.  
  
 **Atrybut**  
 Ta opcja określa, czy Kreator utworzy za pomocą atrybutów lub deklaracji szablonu klasy konsumentów. Po wybraniu tej opcji, kreator używa atrybutów zamiast deklaracji szablonu (jest to opcja domyślna). Jeśli wyłączysz tę opcję, kreator używa deklaracji szablonu zamiast atrybutów.  
  
-   W przypadku wybrania konsumenta **typu** tabeli, kreator używa `db_source` i **db_table —** atrybutów do utworzenia tabeli, a akcesor tabeli deklaracje klas i używa **db_column —**  można utworzyć mapowania kolumn, na przykład:  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     zamiast `CTable` klasy szablonu, aby zadeklarować tabeli i klasy tabeli metody dostępu i makra BEGIN_COLUMN_MAP i END_COLUMN_MAP można utworzyć mapowania kolumn, na przykład:  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   W przypadku wybrania konsumenta **typu** polecenia, kreator używa `db_source` i **db_command —** atrybutów i używa **db_column —** można utworzyć mapowania kolumn, na przykład :  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     Zamiast używać polecenia i polecenia deklaracjach metod dostępu do klasy w pliku .h klasy poleceń, na przykład:  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 Zobacz [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
 **Typ**  
 Wybierz jedną z tych przycisków radiowych, aby określić, czy klasa odbiorcy będą pochodzić z `CTable` lub `CCommand` (ustawienie domyślne).  
  
 **Tabela**  
 Wybierz tę opcję, jeśli chcesz użyć `CTable` lub **db_table —** do utworzenia tabeli, a akcesor tabeli deklaracji klasy.  
  
 **Polecenie**  
 Wybierz tę opcję, jeśli chcesz użyć `CCommand` lub **db_command —** do tworzenia poleceń i polecenia akcesor deklaracji klasy. To ustawienie domyślne.  
  
 **Obsługa**  
 Zaznacz pola wyboru, aby określić typy aktualizacji do konsumenta (domyślna wartość to brak). Następujące ustawi [DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx) i odpowiednie wpisy [DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx) we właściwości należy ustawić mapy.  
  
 **Zmiany**  
 Określa, czy klient obsługuje aktualizacje danych wiersza w zestawie wierszy.  
  
 **Wstaw**  
 Określa, że klient obsługuje wstawiania wierszy w zestawie wierszy.  
  
 **Usuwanie**  
 Określa, czy klient obsługuje usuwania wierszy z zestawu wierszy.  
  
## <a name="see-also"></a>Zobacz też  
 [Konsumenta ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Parametry połączenia i łącza danych (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)
