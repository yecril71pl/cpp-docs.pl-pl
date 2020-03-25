---
title: 'Źródło danych: zarządzanie połączeniami (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213299"
---
# <a name="data-source-managing-connections-odbc"></a>Źródło danych: zarządzanie połączeniami (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie objaśniono:

- [Jak skonfigurować źródło danych](#_core_configuring_a_data_source).

- [Jak środowisko wieloużytkownikowe ma wpływ na źródło danych i jego zestawy rekordów](#_core_working_in_a_multiuser_environment).

- [Dlaczego można uogólnić parametry połączenia do źródła danych](#_core_generalizing_the_connection_string).

- [Jak nawiązać połączenie ze źródłem danych](#_core_connecting_to_a_specific_data_source).

- [Jak rozłączyć się ze źródłem danych](#_core_disconnecting_from_a_data_source).

- [Jak ponownie użyć obiektu CDatabase](#_core_reusing_a_cdatabase_object).

Połączenie ze źródłem danych oznacza ustanowienie komunikacji z systemem DBMS w celu uzyskania dostępu do danych. Po nawiązaniu połączenia ze źródłem danych z aplikacji za pośrednictwem sterownika ODBC sterownik nawiązuje połączenie przez użytkownika lokalnie lub przez sieć.

Możesz połączyć się z dowolnym źródłem danych, dla którego masz sterownik ODBC. Użytkownicy aplikacji muszą także mieć ten sam sterownik ODBC dla źródła danych. Aby uzyskać więcej informacji na temat redystrybucji sterowników ODBC, zobacz [Redystrybuowanie składników ODBC do klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurowanie źródła danych

Administrator ODBC służy do konfigurowania źródeł danych. Możesz również użyć administratora ODBC po instalacji, aby dodać lub usunąć źródła danych. Podczas tworzenia aplikacji można skierować użytkowników do administratora ODBC, aby zezwolić im na Dodawanie źródeł danych, lub można utworzyć tę funkcję w aplikacji, wykonując bezpośrednie wywołania instalacji ODBC. Aby uzyskać więcej informacji, zobacz [administrator ODBC](../../data/odbc/odbc-administrator.md).

Możesz użyć pliku programu Excel jako źródła danych i skonfigurować go tak, aby był zarejestrowany i wyświetlany w oknie dialogowym **Wybierz źródło danych** .

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Aby użyć pliku programu Excel jako źródła danych

1. Skonfiguruj plik za pomocą administratora źródła danych ODBC.

1. Na karcie Plikowe **DSN** kliknij przycisk **Dodaj**.

1. W oknie dialogowym **Utwórz nowe źródło danych** wybierz sterownik programu Excel, a następnie kliknij przycisk **dalej**.

1. Kliknij przycisk **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło danych.

> [!NOTE]
>  Może być konieczne wybranie **wszystkich plików** z menu rozwijanego, aby wyświetlić pliki. xls.

1. Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.

1. W oknie dialogowym **ODBC — Instalator programu Microsoft Excel** wybierz wersję bazy danych i skoroszyt.

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Praca w środowisku wielodostępnym

Jeśli wielu użytkowników jest podłączonych do źródła danych, można zmienić dane podczas manipulowania nimi w zestawach rekordów. Podobnie zmiany mogą wpływać na zestawy rekordów innych użytkowników. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [transakcję (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Uogólnianie parametrów połączenia

Kreatory używają domyślnych parametrów połączenia w celu nawiązania połączenia ze źródłem danych. To połączenie służy do wyświetlania tabel i kolumn podczas tworzenia aplikacji. Jednak te domyślne parametry połączenia mogą nie być odpowiednie dla połączeń użytkowników ze źródłem danych za pomocą aplikacji. Na przykład ich źródło danych i ścieżka do jej lokalizacji mogą być inne niż używane podczas tworzenia aplikacji. W takim przypadku należy wielokrotnie wdrożyć funkcję członkowską [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) w bardziej ogólny sposób i odrzucić implementację kreatora. Można na przykład użyć jednej z następujących metod:

- Zarejestruj parametry połączenia i zarządzaj nimi za pomocą administratora ODBC.

- Edytuj parametry połączenia i Usuń nazwę źródła danych. Platforma dostarcza ODBC jako źródło danych; w czasie wykonywania, ODBC wyświetla okno dialogowe z monitem o podanie nazwy źródła danych i innych wymaganych informacji o połączeniu.

- Podaj tylko nazwę źródła danych. ODBC żąda identyfikatora użytkownika i hasła, jeśli jest to wymagane. Na przykład przed generalizacją parametry połączenia wyglądają następująco:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Te parametry połączenia określają zaufane połączenie, które używa zintegrowanych zabezpieczeń systemu Windows NT. Należy unikać kodowania hasła lub określania pustego hasła, ponieważ powoduje to utworzenie głównej słabego poziomu zabezpieczeń. Zamiast tego można nadać `GetDefaultConnect` nowe parametry połączenia tak, aby wysyłali zapytanie o identyfikator użytkownika i hasło.

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

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Łączenie z określonym źródłem danych

Aby można było połączyć się z określonym źródłem danych, źródło danych musi już być skonfigurowane za pomocą [administratora ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Aby nawiązać połączenie z określonym źródłem danych

1. Konstruowanie obiektu `CDatabase`.

1. Wywołaj swoją `OpenEx` lub `Open` funkcję członkowską.

Aby uzyskać więcej informacji na temat sposobu określania źródła danych, jeśli jest coś innego niż określone za pomocą kreatora, zobacz [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) w *odwołaniu MFC*.

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Odłączanie od źródła danych

Przed wywołaniem `Close` funkcji składowej `CDatabase`należy zamknąć wszystkie otwarte zestawy rekordów. W zestawach rekordów skojarzonych z obiektem `CDatabase`, które mają zostać zamknięte, wszystkie oczekujące instrukcje `AddNew` lub `Edit` są anulowane i wszystkie oczekujące transakcje zostaną wycofane.

#### <a name="to-disconnect-from-a-data-source"></a>Aby rozłączyć się ze źródłem danych

1. Wywołaj funkcję [zamykania](../../mfc/reference/cdatabase-class.md#close) elementu członkowskiego obiektu `CDatabase`.

1. Zniszcz obiekt, chyba że chcesz go ponownie użyć.

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Używanie obiektu CDatabase

Można ponownie użyć `CDatabase` obiektu po odłączeniu od niego, niezależnie od tego, czy jest on używany do ponownego połączenia z tym samym źródłem danych, czy do łączenia się z innym źródłem danych.

#### <a name="to-reuse-a-cdatabase-object"></a>Aby ponownie użyć obiektu CDatabase

1. Zamknij oryginalne połączenie obiektu.

1. Zamiast zniszczyć obiekt, wywołaj ponownie `OpenEx` lub `Open` funkcji członkowskiej.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
