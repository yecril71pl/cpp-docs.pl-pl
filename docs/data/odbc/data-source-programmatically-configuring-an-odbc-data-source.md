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
ms.openlocfilehash: 38f0f383256a05c983fb7e7d7a498e16881c7b78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446947"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Źródło danych: programowe konfigurowanie źródła danych ODBC

W tym temacie wyjaśniono sposób programowego konfigurowania nazw źródeł danych Open Database Connectivity (ODBC). Zapewnia to elastyczność dostępu do danych bez wymuszania, aby użytkownik jawnie używał administratora ODBC lub innych programów do określenia nazw źródeł danych.

Zazwyczaj użytkownik uruchamia administratora ODBC, aby utworzyć źródło danych, jeśli skojarzony system zarządzania bazami danych (DBMS) obsługuje tę operację.

Podczas tworzenia źródła danych Microsoft Access ODBC za pośrednictwem administratora ODBC są dostępne dwie opcje: można wybrać istniejący plik mdb lub utworzyć nowy plik. mdb. Nie istnieje programistyczny sposób tworzenia pliku. mdb z aplikacji MFC ODBC. W związku z tym, jeśli aplikacja wymaga umieszczenia danych w źródle danych programu Microsoft Access (plik. mdb), najprawdopodobniej chcesz mieć pusty plik mdb, którego możesz użyć lub skopiować w dowolnym momencie.

Jednak wiele systemów DBMS umożliwia Programistyczne tworzenie źródła danych. Niektóre źródła danych zachowują specyfikację katalogu dla baz danych. Oznacza to, że katalog jest źródłem danych, a każda tabela w źródle danych jest przechowywana w osobnym pliku (w przypadku programu dBASE, każda tabela jest plikiem. dbf). Sterowniki innych baz danych ODBC, takich jak Microsoft Access i SQL Server, wymagają spełnienia określonych kryteriów przed ustanowieniem źródła danych. Na przykład w przypadku korzystania z SQL Server sterownika ODBC należy nawiązać SQL Server komputerze.

##  <a name="_core_sqlconfigdatasource_example"></a>Przykład SQLConfigDataSource

Poniższy przykład używa funkcji `::SQLConfigDataSource` ODBC API do tworzenia nowego źródła danych programu Excel o nazwie nowe źródło danych programu Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Należy pamiętać, że źródło danych jest w rzeczywistości katalogiem (C:\EXCELDIR); Ten katalog musi istnieć. Sterownik programu Excel używa katalogów jako źródeł danych i plików jako pojedyncze tabele (jedna tabela na plik xls).

