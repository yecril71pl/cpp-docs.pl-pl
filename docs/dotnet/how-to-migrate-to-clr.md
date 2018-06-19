---
title: 'Porady: Migracja do środowiska clr-| Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5d7dafdc377723e33372529af1b8f125561366e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138443"
---
# <a name="how-to-migrate-to-clr"></a>Porady: migracja do /clr
W tym temacie opisano problemy, które wystąpić podczas kompilowania kodu natywnego z **/CLR** (zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji). **/ CLR** umożliwia moduł Visual C++ do wywołania i można wywołać z zestawów platformy .NET, zachowując zgodność z modułami niezarządzane. Zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) i [natywne i .NET współdziałanie](../dotnet/native-and-dotnet-interoperability.md) uzyskać więcej informacji o zaletach kompilowania przy użyciu **/CLR**.  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>Znane problemy dotyczące kompilowania projektów bibliotek z/CLR  
 Visual Studio zawiera niektóre znane problemy występujące podczas kompilowania projektów bibliotek z **/CLR**:  
  
-   Kod może zapytania typów w czasie wykonywania z [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Jednak jeśli typ znajduje się w dll MSIL (skompilowane z **/CLR**), wywołanie `FromName` może zakończyć się niepowodzeniem, jeśli występuje przed uruchomieniem konstruktora statycznego w zarządzanej biblioteki dll (nie będzie mógł przeglądać ten problem wywołania nazwa od sytuacji po kodu wykonane w zarządzanej biblioteki dll). Aby obejść ten problem, możesz wymusić konstrukcji zarządzanych Konstruktor statyczny zdefiniować funkcję w zarządzanej biblioteki dll, eksportowanie go i wywoływanie go z aplikacji natywnej MFC. Na przykład:  
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>Kompiluj z użyciem języka Visual C++  
 Przed użyciem **/CLR** na module w projekcie, należy najpierw skompilować i połącz natywnego projektu za pomocą programu Visual Studio 2010.  
  
 Następujące kroki, a następnie w kolejności, podaj ścieżkę najłatwiejsza do **/CLR** kompilacji. Jest ważne skompilować i uruchomić projekt po wykonaniu tych kroków.  
  
### <a name="versions-prior-to-visual-c-2003"></a>Wersje starsze niż program Visual C++ 2003  
 Jeśli uaktualniasz programu Visual Studio 2010 z wersji przed Visual C++ 2003, mogą zostać wyświetlone błędy kompilatora związane z rozszerzoną zgodność standard C++ w programie Visual C++ 2003  
  
### <a name="upgrading-from-visual-c-2003"></a>Uaktualnianie z programu Visual C++ 2003  
 Projekty poprzedniej skompilowanej za pomocą programu Visual C++ 2003 również najpierw ma być kompilowana bez **/CLR** jak Visual Studio teraz wzrosło zgodność ANSI/ISO i niektóre fundamentalne zmiany. Jest zmiany mogą wymagać uwagi najbardziej [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md). Kod, który używa CRT jest bardzo prawdopodobne wygenerowało ostrzeżenia dotyczące zaniechania. Ostrzeżenia mogą być pomijane, ale migracja do nowego [Security-Enhanced wersji CRT funkcji](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) jest preferowana, jak zapewnić większe bezpieczeństwo i może ujawnić problemy z zabezpieczeniami w kodzie.  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>Uaktualnianie wersji Managed Extensions for C++  
 Począwszy od programu Visual Studio 2005, w obszarze nie skompilować kod napisany za pomocą rozszerzeń zarządzanych dla języka C++ **/CLR**.  
  
## <a name="convert-c-code-to-c"></a>Konwertuj kod w języku C języka c++  
 Mimo że program Visual Studio będzie Kompiluj pliki C, konieczne jest ich konwersja na C++ dla **/CLR** kompilacji. Nazwa pliku nie ma zostać zmienione; można użyć **/Tp** (zobacz [/TC, / TP, / TC, /TP (Określ źródłowy plik typ)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Należy pamiętać, że chociaż plików kodu źródłowego języka C++ są wymagane dla **/CLR**, nie jest konieczne ponowne współczynnika kod, aby używał zorientowane obiektowo wzorcami.  
  
 Kod w języku C jest bardzo prawdopodobne wymagające zmiany, gdy kompilowany jako plik C++. Zabezpieczenie typów reguł C++ są strict, więc konwersje typów musi być jawnie z rzutowania. Na przykład — funkcja malloc zwraca wskaźnik void, ale można przypisać do wskaźnika do dowolnego typu w języku C rzutowanie:  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 Wskaźniki funkcji również są ściśle bezpieczne w języku C++, więc poniższy kod C wymaga modyfikacji. W języku C++ najlepiej utworzyć `typedef` definiuje typ wskaźnika funkcji, a następnie użyć tego typu można rzutować wskaźników funkcji:  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C++ wymaga również, czy funkcje być prototypowana lub całkowicie zdefiniowane przed ich odwołuje się do lub wywołany.  
  
 Identyfikatory używane w kodzie C, które były słowa kluczowe języka C++ (takich jak `virtual`, `new`, `delete`, `bool`, `true`, `false`, itd.) musi zostać zmieniona. Ogólnie można to zrobić z prostych operacji wyszukiwania i zamieniania.  
  
 Na koniec wywołania modelu COM w stylu języka C wymaga jawnego korzystania z tabeli v i `this` wskaźnika, C++ nie obsługuje:  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>Ponownie skonfiguruj ustawienia projektu  
 Po projektu kompiluje i uruchamia w Visual Studio 2010 należy utworzyć nowe konfiguracje projektu dla **/CLR** zamiast modyfikowania konfiguracji domyślnej. **/ CLR** jest niezgodny z niektórych opcji kompilatora i tworzenie oddzielne konfiguracje umożliwia skompilowanie projektu jako macierzysty lub zarządzany. Gdy **/CLR** jest zaznaczona w oknie dialogowym właściwości strony, nie jest zgodne z ustawieniami projektu **/CLR** są wyłączone (i wyłączone opcje nie są automatycznie przywracane **/CLR** jest następnie zaznaczona).  
  
### <a name="create-new-project-configurations"></a>Utwórz nowe konfiguracje projektu  
 Można użyć **Kopiuj ustawienia z** opcji [nowe okno dialogowe konfiguracji projektu](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) do utworzenia konfiguracji projektu na podstawie istniejących ustawień projektu. W tym raz dla konfiguracji debugowania i raz dla wersji konfiguracji. Następnie można zastosować kolejne zmiany do **/CLR** -określonej konfiguracji, pozostawiając bez zmian oryginalnej konfiguracji projektu.  
  
 Użyć reguły niestandardowej kompilacji projektów mogą wymagać uwagi dodatkowe.  
  
 Ten krok ma wpływ różnych projektów, które używają pliki reguł programu make. W takim przypadku można skonfigurować oddzielne docelowy kompilacji lub właściwe dla wersji **/CLR** kompilacji mogą być tworzone z kopię oryginału.  
  
### <a name="change-project-settings"></a>Zmień ustawienia projektu  
 **/ CLR** można wybrać w środowisku programistycznym, zgodnie z instrukcjami w [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md). Jak wspomniano wcześniej, ten krok zostanie automatycznie wyłączyć sprzeczne ustawienia projektu.  
  
> [!NOTE]
>  Podczas uaktualniania zarządzane biblioteki lub projekt usługi sieci web Visual C++ 2003, **/Zl** kompilatora opcja zostanie dodany do **wiersza polecenia** strony właściwości. Spowoduje to LNK2001. Usuń **/Zl** z **wiersza polecenia** strony właściwości do rozpoznania. Zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) i [Praca z właściwościami projektu](../ide/working-with-project-properties.md) Aby uzyskać więcej informacji. Lub Dodaj do konsolidatora msvcrt.lib i msvcmrt.lib **dodatkowe zależności** właściwości.  
  
 Dla projektów z pliki reguł programu make, opcje kompilatora niezgodne musi być wyłączona ręcznie raz **/CLR** został dodany. Zobacz /[/CLR ograniczenia](../build/reference/clr-restrictions.md) informacji o opcjach kompilatora, które nie są zgodne z **/CLR**.  
  
### <a name="precompiled-headers"></a>Prekompilowane nagłówki  
 Prekompilowane nagłówki są obsługiwane w obszarze **/CLR**. Jednak jeśli tylko kompilowania niektóre pliki CPP z **/CLR** (kompilowanie pozostałych jako natywną) pewne zmiany będzie wymagane, ponieważ prekompilowane nagłówki wygenerowane z **/CLR** nie są zgodne z identyfikatorami wygenerowany bez **/CLR**. Jest to niezgodność wynika z faktu, że **/CLR** generuje i wymaga metadanych. Moduły skompilowane **/CLR** w związku z tym nie można użyć polecenia prekompilowane nagłówki, które nie zawierają metadanych i z systemem innym niż **/CLR** modułów nie można użyć pliki prekompilowanego nagłówka, które zawierają metadane.  
  
 Najprostszym sposobem, aby skompilować projekt, w której niektóre moduły są kompilowane **/CLR** jest całkowicie wyłączyć prekompilowanych nagłówków. (W oknie dialogowym stron właściwości projektu, otwórz węzeł C/C++ i wybierz prekompilowanych nagłówków. Następnie zmienić właściwości użycia tworzenie prekompilowanych nagłówków do "Nie przy użyciu prekompilowanych nagłówków").  
  
 Szczególnie w przypadku dużych projektów prekompilowanych nagłówków zapewnia jednak znacznie lepszą szybkości kompilacji, dlatego wyłączenie tej funkcji nie jest pożądane. W takim przypadku warto skonfigurować **/CLR** i **/CLR** pliki używane osobne prekompilowanych nagłówków. Można to zrobić w jednym kroku przez wybierania wielu modułów, które ma być kompilowana **/CLR** za pomocą Eksploratora rozwiązań, klikając prawym przyciskiem myszy w grupie i wybierając polecenie Właściwości. Następnie zmienić właściwości zarówno Utwórz/Użyj PCH za pośrednictwem plików, jak i prekompilowany plik nagłówka do korzystania z inną nazwę pliku i plik PCH odpowiednio.  
  
## <a name="fixing-errors"></a>Rozwiązywanie problemów  
 Kompilowanie przy użyciu **/CLR** może spowodować błędy kompilatora, konsolidatora lub runtime. W tej sekcji omówiono najczęściej występujących problemów.  
  
### <a name="metadata-merge"></a>Scalanie metadanych  
 Różne wersje typów danych może spowodować konsolidator, aby zakończyć się niepowodzeniem, ponieważ metadane wygenerowany dla dwóch typów nie jest zgodny. (Jest to zazwyczaj spowodowane elementów członkowskich typu warunkowo są zdefiniowane, ale warunki nie są takie same dla wszystkich plikach CPP o typie.) W takim przypadku konsolidator kończy się niepowodzeniem, raportowania tylko nazwa symbolu i nazwę drugiego pliku OBJ, których typ został zdefiniowany. Często jest to przydatne zmienić kolejność, że pliki OBJ są wysyłane do konsolidatora do odnalezienia lokalizacji innych wersji typu danych.  
  
### <a name="loader-lock-deadlock"></a>Zakleszczenie blokady modułu ładującego  
 W programie Visual Studio 2010 lub nowszy, "zakleszczenie blokady modułu ładującego" można nadal występują jako w starszych wersjach, ale jest deterministyczna, a wykryto i zgłaszanych w czasie wykonywania. Zobacz [inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md) dla tła szczegółowe, wskazówki i rozwiązania.  
  
### <a name="data-exports"></a>Eksportowanie danych  
 Eksportowanie danych biblioteki DLL jest podatne na błędy i nie jest zalecane. Jest to spowodowane sekcji danych biblioteki DLL nie jest gwarantowana do zainicjowania wykonano część zarządzanej biblioteki DLL. Odwołuj się do metadanych z [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).  
  
### <a name="type-visibility"></a>Widoczność typów  
 Typy natywne są domyślnie prywatne. Może to spowodować typ macierzysty nie jest widoczny spoza biblioteki DLL. Rozwiązać ten problem, dodając `public` do tych typów.  
  
### <a name="floating-point-and-alignment-issues"></a>Liczby zmiennoprzecinkowe punktu i problemy wyrównania  
 `__controlfp` nie jest obsługiwana na środowisko uruchomieniowe języka wspólnego (zobacz [_control87 —, _controlfp —, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) Aby uzyskać więcej informacji). Środowisko CLR będzie również nie przestrzega [Dopasuj](../cpp/align-cpp.md).  
  
### <a name="com-initialization"></a>Zainicjowanie modelu COM  
 Środowisko uruchomieniowe języka wspólnego inicjuje automatycznie COM, podczas inicjowania modułu (gdy COM jest inicjowany automatycznie wystąpiło to jako MTA). W związku z tym jawnie inicjowanie COM daje kody powrotu, wskazujący, że COM jest już zainicjowany. Podjęto próbę jawnie zainicjować modelu COM o jeden model wątkowości, gdy CLR już zainicjowany COM do innego modelu wątkowości może spowodować awarię aplikacji.  
  
 Środowisko uruchomieniowe języka wspólnego uruchamia COM jako MTA domyślnie; Użyj [/CLRTHREADATTRIBUTE (Ustaw CLR wątku atrybut)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) Aby zmodyfikować to ustawienie.  
  
### <a name="performance-issues"></a>Problemy z wydajnością  
 Mogą być widoczne obniżenie wydajności wygenerowane do MSIL metod natywnych języka C++ są wywoływane pośrednio (wywołania funkcji wirtualnej lub przy użyciu wskaźników funkcji). Aby dowiedzieć się więcej na ten temat, zobacz [podwójna konwersja bitowa adresów](../dotnet/double-thunking-cpp.md).  
  
 Podczas przenoszenia z natywnego na MSIL, można zauważyć wzrost rozmiaru zestawu roboczego. Jest to spowodowane środowisko uruchomieniowe języka wspólnego oferują wiele funkcji, aby upewnić się, że programy działać poprawnie. Jeśli Twoje **/CLR** aplikacja nie działa prawidłowo, można włączyć C4793 (domyślnie wyłączone), zobacz [ostrzeżenie kompilatora (poziom 1 i 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) Aby uzyskać więcej informacji.  
  
### <a name="program-crashes-on-shutdown"></a>Program awarii podczas zamykania  
 W niektórych przypadkach CLR można zamknięcia przed zakończeniem kodu zarządzanego uruchomiona. Przy użyciu `std::set_terminate` i `SIGTERM` może to spowodować. Zobacz [sygnał — stałe](../c-runtime-library/signal-constants.md) i [set_terminate —](../c-runtime-library/abnormal-termination.md) Aby uzyskać więcej informacji.  
  
## <a name="using-new-visual-c-features"></a>Korzystać z nowych funkcji programu Visual C++  
 Po kompiluje aplikacji, łączy i działa, możesz rozpocząć korzystanie z funkcji .NET w module skompilowanym z **/CLR**. Aby uzyskać więcej informacji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).  
  
 Jeśli używasz rozszerzeń zarządzanych dla języka C++, możesz przekonwertować kod, aby używał nowej składni. Aby uzyskać szczegółowe informacje o konwersji rozszerzeń zarządzanych dla języka C++, zobacz [C + +/ CLI migracji Elementarz](../dotnet/cpp-cli-migration-primer.md).  
  
 Aby uzyskać informacje na temat programowania w języku Visual C++ .NET, zobacz:  
  
-   [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)