---
title: 'TN048: Pisanie programów instalacyjnych ODBC i administracyjnych dla aplikacji baz danych MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a70ddac1839d8967b9e9f7226a554d0b92449e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401826"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: pisanie programów instalacyjnych i administracyjnych ODBC dla aplikacji baz danych MFC

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Używanie klas baz danych MFC aplikacji należy program instalacyjny, który instaluje składniki ODBC. Może być konieczne programu administracji ODBC, który pobiera informacje o dostępnych sterowników, aby określić domyślne sterowniki i skonfigurować źródła danych. Ta uwaga opisuje korzystanie z interfejsu API Instalatora ODBC do zapisania tych programów.

##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Pisanie programu instalacyjnego ODBC

Aplikacja MFC bazy danych wymaga Menedżera sterowników ODBC (ODBC. Biblioteka DLL) i sterowników ODBC, aby można było uzyskać dostęp do źródeł danych. Wiele sterowników ODBC również wymagać dodatkowych bibliotek DLL sieci i komunikacji. Większość sterowniki ODBC są dostarczane za pomocą programu instalacyjnego, która będzie instalować wymaganych składników ODBC. Deweloperzy aplikacji używanie klas baz danych MFC wykonywać następujące czynności:

- Polegaj na programy ustawienia specyficzne dla sterownika dla instalowanie składników ODBC. Wymaga to żadne dodatkowe prace nad częścią dewelopera — po prostu ponownie dystrybuować program instalacyjny sterownika.

- Alternatywnie można napisać własny program instalacyjny i zainstaluje Menedżer sterowników i sterownika.

Instalator interfejsu API ODBC może służyć do pisania programów ustawienia specyficzne dla aplikacji. Funkcje w Instalatorze interfejsu API są implementowane przez Instalatora ODBC biblioteki DLL — ODBCINST. Biblioteki DLL Windows 16-bitowych i ODBCCP32. Biblioteka DLL na Win32. Aplikacja może wywołać `SQLInstallODBC` w Instalatorze biblioteki DLL, co spowoduje zainstalowanie Menedżera sterowników ODBC, sterowniki ODBC i dowolne wymagane tłumaczy. Zainstalowane sterowniki i tłumaczy następnie rejestruje w ODBCINST. Plik INI (lub rejestru w NT). `SQLInstallODBC` wymaga pełnej ścieżki do ODBC. Plik INF, który zawiera listę sterowników i opisano pliki wchodzące w skład każdego sterownika. Zawiera podobne informacje dotyczące Menedżera sterowników i tłumaczy. ODBC. Pliki INF są zazwyczaj dostarczane przez deweloperów sterowników.

Program można również zainstalować w poszczególnych składników ODBC. Aby zainstalować Menedżera sterowników, najpierw wywołuje program `SQLInstallDriverManager` w Instalatorze biblioteki DLL, aby uzyskać katalog docelowy dla Menedżera sterowników. Zazwyczaj jest to katalog, w którym znajdują się pliki dll Windows. Następnie program używa informacji w sekcji [ODBC Driver Manager] ODBC. Plik INF do skopiowania Menedżera sterowników i powiązane pliki z dysku instalacyjnego do tego katalogu. Aby zainstalować sterownik poszczególnych, najpierw wywołuje program `SQLInstallDriver` w Instalatorze biblioteki DLL do dodania Specyfikacja sterownika do ODBCINST. Plik INI (lub rejestru w NT). `SQLInstallDriver` Zwraca katalog docelowy sterownika — zwykle katalog, w którym znajdują się pliki dll Windows. Następnie program używa informacji w sekcji sterowników ODBC. Plik INF do skopiowania sterownik biblioteki DLL i powiązane pliki z dysku instalacyjnego do tego katalogu.

Aby uzyskać więcej informacji na temat ODBC. INF, ODBCINST. INI i za pomocą Instalatora interfejsu API, zobacz ODBC SDK *odwołania programisty* rozdziale 19, instalowanie oprogramowania ODBC.

##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Zapisywanie ODBC Administrator

Aplikację bazy danych MFC można Instalowanie i konfigurowanie źródła danych ODBC w jeden z dwóch sposobów, w następujący sposób:

- Za pomocą Administratora ODBC (dostępne jako program lub jako element Panelu sterowania).

- Utwórz własny program do konfigurowania źródeł danych.

Program, który umożliwia skonfigurowanie źródła danych sprawia, że wywołania funkcji do Instalatora biblioteki DLL. Instalator DLL wywołuje ustawienia biblioteki DLL, aby skonfigurować źródło danych. Istnieje jeden Instalator biblioteki DLL dla każdego sterownika; być może sterownik biblioteki DLL, samego lub oddzielnych bibliotek DLL. Biblioteka DLL Instalatora monituje użytkownika o informacje, które sterownik musi połączyć się z źródła danych i translator domyślne, jeśli jest obsługiwany. Następnie wywołuje Instalator biblioteki DLL i interfejsów API Windows, aby zapisać te informacje w ODBC. Plik INI (lub rejestru).

Aby wyświetlić okno dialogowe, za pomocą której użytkownik może dodać, modyfikowanie i usuwanie źródeł danych, program wywołuje `SQLManageDataSources` w Instalatorze biblioteki DLL. Ta funkcja jest wywoływana, gdy Instalator Biblioteka DLL jest wywoływana z poziomu Panelu sterowania. Aby dodać, zmodyfikować lub usunąć źródła danych `SQLManageDataSources` wywołania `ConfigDSN` w Instalatorze biblioteki DLL dla sterownika skojarzony z tym źródłem danych. Można bezpośrednio dodawać, modyfikować lub usuwać dane źródeł, program wywołuje `SQLConfigDataSource` w Instalatorze biblioteki DLL. Program przekazuje nazwę źródła danych i opcji, która określa akcję do wykonania. `SQLConfigDataSource` wywołania `ConfigDSN` w Instalatorze biblioteki DLL i przekazuje je argumenty z `SQLConfigDataSource`.

Aby uzyskać więcej informacji, zobacz ODBC SDK *odwołania programisty* działu 23, odwołanie do funkcji DLL konfiguracji i rozdział 24, odwołanie do funkcji DLL Instalatora.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

