---
title: Błędy krytyczne kompilatora — od C999 do C1999
ms.date: 04/21/2019
f1_keywords:
- C1034
- C1036
- C1041
- C1048
- C1049
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
- C1049
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
ms.openlocfilehash: 5ffa1a2633877c8a16eb424f1ddc100bfd6142b8
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857394"
---
# <a name="compiler-fatal-errors-c999-through-c1999"></a>Błędy krytyczne kompilatora — od C999 do C1999

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez Microsoft C /C++ kompilatora.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Message|
|-----------|-------------|
|[Błąd krytyczny C999](../../error-messages/compiler-errors-1/fatal-error-c999.md)|Nieznany komunikat, wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|[Błąd krytyczny C1001](../../error-messages/compiler-errors-1/fatal-error-c1001.md)|Wystąpił błąd wewnętrzny w kompilatorze.<br /> (plik kompilatora '*pliku*", wiersz *numer*)<br /> Aby obejść ten problem, spróbuj uprościć lub zmienić program w pobliżu miejsc wymienionych powyżej. Wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
|[Błąd krytyczny C1002](../../error-messages/compiler-errors-1/fatal-error-c1002.md)|Kompilator nie ma miejsca na stercie w przebiegu 2|
|[Błąd krytyczny C1003](../../error-messages/compiler-errors-1/fatal-error-c1003.md)|Licznik błędów przekracza *numer*; zatrzymywanie kompilacji|
|[Błąd krytyczny C1004](../../error-messages/compiler-errors-1/fatal-error-c1004.md)|Nieoczekiwany koniec pliku znaleziono|
|[Błąd krytyczny C1005](../../error-messages/compiler-errors-1/fatal-error-c1005.md)|ciąg zbyt duże dla buforu|
|[Błąd krytyczny C1007](../../error-messages/compiler-errors-1/fatal-error-c1007.md)|Nierozpoznana flaga "*ciąg*"in"*opcji*"|
|[Błąd krytyczny C1008](../../error-messages/compiler-errors-1/fatal-error-c1008.md)|nie określono pliku wejściowego|
|[Błąd krytyczny C1009](../../error-messages/compiler-errors-1/fatal-error-c1009.md)|ograniczenie kompilatora: makra są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1010](../../error-messages/compiler-errors-1/fatal-error-c1010.md)|Nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego pliku nagłówkowego. Czy zapomniano dodać "#include \< *pliku*>" do źródła?|
|[Błąd krytyczny C1012](fatal-error-c1012.md)|niedopasowane nawiasy: brakuje "*znak*"|
|[Błąd krytyczny C1013](fatal-error-c1013.md)|ograniczenie kompilatora: zbyt wiele otwartych nawiasów|
|[Błąd krytyczny C1014](fatal-error-c1014.md)|zbyt wiele pliki dołączane: głębokość = *numer*|
|[Błąd krytyczny C1016](fatal-error-c1016.md)|ifndef #ifdef / # Oczekiwano identyfikatora|
|[Błąd krytyczny C1017](../../error-messages/compiler-errors-1/fatal-error-c1017.md)|Nieprawidłowa liczba całkowita stałego wyrażenia|
|[Błąd krytyczny C1018](fatal-error-c1018.md)|Nieoczekiwany #elif|
|[Błąd krytyczny C1019](fatal-error-c1019.md)|Nieoczekiwany #else|
|[Błąd krytyczny C1020](fatal-error-c1020.md)|Nieoczekiwany #endif|
|[Błąd krytyczny C1021](fatal-error-c1021.md)|Nieprawidłowe polecenie preprocesora "*ciąg*"|
|[Błąd krytyczny C1022](fatal-error-c1022.md)|Oczekiwano #endif|
|[Błąd krytyczny C1023](fatal-error-c1023.md)|"*pliku*": nieoczekiwany błąd w pch, spróbuj przebudować pch|
|[Błąd krytyczny C1026](../../error-messages/compiler-errors-1/fatal-error-c1026.md)|przepełnienie stosu analizatora składni, zbyt złożony program|
|[Błąd krytyczny C1033](../../error-messages/compiler-errors-1/fatal-error-c1033.md)|Nie można otworzyć bazy danych programu "*pliku*"|
|Błąd krytyczny C1034|*plik*: nie obejmuje ścieżek|
|[Błąd krytyczny C1035](fatal-error-c1035.md)|wyrażenie jest zbyt złożone; Uprość wyrażenie|
|Błąd krytyczny C1036|Nie można zastąpić wcześniej formatu programu bazy danych, Usuń "*pliku*' i skompiluj ponownie|
|[Błąd krytyczny C1037](fatal-error-c1037.md)|Nie można otworzyć pliku obiektu "*pliku*"|
|[Błąd krytyczny C1038](fatal-error-c1038.md)|ograniczenie kompilatora: '*funkcja*": zbyt złożone, stan przepływu sterowania; Uprość funkcję|
|Błąd krytyczny C1041|Nie można otworzyć bazy danych programu "*pliku*'; Jeśli wiele CL. Zapisywanie EXE w usłudze takie same. Plik PDB plików, użyj /FS|
|[Błąd krytyczny C1045](fatal-error-c1045.md)|ograniczenie kompilatora: powiązanie konsolidacji zagnieżdżono zbyt głęboko|
|[Błąd krytyczny C1046](../../error-messages/compiler-errors-1/fatal-error-c1046.md)|ograniczenie kompilatora: *struktury* są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1047](fatal-error-c1047.md)|Plik obiektu lub biblioteki "*pliku*' został utworzony za pomocą starszego kompilatora niż inne obiekty; obiekty stare ponownej kompilacji i biblioteki|
|Błąd krytyczny C1048|Nieznana opcja '*ciąg*"in"*opcji*"|
|Błąd krytyczny C1049|Nieprawidłowy argument numeryczny "*wartość*"|
|[Błąd krytyczny C1051](../../error-messages/compiler-errors-1/fatal-error-c1051.md)|plik bazy danych programu "*pliku*", ma przestarzały format, usuń go i ponownie skompilować|
|[Błąd krytyczny C1052](fatal-error-c1052.md)|plik bazy danych programu "*filename*", został wygenerowany przez konsolidator przy użyciu fastlink; kompilator nie może aktualizować takich plików PDB; usuń go lub użyj elementu /Fd w celu określenia innej nazwy pliku PDB|
|[Błąd krytyczny C1053](fatal-error-c1053.md)|"*funkcja*": funkcja zbyt duża|
|[Błąd krytyczny C1054](../../error-messages/compiler-errors-1/fatal-error-c1054.md)|ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko|
|[Błąd krytyczny C1055](../../error-messages/compiler-errors-1/fatal-error-c1055.md)|ograniczenie kompilatora: Brak kluczy|
|[Błąd krytyczny C1057](../../error-messages/compiler-errors-1/fatal-error-c1057.md)|Nieoczekiwany koniec pliku w rozwinięciu makra|
|[Błąd krytyczny C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)|Kompilator nie ma miejsca na stercie|
|[Błąd krytyczny C1061](../../error-messages/compiler-errors-1/fatal-error-c1061.md)|ograniczenie kompilatora: bloki są zagnieżdżone zbyt głęboko|
|Błąd krytyczny C1063|ograniczenie kompilatora: przepełnienie stosu kompilatora|
|[Błąd krytyczny C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)|ograniczenie kompilatora: token spowodował przepełnienie buforu wewnętrznego|
|[Błąd krytyczny C1065](../../error-messages/compiler-errors-1/fatal-error-c1065.md)|ograniczenie kompilatora: Brak tagów|
|[Błąd krytyczny C1067](../../error-messages/compiler-errors-1/fatal-error-c1067.md)|ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu|
|[Błąd krytyczny C1068](fatal-error-c1068.md)|Nie można otworzyć pliku "*pliku*"|
|Błąd krytyczny C1069|Nie można odczytać wiersza polecenia kompilatora|
|[Błąd krytyczny C1070](fatal-error-c1070.md)|Niezgodność #if / #endif pair w pliku "*pliku*"|
|[Błąd krytyczny C1071](../../error-messages/compiler-errors-1/fatal-error-c1071.md)|Nieoczekiwany koniec pliku w komentarzu|
|[Błąd krytyczny C1073](../../error-messages/compiler-errors-1/fatal-error-c1073.md)|Wewnętrzny błąd dotyczący kompilacji przyrostowej (plik kompilatora '*pliku*", wiersz *numer*)|
|[Błąd krytyczny C1074](fatal-error-c1074.md)|"IDB" jest niedozwolonym rozszerzeniem pliku PDB: *pliku*|
|[Błąd krytyczny C1075](../../error-messages/compiler-errors-1/fatal-error-c1075.md)|po lewej stronie *tokenu* został niedopasowane na końcu pliku|
|[Błąd krytyczny C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)|ograniczenie kompilatora: wewnętrzny limit sterty osiągnięty; Użyj/zm, aby określić wyższy limit|
|[Błąd krytyczny C1077](fatal-error-c1077.md)|ograniczenie kompilatora: nie może mieć więcej niż *numer* opcje wiersza polecenia|
|[Błąd krytyczny C1079](../../error-messages/compiler-errors-1/fatal-error-c1079.md)|ograniczenie kompilatora: Przekroczono limit rozmiaru pliku PCH|
|[Błąd krytyczny C1080](../../error-messages/compiler-errors-1/fatal-error-c1080.md)|ograniczenie kompilatora: opcja przekroczyła limit wiersza polecenia *numer* znaków|
|[Błąd krytyczny C1081](../../error-messages/compiler-errors-1/fatal-error-c1081.md)|"*pliku*": zbyt długa nazwa pliku|
|[Błąd krytyczny C1082](fatal-error-c1082.md)|Nie można zamknąć *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1083](../../error-messages/compiler-errors-1/fatal-error-c1083.md)|Nie można otworzyć *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1084](../../error-messages/compiler-errors-1/fatal-error-c1084.md)|Nie można odczytać *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1085](../../error-messages/compiler-errors-1/fatal-error-c1085.md)|Nie można zapisać *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1086](fatal-error-c1086.md)|Nie można wyszukać *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1087](fatal-error-c1087.md)|Nie można rozróżnić *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1088](fatal-error-c1088.md)|Nie można opróżnić *typu* pliku: "*pliku*": *wiadomości*|
|[Błąd krytyczny C1089](fatal-error-c1089.md)|Nie można obciąć *typu* pliku: "*pliku*": *wiadomości*|
|Błąd krytyczny C1090|Wywołanie PDB API nie powiodło się, kod błędu: "*kodu*": "*komunikat*"|
|[Błąd krytyczny C1091](fatal-error-c1091.md)|ograniczenie kompilatora: ciąg przekracza *numer* bajtów długości|
|[Błąd krytyczny C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)|Edytuj i Kontynuuj nie obsługuje zmiany typów danych; Tworzenie wymagane|
|[Błąd krytyczny C1093](../../error-messages/compiler-errors-1/fatal-error-c1093.md)|Wywołanie interfejsu API "*funkcja*"nie powiodło się"*HRESULT*": "*opis*"|
|[Błąd krytyczny C1094](../../error-messages/compiler-errors-1/fatal-error-c1094.md)|"-Zm*numer*": opcja wiersza polecenia jest niespójna z wartością używany do tworzenia prekompilowanego pliku nagłówkowego ("-Zm*numer*")|
|[Błąd krytyczny C1098](fatal-error-c1098.md)|Niezgodność wersji z silnikiem Edytuj i Kontynuuj|
|[Błąd krytyczny C1099](fatal-error-c1099.md)|Edytuj i Kontynuuj kończy kompilację aparatu|
|[Błąd krytyczny C1100](fatal-error-c1100.md)|Nie można zainicjować interfejsu OLE: *błąd*|
|Błąd krytyczny C1101|Nie można utworzyć uchwytu dla atrybutu "*identyfikator*"|
|Błąd krytyczny C1102|Nie można zainicjować: *błąd*|
|[Błąd krytyczny C1103](fatal-error-c1103.md)|krytyczny błąd importu progid: "*komunikat*"|
|[Błąd krytyczny C1104](fatal-error-c1104.md)|krytyczny błąd importu libid: "*komunikat*"|
|Błąd krytyczny C1105|*komunikat*: *błąd*|
|[Błąd krytyczny C1107](../../error-messages/compiler-errors-1/fatal-error-c1107.md)|Nie można odnaleźć zestawu "*zestawu*': Określ ścieżkę wyszukiwania zestawu za pomocą /AI lub przez ustawienie zmiennej środowiskowej LIBPATH|
|[Błąd krytyczny C1108](fatal-error-c1108.md)|Nie można odnaleźć biblioteki DLL: "*pliku*"|
|[Błąd krytyczny C1109](fatal-error-c1109.md)|Nie można odnaleźć '*symbol*"w pliku DLL"*pliku*"|
|Błąd krytyczny C1110|zbyt wiele zagnieżdżonych szablonów/ogólne definicji|
|Błąd krytyczny C1111|zbyt wiele parametrów szablonu/ogólne|
|Błąd krytyczny C1112|ograniczenie kompilatora: `'number`"zbyt wiele argumentów makra, tylko *numer* dozwolone|
|[Błąd krytyczny C1113](../../error-messages/compiler-errors-1/fatal-error-c1113.md)|#using nie powiodło się "*pliku*"|
|Błąd krytyczny C1114|"*pliku*": WinRT nie obsługuje #using dla zestawu zarządzanego|
|[Błąd krytyczny C1120](../../error-messages/compiler-errors-1/fatal-error-c1120.md)|Wywołanie funkcji GetProcAddress nie powiodło się dla "*funkcja*"|
|[Błąd krytyczny C1121](../../error-messages/compiler-errors-1/fatal-error-c1121.md)|Wywołanie CryptoAPI nie powiodło się|
|[Błąd krytyczny C1126](../../error-messages/compiler-errors-1/fatal-error-c1126.md)|Automatyczna alokacja przekracza *rozmiar*|
|[Błąd krytyczny C1128](../../error-messages/compiler-errors-1/fatal-error-c1128.md)|Liczba sekcji przekroczyła limit formatu pliku obiektowego: skompiluj z parametrem/bigobj|
|[Błąd krytyczny C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)|#error: *wiadomości*|
|[Błąd krytyczny C1190](fatal-error-c1190.md)|docelowy kod zarządzany wymaga "/ clr" opcja|
|[Błąd krytyczny C1191](../../error-messages/compiler-errors-1/fatal-error-c1191.md)|"*pliku*" mogą być importowane w zakresie globalnym|
|[Błąd krytyczny C1192](../../error-messages/compiler-errors-1/fatal-error-c1192.md)|#using nie powiodło się "*pliku*"|
|Błąd krytyczny C1193|Błąd w oczekiwany *pliku*(*wiersza*) nie został osiągnięty|
|Błąd krytyczny C1195|Korzystanie z /Yu i /Yc w tym samym wierszu polecenia jest niezgodne z opcją/CLR|
|[Błąd krytyczny C1196](fatal-error-c1196.md)|"*identyfikator*": identyfikator znaleziony w bibliotece typów "*typelib*" nie jest prawidłowym identyfikatorem języka C++|
|[Błąd krytyczny C1197](../../error-messages/compiler-errors-1/fatal-error-c1197.md)|nie może odwoływać się "*pliku*"as program istnieje już odwołanie do'*pliku*"|
|[Błąd krytyczny C1201](fatal-error-c1201.md)|Nie można kontynuować po błędzie składniowym w definicji szablonu klasy|
|[Błąd krytyczny C1202](fatal-error-c1202.md)|cyklicznego typu lub funkcji zależności kontekstu zbyt złożony|
|[Błąd krytyczny C1205](fatal-error-c1205.md)|Typy ogólne nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1206](fatal-error-c1206.md)|Dane dla domeny appdomain nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1207](fatal-error-c1207.md)|Zarządzane szablony nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1208](fatal-error-c1208.md)|Przydzielanie klas odwołujących na stosie nie jest obsługiwana przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1209](fatal-error-c1209.md)|Przyjazne zestawy nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1210](fatal-error-c1210.md)|/ CLR: pure i/CLR: Safe nie są obsługiwane przez wersję zainstalowanego środowiska uruchomieniowego|
|[Błąd krytyczny C1211](fatal-error-c1211.md)|Atrybut niestandardowy TypeForwardedTo nie jest obsługiwany przez wersję zainstalowanego środowiska uruchomieniowego|
|Błąd krytyczny C1300|Błąd podczas uzyskiwania dostępu do bazy danych programu *pliku* (*komunikat*)|
|Błąd krytyczny C1301|Błąd podczas uzyskiwania dostępu do bazy danych programu *pliku*, nieprawidłowe formatowanie, Usuń i ponownie skompiluj|
|Błąd krytyczny C1302|Brak danych profilowych dla modułu "*modułu*"w profilowej bazie danych"*pliku*"|
|[Błąd krytyczny C1305](../../error-messages/compiler-errors-1/fatal-error-c1305.md)|Baza danych profilu "*pliku*" jest przeznaczona dla innej architektury|
|Błąd krytyczny C1306|Ostatnia zmiana w bazie danych usługi profilu "*pliku*" nie była analizą optymalizacji; decyzje o optymalizacji mogą być nieaktualne|
|[Błąd krytyczny C1307](../../error-messages/compiler-errors-1/fatal-error-c1307.md)|Program został wyedytowany od czasu zebrania danych profilowych|
|[Błąd krytyczny C1308](../../error-messages/compiler-errors-1/fatal-error-c1308.md)|*plik*: łączenie zestawów nie jest obsługiwana.|
|[Błąd krytyczny C1309](../../error-messages/compiler-errors-1/fatal-error-c1309.md)|Niezgodność wersji C2. Biblioteki DLL i pgodb*ver*. BIBLIOTEKI DLL|
|[Błąd krytyczny C1310](fatal-error-c1310.md)|Optymalizacje profilowe z przewodnikiem nie są dostępne z OpenMP|
|[Błąd krytyczny C1311](../../error-messages/compiler-errors-1/fatal-error-c1311.md)|COFF format statycznie nie może zainicjować "*symbol*" za pomocą *numer* bajtem(ów) adresu|
|[Błąd krytyczny C1312](fatal-error-c1312.md)|Zbyt wiele warunkowych gałęzi w funkcji.  Uprość lub zrefaktoryzuj kod źródłowy.|
|[Błąd krytyczny C1313](../../error-messages/compiler-errors-1/fatal-error-c1313.md)|ograniczenie kompilatora: *typu* bloki nie mogą być zagnieżdżone głębiej niż *numer* poziomy|
|[Błąd krytyczny C1350](../../error-messages/compiler-errors-1/fatal-error-c1350.md)|Wystąpił błąd podczas ładowania biblioteki dll "*pliku*": nie można odnaleźć biblioteki dll|
|[Błąd krytyczny C1351](../../error-messages/compiler-errors-1/fatal-error-c1351.md)|Wystąpił błąd podczas ładowania biblioteki dll "*pliku*": niezgodność wersji|
|[Błąd krytyczny C1352](fatal-error-c1352.md)|Nieprawidłowe lub uszkodzone MSIL w funkcji "*funkcja*"z modułu"*modułu*"|
|[Błąd krytyczny C1353](fatal-error-c1353.md)|Operacja metadanych nie powiodła się: środowisko uruchomieniowe nie jest zainstalowane lub niezgodność wersji|
|[Błąd krytyczny C1382](../../error-messages/compiler-errors-1/fatal-error-c1382.md)|Plik PCH "*pliku*"został przebudowany od"*obj*" został wygenerowany. Przebuduj ten obiekt|
|[Błąd krytyczny C1383](fatal-error-c1383.md)|— Opcja kompilatora /GL jest niezgodna z zainstalowaną wersją środowiska uruchomieniowego języka wspólnego|
|Błąd krytyczny C1384|Nieprawidłowe ustawienie dla PGO_PATH_TRANSLATION podczas łączenia "*pliku*"|
|Błąd krytyczny C1451|Nie można wygenerować informacji debugowania podczas kompilacji wykresu wywołań dla concurrency::parallel_for_each: "*miejsca wywołania*"|
|Błąd krytyczny C1505|Błąd w horyzoncie analizatora nieodwracalny|
|[Błąd krytyczny C1506](../../error-messages/compiler-errors-1/fatal-error-c1506.md)|Błąd w zakresie bloku nieodwracalny|
|[Błąd krytyczny C1508](fatal-error-c1508.md)|ograniczenie kompilatora: '*funkcja*": więcej niż 65 535 bajtów argumentu|
|[Błąd krytyczny C1509](../../error-messages/compiler-errors-1/fatal-error-c1509.md)|ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "*funkcja*"; Uprość funkcję|
|[Błąd krytyczny C1510](../../error-messages/compiler-errors-1/fatal-error-c1510.md)|Nie można otworzyć zasobu językowego clui.dll|
|[Błąd krytyczny C1601](../../error-messages/compiler-errors-1/fatal-error-c1601.md)|Nieobsługiwany wbudowany zestaw opcode|
|[Błąd krytyczny C1602](../../error-messages/compiler-errors-1/fatal-error-c1602.md)|nieobsługiwane wewnętrzne|
|[Błąd krytyczny C1603](../../error-messages/compiler-errors-1/fatal-error-c1603.md)|cel rozgałęzienia zestawu wbudowanego poza zakresem, *numer* bajtów|
|[Błąd krytyczny C1852](fatal-error-c1852.md)|"*pliku*" nie jest prawidłowym prekompilowanym plikiem nagłówkowym|
|[Błąd krytyczny C1853](../../error-messages/compiler-errors-1/fatal-error-c1853.md)|"*pliku*" prekompilowanego pliku nagłówkowego pochodzi z poprzedniej wersji kompilatora lub prekompilowany plik nagłówkowy jest w języku C++ i używania go z C (lub odwrotnie)|
|[Błąd krytyczny C1854](../../error-messages/compiler-errors-1/fatal-error-c1854.md)|Nie można zastąpić informacji utworzonej podczas tworzenia prekompilowanego pliku nagłówkowego w pliku obiektu: "*pliku*"|
|[Błąd krytyczny C1900](../../error-messages/compiler-errors-1/fatal-error-c1900.md)|Niezgodność IL między "*narzędzie*"version"*numer*"i"*narzędzie*"version"*numer*"|
|Błąd krytyczny C1901|Błąd wewnętrzny zarządzania pamięcią|
|[Błąd krytyczny C1902](../../error-messages/compiler-errors-1/fatal-error-c1902.md)|Niezgodność Menedżera bazy danych programu; Sprawdź instalację|
|[Błąd krytyczny C1903](fatal-error-c1903.md)|Nie można odzyskać od poprzedniego błędu(ów); zatrzymywanie kompilacji|
|[Błąd krytyczny C1904](fatal-error-c1904.md)|Zły dostawca interakcji: "*pliku*"|
|[Błąd krytyczny C1905](../../error-messages/compiler-errors-1/fatal-error-c1905.md)|Frontonu i zaplecza nie jest zgodne (muszą wskazywać tego samego procesora).|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md)
