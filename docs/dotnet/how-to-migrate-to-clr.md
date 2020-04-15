---
title: 'Instrukcje: migracja do /clr'
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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376080"
---
# <a name="how-to-migrate-to-clr"></a>Porady: migracja do /clr

W tym temacie omówiono problemy, które pojawiają się podczas kompilowania kodu macierzystego z **/clr** (zobacz [/clr (kompilacja środowiska wykonawczego języka wspólnego), aby](../build/reference/clr-common-language-runtime-compilation.md) uzyskać więcej informacji). **/clr** umożliwia natywnego kodu C++ do wywołania i być wywoływane z .NET zestawów oprócz innych natywnych kodu C++. Zobacz [Mieszane (natywne i zarządzane) zestawy](../dotnet/mixed-native-and-managed-assemblies.md) oraz [natywna i .NET Interoperacyjność, aby](../dotnet/native-and-dotnet-interoperability.md) uzyskać więcej informacji na temat zalet kompilacji z **/clr**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Znane problemy kompilowanie projektów biblioteki z /clr

Visual Studio zawiera kilka znanych problemów podczas kompilowania projektów biblioteki z **/clr:**

- Kod może wysyłać zapytania typów w czasie wykonywania z [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Jeśli jednak typ znajduje się w pliku MSIL .dll (skompilowany z **/clr),** wywołanie może zakończyć `FromName` się niepowodzeniem, jeśli wystąpi przed uruchomieniem statycznych konstruktorów w zarządzanym pliku dll (ten problem nie zostanie wyświetlony, jeśli wywołanie FromName nastąpi po wykonaniu kodu w zarządzanej .dll). Aby obejść ten problem, można wymusić budowę zarządzanego konstruktora statycznego, definiując funkcję w zarządzanej .dll, eksportując ją i wywołując ją z natywnej aplikacji MFC. Przykład:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompilowanie z programem Visual C++

Przed **użyciem /clr** na dowolnym module w projekcie, najpierw skompilować i połączyć swój projekt macierzysty z visual studio 2010.

Następujące kroki, a następnie w kolejności, zapewniają najłatwiejszą ścieżkę do **kompilacji /clr.** Ważne jest, aby skompilować i uruchomić projekt po każdym z tych kroków.

### <a name="versions-prior-to-visual-studio-2003"></a>Wersje poprzedzane programem Visual Studio 2003

W przypadku uaktualniania do programu Visual Studio 2010 z wersji poprzedzają program Visual Studio 2003 mogą wystąpić błędy kompilatora związane z ulepszoną zgodnością ze standardem C++ w programie Visual Studio 2003

### <a name="upgrading-from-visual-studio-2003"></a>Uaktualnianie z programu Visual Studio 2003

Projekty poprzednio zbudowany z Visual Studio 2003 również najpierw powinny być kompilowane bez **/clr** jak Visual Studio teraz zwiększył zgodność ANSI/ISO i niektóre zmiany breaking. Zmiana, która może wymagać największej uwagi, to [funkcje zabezpieczeń w crt](../c-runtime-library/security-features-in-the-crt.md). Kod, który używa CRT jest bardzo prawdopodobne, aby utworzyć ostrzeżenia o umorzenie. Ostrzeżenia te mogą być pomijane, ale migracja do nowych [wersji funkcji CRT o podwyższonym udoskonaleniu zabezpieczeń](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) jest preferowana, ponieważ zapewniają one lepsze zabezpieczenia i mogą ujawnić problemy z zabezpieczeniami w kodzie.

### <a name="upgrading-from-managed-extensions-for-c"></a>Uaktualnianie z rozszerzeń zarządzanych dla języka C++

Począwszy od programu Visual Studio 2005, kod napisany z rozszerzeniami zarządzanymi dla języka C++ nie będzie kompilowany w **obszarze /clr**.

## <a name="convert-c-code-to-c"></a>Konwertuj kod C na C++

Mimo że visual studio skompiluje pliki C, konieczne jest przekonwertowanie ich na język C++ dla **kompilacji /clr.** Rzeczywista nazwa pliku nie musi być zmieniona; można użyć **/Tp** (patrz [/Tc, /Tp, /TC, /TP (Określ typ pliku źródłowego).](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) Należy zauważyć, że chociaż pliki kodu źródłowego języka C++ są wymagane dla **/clr,** nie jest konieczne ponowne uwzględnienie kodu w celu użycia paradygmatów obiektowych.

Kod C jest bardzo prawdopodobne, aby wymagać zmian podczas kompilacji jako plik C++. Zasady bezpieczeństwa typu C++ są surowe, więc konwersje typu muszą być wyraźnie określone za pomocą rzutów. Na przykład malloc zwraca wskaźnik void, ale można przypisać do wskaźnika do dowolnego typu w języku C z rzutowania:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Wskaźniki funkcji są również ściśle bezpieczne dla typu w języku C++, więc poniższy kod C wymaga modyfikacji. W języku C++ najlepiej jest `typedef` utworzyć typ wskaźnika funkcji, a następnie użyć tego typu do rzutowania wskaźników funkcji:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ wymaga również, aby funkcje są prototypowane lub w pełni zdefiniowane, zanim będą mogły się odwoływać lub wywoływać.

Identyfikatory używane w kodzie C, które są słowami kluczowymi w języku C++ (takimi jak **wirtualne,** **nowe,** **delete,** **bool,** **true,** **false**itp.) muszą zostać zmienione. Zazwyczaj można to zrobić za pomocą prostych operacji wyszukiwania i wymiany.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Ponowne konfigurowanie ustawień projektu

Po projekt kompiluje i działa w programie Visual Studio 2010 należy utworzyć nowe konfiguracje projektu dla **/clr** zamiast modyfikowania konfiguracji domyślnych. **/clr** jest niezgodne z niektórych opcji kompilatora i tworzenie oddzielnych konfiguracji pozwala na tworzenie projektu jako natywne lub zarządzane. Gdy **/clr** jest zaznaczone w oknie dialogowym strony właściwości, ustawienia projektu niezgodne z **/clr** są wyłączone (i wyłączone opcje nie są automatycznie przywracane, jeśli **/clr** jest następnie niezaznaczone).

### <a name="create-new-project-configurations"></a>Tworzenie nowych konfiguracji projektu

Za pomocą opcji **Kopiuj ustawienia z** okna **dialogowego Nowa konfiguracja projektu** **(Build** > **Configuration Manager** > **Active Solution Configuration** > **New)** można utworzyć konfigurację projektu na podstawie istniejących ustawień projektu. Zrób to raz dla konfiguracji debugowania i raz dla konfiguracji wydania. Kolejne zmiany mogą być następnie stosowane tylko do **/clr** -konfiguracje specyficzne, pozostawiając oryginalne konfiguracje projektu nienaruszone.

Projekty korzystające z reguł kompilacji niestandardowej mogą wymagać dodatkowej uwagi.

Ten krok ma różne implikacje dla projektów, które używają makefiles. W takim przypadku można skonfigurować oddzielny obiekt docelowy kompilacji lub można utworzyć wersję specyficzną dla **kompilacji /clr** z kopii oryginału.

### <a name="change-project-settings"></a>Zmienianie ustawień projektu

**/clr** można wybrać w środowisku programistycznym, postępując zgodnie z instrukcjami w [/clr (Common Language Runtime Compilation).](../build/reference/clr-common-language-runtime-compilation.md) Jak wspomniano wcześniej, ten krok automatycznie wyłączy sprzeczne ustawienia projektu.

> [!NOTE]
> Podczas uaktualniania zarządzanej biblioteki lub projektu usługi sieci web z programu Visual Studio 2003 do strony właściwości **wiersza polecenia** zostanie dodana opcja kompilatora **/Zl.** Spowoduje to LNK2001. Usuń **/Zl** ze strony właściwości **wiersza polecenia,** aby rozwiązać problem. Zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) i [Ustaw kompilator i właściwości kompilacji, aby](../build/working-with-project-properties.md) uzyskać więcej informacji. Możesz też dodać msvcrt.lib i msvcmrt.lib do właściwości **Dodatkowe zależności konsolidatora.**

W przypadku projektów zbudowanych za pomocą plików makefiles niezgodne opcje kompilatora muszą być wyłączone ręcznie po **dodaniu /clr.** Zobacz /[/clr Ograniczenia, aby](../build/reference/clr-restrictions.md) uzyskać informacje na temat opcji kompilatora, które nie są zgodne z **/clr**.

### <a name="precompiled-headers"></a>Wstępnie skompilowane nagłówki

Wstępnie skompilowane nagłówki są obsługiwane w obszarze **/clr**. Jeśli jednak skompilowano tylko niektóre pliki CPP z **/clr** (kompilowanie pozostałych jako natywnych) niektóre zmiany będą wymagane, ponieważ wstępnie skompilowane nagłówki generowane za pomocą **/clr** nie są zgodne z tymi generowanymi bez **/clr**. Ta niezgodność wynika z faktu, że **/clr** generuje i wymaga metadanych. Moduły skompilowane **/clr** nie mogą zatem używać wstępnie skompilowanych nagłówków, które nie zawierają metadanych, a moduły inne **niż /clr** nie mogą używać wstępnie skompilowanych plików nagłówkowych zawierających metawyborze.

Najprostszym sposobem skompilowania projektu, w którym niektóre moduły są kompilowane **/clr** jest całkowite wyłączenie wstępnie skompilowanych nagłówków. (W oknie dialogowym Strony właściwości projektu otwórz węzeł C/C++ i wybierz wstępnie skompilowane nagłówki. Następnie zmień właściwość Utwórz/Użyj wstępnie skompilowanych nagłówków na "Nie używając wstępnie skompilowanych nagłówków".)

Jednak szczególnie w przypadku dużych projektów wstępnie skompilowane nagłówki zapewniają znacznie lepszą szybkość kompilacji, więc wyłączenie tej funkcji nie jest pożądane. W takim przypadku najlepiej jest skonfigurować pliki **/clr** i non **/clr,** aby używać oddzielnych wstępnie skompilowanych nagłówków. Można to zrobić w jednym kroku, wybierając wiele modułów, które mają być skompilowane **/clr** za pomocą **Eksploratora rozwiązań,** klikając prawym przyciskiem myszy na grupę i wybierając właściwości. Następnie zmień właściwości Tworzenie/Używanie PCH przez plik i Wstępnie skompilowany plik nagłówka, aby użyć odpowiednio innej nazwy pliku nagłówka i pliku PCH.

## <a name="fixing-errors"></a>Błędy naprawiania

Kompilowanie z **/clr** może spowodować błędy kompilatora, konsolidatora lub środowiska uruchomieniowego. W tej sekcji omówiono najczęstsze problemy.

### <a name="metadata-merge"></a>Scalanie metadanych

Różne wersje typów danych może spowodować, że konsolidator zakończy się niepowodzeniem, ponieważ metadane wygenerowane dla dwóch typów nie jest zgodny. (Jest to zwykle spowodowane, gdy elementy członkowskie typu są warunkowo zdefiniowane, ale warunki nie są takie same dla wszystkich plików CPP, które używają tego typu.) W takim przypadku konsolidator kończy się niepowodzeniem, zgłaszając tylko nazwę symbolu i nazwę drugiego pliku OBJ, w którym zdefiniowano typ. Często warto obrócić kolejność wysyłania plików OBJ do konsolidatora w celu odnajdywanie lokalizacji innej wersji typu danych.

### <a name="loader-lock-deadlock"></a>Zakleszczenie blokady ładowarki

"Zakleszczenie blokady modułu ładującego" może wystąpić, ale jest deterministyczny i jest wykrywany i zgłaszany w czasie wykonywania. Zobacz [Inicjowanie zestawów mieszanych, aby](../dotnet/initialization-of-mixed-assemblies.md) uzyskać szczegółowe informacje na temat tła, wskazówek i rozwiązań.

### <a name="data-exports"></a>Eksport danych

Eksportowanie danych DLL jest podatne na błędy i nie jest zalecane. Jest tak, ponieważ sekcja danych biblioteki DLL nie jest gwarantowana do zainicjowania, dopóki nie zostanie wykonana część zarządzana biblioteki DLL. Odwołują się do metadanych za pomocą [dyrektywy #using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Widoczność typów

Typy macierzyste są domyślnie prywatne. Może to spowodować, że typ macierzysty nie jest widoczny poza biblioteką DLL. Rozwiąż ten `public` błąd, dodając do tych typów.

### <a name="floating-point-and-alignment-issues"></a>Problemy z zmiennoprzecinkowym i wyrównaniem

`__controlfp`nie jest obsługiwany w czasie wykonywania języka wspólnego (zobacz [_control87, \__controlfp, _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) aby uzyskać więcej informacji). CLR również nie będzie przestrzegać [wyrównać](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Inicjowanie COM

Środowisko wykonawcze języka wspólnego inicjuje com automatycznie po zainicjowaniu modułu (gdy com jest inicjowany automatycznie odbywa się tak, jak MTA). W rezultacie jawnie inicjowanie COM daje kody zwrotu wskazujące, że COM jest już zainicjowany. Próba jawnego zainicjowania modelu COM za pomocą jednego modelu wątkowego, gdy program CLR został już zainicjowany przez model COM do innego modelu wątkowego, może spowodować niepowodzenie aplikacji.

Środowisko wykonawcze języka wspólnego domyślnie uruchamia com jako MTA; użyj [/CLRTHREADATTRIBUTE (Set CLR Thread Attribute),](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) aby to zmodyfikować.

### <a name="performance-issues"></a>Problemy z wydajnością

Możesz zobaczyć zmniejszoną wydajność, gdy natywne metody C++ generowane do MSIL są wywoływane pośrednio (wywołania funkcji wirtualnych lub przy użyciu wskaźników funkcji). Aby dowiedzieć się więcej na ten temat, zobacz [Double Thunking](../dotnet/double-thunking-cpp.md).

Podczas przechodzenia z macierzystego do MSIL, można zauważyć wzrost rozmiaru zestawu roboczego. Jest tak, ponieważ środowisko wykonawcze języka wspólnego udostępnia wiele funkcji, aby upewnić się, że programy działają poprawnie. Jeśli aplikacja **/clr** nie działa poprawnie, można włączyć C4793 (domyślnie wyłączone), zobacz [Ostrzeżenie kompilatora (poziom 1 i 3) C4793,](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) aby uzyskać więcej informacji.

### <a name="program-crashes-on-shutdown"></a>Program ulega awarii przy zamykaniu systemu

W niektórych przypadkach clr można zamknąć przed kodem zarządzanym jest gotowy do pracy. Korzystanie `std::set_terminate` `SIGTERM` i może to spowodować. Aby uzyskać więcej informacji, zobacz [stałe sygnałowe](../c-runtime-library/signal-constants.md) i [set_terminate.](../c-runtime-library/abnormal-termination.md)

## <a name="using-new-visual-c-features"></a>Korzystanie z nowych funkcji visual c++

Po skompilowaniu, łączach i uruchomieniu aplikacji można rozpocząć korzystanie z funkcji .NET w dowolnym module skompilowanym z **/clr**. Aby uzyskać więcej informacji, zobacz [Rozszerzenia składników dla platform środowiska wykonawczego](../extensions/component-extensions-for-runtime-platforms.md).

Aby uzyskać informacje na temat programowania platformy .NET w języku Visual C++, zobacz:

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Zobacz też

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
