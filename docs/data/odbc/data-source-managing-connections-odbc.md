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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374528"
---
# <a name="data-source-managing-connections-odbc"></a>Źródło danych: zarządzanie połączeniami (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono:

- [Jak skonfigurować źródło danych](#_core_configuring_a_data_source).

- [Jak środowisko wieloużytkownikowe wpływa na źródło danych i jego zestawy rekordów](#_core_working_in_a_multiuser_environment).

- [Dlaczego można uogólnić parametry połączenia ze źródłem danych](#_core_generalizing_the_connection_string).

- [Jak połączyć się ze źródłem danych](#_core_connecting_to_a_specific_data_source).

- [Jak odłączyć się od źródła danych](#_core_disconnecting_from_a_data_source).

- [Jak ponownie użyć obiektu CDatabase](#_core_reusing_a_cdatabase_object).

Łączenie się ze źródłem danych oznacza nawiązanie komunikacji z systemem dbms w celu uzyskania dostępu do danych. Po nawiązaniu połączenia ze źródłem danych z aplikacji za pośrednictwem sterownika ODBC sterownik nawiązuje połączenie lokalnie lub za pośrednictwem sieci.

Można połączyć się z dowolnym źródłem danych, dla którego masz sterownik ODBC. Użytkownicy aplikacji muszą mieć również ten sam sterownik ODBC dla swojego źródła danych. Aby uzyskać więcej informacji na temat redystrybucji sterowników ODBC, zobacz [Redystrybucja składników ODBC do klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurowanie źródła danych

Administrator ODBC służy do konfigurowania źródeł danych. Można również użyć administratora ODBC po instalacji, aby dodać lub usunąć źródła danych. Podczas tworzenia aplikacji można skierować użytkowników do administratora ODBC, aby umożliwić im dodawanie źródeł danych lub można utworzyć tę funkcję do aplikacji, wykonując bezpośrednie wywołania instalacji ODBC. Aby uzyskać więcej informacji, zobacz [Administrator ODBC](../../data/odbc/odbc-administrator.md).

Można użyć pliku programu Excel jako źródła danych i skonfigurować plik tak, aby był zarejestrowany i wyświetlany w oknie dialogowym **Wybieranie źródła danych.**

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Aby użyć pliku programu Excel jako źródła danych

1. Skonfiguruj plik za pomocą administratora źródła danych ODBC.

1. Na karcie **Plik DSN** kliknij pozycję **Dodaj**.

1. W oknie dialogowym **Tworzenie nowego źródła danych** wybierz sterownik programu Excel, a następnie kliknij przycisk **Dalej**.

1. Kliknij **przycisk Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło daty.

> [!NOTE]
> Aby wyświetlić pliki xls, może być konieczne wybranie opcji **Wszystkie pliki** z menu rozwijanego.

1. Kliknij przycisk **Dalej**, a następnie kliknij przycisk **Zakończ**.

1. W oknie dialogowym **Instalator programu ODBC programu Microsoft Excel** wybierz wersję bazy danych i skoroszyt.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Praca w środowisku wielodochlotowym

Jeśli wielu użytkowników jest połączonych ze źródłem danych, mogą zmieniać dane podczas manipulowania nimi w zestawach rekordów. Podobnie zmiany mogą mieć wpływ na zestawy rekordów innych użytkowników. Aby uzyskać więcej informacji, zobacz [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Uogólnianie ciągu połączenia

Kreatorzy używają domyślnego ciągu połączenia do nawiązywać połączenie ze źródłem danych. To połączenie służy do wyświetlania tabel i kolumn podczas tworzenia aplikacji. Jednak ten domyślny ciąg połączenia może nie być odpowiedni dla połączeń użytkowników ze źródłem danych za pośrednictwem aplikacji. Na przykład ich źródło danych i ścieżka do jego lokalizacji może się różnić od używanej do tworzenia aplikacji. W takim przypadku należy ponownie wdrożyć funkcję elementu członkowskiego [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) w bardziej ogólny sposób i odrzucić implementację kreatora. Na przykład użyj jednego z następujących podejść:

- Rejestrowanie ciągów połączeń i zarządzanie nimi przy użyciu administratora ODBC.

- Edytuj parametry połączenia i usuń nazwę źródła danych. Ramy dostarcza ODBC jako źródło danych; w czasie wykonywania odbc wyświetla okno dialogowe z prośbą o nazwę źródła danych i inne wymagane informacje o połączeniu.

- Podaj tylko nazwę źródła danych. Odbc prosi o identyfikator użytkownika i hasło, jeśli jest to wymagane. Na przykład przed uogólnieniem parametry połączenia wyglądają następująco:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Ten ciąg połączenia określa zaufane połączenie, które korzysta ze zintegrowanych zabezpieczeń systemu Windows NT. Należy unikać twardego kodowania hasła lub określania pustego hasła, ponieważ powoduje to poważne osłabienie zabezpieczeń. Zamiast tego można `GetDefaultConnect` nadać nowy ciąg połączenia, dzięki czemu kwerendy dla identyfikatora użytkownika i hasła.

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Łączenie się z określonym źródłem danych

Aby połączyć się z określonym źródłem danych, źródło danych musi być już skonfigurowane z [administratorem ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Aby połączyć się z określonym źródłem danych

1. Konstruuj `CDatabase` obiekt.

1. Wywołanie `OpenEx` `Open` jego lub funkcji członka.

Aby uzyskać więcej informacji na temat określania źródła danych, jeśli jest to coś innego niż określone za pomocą [kreatora, zobacz CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) w *odwołaniu MFC*.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Rozłączanie ze źródłem danych

Przed wywołaniem `Close` funkcji elementu członkowskiego `CDatabase`. W zestawieniach rekordów skojarzonych z obiektem, `CDatabase` który chcesz zamknąć, wszelkie oczekujące `AddNew` lub `Edit` wyciągi są anulowane, a wszystkie oczekujące transakcje są przywracane.

#### <a name="to-disconnect-from-a-data-source"></a>Aby odłączyć się od źródła danych

1. Wywołanie `CDatabase` funkcji [zamknij](../../mfc/reference/cdatabase-class.md#close) elementu członkowskiego obiektu.

1. Zniszcz obiekt, chyba że chcesz go użyć ponownie.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Ponowne odtwarzanie obiektu CDatabase

Obiekt można użyć `CDatabase` ponownie po odłączeniu od niego, niezależnie od tego, czy używasz go do ponownego połączenia z tym samym źródłem danych, czy do nawiązania połączenia z innym źródłem danych.

#### <a name="to-reuse-a-cdatabase-object"></a>Aby ponownie użyć obiektu CDatabase

1. Zamknij oryginalne połączenie obiektu.

1. Zamiast niszczyć obiekt, wywołaj `OpenEx` `Open` jego lub element członkowski funkcji ponownie.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
