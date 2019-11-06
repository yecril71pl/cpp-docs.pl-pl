---
title: Błędy krytyczne kompilatora — od C999 do C1999
ms.date: 04/21/2019
f1_keywords:
- C1034
- C1036
- C1041
- C1048
- C1063
- C1069
- C1101
- C1102
- C1105
- C1110
- C1111
- C1112
- C1114
- C1193
- C1195
- C1300
- C1301
- C1302
- C1306
- C1384
- C1451
- C1505
- C1901
helpviewer_keywords:
- C1034
- C1036
- C1041
- C1048
- C1063
- C1069
- C1101
- C1102
- C1105
- C1110
- C1111
- C1112
- C1114
- C1193
- C1195
- C1300
- C1301
- C1302
- C1306
- C1384
- C1451
- C1505
- C1901
ms.assetid: 6c8df109-7594-48ed-987a-97d9fe2b04af
ms.openlocfilehash: 395d7403ef4fe04b671a84a61d320b27ad8ad1c7
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626567"
---
# <a name="compiler-fatal-errors-c999-through-c1999"></a>Błędy krytyczne kompilatora — od C999 do C1999

Artykuły w tej sekcji dokumentacji wyjaśniają podzestaw komunikatów o błędach generowanych przez kompilator Microsoft C/C++ .

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd krytyczny C999](../../error-messages/compiler-errors-1/fatal-error-c999.md)|NIEZNANY komunikat wybierz polecenie Pomoc techniczna w menu Pomoc wizualna C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|[Błąd krytyczny C1001](../../error-messages/compiler-errors-1/fatal-error-c1001.md)|Wystąpił błąd wewnętrzny w kompilatorze.<br /> (plik kompilatora "*plik*", *numer*wiersza)<br /> Aby obejść ten problem, wypróbuj uproszczenie lub zmianę programu w pobliżu lokalizacji wymienionych powyżej. Wybierz polecenie Pomoc techniczna w menu Pomoc wizualna C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|[Błąd krytyczny C1002](../../error-messages/compiler-errors-1/fatal-error-c1002.md)|Kompilator nie ma miejsca na stercie w przebiegu 2|
|[Błąd krytyczny C1003](../../error-messages/compiler-errors-1/fatal-error-c1003.md)|Liczba błędów przekracza *liczbę*; Zatrzymywanie kompilacji|
|[Błąd krytyczny C1004](../../error-messages/compiler-errors-1/fatal-error-c1004.md)|znaleziono nieoczekiwany koniec pliku|
|[Błąd krytyczny C1005](../../error-messages/compiler-errors-1/fatal-error-c1005.md)|zbyt duży ciąg dla buforu|
|[Błąd krytyczny C1007](../../error-messages/compiler-errors-1/fatal-error-c1007.md)|Nierozpoznana flaga "*String*" w elemencie "*Option*"|
|[Błąd krytyczny C1008](../../error-messages/compiler-errors-1/fatal-error-c1008.md)|nie określono pliku wejściowego|
|[Błąd krytyczny C1009](../../error-messages/compiler-errors-1/fatal-error-c1009.md)|ograniczenie kompilatora: makra są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1010](../../error-messages/compiler-errors-1/fatal-error-c1010.md)|nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego nagłówka. Czy zapomnisz dodać "#include \<*pliku*>" do źródła?|
|[Błąd krytyczny C1012](fatal-error-c1012.md)|Niedopasowane nawiasy: Brak znaku "*Character*"|
|[Błąd krytyczny C1013](fatal-error-c1013.md)|ograniczenie kompilatora: zbyt wiele otwartych nawiasów|
|[Błąd krytyczny C1014](fatal-error-c1014.md)|zbyt wiele plików dołączanych: Głębokość = *Liczba*|
|[Błąd krytyczny C1016](fatal-error-c1016.md)|#ifdef/#ifndef Oczekiwano identyfikatora|
|[Błąd krytyczny C1017](../../error-messages/compiler-errors-1/fatal-error-c1017.md)|nieprawidłowe wyrażenie stałej całkowitej|
|[Błąd krytyczny C1018](fatal-error-c1018.md)|nieoczekiwany #elif|
|[Błąd krytyczny C1019](fatal-error-c1019.md)|nieoczekiwany #else|
|[Błąd krytyczny C1020](fatal-error-c1020.md)|nieoczekiwany #endif|
|[Błąd krytyczny C1021](fatal-error-c1021.md)|Nieprawidłowe polecenie preprocesora "*String*"|
|[Błąd krytyczny C1022](fatal-error-c1022.md)|oczekiwane #endif|
|[Błąd krytyczny C1023](fatal-error-c1023.md)|"*plik*": nieoczekiwany błąd w PCH, spróbuj ponownie skompilować PCH|
|[Błąd krytyczny C1026](../../error-messages/compiler-errors-1/fatal-error-c1026.md)|przepełnienie stosu parsera, zbyt skomplikowany program|
|[Błąd krytyczny C1033](../../error-messages/compiler-errors-1/fatal-error-c1033.md)|nie można otworzyć programu bazy danych "*File*"|
|Błąd krytyczny C1034|*plik*: nie ma ustawionej ścieżki include|
|[Błąd krytyczny C1035](fatal-error-c1035.md)|wyrażenie jest zbyt złożone; Uprość wyrażenie|
|Błąd krytyczny C1036|nie można zastąpić starszego formatu programu bazy danych, usunąć*pliku*i ponownie skompilować|
|[Błąd krytyczny C1037](fatal-error-c1037.md)|nie można otworzyć pliku obiektu "*File*"|
|[Błąd krytyczny C1038](fatal-error-c1038.md)|ograniczenie kompilatora: "*Function*": stan przepływu sterowania zbyt skomplikowany; Uprość funkcję|
|Błąd krytyczny C1041|nie można otworzyć programu bazy danych "*File*"; Jeśli wielokrotne CL. Zapisz w pliku EXE. Plik PDB, użyj/FS|
|[Błąd krytyczny C1045](fatal-error-c1045.md)|ograniczenie kompilatora: wymagania dotyczące konsolidacji są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1046](../../error-messages/compiler-errors-1/fatal-error-c1046.md)|ograniczenie kompilatora: *Struktura* zagnieżdżona zbyt głęboko|
|[Błąd krytyczny C1047](fatal-error-c1047.md)|Obiekt lub plik biblioteki "*File*" został utworzony za pomocą starszego kompilatora niż inne obiekty; ponowne kompilowanie starych obiektów i bibliotek|
|Błąd krytyczny C1048|nieznana opcja "*String*" w*opcji "Option*"|
|[Błąd krytyczny C1049](fatal-error-c1049.md)|Nieprawidłowy liczbowy argument "*Value*"|
|[Błąd krytyczny C1051](../../error-messages/compiler-errors-1/fatal-error-c1051.md)|plik bazy danych programu,*plik*", ma przestarzały format, usuń go i ponownie skompiluj|
|[Błąd krytyczny C1052](fatal-error-c1052.md)|plik bazy danych programu "*filename*" został wygenerowany przez konsolidator przy użyciu parametru/Debug: Fastlink; Kompilator nie może zaktualizować takich plików PDB; Usuń go lub użyj/FD, aby określić inną nazwę pliku PDB|
|[Błąd krytyczny C1053](fatal-error-c1053.md)|"*Function*": funkcja zbyt duża|
|[Błąd krytyczny C1054](../../error-messages/compiler-errors-1/fatal-error-c1054.md)|ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1055](../../error-messages/compiler-errors-1/fatal-error-c1055.md)|ograniczenie kompilatora: brak kluczy|
|[Błąd krytyczny C1057](../../error-messages/compiler-errors-1/fatal-error-c1057.md)|nieoczekiwany koniec pliku w rozwinięciu makra|
|[Błąd krytyczny C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)|Kompilator nie ma miejsca na stercie|
|[Błąd krytyczny C1061](../../error-messages/compiler-errors-1/fatal-error-c1061.md)|ograniczenie kompilatora: bloki są zagnieżdżone zbyt głęboko|
|Błąd krytyczny C1063|ograniczenie kompilatora: przepełnienie stosu kompilatora|
|[Błąd krytyczny C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)|ograniczenie kompilatora: token spowodował przepełnienie buforu wewnętrznego|
|[Błąd krytyczny C1065](../../error-messages/compiler-errors-1/fatal-error-c1065.md)|ograniczenie kompilatora: Brak tagów|
|[Błąd krytyczny C1067](../../error-messages/compiler-errors-1/fatal-error-c1067.md)|ograniczenie kompilatora: przekroczono limit 64 KB rozmiaru rekordu typu|
|[Błąd krytyczny C1068](fatal-error-c1068.md)|nie można otworzyć pliku "*File*"|
|Błąd krytyczny C1069|nie można odczytać wiersza polecenia kompilatora|
|[Błąd krytyczny C1070](fatal-error-c1070.md)|niezgodna para #if/#endif w pliku "*File*"|
|[Błąd krytyczny C1071](../../error-messages/compiler-errors-1/fatal-error-c1071.md)|znaleziono nieoczekiwany koniec pliku w komentarzu|
|[Błąd krytyczny C1073](../../error-messages/compiler-errors-1/fatal-error-c1073.md)|Błąd wewnętrzny dotyczący kompilacji przyrostowej (plik kompilatora "*File*", *numer*wiersza)|
|[Błąd krytyczny C1074](fatal-error-c1074.md)|"IDB" jest niedozwolonym rozszerzeniem pliku PDB: *File*|
|[Błąd krytyczny C1075](../../error-messages/compiler-errors-1/fatal-error-c1075.md)|lewy *token* nie został dopasowany na końcu pliku|
|[Błąd krytyczny C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)|ograniczenie kompilatora: osiągnięto limit sterty wewnętrznej; Użyj/zm, aby określić wyższy limit|
|[Błąd krytyczny C1077](fatal-error-c1077.md)|ograniczenie kompilatora: nie może być więcej niż *Liczba* opcji wiersza polecenia|
|[Błąd krytyczny C1079](../../error-messages/compiler-errors-1/fatal-error-c1079.md)|ograniczenie kompilatora: przekroczono limit rozmiaru pliku PCH|
|[Błąd krytyczny C1080](../../error-messages/compiler-errors-1/fatal-error-c1080.md)|ograniczenie kompilatora: opcja wiersza polecenia przekroczyła limit *liczby* znaków|
|[Błąd krytyczny C1081](../../error-messages/compiler-errors-1/fatal-error-c1081.md)|"*plik*": zbyt długa nazwa pliku|
|[Błąd krytyczny C1082](fatal-error-c1082.md)|nie można zamknąć pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1083](../../error-messages/compiler-errors-1/fatal-error-c1083.md)|nie można otworzyć pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1084](../../error-messages/compiler-errors-1/fatal-error-c1084.md)|nie można odczytać pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1085](../../error-messages/compiler-errors-1/fatal-error-c1085.md)|nie można zapisać pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1086](fatal-error-c1086.md)|nie można wyszukać pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1087](fatal-error-c1087.md)|nie można określić pliku *typu* : "*plik*": *komunikat*|
|[Błąd krytyczny C1088](fatal-error-c1088.md)|nie można opróżnić *typu* pliku: "*plik*": *komunikat*|
|[Błąd krytyczny C1089](fatal-error-c1089.md)|nie można obciąć pliku *typu* : "*plik*": *komunikat*|
|Błąd krytyczny C1090|Wywołanie interfejsu API PDB nie powiodło się, kod błędu "*Code*": "*Message*"|
|[Błąd krytyczny C1091](fatal-error-c1091.md)|ograniczenie kompilatora: długość ciągu przekracza *liczbę* bajtów|
|[Błąd krytyczny C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)|Edytuj i Kontynuuj nie obsługuje zmiany typów danych; wymagana kompilacja|
|[Błąd krytyczny C1093](../../error-messages/compiler-errors-1/fatal-error-c1093.md)|Wywołanie interfejsu API "*Function*" nie powiodło się "*HRESULT*": "*Description*"|
|[Błąd krytyczny C1094](../../error-messages/compiler-errors-1/fatal-error-c1094.md)|"-Zm*Number*": opcja wiersza polecenia jest niespójna z wartością używaną do kompilowania prekompilowanego nagłówka ("-zm*Number*")|
|[Błąd krytyczny C1098](fatal-error-c1098.md)|Niezgodność wersji z silnikiem Edytuj i Kontynuuj|
|[Błąd krytyczny C1099](fatal-error-c1099.md)|Edytuj i Kontynuuj aparat kończący kompilację|
|[Błąd krytyczny C1100](fatal-error-c1100.md)|nie można zainicjować OLE: *błąd*|
|Błąd krytyczny C1101|nie można utworzyć procedury obsługi dla atrybutu "*Identifier*"|
|Błąd krytyczny C1102|nie można zainicjować: *błąd*|
|[Błąd krytyczny C1103](fatal-error-c1103.md)|Błąd krytyczny podczas importowania identyfikatora ProgID: "*Message*"|
|[Błąd krytyczny C1104](fatal-error-c1104.md)|Błąd krytyczny podczas importowania identyfikatora LIBID: "*Message*"|
|Błąd krytyczny C1105|*komunikat*: *błąd*|
|[Błąd krytyczny C1107](../../error-messages/compiler-errors-1/fatal-error-c1107.md)|nie można znaleźć zestawu "*Assembly*": Określ ścieżkę wyszukiwania zestawu za pomocą/AI lub przez ustawienie zmiennej ŚRODOWISKowej LIBPATH|
|[Błąd krytyczny C1108](fatal-error-c1108.md)|nie można odnaleźć biblioteki DLL: "*plik*"|
|[Błąd krytyczny C1109](fatal-error-c1109.md)|nie można znaleźć*symbolu "symbol*" w*pliku*dll "|
|Błąd krytyczny C1110|zbyt wiele zagnieżdżonych szablonów/definicji ogólnych|
|Błąd krytyczny C1111|zbyt wiele parametrów szablonu/generycznego|
|Błąd krytyczny C1112|ograniczenie kompilatora: `'number`"zbyt wiele argumentów makra, dozwolone są tylko *liczby*|
|[Błąd krytyczny C1113](../../error-messages/compiler-errors-1/fatal-error-c1113.md)|nie można #using "*plik*"|
|Błąd krytyczny C1114|"*plik*": WinRT nie obsługuje #using zestawu zarządzanego|
|[Błąd krytyczny C1120](../../error-messages/compiler-errors-1/fatal-error-c1120.md)|Wywołanie funkcji GetProcAddress nie powiodło się dla elementu "*Function*"|
|[Błąd krytyczny C1121](../../error-messages/compiler-errors-1/fatal-error-c1121.md)|Wywołanie CryptoAPI nie powiodło się|
|[Błąd krytyczny C1126](../../error-messages/compiler-errors-1/fatal-error-c1126.md)|Alokacja automatyczna przekracza *rozmiar*|
|[Błąd krytyczny C1128](../../error-messages/compiler-errors-1/fatal-error-c1128.md)|Liczba sekcji przekroczyła limit formatu pliku obiektu: Kompiluj z/bigobj|
|[Błąd krytyczny C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)|#error: *komunikat*|
|[Błąd krytyczny C1190](fatal-error-c1190.md)|zarządzany kod źródłowy wymaga opcji "/CLR"|
|[Błąd krytyczny C1191](../../error-messages/compiler-errors-1/fatal-error-c1191.md)|*plik "File*" można zaimportować tylko w zakresie globalnym|
|[Błąd krytyczny C1192](../../error-messages/compiler-errors-1/fatal-error-c1192.md)|nie można #using "*plik*"|
|Błąd krytyczny C1193|błąd oczekiwany w *pliku*(*wiersz*) nie został osiągnięty|
|Błąd krytyczny C1195|Użycie/Yu i/Yc w tym samym wierszu polecenia jest niezgodne z opcją/CLR|
|[Błąd krytyczny C1196](fatal-error-c1196.md)|"*Identyfikator*": identyfikator znaleziony w bibliotece typów "*TypeLib*" nie jest prawidłowym C++ identyfikatorem|
|[Błąd krytyczny C1197](../../error-messages/compiler-errors-1/fatal-error-c1197.md)|nie można odwołać się do*pliku*, ponieważ w programie istnieje już odwołanie do*pliku*.|
|[Błąd krytyczny C1201](fatal-error-c1201.md)|nie można kontynuować po błędzie składniowym w definicji szablonu klasy|
|[Błąd krytyczny C1202](fatal-error-c1202.md)|kontekst cyklicznego typu lub funkcji zależności zbyt złożony|
|[Błąd krytyczny C1205](fatal-error-c1205.md)|Typy ogólne nie są obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1206](fatal-error-c1206.md)|Dane dla domeny aplikacji nie są obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1207](fatal-error-c1207.md)|Zarządzane szablony nie są obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1208](fatal-error-c1208.md)|Przydzielanie klas referencyjnych na stosie nie jest obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1209](fatal-error-c1209.md)|Przyjazne zestawy nie są obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1210](fatal-error-c1210.md)|/CLR: Pure i/CLR: Safe nie są obsługiwane przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|[Błąd krytyczny C1211](fatal-error-c1211.md)|Atrybut niestandardowy TypeForwardedTo nie jest obsługiwany przez zainstalowaną wersję środowiska uruchomieniowego w trakcie wykonania|
|Błąd krytyczny C1300|błąd podczas uzyskiwania dostępu do *pliku* bazy danych programu (*komunikat*)|
|Błąd krytyczny C1301|Wystąpił błąd podczas uzyskiwania dostępu do *pliku*bazy danych programu, nieprawidłowy format, Usuń i Skompiluj ponownie|
|Błąd krytyczny C1302|Brak danych profilu modułu "*module*" w*pliku "File*" profilu|
|[Błąd krytyczny C1305](../../error-messages/compiler-errors-1/fatal-error-c1305.md)|Baza danych profilu "*File*" ma dla innej architektury|
|Błąd krytyczny C1306|Ostatnia zmiana w profilowej bazie danych "*File*" nie była analizą optymalizacji. decyzje dotyczące optymalizacji mogą być nieaktualne|
|[Błąd krytyczny C1307](../../error-messages/compiler-errors-1/fatal-error-c1307.md)|Program został wyedytowany od czasu zebrania danych profilowych|
|[Błąd krytyczny C1308](../../error-messages/compiler-errors-1/fatal-error-c1308.md)|*plik*: łączenie zestawów nie jest obsługiwane|
|[Błąd krytyczny C1309](../../error-messages/compiler-errors-1/fatal-error-c1309.md)|Niezgodne wersje C2. DLL i PGODB*Ver*. BIBLIOTECE|
|[Błąd krytyczny C1310](fatal-error-c1310.md)|Profilowana Optymalizacja nie jest dostępna w przypadku używania OpenMP|
|[Błąd krytyczny C1311](../../error-messages/compiler-errors-1/fatal-error-c1311.md)|Format COFF statycznie nie może zainicjować "*symbol*" z *liczbą* bajtów adresu|
|[Błąd krytyczny C1312](fatal-error-c1312.md)|Zbyt wiele gałęzi warunkowych w funkcji.  Uprość lub Refaktoryzacja kodu źródłowego.|
|[Błąd krytyczny C1313](../../error-messages/compiler-errors-1/fatal-error-c1313.md)|ograniczenie kompilatora: bloki *typów* nie mogą być zagnieżdżone głębiej niż poziomy *liczbowe*|
|[Błąd krytyczny C1350](../../error-messages/compiler-errors-1/fatal-error-c1350.md)|Wystąpił błąd podczas ładowania biblioteki dll "*File*": nie znaleziono biblioteki DLL|
|[Błąd krytyczny C1351](../../error-messages/compiler-errors-1/fatal-error-c1351.md)|Wystąpił błąd podczas ładowania biblioteki dll "*File*": niezgodna wersja|
|[Błąd krytyczny C1352](fatal-error-c1352.md)|Nieprawidłowe lub uszkodzone MSIL w funkcji "*Function*" z modułu "*module*"|
|[Błąd krytyczny C1353](fatal-error-c1353.md)|Operacja metadanych nie powiodła się: środowisko uruchomieniowe nie jest zainstalowane lub niezgodność wersji|
|[Błąd krytyczny C1382](../../error-messages/compiler-errors-1/fatal-error-c1382.md)|plik PCH "*File*" został odbudowany od momentu wygenerowania "*obj*". Skompiluj ponownie ten obiekt|
|[Błąd krytyczny C1383](fatal-error-c1383.md)|Opcja kompilatora/GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego języka wspólnego|
|Błąd krytyczny C1384|Nieprawidłowe ustawienie dla PGO_PATH_TRANSLATION podczas łączenia "*plik*"|
|Błąd krytyczny C1451|Nie można wygenerować informacji debugowania podczas kompilowania grafu wywołań dla concurrency::p arallel_for_each w: "*szczegóły*"|
|Błąd krytyczny C1505|nieodwracalny błąd wyszukiwania analizatora|
|[Błąd krytyczny C1506](../../error-messages/compiler-errors-1/fatal-error-c1506.md)|nieodwracalny błąd zakresu bloku|
|[Błąd krytyczny C1508](fatal-error-c1508.md)|ograniczenie kompilatora: "*Function*": więcej niż 65535 bajtów argumentu|
|[Błąd krytyczny C1509](../../error-messages/compiler-errors-1/fatal-error-c1509.md)|ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "*Function*"; Uprość funkcję|
|[Błąd krytyczny C1510](../../error-messages/compiler-errors-1/fatal-error-c1510.md)|Nie można otworzyć zasobu języka językowego clui. dll.|
|[Błąd krytyczny C1601](../../error-messages/compiler-errors-1/fatal-error-c1601.md)|nieobsługiwany Wbudowany zestaw opcode|
|[Błąd krytyczny C1602](../../error-messages/compiler-errors-1/fatal-error-c1602.md)|Nieobsługiwane wewnętrznie|
|[Błąd krytyczny C1603](../../error-messages/compiler-errors-1/fatal-error-c1603.md)|cel rozgałęzienia zestawu wbudowanego poza zakresem przez *liczbę* bajtów|
|[Błąd krytyczny C1852](fatal-error-c1852.md)|"*plik*" nie jest prawidłowym prekompilowanym plikiem nagłówkowym|
|[Błąd krytyczny C1853](../../error-messages/compiler-errors-1/fatal-error-c1853.md)|prekompilowany plik nagłówkowy "*File*" pochodzi z poprzedniej wersji kompilatora lub prekompilowanego nagłówka jest i jest C++ używany w języku C (lub odwrotnie)|
|[Błąd krytyczny C1854](../../error-messages/compiler-errors-1/fatal-error-c1854.md)|nie można zastąpić informacji utworzonych podczas tworzenia prekompilowanego nagłówka w pliku obiektu: "*plik*"|
|[Błąd krytyczny C1900](../../error-messages/compiler-errors-1/fatal-error-c1900.md)|Niezgodność Il między *""* *numer* *"* *i" wersją*"narzędzia|
|Błąd krytyczny C1901|Błąd wewnętrznego zarządzania pamięcią|
|[Błąd krytyczny C1902](../../error-messages/compiler-errors-1/fatal-error-c1902.md)|Niezgodność Menedżera bazy danych programu; Sprawdź instalację|
|[Błąd krytyczny C1903](fatal-error-c1903.md)|nie można odzyskać z poprzednich błędów; Zatrzymywanie kompilacji|
|[Błąd krytyczny C1904](fatal-error-c1904.md)|niewłaściwy sposób interakcji z dostawcą: "*plik*"|
|[Błąd krytyczny C1905](../../error-messages/compiler-errors-1/fatal-error-c1905.md)|Fronton i zaplecze nie są zgodne (muszą dotyczyć tego samego procesora).|

## <a name="see-also"></a>Zobacz także

[Błędy iC++ ostrzeżenia narzędzi języka C/kompilatora i kompilacji](../compiler-errors-1/c-cpp-build-errors.md)
