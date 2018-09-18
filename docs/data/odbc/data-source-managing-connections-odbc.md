---
title: 'Źródło danych: Zarządzanie połączeniami (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a8f5a57b1ef97b38b6756931038ec18045aea746
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053729"
---
# <a name="data-source-managing-connections-odbc"></a>Źródło danych: zarządzanie połączeniami (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
W tym temacie opisano:  
  
- [Jak skonfigurować źródło danych](#_core_configuring_a_data_source).  
  
- [Wpływ środowiska z wieloma użytkownikami na źródło danych i jego zestawy rekordów](#_core_working_in_a_multiuser_environment).  
  
- [Dlaczego uogólniać ciąg połączenia ze źródłem danych](#_core_generalizing_the_connection_string).  
  
- [Jak połączyć się ze źródłem danych](#_core_connecting_to_a_specific_data_source).  
  
- [Jak odłączyć źródło danych](#_core_disconnecting_from_a_data_source).  
  
- [Jak ponownie użyć obiektu CDatabase](#_core_reusing_a_cdatabase_object).  
  
Łączenie ze źródłem danych oznacza ustanowienie komunikacji z systemem DBMS dostępu do danych. Po nawiązaniu połączenia ze źródłem danych z aplikacji przez sterownik ODBC, sterownik wykonuje połączenie, lokalnie lub w sieci.  
  
Możesz połączyć do żadnego źródła danych, do której masz sterownika ODBC. Użytkownicy twojej aplikacji również musi mieć ten sam sterownik ODBC dla swojego źródła danych. Aby uzyskać więcej informacji dotyczących redystrybucji sterowników ODBC, zobacz [Redystrybucja składników ODBC do klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a> Konfigurowanie źródła danych  

ODBC Administrator jest używany do konfigurowania źródeł danych. Umożliwia także Administratora ODBC po instalacji można dodać lub usunąć źródła danych. Podczas tworzenia aplikacji, możesz skierować użytkowników do administratora ODBC i pozwolić im na dodawanie źródeł danych, lub możesz kompilować tę funkcję w aplikacji przez wykonanie bezpośrednich wywołań instalacji ODBC. Aby uzyskać więcej informacji, zobacz [Administratora ODBC](../../data/odbc/odbc-administrator.md).  
  
Przy użyciu pliku programu Excel jako źródła danych i należy skonfigurować plik, który jest zarejestrowany i zostanie wyświetlony w **wybierz źródło danych** okno dialogowe.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Aby skorzystać z pliku programu Excel jako źródła danych  
  
1. Skonfiguruj plik z Administratora źródeł danych ODBC.  
  
1. Na **plikową nazwę DSN** kliknij pozycję **Dodaj**.  
  
1. W **Utwórz nowe źródło danych** okno dialogowe, wybierz sterownik programu Excel, a następnie kliknij przycisk **dalej**.  
  
1. Kliknij przycisk **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło daty.  
  
> [!NOTE]
>  Może być konieczne wybranie **wszystkie pliki** w menu rozwijanego, aby wyświetlić pliki z rozszerzeniem .xls.  
  
1. Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.  
  
1. W **ODBC — ustawienia dla programu Microsoft Excel** okna dialogowego Wybierz wersję bazy danych i skoroszyt.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> Praca w środowisku wielu użytkowników  

Jeśli wielu użytkowników jest połączonych ze źródłem danych, mogą zmieniać dane, podczas gdy Ty manipulujesz w zestawach rekordów. Podobnie zmiany mogą mieć wpływ na zestawy rekordów innych użytkowników. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a> Uogólnianie parametrów połączenia  

Kreatory korzystają z domyślnego ciągu połączeń do ustanowienia połączenia ze źródłem danych. To połączenie umożliwia wyświetlanie tabel i kolumn podczas programowania Twojej aplikacji. Jednak te domyślne parametry połączenia mogą nie być właściwe dla połączeń użytkowników ze źródłem danych w Twojej aplikacji. Na przykład ich źródła danych i ścieżka do lokalizacji może być inny niż ten używany do tworzenia aplikacji. W takim przypadku należy ponownie [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) element członkowski funkcji w sposób bardziej ogólny i odrzucić implementację kreatora. Na przykład użyj jednej z następujących metod:  
  
- Zarejestruj i Zarządzaj ciągami połączeń przy użyciu Administratora ODBC.  
  
- Edytuj parametry połączenia i Usuń nazwę źródła danych. Struktura dostarcza ODBC jako źródła danych; w czasie wykonywania ODBC wyświetla okno dialogowe z pytaniem, czy informacje o nazwie i inne wymagane połączenia w źródle danych.  
  
- Podaj tylko nazwę źródła danych. ODBC prosi o identyfikator użytkownika i hasło, jeśli jest to wymagane. Na przykład przed uogólnieniem parametry połączenia wyglądają następująco:  
  
    ```cpp  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Ten ciąg połączeń określa zaufane połączenie, które korzysta z systemu Windows NT zintegrowanych zabezpieczeń. Nie należy kodować hasła lub określania pustego hasła, ponieważ w ten sposób tworzy do osłabienia zabezpieczeń głównych. Zamiast tego możesz nadać `GetDefaultConnect` nowe parametry połączenia, aby wysyła zapytanie o nazwę użytkownika i hasło.  
  
    ```cpp  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> Nawiązywanie połączenia z określonym źródłem danych  

Aby połączyć się z określonym źródłem danych, źródła danych musi być już skonfigurowane za pomocą [Administratora ODBC](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Aby nawiązać połączenie z określonym źródłem danych  
  
1. Konstruowania `CDatabase` obiektu.  
  
1. Wywoływanie jej `OpenEx` lub `Open` funkcja elementu członkowskiego.  
  
Aby uzyskać więcej informacji na temat sposobu określania źródła danych, jeśli jest coś innego niż ten, który został określony za pomocą kreatora, zobacz [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) w *MFC Odwołanie*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> Odłączanie od źródła danych  

Należy zamknąć otwarty zestaw rekordów przed wywołaniem `Close` funkcji składowej typu `CDatabase`. W zestawie rekordów skojarzonych z `CDatabase` obiekt ma zostać zamknięty, wszelkie toczące `AddNew` lub `Edit` instrukcje są anulowane, a wszystkie oczekujące transakcje są wycofywane.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Aby odłączyć od źródła danych  
  
1. Wywołaj `CDatabase` obiektu [Zamknij](../../mfc/reference/cdatabase-class.md#close) funkcja elementu członkowskiego.  
  
1. Zniszcz obiekt, chyba że chcesz użyć go ponownie.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> Ponowne używanie obiektu CDatabase  

Można użyć ponownie `CDatabase` obiektu po odłączeniu od niego, czy są używane do ponownego połączenia z tym samym źródłem danych lub połączyć się z innym źródłem danych.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Aby ponownie użyć obiektu CDatabase  
  
1. Zamknij połączenie oryginalnego obiektu.  
  
1. Zamiast zniszczenia obiektu, wywołaj jej `OpenEx` lub `Open` ponownie funkcja elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)