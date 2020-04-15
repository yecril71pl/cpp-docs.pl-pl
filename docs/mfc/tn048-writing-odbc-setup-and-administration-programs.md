---
title: 'TN048: pisanie programów instalacyjnych i administracyjnych ODBC dla aplikacji baz danych MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365484"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: pisanie programów instalacyjnych i administracyjnych ODBC dla aplikacji baz danych MFC

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

Aplikacje korzystające z klas bazy danych MFC będą potrzebowały programu instalacyjnego, który instaluje składniki ODBC. Mogą również potrzebować programu administracji ODBC, który będzie pobierał informacje o dostępnych sterownikach, określał sterowniki domyślne i konfigurował źródła danych. W tej notatce opisano użycie interfejsu API instalatora ODBC do pisania tych programów.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>Pisanie programu instalacyjnego ODBC

Aplikacja bazy danych MFC wymaga menedżera sterowników ODBC (ODBC. DLL) i sterowniki ODBC, aby móc uzyskać dostęp do źródeł danych. Wiele sterowników ODBC wymaga również dodatkowych bibliotek DLL sieci i komunikacji. Większość sterowników ODBC dostarczanych z programem instalacyjnym, który zainstaluje wymagane komponenty ODBC. Deweloperzy aplikacji przy użyciu klas bazy danych MFC mogą:

- Polegaj na programach instalacyjnych specyficznych dla sterownika do instalowania komponentów ODBC. Nie będzie to wymagało dalszych prac ze strony dewelopera — możesz po prostu rozpowszechniać program instalacyjny sterownika.

- Alternatywnie, można napisać własny program instalacyjny, który zainstaluje menedżera sterowników i sterownika.

Interfejs API instalatora ODBC może być używany do pisania programów instalacyjnych specyficznych dla aplikacji. Funkcje w interfejsie API instalatora są implementowane przez bibliotekę DLL instalatora ODBC — ODBCINST. DLL w 16-bitowych systemach Windows i ODBCCP32. DLL na Win32. Aplikacja może `SQLInstallODBC` wywołać w biblioteki DLL instalatora, który zainstaluje menedżera sterowników ODBC, sterowniki ODBC i wszelkie wymagane tłumaczy. Następnie rejestruje zainstalowane sterowniki i tłumaczy w ODBCINST. ini (lub rejestru, na NT). `SQLInstallODBC`wymaga pełnej ścieżki do ODBC. PLIK INF, który zawiera listę sterowników do zainstalowania i opisuje pliki, które składają się na każdy sterownik. Zawiera również podobne informacje na temat menedżera sterowników i tłumaczy. Odbc. Pliki INF są zazwyczaj dostarczane przez deweloperów sterowników.

Program może również zainstalować poszczególne składniki ODBC. Aby zainstalować Menedżera sterowników, `SQLInstallDriverManager` program najpierw wywołuje w biblioteki DLL instalatora, aby uzyskać katalog docelowy dla Menedżera sterowników. Zazwyczaj jest to katalog, w którym znajdują się biblioteki DLL systemu Windows. Następnie program używa informacji w sekcji [MENEDŻER STEROWNIKÓW ODBC] odBC. PLIK INF do kopiowania Menedżera sterowników i powiązanych plików z dysku instalacyjnego do tego katalogu. Aby zainstalować pojedynczy sterownik, program `SQLInstallDriver` najpierw wywołuje w emIB instalatora, aby dodać specyfikację sterownika do ODBCINST. ini (lub rejestru, na NT). `SQLInstallDriver`zwraca katalog docelowy sterownika — zwykle katalog, w którym znajdują się biblioteki DLL systemu Windows. Następnie program używa informacji w sekcji sterownika ODBC. inf, aby skopiować bibliotekę DLL sterownika i powiązane pliki z dysku instalacyjnego do tego katalogu.

Aby uzyskać więcej informacji na temat ODBC. INF, ODBCINST. INI i za pomocą interfejsu API instalatora, patrz OdBC SDK *Programmer's Reference,* Rozdział 19, Instalowanie oprogramowania ODBC.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>Pisanie administratora ODBC

Aplikacja bazy danych MFC można skonfigurować i skonfigurować źródła danych ODBC na jeden z dwóch sposobów, w następujący sposób:

- Użyj administratora ODBC (dostępnego jako program lub jako element Panelu sterowania).

- Utwórz własny program do konfigurowania źródeł danych.

Program, który konfiguruje źródła danych, wywołuje funkcje do biblioteki DLL instalatora. Biblioteka DLL instalatora wywołuje bibliotekę DLL konfiguracji w celu skonfigurowania źródła danych. Istnieje jedna biblioteka DLL konfiguracji dla każdego sterownika; może to być sam dll sterownika lub oddzielna biblioteka DLL. Biblioteka DLL instalatora monituje użytkownika o informacje, które sterownik musi połączyć się ze źródłem danych i domyślnym tłumaczem, jeśli jest obsługiwany. Następnie wywołuje bibliotekę DLL instalatora i interfejsy API systemu Windows, aby zarejestrować te informacje w odbc. ini (lub rejestru).

Aby wyświetlić okno dialogowe, za pomocą którego użytkownik może dodawać, modyfikować i usuwać źródła danych, program wywołuje `SQLManageDataSources` w biblioteki DLL instalatora. Ta funkcja jest wywoływana, gdy biblioteka DLL instalatora jest wywoływana z Panelu sterowania. Aby dodać, zmodyfikować lub usunąć `SQLManageDataSources` `ConfigDSN` źródło danych, wywoła wywołanie biblioteki DLL instalatora dla sterownika skojarzonego z tym źródłem danych. Aby bezpośrednio dodać, zmodyfikować lub usunąć źródła `SQLConfigDataSource` danych, program wywołuje bibliotekę DLL instalatora. Program przekazuje nazwę źródła danych i opcję określającą akcję do podjęcia. `SQLConfigDataSource`wywołuje `ConfigDSN` w dll konfiguracji i przekazuje `SQLConfigDataSource`jej argumenty z .

Aby uzyskać więcej informacji, zobacz *Odwołanie programisty* SDK ODBC, rozdział 23, Odwołanie do funkcji DLL instalatora i rozdział 24, odwołanie do funkcji biblioteki DLL instalatora.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
