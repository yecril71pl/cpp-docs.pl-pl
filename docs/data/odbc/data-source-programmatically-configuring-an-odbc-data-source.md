---
title: "Źródło danych: Programowe Konfigurowanie źródła danych ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQLConfigDataSource
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac5756452a8b1c2d5dbf2f27ac7d3e1a8b069ca2
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Źródło danych: programowe konfigurowanie źródła danych ODBC
W tym temacie wyjaśniono, jak konfigurować nazwy źródeł danych Otwórz połączenie bazy danych (ODBC) programowo. Zapewnia to elastyczność uzyskują dostęp do danych bez wymuszania użytkownikowi jawnie Użyj ODBC Administrator lub inne programy, aby określić nazwy źródeł danych.  
  
 Zazwyczaj użytkownik uruchamia Administrator ODBC, aby utworzyć źródło danych, jeśli system zarządzania skojarzonej bazy danych (DBMS) obsługuje tej operacji.  
  
 Podczas tworzenia źródła danych ODBC dostępu firmy Microsoft za pośrednictwem Administrator ODBC, są podane dwie opcje: można wybrać istniejący plik mdb lub można utworzyć nowego pliku mdb. Nie istnieje sposób programowe tworzenie pliku mdb z aplikacji MFC ODBC. W związku z tym jeśli aplikacja wymaga umieszczenia danych do źródła danych programu Microsoft Access (plik mdb), najprawdopodobniej chcesz utworzyć plik mdb pusty możesz użyć lub skopiuj zawsze, gdy zajdzie taka potrzeba.  
  
 Jednak wielu systemach DBMS umożliwia tworzenie źródła danych programowe. Niektórych źródeł danych, Obsługa specyfikacji katalogu dla baz danych. Oznacza to, że katalog jest źródłem danych i każdej tabeli w źródle danych są przechowywane w osobnym pliku (w przypadku dBASE, każda tabela jest plik .dbf). Sterowniki dla innych baz danych ODBC, takich jak program Microsoft Access i SQL Server wymagają, że spełnione pewne określone kryteria przed nawiązaniem źródła danych. Na przykład gdy za pomocą sterownika ODBC programu SQL Server, musisz zostało ustanowione komputera programu SQL Server.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource Example  
 W poniższym przykładzie użyto **:: SQLConfigDataSource** funkcji interfejsu API ODBC do tworzenia nowego źródła danych programu Excel o nazwie nowego źródła danych programu Excel:  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 Należy pamiętać, że źródło danych jest w rzeczywistości katalogiem (C:\EXCELDIR); Ten katalog musi istnieć. Sterownik programu Excel używa katalogi jako jej źródeł danych i pliki jako poszczególnych tabel (jedna tabela w pliku xls).  
  
 Aby uzyskać więcej informacji na temat tworzenia tabel, zobacz [źródła danych: programowe tworzenie tabeli w źródle danych ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
 Następujące informacje w tym artykule omówiono parametrów, które muszą zostać przekazane do **:: SQLConfigDataSource** funkcji interfejsu API ODBC. Aby użyć **:: SQLConfigDataSource**, musisz uwzględnić plik nagłówka Odbcinst.h i korzystanie z biblioteki importu Odbcinst.lib. Ponadto Odbccp32.dll musi być w ścieżce w czasie wykonywania (lub Odbcinst.dll do 16-bitowe).  
  
 Można utworzyć przy użyciu ODBC Administrator lub podobne narzędzia nazwę źródła danych ODBC. Jednak czasami jest pożądane, aby utworzyć nazwę źródła danych bezpośrednio z aplikacji można uzyskać dostęp bez konieczności użytkownika o uruchomienie innego narzędzia.  
  
 Administrator ODBC (zazwyczaj zainstalowany w Panelu sterowania) tworzy nowe źródło danych, umieszczając wpisy w rejestrze systemu Windows (lub dla 16-bitowych, w pliku Odbc.ini). Ten plik można uzyskać wymaganych informacji o źródle danych wysyła zapytanie do Menedżera sterowników ODBC. Ważne jest, aby dowiedzieć się, jakie informacje musi być umieszczona w rejestrze, ponieważ musisz dostarczyć wywołanie **:: SQLConfigDataSource**.  
  
 Chociaż te informacje można są zapisywane bezpośrednio w rejestrze bez użycia **:: SQLConfigDataSource**, każda aplikacja, która wykonuje jest polegania na bieżącej metody, która Menedżera sterowników używane do obsługi danych. Jeśli nowsza wersja Menedżera sterowników ODBC implementuje prowadzenia o źródłach danych w inny sposób dowolnej aplikacji, która korzysta z tej techniki zostanie przerwane. Ogólnie zaleca używana jest funkcja interfejsu API, gdy zostało ono określone. Na przykład kodu jest przenośny z 16-bitowych 32-bitowy, jeśli używasz **:: SQLConfigDataSource** działać, ponieważ funkcja poprawnie zapisuje do pliku Odbc.ini lub w rejestrze.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource Parameters  
 Poniżej opisano parametry **:: SQLConfigDataSource** funkcji. Wiele informacji jest pobierana z interfejsu API ODBC *Podręcznik programisty* dostarczonego z programem Visual C++ w wersji 1.5 lub nowszym.  
  
###  <a name="_core_function_prototype"></a> Prototype — funkcja  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>Uwagi  
  
####  <a name="_core_parameters_and_usage"></a> Parametry i użycia  
 *hwndParent*  
 Okna, określony jako właściciel wszystkie okna dialogowe, które Menedżera sterowników ODBC lub konkretny sterownik ODBC tworzy, aby uzyskać dodatkowe informacje od użytkownika o nowe źródło danych. Jeśli `lpszAttributes` parametru nie dostarcza informacji wystarczających, zostanie wyświetlone okno dialogowe. *HwndParent* parametru może być **NULL**.  
  
 `lpszDriver`  
 Opis sterownika. Jest to nazwa widoczne dla użytkowników, a nie nazwa sterownika fizycznych (DLL).  
  
 `lpszAttributes`  
 Lista atrybutów w formie "keyname = wartość". Te parametry są oddzielone null terminatory z dwóch kolejnych terminatory wartości null na końcu listy. Te atrybuty są głównie domyślnych sterownika wpisów, które przechodzą w rejestrze dla nowego źródła danych. Jeden klucz ważne, które nie są opisane w dokumentacji interfejsu API ODBC dla tej funkcji jest "DSN" ("Nazwa źródła danych"), który określa nazwę nowego źródła danych. Pozostałe wpisy są specyficzne dla sterownika dla nowego źródła danych. Często nie jest konieczne do dostarczania wszystkich wpisów, ponieważ sterownik może monitować użytkownika z okien dialogowych służących do nowej wartości. (Ustaw *hwndParent* do **NULL** to spowodować.) Można jawnie Podaj wartości domyślne, dzięki czemu użytkownik nie jest monitowany.  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Aby określić opis sterownika dla parametru lpszDriver przy użyciu ODBC Administrator  
  
1.  Administrator ODBC wykonywania.  
  
2.  Kliknij przycisk **Dodaj**.  
  
 Wyświetla listę zainstalowanych sterowników i ich opisy. Użyj tego opisu jako `lpszDriver` parametru. Należy pamiętać, że używasz pełny opis, takie jak "Pliki programu Excel (*.xls)", łącznie z rozszerzenie nazwy pliku i nawiasy, jeśli istnieją w opisie.  
  
 Alternatywnie, można sprawdzić rejestru (lub, w przypadku 16-bitowy plik Odbcinst.ini), który zawiera listę wszystkich wpisów sterownika i opisy w kluczu rejestru "Sterowników ODBC" (lub sekcji [sterowników ODBC] Odbcinst.ini).  
  
 Aby znaleźć keynames i wartości dla `lpszAttributes` parametr ma zapoznaj się z plikiem Odbc.ini dla źródła danych już skonfigurowany (możliwe, że taki, który został skonfigurowany przez administratora ODBC).  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Aby znaleźć keynames i wartości dla parametru lpszAttributes  
  
1.  Uruchom Edytor rejestru systemu Windows (lub dla 16-bitowych, otwórz plik Odbc.ini).  
  
2.  Znajdź informacje źródła danych ODBC przy użyciu jednej z następujących czynności:  
  
    -   32-bitowe, można znaleźć w kluczu **HKEY_CURRENT_USER\Software\ODBC\ODBC. Źródła danych INI\ODBC** w okienku po lewej stronie.  
  
         Okienku po prawej stronie listy wpisów w postaci: "pub: REG_SZ:*<data source name>*", gdzie  *<data source name>*  jest to źródło danych, który został już skonfigurowany przy użyciu ustawień odpowiednią dla sterownika mają Aby użyć. Wybierz źródło danych, które mają, na przykład program SQL Server. Elementy występujące po słowie ciąg "pub:" są w kolejności, keyname i wartość do użycia w Twojej `lpszAttributes` parametru.  
  
    -   Dla 16-bitowych, Znajdź sekcję w pliku Odbc.ini oznaczony przez [*\<nazwa źródła danych >*].  
  
         Wiersze po tym wierszu są w formie "keyname = wartość". Są to dokładnie wpisów do użycia w Twojej `lpszAttributes` parametru.  
  
 Można również sprawdzić dokumentację dla określonego sterownika, którego chcesz użyć. Przydatne informacje można znaleźć w Pomocy online dla sterowników, które można otworzyć, uruchamiając ODBC Administrator. Te pliki pomocy są zwykle umieszczane w katalogu WINDOWS\SYSTEM dla systemu Windows NT, Windows 3.1 lub Windows 95.  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Aby uzyskać pomoc dotyczącą sterownika ODBC  
  
1.  Administrator ODBC wykonywania.  
  
2.  Kliknij przycisk **Dodaj**.  
  
3.  Wybierz nazwę sterownika.  
  
4.  Kliknij przycisk **OK**.  
  
 Gdy ODBC Administrator Wyświetla informacje dotyczące tworzenia nowego źródła danych dla tego konkretnego sterownika, kliknij przycisk **pomocy**. Spowoduje to otwarcie pliku pomocy dla tego konkretnego sterownika, który zwykle zawiera ważne informacje dotyczące używania sterownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)