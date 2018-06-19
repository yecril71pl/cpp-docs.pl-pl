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
ms.openlocfilehash: 2c08366f995c1ecb4182fff04a88ac37fe7334bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384267"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: pisanie programów instalacyjnych i administracyjnych ODBC dla aplikacji baz danych MFC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Używanie klas baz danych MFC aplikacji należy program instalacyjny, który instaluje składniki ODBC. Może być konieczne programu ODBC administracji, który pobiera informacje o dostępnych sterowników, aby określić domyślny sterowniki oraz konfigurowanie źródeł danych. Ta uwaga Opisuje interfejs API Instalatora ODBC do zapisania tych programów.  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Pisanie programu instalacyjnego ODBC  
 Aplikacja bazy danych MFC wymaga Menedżera sterowników ODBC (ODBC. Biblioteki DLL) i sterowników ODBC, aby można było uzyskać dostęp do źródła danych. Wiele sterowników ODBC wymaga również dodatkowe sieci i komunikacja z biblioteki dll. Większość sterowników ODBC dostarczanych z programem instalacyjnym, która będzie instalować składniki wymagane ODBC. Używanie klas baz danych MFC deweloperzy aplikacji można:  
  
-   Zależne od programów instalacyjnych sterownika ODBC — składniki instalacji. Wymaga to żadnych pracy w części dewelopera — można po prostu ponownie rozesłać program instalacyjny sterownika.  
  
-   Alternatywnie można napisać własny program instalacyjny, co spowoduje zainstalowanie Menedżera sterowników i sterownika.  
  
 Interfejs API Instalatora ODBC umożliwia pisanie programów instalacyjnych specyficzne dla aplikacji. Funkcje w Instalatorze interfejsu API są implementowane przez Instalatora ODBC biblioteki DLL — ODBCINST. Biblioteki DLL 16-bitowego systemu Windows i ODBCCP32. Biblioteki DLL na Win32. Aplikacja może wywołać **SQLInstallODBC** w Instalatorze biblioteki DLL, co spowoduje zainstalowanie menedżera sterownika ODBC, sterowników ODBC i wszystkie wymagane programy do tłumaczenia. Go następnie rejestruje, zainstalowane sterowniki i tłumaczy w ODBCINST. Plik INI (lub w rejestrze, w NT). **SQLInstallODBC** wymaga pełnej ścieżki do ODBC. Plik INF, który zawiera listę sterowników i opisuje pliki wchodzące w skład każdego sterownika. Zawiera również podobne informacji na temat Menedżera sterowników i tłumaczy. ODBC. Plików INF zwykle są dostarczane przez deweloperów sterowników.  
  
 Program można również zainstalować pojedynczych składników ODBC. Aby zainstalować Menedżera sterowników, najpierw wywołuje program **SQLInstallDriverManager** w Instalatorze biblioteki DLL w celu pobrania katalog docelowy dla Menedżera sterowników. Jest to zwykle katalog, w którym znajdują się biblioteki DLL systemu Windows. Następnie program używa informacji w sekcji [Menedżera sterowników ODBC] ODBC. Plik INF skopiuj Menedżera sterowników i powiązane pliki z dysku instalacyjnego do tego katalogu. Aby zainstalować sterownik poszczególnych, najpierw wywołuje program **Procedura SQLInstallDriver** w Instalatorze biblioteki DLL do dodania specyfikacji sterownik do ODBCINST. Plik INI (lub w rejestrze, w NT). **Procedura SQLInstallDriver** zwraca katalog docelowy sterownika — zwykle katalog, w którym znajdują się biblioteki DLL systemu Windows. Następnie program używa informacji w sekcji sterowników ODBC. Plik INF skopiuj sterownik biblioteki DLL i powiązane pliki z dysku instalacyjnego do tego katalogu.  
  
 Aby uzyskać więcej informacji na temat ODBC. INF, ODBCINST. INI i za pomocą Instalatora interfejsu API, zobacz ODBC SDK *Podręcznik programisty* rozdziale 19, instalowanie oprogramowania ODBC.  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Pisanie ODBC Administrator  
 Aplikacji bazy danych MFC mogą Instalowanie i konfigurowanie źródeł danych ODBC w jeden z dwóch sposobów, w następujący sposób:  
  
-   Użyj Administratora ODBC (dostępne jako program lub jako element Panelu sterowania).  
  
-   Utwórz program do konfigurowania źródeł danych.  
  
 Wywołania funkcji DLL Instalatora sprawia, że program, który konfiguruje źródła danych. Instalator DLL wywołuje ustawienia biblioteki DLL w celu skonfigurowania źródła danych. Jest plikiem Instalatora biblioteki DLL dla każdego sterownika; może być DLL samego sterownika, lub oddzielnych bibliotekach DLL. Biblioteka DLL Instalatora monituje użytkownika o informacje, które sterownik musi łączyć się z źródła danych i translator domyślne, jeśli jest to obsługiwane. Następnie wywołuje Instalator DLL i interfejsów API systemu Windows, aby zarejestrować te informacje w ODBC. Plik INI (lub rejestru).  
  
 Aby wyświetlić okno dialogowe, z którą użytkownik może dodać, modyfikowanie i usuwanie źródeł danych, program wywołuje **SQLManageDataSources** w Instalatorze biblioteki DLL. Ta funkcja jest wywoływana, gdy Instalator biblioteki DLL jest wywoływana z poziomu Panelu sterowania. Aby dodać, zmodyfikować lub usunąć źródła danych, **SQLManageDataSources** wywołania **: ConfigDSN** w ustawieniach DLL sterownika skojarzony z tym źródłem danych. Aby bezpośrednio dodawać, modyfikować lub usuwać dane źródeł, program wywołuje **SQLConfigDataSource** w Instalatorze biblioteki DLL. Program przekazuje nazwę źródła danych i opcji, która określa działanie podejmowane. **SQLConfigDataSource** wywołania **: ConfigDSN** w ustawieniach biblioteki DLL i przekazuje je argumenty z **SQLConfigDataSource**.  
  
 Aby uzyskać więcej informacji, zobacz ODBC SDK *Podręcznik programisty* działu 23, dotyczące funkcji DLL instalacji i rozdziału 24 odwołanie funkcji DLL Instalatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

