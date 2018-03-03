---
title: "Źródło danych: Zarządzanie połączeniami (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b83093496d355fdba8b5d714875d08040ae28ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-managing-connections-odbc"></a>Źródło danych: zarządzanie połączeniami (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano:  
  
-   [Jak skonfigurować źródła danych](#_core_configuring_a_data_source).  
  
-   [Wpływ źródła danych i jego zestawów rekordów w środowisku wielodostępnym](#_core_working_in_a_multiuser_environment).  
  
-   [Dlaczego generalize ciąg połączenia ze źródłem danych](#_core_generalizing_the_connection_string).  
  
-   [Sposób nawiązywania połączenia ze źródłem danych](#_core_connecting_to_a_specific_data_source).  
  
-   [Jak odłączyć od źródła danych](#_core_disconnecting_from_a_data_source).  
  
-   [Jak ponownie użyć obiektu cdatabase —](#_core_reusing_a_cdatabase_object).  
  
 Połączenie ze źródłem danych oznacza nawiązywania łączności z bazami danych w celu dostępu do danych. Podczas łączenia ze źródłem danych z aplikacji za pośrednictwem sterownika ODBC sterownika nawiązuje połączenie, lokalnie lub w sieci.  
  
 Można nawiązać połączenia dowolnego źródła danych, dla którego masz sterownik ODBC. Użytkownicy aplikacji musi mieć również z tego samego sterownika ODBC dla ich źródła danych. Aby uzyskać więcej informacji na temat redystrybuowanie sterowników ODBC, zobacz [Redystrybucja składników ODBC wśród klientów Your](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a>Konfigurowanie źródła danych  
 ODBC Administrator służy do konfigurowania źródeł danych. Umożliwia także ODBC Administrator po zakończeniu instalacji można dodać ani usunąć źródła danych. Podczas tworzenia aplikacji albo można nakazać użytkownikom umożliwiających im Dodaj źródła danych, aby Administrator ODBC, lub można utworzyć tej funkcji do aplikacji przez bezpośrednie wywołania instalacji ODBC. Aby uzyskać więcej informacji, zobacz [ODBC Administrator](../../data/odbc/odbc-administrator.md).  
  
 Plik programu Excel można użyć jako źródła danych i należy skonfigurować plik, który został zarejestrowany i zostanie wyświetlony w **wybierz źródło danych** okno dialogowe.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Aby użyć pliku programu Excel jako źródła danych  
  
1.  Konfigurowanie pliku z Administrator źródła danych ODBC.  
  
2.  Na **pliku DSN** , kliknij pozycję **Dodaj**.  
  
3.  W **Utwórz nowe źródło danych** okno dialogowe, wybierz sterownik programu Excel, a następnie kliknij przycisk **dalej**.  
  
4.  Kliknij przycisk **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło daty.  
  
> [!NOTE]
>  Może być konieczne wybranie **wszystkie pliki** w menu rozwijanego, aby wyświetlić pliki xls.  
  
1.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.  
  
2.  W **ustawienia ODBC programu Microsoft Excel** oknie dialogowym Wybierz skoroszyt i wersji bazy danych.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a>Praca w środowisku wielodostępnym  
 Jeśli wielu użytkowników są podłączone do źródła danych, podczas gdy modyfikujesz w zestawach rekordów mogą zmienić danych. Podobnie zmiany mogą mieć wpływ na zestawy rekordów innych użytkowników. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a>Uogólnianie parametrów połączenia  
 Kreatorzy użyć domyślnego ciągu połączenia do nawiązania połączenia ze źródłem danych. To połączenie umożliwia przeglądanie tabel i kolumn podczas tworzenia aplikacji. Jednak ten domyślnego ciągu połączenia może nie być odpowiednie dla użytkowników połączeń ze źródłem danych za pośrednictwem aplikacji. Na przykład ich źródła danych i ścieżkę do lokalizacji może być inny niż ten, który służy do tworzenia aplikacji. W takim przypadku należy reimplement [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) elementu członkowskiego działać w sposób bardziej ogólnym i odrzucić implementacji kreatora. Na przykład użyj jednej z następujących metod:  
  
-   Zarejestruj i zarządzaj nimi parametry połączenia za pomocą Administratora ODBC.  
  
-   Edytuj parametry połączenia i Usuń nazwę źródła danych. Platformę dostarcza ODBC jako źródła danych; w czasie wykonywania ODBC wyświetla okno dialogowe z pytaniem, czy informacje o nazwie i inne wymagane połączenia źródła danych.  
  
-   Podaj tylko nazwa źródła danych. ODBC poprosi o podanie nazwy użytkownika i hasła, jeśli jest to wymagane. Na przykład przed uogólnianie, ciąg połączenia wygląda następująco:  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Ten ciąg połączenia określa zaufanego połączenia, który używa zabezpieczenia zintegrowane systemu Windows NT. Nie należy kodować hasła lub określenia pustego hasła, ponieważ w ten sposób tworzy do osłabienia zabezpieczeń głównych. Zamiast tego można nadać `GetDefaultConnect` ciągu nowe połączenie, aby wysyła zapytanie o nazwę użytkownika i hasło.  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a>Nawiązywanie połączenia z określonego źródła danych  
 Aby połączyć się z określonego źródła danych, źródła danych musi już zostały skonfigurowane z [ODBC Administrator](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Nawiązywania połączenia z określonego źródła danych  
  
1.  Utworzyć `CDatabase` obiektu.  
  
2.  Wywołaj jego `OpenEx` lub **Otwórz** funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji o sposobie określania źródła danych, jeśli jest inny niż określony za pomocą kreatora, zobacz [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) w *MFC Odwołanie*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a>Odłączanie od źródła danych  
 Należy zamknąć wszystkie otwarte zestawów rekordów przed wywołaniem **zamknąć** funkcji członkowskiej klasy `CDatabase`. W zestawach rekordów skojarzone z `CDatabase` obiekt, aby zamknąć wszystkie oczekujące `AddNew` lub **Edytuj** instrukcje są anulowane i wszystkie oczekujące transakcje są wycofywane.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Aby odłączyć od źródła danych  
  
1.  Wywołanie `CDatabase` obiektu [Zamknij](../../mfc/reference/cdatabase-class.md#close) funkcję elementu członkowskiego.  
  
2.  Obiekt należy zniszczyć, chyba że chcesz użyć go ponownie.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a>Ponowne użycie obiektu cdatabase —  
 Można użyć ponownie `CDatabase` obiektu po rozłączeniu z niej, czy używać ponowne połączenie z tym samym źródłem danych lub połączyć się z innym źródłem danych.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Aby ponownie użyć obiektu cdatabase —  
  
1.  Zamknij oryginalne połączenie z obiektu.  
  
2.  Zamiast niszczenie obiekt, należy wywołać jej `OpenEx` lub **Otwórz** funkcji członkowskiej ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Źródła danych (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Źródło danych: Określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)