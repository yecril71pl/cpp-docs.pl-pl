---
title: 'Źródło danych: Programowe Konfigurowanie źródła danych ODBC'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 33269b65835812a6e1a03e091833831781d97b6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395936"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Źródło danych: Programowe Konfigurowanie źródła danych ODBC

W tym temacie wyjaśniono, jak programowo możesz skonfigurować nazw źródeł danych Open Database Connectivity (ODBC). Zapewnia to elastyczność dostępu do danych bez zmuszania użytkownika do użycia Administratora ODBC lub innych programów do określenia nazw źródeł danych.

Zazwyczaj użytkownik uruchamia Administratora ODBC, aby utworzyć źródło danych, jeśli skojarzone system zarządzania bazami danych (DBMS) obsługuje tę operację.

Podczas tworzenia źródła danych Microsoft Access ODBC przez administratora ODBC, masz dwie możliwości: Możesz wybrać istniejący plik .mdb lub utworzyć nowy plik .mdb. Nie ma sposobu na utworzenie pliku .mdb z aplikacji MFC ODBC. W związku z tym jeśli aplikacja wymaga umieszczenia danych w źródle danych Microsoft Access (plik .mdb), najprawdopodobniej chcesz posiadać pusty plik .mdb, który możesz kopiować i używać zawsze wtedy, gdy ich potrzebujesz.

Jednak wiele systemów DBMS umożliwia programistyczne tworzenie źródła danych. Niektóre źródła danych utrzymują specyfikację katalogu dla baz danych. Oznacza to, że katalog jest źródłem danych i każdej tabeli w źródle danych są przechowywane w oddzielnym pliku (w przypadku programu dBASE każda tabela to plik dbf). Sterowniki dla innych baz danych ODBC, takich jak program Microsoft Access i SQL Server, wymagają, że niektóre szczególne kryteria zostały spełnione, zanim może zostać nawiązana źródła danych. Na przykład używając sterownika SQL Server ODBC, musisz ustalonymi komputera programu SQL Server.

##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource Example

W poniższym przykładzie użyto `::SQLConfigDataSource` funkcji interfejsu API ODBC, aby utworzyć nowe źródło danych programu Excel o nazwie nowe źródło danych programu Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Należy pamiętać, że źródła danych jest w rzeczywistości katalogiem (C:\EXCELDIR); Ten katalog musi istnieć. Sterownik programu Excel używa katalogów jako źródła danych i plików jako poszczególnych tabel (jedna tabela na plik xls).

