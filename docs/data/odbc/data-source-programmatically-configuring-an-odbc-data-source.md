---
title: 'Źródło danych: programowe konfigurowanie źródła danych ODBC'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358858"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Źródło danych: programowe konfigurowanie źródła danych ODBC

W tym temacie wyjaśniono, jak programowo skonfigurować nazwy źródeł danych Open Database Connectivity (ODBC). Zapewnia to elastyczność dostępu do danych bez zmuszania użytkownika do jawnego używania administratora ODBC lub innych programów do określania nazw źródeł danych.

Zazwyczaj użytkownik uruchamia administratora ODBC, aby utworzyć źródło danych, jeśli skojarzony system zarządzania bazami danych (DBMS) obsługuje tę operację.

Podczas tworzenia źródła danych OdBC programu Microsoft Access za pośrednictwem administratora ODBC dostępne są dwie opcje: można wybrać istniejący plik mdb lub utworzyć nowy plik mdb. Nie ma programowego sposobu tworzenia pliku .mdb z aplikacji MFC ODBC. W związku z tym jeśli aplikacja wymaga umieszczenia danych w źródle danych programu Microsoft Access (plik mdb), najprawdopodobniej chcesz mieć pusty plik mdb, który można użyć lub skopiować w dowolnym momencie.

Jednak wiele dbmss umożliwiają programowe tworzenie źródła danych. Niektóre źródła danych zachowują specyfikację katalogu dla baz danych. Oznacza to, że katalog jest źródłem danych, a każda tabela w źródle danych jest przechowywana w oddzielnym pliku (w przypadku dBASE każda tabela jest plikiem .dbf). Sterowniki dla innych baz danych ODBC, takich jak Microsoft Access i SQL Server, wymagają, aby niektóre określone kryteria zostały spełnione przed utworzeniem źródła danych. Na przykład podczas korzystania ze sterownika ODBC programu SQL Server należy ustanowić komputer programu SQL Server.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>Przykład usługi SQLConfigDataSource

W poniższym przykładzie `::SQLConfigDataSource` użyto funkcji INTERFEJSU API ODBC do utworzenia nowego źródła danych programu Excel o nazwie Nowe źródło danych programu Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Należy zauważyć, że źródło danych jest w rzeczywistości katalogiem (C:\EXCELDIR); ten katalog musi istnieć. Sterownik programu Excel używa katalogów jako źródeł danych i plików jako poszczególnych tabel (jedna tabela na plik xls).