Aby uzyskać więcej informacji na temat tworzenia tabel, zobacz [Źródło danych: programowe tworzenie tabeli w źródle danych ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Poniższe informacje omawiają parametry, które muszą zostać przesłane do funkcji interfejsu API `::SQLConfigDataSource` ODBC. Aby użyć `::SQLConfigDataSource`, należy dołączyć plik nagłówka Odbcinst. h i użyć biblioteki Import Odbcinst. lib. Ponadto ODBCCP32. dll musi znajdować się w ścieżce w czasie wykonywania (lub Odbcinst. dll dla 16-bitowych).

Można utworzyć nazwę źródła danych ODBC przy użyciu Administratora ODBC lub podobnego narzędzia. Jednak czasami pożądane jest utworzenie nazwy źródła danych bezpośrednio z aplikacji w celu uzyskania dostępu, bez konieczności korzystania przez użytkownika z osobnego narzędzia.

Administrator ODBC (zazwyczaj instalowany w panelu sterowania) tworzy nowe źródło danych przez umieszczenie wpisów w rejestrze systemu Windows (lub, w przypadku 16-bitowych, w pliku ODBC. ini). Menedżer sterowników ODBC wysyła zapytanie do tego pliku w celu uzyskania wymaganych informacji o źródle danych. Ważne jest, aby wiedzieć, jakie informacje muszą być umieszczone w rejestrze, ponieważ należy przekazać je z wywołaniem do `::SQLConfigDataSource`.

Chociaż te informacje mogą być zapisywane bezpośrednio w rejestrze bez używania `::SQLConfigDataSource`, każda aplikacja, która jest zależna od bieżącej techniki używanej przez Menedżera sterowników do przechowywania danych. Jeśli nowsza wersja Menedżera sterowników ODBC implementuje zapisywanie rekordów o źródłach danych w inny sposób, każda aplikacja, która używa tej techniki, jest uszkodzona. Ogólnie zaleca się użycie funkcji API, gdy jest ona dostępna. Na przykład kod jest przenośny z 16-bitowego do 32 bitowej, jeśli używasz funkcji `::SQLConfigDataSource`, ponieważ funkcja poprawnie zapisuje w pliku ODBC. ini lub w rejestrze.

##  <a name="_core_sqlconfigdatasource_parameters"></a>Parametry SQLConfigDataSource

Poniżej objaśniono parametry funkcji `::SQLConfigDataSource`. Większość informacji jest pobierana z *dokumentacji programisty* interfejsu API ODBC dostarczonej z Visual C++ wersji 1,5 i nowszych.

###  <a name="_core_function_prototype"></a>Prototyp funkcji

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Uwagi

####  <a name="_core_parameters_and_usage"></a>Parametry i użycie

*hwndParent*<br/>
Okno określone jako właściciel okien dialogowych, które są tworzone przez Menedżera sterowników ODBC lub konkretny sterownik ODBC, aby uzyskać dodatkowe informacje od użytkownika dotyczące nowego źródła danych. Jeśli parametr *lpszAttributes* nie dostarcza wystarczającej ilości informacji, zostanie wyświetlone okno dialogowe. Parametr *hwndParent* może mieć wartość null.

*Lpsdriver*<br/>
Opis sterownika. Jest to nazwa wyświetlana użytkownikom, a nie nazwa sterownika fizycznego (DLL).

*lpszAttributes*<br/>
Lista atrybutów w postaci "NazwaKlucza = Value". Te ciągi są oddzielane terminatorami o wartości null z dwoma kolejnymi terminatorami null na końcu listy. Te atrybuty są głównie domyślnymi wpisami specyficznymi dla sterownika, które przechodzą do rejestru dla nowego źródła danych. Jednym z ważnych kluczy, które nie są wymienione w dokumentacji interfejsu API ODBC dla tej funkcji jest "DSN" ("Nazwa źródła danych"), która określa nazwę nowego źródła danych. Pozostałe wpisy są specyficzne dla sterownika dla nowego źródła danych. Często nie jest konieczne dostarczenie wszystkich wpisów, ponieważ sterownik może monitować użytkownika o wprowadzenie nowych wartości w oknach dialogowych. (Ustaw *hwndParent* na wartość null, aby to spowodować). Możesz chcieć jawnie podać wartości domyślne, aby użytkownik nie był monitowany.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Aby określić opis sterownika dla parametru Lpsdriver przy użyciu Administratora ODBC

1. Uruchom administratora ODBC.

1. Kliknij pozycję **Add** (Dodaj).

Zapewnia to listę zainstalowanych sterowników i ich opisów. Użyj tego opisu jako parametru *lpsdriver* . Zwróć uwagę na to, że używasz całego opisu, takiego jak "pliki programu Excel (*. xls)", w tym rozszerzenie nazwy pliku i nawiasy, jeśli istnieją w opisie.

Alternatywnie można przeanalizować Rejestr (lub, dla 16-bitowego pliku Odbcinst. ini), który zawiera listę wszystkich wpisów sterowników i opisów w kluczu rejestru "ODBC Drivers" (lub sekcję [ODBC Drivers] w pliku Odbcinst. ini).

Jednym ze sposobów znalezienia nazw i wartości parametrów *lpszAttributes* jest sprawdzenie pliku ODBC. ini dla już skonfigurowanego źródła danych (być może jest to, które zostało skonfigurowane przez administratora ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Aby znaleźć nazwy i wartości parametrów lpszAttributes

1. Uruchom Edytor rejestru systemu Windows (lub, w przypadku 16-bitowych, Otwórz plik ODBC. ini).

1. Znajdź informacje o źródłach danych ODBC przy użyciu jednej z następujących czynności:

   - W przypadku 32 bitów Znajdź klucz **HKEY_CURRENT_USER \software\odbc\odbc. INI\ODBC źródła danych** w okienku po lewej stronie.

      Okienko po prawej stronie zawiera listę wpisów w postaci: "pub: REG_SZ: *\<nazwa źródła danych >* ", gdzie *\<nazwa źródła danych >* to źródło danych, które zostało już skonfigurowane przy użyciu żądanych ustawień dla sterownika, którego zamierzasz użyć. Wybierz odpowiednie źródło danych, na przykład SQL Server. Elementy po ciągu "pub:" to, w kolejności, wartości KeyName i value do użycia w parametrze *lpszAttributes* .

   - W przypadku 16 bitów Znajdź sekcję w pliku ODBC. ini oznaczonym przez [ *\<nazwę źródła danych >* ].

      Wiersze po tym wierszu mają postać "NazwaKlucza = Value". Są to dokładnie wpisy do użycia w parametrze *lpszAttributes* .

Warto również zapoznać się z dokumentacją dotyczącą konkretnego sterownika, który ma być używany. Przydatne informacje można znaleźć w pomocy online dla sterownika, do którego można uzyskać dostęp za pomocą administratora ODBC. Te pliki pomocy są zwykle umieszczane w katalogu WINDOWS\SYSTEM dla systemu Windows NT, Windows 3,1 lub Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Aby uzyskać pomoc online dotyczącą sterownika ODBC

1. Uruchom administratora ODBC.

1. Kliknij pozycję **Add** (Dodaj).

1. Wybierz nazwę sterownika.

1. Kliknij przycisk **OK**.

Gdy administrator ODBC wyświetla informacje dotyczące tworzenia nowego źródła danych dla tego konkretnego sterownika, kliknij przycisk **Pomoc**. Spowoduje to otwarcie pliku pomocy dla danego sterownika, który zwykle zawiera ważne informacje dotyczące korzystania z sterownika.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
