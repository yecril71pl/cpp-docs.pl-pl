---
title: 'Instrukcje: Migracja do -clr'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 0c21fe585049ebce6383c5d8f673704e7362cd72
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225699"
---
# <a name="how-to-migrate-to-clr"></a>Porady: migracja do /clr

W tym temacie omówiono problemy, które powstają podczas kompilowania kodu natywnego z **/CLR** (zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md) , aby uzyskać więcej informacji. **/CLR** umożliwia natywny kod c++ wywoływany i wywoływany z zestawów .net oprócz innych natywnego kodu c++. Zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) oraz [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md) , aby uzyskać więcej informacji na temat zalet kompilacji z **/CLR**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Znane problemy podczas kompilowania projektów biblioteki z/CLR

Program Visual Studio zawiera znane problemy podczas kompilowania projektów biblioteki z **/CLR**:

- Kod może badać typy w czasie wykonywania za pomocą [CRuntimeClass:: from](../mfc/reference/cruntimeclass-structure.md#fromname). Jeśli jednak typ znajduje się w pliku MSIL. dll (skompilowane z **/CLR**), wywołanie `FromName` może zakończyć się niepowodzeniem, jeśli występuje przed uruchomieniem konstruktorów statycznych w zarządzanej bibliotece DLL (ten problem nie będzie wyświetlany, jeśli wywołanie from ma miejsce po wykonaniu kodu w zarządzanym pliku dll). Aby obejść ten problem, można wymusić konstruowanie zarządzanego konstruktora statycznego, definiując funkcję w zarządzanej bibliotece DLL, eksportując ją i wywołując ją z natywnej aplikacji MFC. Na przykład:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompiluj z Visual C++

Przed użyciem opcji **/CLR** na dowolnym module w projekcie należy najpierw skompilować i połączyć swój projekt macierzysty z programem Visual Studio 2010.

Wykonaj następujące czynności, a następnie podaj najłatwą ścieżkę do kompilacji **/CLR** . Ważne jest, aby skompilować i uruchomić projekt po każdym z tych kroków.

### <a name="versions-prior-to-visual-studio-2003"></a>Wersje wcześniejsze niż program Visual Studio 2003

W przypadku uaktualniania do programu Visual Studio 2010 z wersji wcześniejszej niż Visual Studio 2003 można zobaczyć błędy kompilatora związane z rozszerzoną zgodnością standardu C++ w programie Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Uaktualnianie z programu Visual Studio 2003

Projekty utworzone wcześniej z programem Visual Studio 2003 powinny również być kompilowane bez **/CLR** , ponieważ program Visual Studio ma teraz zwiększoną zgodność ANSI/ISO i pewne istotne zmiany. Zmiana, która prawdopodobnie wymaga najwyższej uwagi, to [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md). Kod, który korzysta z CRT, prawdopodobnie wygenerował ostrzeżenia o wycofaniu. Te ostrzeżenia można pominąć, ale jest to preferowane przeprowadzenie migracji do nowych, [ulepszonych pod względem zabezpieczeń wersji funkcji CRT](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) , ponieważ zapewniają one lepsze zabezpieczenia i mogą ujawniać problemy z zabezpieczeniami w kodzie.

### <a name="upgrading-from-managed-extensions-for-c"></a>Uaktualnianie z Managed Extensions for C++

Począwszy od programu Visual Studio 2005, kod zapisany z Managed Extensions for C++ nie zostanie skompilowany w obszarze **/CLR**.

## <a name="convert-c-code-to-c"></a>Konwertuj kod C na język C++

Mimo że program Visual Studio kompiluje pliki C, konieczne jest ich przekonwertowanie do języka C++ w przypadku kompilacji **/CLR** . Nie trzeba zmieniać rzeczywistej nazwy pliku; można użyć **/TP** (zobacz [/TC,/TP,/TC,/TP (Określ typ pliku źródłowego)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md). Należy pamiętać, że chociaż pliki kodu źródłowego C++ są wymagane dla opcji **/CLR**, nie jest konieczne ponowne użycie kodu w celu użycia modelowania zorientowanego obiektowo.

Kod języka C jest bardzo prawdopodobnie wymagał zmian w przypadku skompilowania go jako pliku C++. Reguły bezpieczeństwa typów języka C++ są ścisłe, dlatego konwersje typów muszą być jawnie wykonane z rzutowania. Na przykład funkcja malloc zwraca wskaźnik void, ale może być przypisana do wskaźnika do dowolnego typu w C z rzutem:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Wskaźniki funkcji są również ściśle bezpieczne w języku C++, więc Poniższy kod C wymaga modyfikacji. W języku C++ najlepiej utworzyć element, **`typedef`** który definiuje typ wskaźnika funkcji, a następnie użyć tego typu do rzutowania wskaźników funkcji:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

Język C++ wymaga również, aby funkcje były prototypowe lub w pełni zdefiniowane, zanim będą mogły zostać przywoływane lub wywołane.

Identyfikatory używane w kodzie C, które mają być słowami kluczowymi w języku C++ (takie jak,,,, **`virtual`** **`new`** **`delete`** **`bool`** **`true`** **`false`** itp.), należy zmienić nazwę. Zwykle można to zrobić przy użyciu prostych operacji wyszukiwania i zamieniania.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Skonfiguruj ponownie ustawienia projektu

Po skompilowaniu i uruchomieniu projektu w programie Visual Studio 2010 należy utworzyć nowe konfiguracje projektu dla **/CLR** zamiast modyfikować konfiguracje domyślne. **/CLR** jest niezgodna z opcjami kompilatora i Tworzenie oddzielnych konfiguracji umożliwia skompilowanie projektu jako natywnego lub zarządzanego. Gdy opcja **/CLR** jest zaznaczona w oknie dialogowym strony właściwości, ustawienia projektu niezgodne z **/CLR** są wyłączone (i wyłączone opcje nie są automatycznie przywracane, jeśli nie wybrano opcji **/CLR** ).

### <a name="create-new-project-configurations"></a>Utwórz nowe konfiguracje projektu

Możesz użyć opcji **Kopiuj ustawienia z z** w oknie **dialogowym Nowa konfiguracja projektu** (**kompilacja**,  >  **Configuration Manager**  >  Nowa**Konfiguracja rozwiązania**  >  **New**), aby utworzyć konfigurację projektu na podstawie istniejących ustawień projektu. Wykonaj tę czynność raz, aby przeprowadzić konfigurację debugowania i jeden raz dla konfiguracji wydania. Kolejne zmiany można następnie zastosować tylko do konfiguracji specyficznych dla programu **/CLR** , pozostawiając oryginalne konfiguracje projektu bez zmian.

Projekty używające niestandardowych reguł kompilacji mogą wymagać dodatkowej uwagi.

Ten krok ma inne konsekwencje dla projektów używających plików reguł programu make. W takim przypadku można skonfigurować oddzielny obiekt docelowy kompilacji lub można utworzyć wersję z **opcją/CLR** dla kompilacji z kopii oryginalnej.

### <a name="change-project-settings"></a>Zmień ustawienia projektu

**/CLR** można wybrać w środowisku programistycznym, wykonując instrukcje w [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md). Jak wspomniano wcześniej, ten krok spowoduje automatyczne wyłączenie ustawień projektu powodujących konflikt.

> [!NOTE]
> Podczas uaktualniania biblioteki zarządzanej lub projektu usługi sieci Web z programu Visual Studio 2003 opcja kompilatora **/zl** zostanie dodana do strony właściwości **wiersza polecenia** . Spowoduje to LNK2001. Usuń **/zl** z strony właściwości **wiersza polecenia** , aby rozwiązać ten problem. Zobacz [/zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) i [Ustaw właściwości kompilatora i Build](../build/working-with-project-properties.md) , aby uzyskać więcej informacji. Lub Dodaj msvcrt. lib i msvcmrt. lib do właściwości **dodatkowe zależności** konsolidatora.

W przypadku projektów utworzonych przy użyciu plików reguł programu make niezgodne opcje kompilatora muszą być wyłączone ręcznie po dodaniu **/CLR** . Aby uzyskać informacje na temat opcji kompilatora, które nie są zgodne z **/CLR**, zobacz/[/CLR](../build/reference/clr-restrictions.md) .

### <a name="precompiled-headers"></a>Wstępnie skompilowane nagłówki

Wstępnie skompilowane nagłówki są obsługiwane w opcji **/CLR**. Jednak w przypadku kompilowania tylko niektórych plików CPP z **/CLR** (kompilacja reszty jako natywny) pewne zmiany będą wymagane, ponieważ prekompilowane nagłówki generowane z **/CLR** nie są zgodne z tymi wygenerowanymi bez **/CLR**. Niezgodność wynika z faktu, że **/CLR** generuje i wymaga metadanych. Z tego powodu skompilowane moduły **/CLR** nie mogą używać prekompilowanych nagłówków, które nie zawierają metadanych, a moduły niebędące **nie/CLR** nie mogą używać prekompilowanych plików nagłówkowych, które zawierają meta dane.

Najprostszym sposobem kompilowania projektu, w którym zostały skompilowane niektóre moduły **/CLR** jest wyłączenie prekompilowanych nagłówków. (W oknie dialogowym strony właściwości projektu Otwórz węzeł C/C++ i wybierz opcję prekompilowane nagłówki. Następnie zmień właściwość Utwórz/Użyj prekompilowanych nagłówków na "nie używa prekompilowanych nagłówków".)

Jednak szczególnie w przypadku dużych projektów prekompilowane nagłówki zapewniają znacznie lepszą szybkość kompilacji, więc wyłączenie tej funkcji nie jest pożądane. W tym przypadku najlepszym rozwiązaniem jest skonfigurowanie plików **/CLR** i **nie/CLR** w celu użycia oddzielnych prekompilowanych nagłówków. Można to zrobić w jednym kroku przez wybór wielu modułów do skompilowania **/CLR** przy użyciu **Eksplorator rozwiązań**, kliknięcie prawym przyciskiem myszy grupy i wybranie właściwości. Następnie zmień właściwości plik PCH/use za pomocą pliku i prekompilowanego pliku nagłówkowego w taki sposób, aby używały odpowiednio innej nazwy pliku nagłówka i pliku PCH.

## <a name="fixing-errors"></a>Poprawianie błędów

Kompilowanie z **/CLR** może spowodować błędy kompilatora, konsolidatora lub czasu wykonania. W tej sekcji omówiono najczęstsze problemy.

### <a name="metadata-merge"></a>Scalanie metadanych

Różne wersje typów danych mogą spowodować niepowodzenie konsolidatora, ponieważ metadane generowane dla dwóch typów nie są zgodne. (Zwykle jest to spowodowane tym, że elementy członkowskie typu są definiowane warunkowo, ale warunki te nie są takie same dla wszystkich plików CPP, które używają typu). W takim przypadku konsolidator nie powiedzie się, zgłasza tylko nazwę symbolu i nazwę drugiego pliku OBJ, w którym typ został zdefiniowany. Często warto obrócić zamówienie, że pliki OBJ są wysyłane do konsolidatora, aby odnaleźć lokalizację innej wersji typu danych.

### <a name="loader-lock-deadlock"></a>Zakleszczenie blokady modułu ładującego

Może wystąpić "zakleszczenie blokady modułu ładującego", ale jest to deterministyczne i jest wykrywane i raportowane w czasie wykonywania. Zobacz [Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md) , aby uzyskać szczegółowe informacje, wskazówki i rozwiązania.

### <a name="data-exports"></a>Eksportowanie danych

Eksportowanie danych DLL jest podatne na błędy i nie jest zalecane. Wynika to z faktu, że sekcja danych biblioteki DLL nie zostanie zainicjowana do momentu wykonania pewnej zarządzanej części biblioteki DLL. Odwołuj się do metadanych przy użyciu [dyrektywy #using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Widoczność typów

Typy natywne są domyślnie prywatne. Może to spowodować, że typ natywny nie jest widoczny poza biblioteką DLL. Usuń ten błąd, dodając **`public`** do tych typów.

### <a name="floating-point-and-alignment-issues"></a>Problemy dotyczące zmiennoprzecinkowych i wyrównania

`__controlfp`nie jest obsługiwany w środowisku uruchomieniowym języka wspólnego (zobacz [_control87, _controlfp, \_ _control87_2,](../c-runtime-library/reference/control87-controlfp-control87-2.md) Aby uzyskać więcej informacji). Środowisko CLR również nie będzie uwzględniać [wyrównania](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicjowanie modelu COM

Środowisko uruchomieniowe języka wspólnego inicjuje COM automatycznie po zainicjowaniu modułu (gdy COM jest inicjowany automatycznie, robi to jako MTA). W związku z tym Jawne inicjowanie modelu COM daje kody powrotne wskazujące, że COM jest już zainicjowany. Próba jawnego zainicjowania modelu COM z jednym modelem wątkowości, gdy środowisko CLR zostało już zainicjowane przez model COM w innym modelu wątków, może spowodować niepowodzenie aplikacji.

Środowisko uruchomieniowe języka wspólnego domyślnie uruchamia model COM jako MTA; Użyj [/CLRTHREADATTRIBUTE (ustaw atrybut wątku CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) , aby go zmodyfikować.

### <a name="performance-issues"></a>Problemy z wydajnością

Obniżenie wydajności może wystąpić, gdy natywne metody języka C++ wygenerowane dla MSIL są nazywane pośrednio (wywołaniami funkcji wirtualnych lub przy użyciu wskaźników funkcji). Aby dowiedzieć się więcej na ten temat, zobacz [Double podwójna](../dotnet/double-thunking-cpp.md).

Podczas przechodzenia z natywnego do MSIL można zauważyć zwiększenie rozmiaru zestawu roboczego. Wynika to z faktu, że środowisko uruchomieniowe języka wspólnego udostępnia wiele funkcji, aby upewnić się, że programy działają poprawnie. Jeśli aplikacja **/CLR** nie działa prawidłowo, możesz włączyć C4793 (domyślnie wyłączone), aby uzyskać więcej informacji, zobacz [Ostrzeżenie kompilatora (poziom 1 i 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) .

### <a name="program-crashes-on-shutdown"></a>Awaria programu po zamknięciu

W niektórych przypadkach środowisko CLR można zamknąć przed zakończeniem działania kodu zarządzanego. Korzystanie z `std::set_terminate` i `SIGTERM` może to spowodować. Aby uzyskać więcej informacji, zobacz [stałe sygnałów](../c-runtime-library/signal-constants.md) i [set_terminate](../c-runtime-library/abnormal-termination.md) .

## <a name="using-new-visual-c-features"></a>Korzystanie z nowych funkcji Visual C++

Gdy aplikacja będzie kompilować, linki i uruchomienia, możesz zacząć korzystać z funkcji .NET w dowolnym module skompilowanym z **/CLR**. Aby uzyskać więcej informacji, zobacz [rozszerzenia składników dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md).

Aby uzyskać informacje na temat programowania .NET w Visual C++, zobacz:

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