Aby uzyskać więcej informacji na temat tworzenia tabel, zobacz [Źródło danych: Programowo tworzenie tabeli w źródle danych ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Poniżej omówiono parametry, które muszą zostać `::SQLConfigDataSource` przekazane do funkcji interfejsu API ODBC. Aby `::SQLConfigDataSource`użyć , należy dołączyć plik nagłówka Odbcinst.h i użyć biblioteki importu Odbcinst.lib. Ponadto odbccp32.dll musi znajdować się w ścieżce w czasie wykonywania (lub Odbcinst.dll dla 16 bitów).

Nazwę źródła danych ODBC można utworzyć przy użyciu administratora ODBC lub podobnego narzędzia. Jednak czasami jest pożądane, aby utworzyć nazwę źródła danych bezpośrednio z aplikacji, aby uzyskać dostęp bez konieczności użytkownika do uruchomienia oddzielnego narzędzia.

Odbc Administrator (zazwyczaj zainstalowany w Panelu sterowania) tworzy nowe źródło danych, umieszczając wpisy w rejestrze systemu Windows (lub, dla 16-bitowych, w pliku Odbc.ini). Menedżer sterowników ODBC wysyła zapytanie do tego pliku w celu uzyskania wymaganych informacji o źródle danych. Ważne jest, aby wiedzieć, jakie informacje należy umieścić w rejestrze, `::SQLConfigDataSource`ponieważ trzeba podać go z wezwaniem do .

Chociaż informacje te mogą być zapisywane bezpośrednio `::SQLConfigDataSource`do rejestru bez użycia, każda aplikacja, która to robi, polega na bieżącej technice używanej przez Menedżera sterowników do obsługi swoich danych. Jeśli późniejsza wersja menedżera sterowników ODBC implementuje przechowywanie rekordów dotyczących źródeł danych w inny sposób, każda aplikacja, która używa tej techniki, zostanie przerwana. Ogólnie zaleca się użycie funkcji interfejsu API, gdy jest dostępna. Na przykład kod jest przenośny od 16 bit do `::SQLConfigDataSource` 32 bitów, jeśli używasz funkcji, ponieważ funkcja poprawnie zapisuje do pliku Odbc.ini lub do rejestru.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>Parametry sqlconfigdatasource

Poniżej wyjaśniono parametry `::SQLConfigDataSource` funkcji. Wiele informacji pochodzi z odwołania *programisty* interfejsu API ODBC dostarczane z visual C++ w wersji 1.5 i nowszych.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>Prototyp funkcji

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Uwagi

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Parametry i użycie

*hwndRodziciela*<br/>
Okno określone jako właściciel wszystkich okien dialogowych, które menedżer sterowników ODBC lub określony sterownik ODBC tworzy w celu uzyskania dodatkowych informacji od użytkownika o nowym źródle danych. Jeśli parametr *lpszAttributes* nie zawiera wystarczającej ilości informacji, zostanie wyświetlone okno dialogowe. Parametr *hwndParent* może mieć wartość NULL.

*lpszDriver*<br/>
Opis sterownika. Jest to nazwa przedstawiona użytkownikom, a nie nazwa sterownika fizycznego (biblioteka DLL).

*lpszAttributes*<br/>
Lista atrybutów w formularzu "keyname=value". Te ciągi są oddzielone przez terminatory null z dwóch kolejnych terminatorów null na końcu listy. Te atrybuty są przede wszystkim domyślne wpisy specyficzne dla sterownika, które przechodzą do rejestru dla nowego źródła danych. Jednym z ważnych kluczy, który nie jest wymieniony w odwołaniu interfejsu API ODBC dla tej funkcji jest "DSN" ("nazwa źródła danych"), który określa nazwę nowego źródła danych. Pozostałe wpisy są specyficzne dla sterownika dla nowego źródła danych. Często nie jest konieczne podanie wszystkich wpisów, ponieważ sterownik może monitować użytkownika o okna dialogowe dla nowych wartości. (Ustaw *hwndParent* na NULL, aby to spowodować.) Można jawnie podać wartości domyślne, tak aby użytkownik nie jest monitowany.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Aby ustalić opis sterownika parametru lpszDriver przy użyciu odbc administrator

1. Uruchom administratora ODBC.

1. Kliknij pozycję **Add** (Dodaj).

Daje to listę zainstalowanych sterowników i ich opisy. Użyj tego opisu jako parametru *lpszDriver.* Należy zauważyć, że używasz całego opisu, takiego jak "Pliki programu Excel (*.xls)", w tym rozszerzenia nazwy pliku i nawiasów, jeśli istnieją one w opisie.

Alternatywnie, można sprawdzić rejestru (lub, dla 16 bit, plik Odbcinst.ini), który zawiera listę wszystkich wpisów sterowników i opisów pod kluczem rejestru "Sterowniki ODBC" (lub sekcji [Sterowniki ODBC] w Odbcinst.ini).

Jednym ze sposobów znalezienia nazwy kluczy i wartości parametru *lpszAttributes* jest zbadanie pliku Odbc.ini dla już skonfigurowanego źródła danych (być może skonfigurowanego przez administratora ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Aby znaleźć nazwy klawiszy i wartości parametru lpszAttributes

1. Uruchom edytor rejestru systemu Windows (lub, dla 16-bitowego, otwórz plik Odbc.ini).

1. Znajdź informacje o źródłach danych ODBC, korzystając z jednej z następujących czynności:

   - W przypadku 32-bitowych znajdź klucz **HKEY_CURRENT_USER\Software\ODBC\ODBC. Źródła danych INI\ODBC** w lewym okienku.

      W prawym okienku znajdują się wpisy formularza: "pub: REG_SZ:*\<nazwa źródła danych>*", gdzie * \<nazwa źródła danych>* jest źródłem danych, które zostało już skonfigurowane z żądanymi ustawieniami sterownika, którego zamierzasz użyć. Wybierz źródło danych, na przykład SQL Server. Elementy następujące po ciągu "pub:" są, w kolejności, nazwa klucza i wartość do użycia w *lpszAttributes* parametru.

   - Dla 16-bitowych znajdź sekcję w pliku Odbc.ini oznaczoną przez [*\<nazwa źródła danych>*].

      Wiersze następujące po tym wierszu mają postać "keyname=value". Są to dokładnie wpisy do użycia w *parametrze lpszAttributes.*

Można również zapoznać się z dokumentacją dla określonego sterownika, którego zamierzasz użyć. Przydatne informacje można znaleźć w pomocy online dla sterownika, do której można uzyskać dostęp, uruchamiając administratora ODBC. Te pliki Pomocy są zwykle umieszczane w katalogu WINDOWS\SYSTEM dla systemów Windows NT, Windows 3.1 lub Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Aby uzyskać pomoc online dla sterownika ODBC

1. Uruchom administratora ODBC.

1. Kliknij pozycję **Add** (Dodaj).

1. Wybierz nazwę sterownika.

1. Kliknij przycisk **OK**.

Gdy administrator ODBC wyświetli informacje dotyczące tworzenia nowego źródła danych dla danego sterownika, kliknij przycisk **Pomoc**. Spowoduje to otwarcie pliku Pomocy dla danego sterownika, który zazwyczaj zawiera ważne informacje dotyczące korzystania ze sterownika.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