Aby uzyskać więcej informacji na temat tworzenia tabel, zobacz [źródła danych: Programowe tworzenie tabeli w źródle danych ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Poniższe informacje omawiają parametry, które muszą zostać przekazane do `::SQLConfigDataSource` funkcji interfejsu API ODBC. Aby użyć `::SQLConfigDataSource`, musisz uwzględnić plik nagłówka Odbcinst.h i użyć importu odbcinst.lib. Ponadto Odbccp32.dll musi być w ścieżce w czasie wykonywania (lub Odbcinst.dll dla 16-bitowych).

Możesz utworzyć nazwę źródła danych ODBC używając Administratora ODBC lub podobnej użyteczności. Jednak czasami jest pożądane, aby utworzyć nazwę źródła danych bezpośrednio z poziomu aplikacji, aby uzyskać dostęp niewymagający od użytkownika uruchamiania oddzielnego narzędzia.

Administrator ODBC (zazwyczaj zainstalowany w Panelu sterowania) tworzy nowe źródło danych, umieszczając wpisy w rejestrze systemu Windows (lub dla 16-bitowych w pliku Odbc.ini). ODBC Driver Manager wysyła zapytanie do tego pliku, aby otrzymać wymagane informacje o źródle danych. Ważne jest, aby wiedzieć, jakie informacje należy umieścić w rejestrze, ponieważ trzeba go dostarczyć z wywołaniem `::SQLConfigDataSource`.

Mimo że to informacje mogłyby być zapisywane bezpośrednio w rejestrze bez korzystania z `::SQLConfigDataSource`, każda aplikacja, która wykonuje tę funkcję, powołuje się na bieżącą metodę, której Menedżer sterowników używa do przechowywania swoich danych. Jeśli późniejsze poprawki do ODBC Driver Manager zaimplementują przechowywanie rekordów o źródłach danych w inny sposób, każdej aplikacji korzystającej z tej techniki zostanie przerwane. Ogólnie zaleca się wykorzystanie funkcji API, jeśli została dostarczona. Na przykład kodu jest przenośny z 16-bitowego do 32-bitowego, jeśli używasz `::SQLConfigDataSource` działać, ponieważ ta funkcja poprawnie zapisuje dane w pliku Odbc.ini lub w rejestrze.

##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource Parameters

Poniżej wyjaśniono parametry `::SQLConfigDataSource` funkcji. Wiele informacji jest pobierana z interfejsu API ODBC *odwołania programisty* dostarczone z programem Visual C++ w wersji 1.5 lub nowszej.

###  <a name="_core_function_prototype"></a> Prototyp funkcji

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Uwagi

####  <a name="_core_parameters_and_usage"></a> Parametry i użycie

*hwndParent*<br/>
Okno określone jako właściciel każdego okna dialogowego, utworzone przez Menedżera sterowników ODBC lub konkretny sterownik ODBC w celu uzyskania dodatkowych informacji od użytkownika dotyczących nowego źródła danych. Jeśli *lpszAttributes* parametru nie dostarcza wystarczających informacji, pojawi się okno dialogowe. *HwndParent* parametr może mieć wartości NULL.

*lpszDriver*<br/>
Opis sterownika. Jest to nazwa przedstawiana użytkownikom, a nie nazwa sterownika fizycznego (DLL).

*lpszAttributes*<br/>
Lista atrybutów w formie "NazwaKlucza = wartość". Te ciągi są oddzielane przez zerowe znaki kończące z dwoma kolejnymi znakami kończącymi na końcu listy. Te atrybuty są głównie domyślne specyficzne dla sterownika zapisów, które przechodzą do rejestru dla nowego źródła danych. Jednym ważnym kluczem, który nie jest wymieniony w odwołaniu ODBC API dla tej funkcji jest "DSN" ("dane nazwa źródła"), która określa nazwę nowego źródła danych. Pozostałe wpisy są charakterystyczne dla sterownika dla nowego źródła danych. Często nie jest konieczne dostarczanie wszystkich wpisów, ponieważ sterownik monitować użytkownika o oknach dialogowych o nowe wartości. (Ustaw *hwndParent* na wartość NULL, aby to spowodować.) Można jawnie dostarczyć domyślne wartości, dzięki czemu użytkownik nie jest monitowany.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Aby określić opis sterownika dla parametru Lpsdriver z wykorzystaniem Administratora ODBC

1. Uruchom Administratora ODBC.

1. Kliknij przycisk **Dodaj**.

Wyświetla listę zainstalowanych sterowników i ich opisy. Użyj tego opisu, jako *Lpsdriver* parametru. Należy pamiętać, że używasz cały opis, takie jak "Pliki programu Excel (*.xls)", włącznie z rozszerzenia nazwy pliku i nawiasami, jeśli istnieją w opisie.

Alternatywnie, można zbadać rejestr (lub dla 16-bitowych, plik Odbcinst.ini), który zawiera listę wszystkich wpisów sterowników i opisy w kluczu rejestru "Sterowniki ODBC" (lub sekcji [ODBC Drivers] odbcinst.ini).

Jednym ze sposobów odszukania nazw kluczy i wartości dla *lpszAttributes* parametru jest zbadanie pliku ODBC.ini pod kątem już skonfigurowanego źródła danych (może być taki, który został skonfigurowany przez administratora ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Aby znaleźć i wartości dla parametru lpszAttributes

1. Uruchom Edytor rejestru Windows (lub dla 16-bitowych, otwórz plik Odbc.ini).

1. Znajdź informacje źródła danych ODBC, przy użyciu jednej z następujących czynności:

   - Dla 32-bitowych Znajdź klucz **HKEY_CURRENT_USER\Software\ODBC\ODBC. Źródła danych INI\ODBC** w okienku po lewej stronie.

      W okienku po prawej stronie wyświetla wpisy w postaci: "pub: REG_SZ:*<data source name>*", gdzie *<data source name>* jest źródłem danych, która została już skonfigurowana przy użyciu odpowiednie ustawienia dla sterownika, których zamierzasz używać. Wybierz źródło danych, której potrzebujesz, na przykład SQL Server. Elementy występujące po ciągu "pub:" są w kolejności, klucza i wartości do użycia w Twojej *lpszAttributes* parametru.

   - Dla 16-bitowych, Znajdź sekcję w pliku Odbc.ini oznaczone przez [*\<nazwa źródła danych >*].

      Wiersze po tym wierszu mają postać "NazwaKlucza = wartość". Są to wpisy do użycia w Twojej *lpszAttributes* parametru.

Można też zbadanie dokumentacji dla określonego sterownika, którego chcesz użyć. Przydatne informacje można znaleźć w Pomocy online dla sterownika, który możesz uzyskać dostęp uruchamiając Administratora ODBC. Te pliki pomocy są zwyczajowo umieszczane w katalogu WINDOWS\SYSTEM dla Windows NT, Windows 3.1 lub Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Aby uzyskać pomoc online dla sterownika ODBC

1. Uruchom Administratora ODBC.

1. Kliknij przycisk **Dodaj**.

1. Wybierz nazwę sterownika.

1. Kliknij przycisk **OK**.

Kiedy ODBC Administrator Wyświetla informacje dotyczące tworzenia nowego źródła danych dla tego konkretnego sterownika, kliknij przycisk **pomocy**. Spowoduje to otwarcie pliku pomocy dla tego konkretnego sterownika, który typowo zawiera ważne informacje na temat użycia sterownika.

## <a name="see-also"></a>Zobacz także

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
