---
title: 'Porady: Migracja do / clr'
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
ms.openlocfilehash: d293b6c3795b9abe57da0c6bcb92dd3f1de810ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454447"
---
# <a name="how-to-migrate-to-clr"></a>Porady: migracja do /clr

W tym temacie omówiono problemy, które powstają, gdy kompilacja kodu natywnego za pomocą **/CLR** (zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji). **/ CLR** umożliwia macierzystego kodu C++ do wywołania i można wywołać z zestawów platformy .NET, oprócz innych macierzystego kodu C++. Zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) i [natywne i .NET współdziałanie](../dotnet/native-and-dotnet-interoperability.md) Aby uzyskać więcej informacji na temat korzyści wynikające z kompilowania za pomocą **/CLR**.

## <a name="known-issues-compiling-library-projects-with-clr"></a>Znane problemy dotyczące kompilowania projektów bibliotek z/CLR

Program Visual Studio zawiera niektóre znane problemy występujące podczas kompilowania projektów biblioteki za pomocą **/CLR**:

- Twój kod może zbadać typów w czasie wykonywania za pomocą [CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname). Jednakże jeśli typ znajduje się w dll MSIL (skompilowany przy użyciu **/CLR**), wywołanie `FromName` może zakończyć się niepowodzeniem, jeśli wystąpi przed konstruktorów statycznych w pliku .dll zarządzanych (nie będzie mógł przeglądać ten problem wywołanie nazwa od sytuacji po kodzie wykonania w zarządzanej .dll). Aby obejść ten problem, możesz wymusić konstrukcji zarządzanych Konstruktor statyczny definiujący funkcję w zarządzanych .dll, eksportując je i wywoływania go z natywnych aplikacji MFC. Na przykład:

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>Kompiluj przy użyciu języka Visual C++

Przed rozpoczęciem korzystania z **/CLR** w module w projekcie, należy najpierw skompilować i połączyć natywnego projektu za pomocą programu Visual Studio 2010.

W poniższych krokach, a następnie w kolejności, przedstawiono Najłatwiejszą drogą do **/CLR** kompilacji. Jest ważne skompilować i uruchomić projekt po każdym z tych kroków.

### <a name="versions-prior-to-visual-c-2003"></a>Wersje przed Visual C++ 2003

Jeśli uaktualniasz Visual Studio 2010 w wersji wcześniejszej niż Visual C++ 2003, może zostać wyświetlony błędy kompilatora dotyczące rozszerzoną zgodność standardowego języka C++ w Visual C++ 2003

### <a name="upgrading-from-visual-c-2003"></a>Uaktualnianie z programu Visual C++ 2003

Poprzednie projektów utworzonych za pomocą programu Visual C++ 2003 również najpierw powinna być skompilowana bez **/CLR** zgodnie z programu Visual Studio teraz wzrosło zgodność ANSI/ISO i niektórych ważnych zmian. Jest zmiany mogą wymagać uwagi najbardziej [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md). Kod, który używa CRT jest bardzo prawdopodobne wygenerować ostrzeżeń dotyczących zakończenia obsługi. Ostrzeżenia te mogą być pomijane, ale migracja do nowego [Security-Enhanced wersje CRT funkcji](../c-runtime-library/security-enhanced-versions-of-crt-functions.md) jest preferowane, ponieważ zapewniają większe bezpieczeństwo i może spowodować ujawnienie problemów z zabezpieczeniami w kodzie.

### <a name="upgrading-from-managed-extensions-for-c"></a>Uaktualnianie z zarządzanych rozszerzeń dla C++

Począwszy od programu Visual Studio 2005 kod napisany za pomocą zarządzanych rozszerzeń języka C++ nie kompilacji w ramach **/CLR**.

## <a name="convert-c-code-to-c"></a>Konwertowanie C kodu języka c++

Mimo że program Visual Studio zostanie skompilowany plików języka C, należy go przekonwertować w języku C++ **/CLR** kompilacji. Nazwa pliku nie ma zostać zmieniony; Możesz użyć **/Tp** (zobacz [TP, /Tp-TP, /TP (Określ źródło pliku typu)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md).) Należy zauważyć, że pliki kodu źródłowego języka C++ są wymagane dla **/CLR**, nie jest konieczne ponowne wziąć pod uwagę kodu, aby użyć paradygmatów zorientowane obiektowo.

Kod języka C jest bardzo prawdopodobne wymagać zmiany, gdy kompilowany jako plik C++. Zasady bezpieczeństwa typów języka C++ są strict, więc konwersje typów, należy jawnie rzutowania. Na przykład — funkcja malloc zwraca pusty wskaźnik, ale mogą być przypisane do wskaźnika do dowolnego typu w języku C za pomocą rzutowania:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

Wskaźniki funkcji również są ściśle bezpieczny w języku C++, więc wymaga modyfikacji, poniższy kod C. W języku C++ jest najlepiej utworzyć `typedef` który definiuje typ wskaźnika funkcji, a następnie użyj tego typu rzutowanie wskaźników do funkcji:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++ wymaga również, że funkcje być prototypowane lub w pełni zdefiniowana przed ich odwołania lub wywołany.

Identyfikatory użytą w kodzie C, które należą do słów kluczowych w języku C++ (takie jak **wirtualnego**, **nowe**, **Usuń**, **bool**, **true** , **false**, itp.) musi zostać zmieniona. Zazwyczaj można to zrobić przy użyciu prostych operacji wyszukiwania i zamieniania.

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>Zmień konfigurację ustawień projektu

Po projekt kompiluje i uruchamia w programie Visual Studio 2010 należy utworzyć nowe konfiguracje projektu dla **/CLR** zamiast modyfikowanie domyślnej konfiguracji. **/ CLR** jest niezgodna z niektóre opcje kompilatora i tworzenia oddzielne konfiguracje umożliwia kompilowanie projektu jako macierzysty lub zarządzany. Gdy **/CLR** jest zaznaczona w oknie dialogowym stron właściwości, nie jest zgodna z ustawień projektu **/CLR** są wyłączone (i wyłączonych opcjach nie są automatycznie przywracane **/CLR** jest następnie zaznaczona).

### <a name="create-new-project-configurations"></a>Utwórz nowe konfiguracje projektu

Możesz użyć **Kopiuj ustawienia z** opcji **nowe okno dialogowe konfiguracji projektu** (**kompilacji** > **programu Configuration Manager**  >  **Aktywną konfigurację rozwiązania** > **New**) do utworzenia konfiguracji projektu, w oparciu o istniejących ustawień projektu. Wykonaj tę czynność jeden raz dla konfiguracji debugowania i raz dla konfiguracji wydania. Następnie można zastosować kolejne zmiany do **/CLR** -określonej konfiguracji, pozostawiając bez zmian do oryginalnej konfiguracji projektu.

Projektów, które korzystają z niestandardowych regułach kompilacji mogą wymagać uwagi dodatkowe.

Ten krok ma różne znaczenie dla projektów, które używają plików reguł programu make. W tym przypadku można skonfigurować oddzielne docelowe kompilacji lub wersji specyficzne dla **/CLR** kompilacji można tworzyć na podstawie kopię oryginału.

### <a name="change-project-settings"></a>Zmień ustawienia projektu

**/ CLR** można wybrać w środowisku programistycznym, postępując zgodnie z instrukcjami w [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md). Jak wspomniano wcześniej, w tym kroku zostanie automatycznie wyłączyć sprzeczne ustawienia projektu.

> [!NOTE]
>  Podczas uaktualniania zarządzanej biblioteki lub projekt usługi sieci web z Visual C++ 2003 **/Zl** kompilatora opcja zostanie dodany do **wiersza polecenia** stronę właściwości. Spowoduje to LNK2001. Usuń **/Zl** z **wiersza polecenia** strony właściwości, aby rozwiązać. Zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) i [Praca z właściwościami projektu](../ide/working-with-project-properties.md) Aby uzyskać więcej informacji. Lub Dodaj biblioteki msvcrt.lib i msvcmrt.lib do konsolidatora **dodatkowe zależności** właściwości.

W przypadku projektów utworzonych za pomocą plików reguł programu make opcje niezgodne kompilatora musi zostać wyłączona ręcznie po **/CLR** zostanie dodany. Zobacz /[/CLR ograniczenia](../build/reference/clr-restrictions.md) informacji o opcjach kompilatora, które nie są zgodne z **/CLR**.

### <a name="precompiled-headers"></a>Prekompilowane nagłówki

Prekompilowane nagłówki są wspierane w ramach **/CLR**. Jednak jeśli tylko kompilowania niektóre pliki CPP z **/CLR** (kompilowanie pozostałych jako natywną) pewne zmiany będzie wymagane, ponieważ prekompilowanych nagłówków, wygenerowane za pomocą **/CLR** nie są zgodne z tymi wygenerowany bez **/CLR**. Ta niezgodność to wynika z faktu, że **/CLR** generuje i wymaga metadanych. Moduły skompilowane **/CLR** w związku z tym nie można użyć polecenia wstępnie skompilowanych nagłówków, które nie zawierają metadanych i innych niż **/CLR** modułów nie można użyć wstępnie skompilowanego nagłówka pliki, które zawierają metadane.

Najprostszym sposobem, aby skompilować projekt, w której niektóre moduły są kompilowane **/CLR** jest całkowicie wyłączyć wstępnie skompilowanych nagłówków. (W oknie dialogowym strony właściwości projektu, otwórz węzeł C/C++ i wybierz polecenie prekompilowanych nagłówków. Następnie zmień właściwość Utwórz bądź użyj prekompilowanych nagłówków na "Nie przy użyciu wstępnie skompilowane nagłówki").

Szczególnie w przypadku dużych projektów, wstępnie skompilowane nagłówki zapewnia jednak znacznie lepszą szybkość kompilacji tak wyłączeniem tej funkcji nie jest pożądane. W takim przypadku najlepiej skonfigurować **/CLR** i innych niż **/CLR** pliki używane oddzielne wstępnie skompilowanych nagłówków. Można to zrobić w jednym kroku przez zaznaczenie wielu modułów do skompilowania **/CLR** przy użyciu **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy w grupie i wybierając polecenie Właściwości. Następnie zmienić Utwórz/Użyj PCH za pośrednictwem pliku i Prekompilowanego pliku nagłówkowego właściwości mają zostać użyte inną nazwę pliku, a plik PCH, odpowiednio.

## <a name="fixing-errors"></a>Naprawianie błędów

Kompilowanie przy użyciu **/CLR** może powodować błędy kompilatora, konsolidatora lub środowiska uruchomieniowego. W tej sekcji omówiono najbardziej typowe problemy.

### <a name="metadata-merge"></a>Scalanie metadanych

Wersje różnych typów danych może spowodować konsolidator, aby zakończyć się niepowodzeniem, ponieważ metadane wygenerowany dla dwóch typów nie jest zgodny. (Jest to zazwyczaj spowodowane elementy członkowskie typu warunkowo są definiowane, kiedy warunki nie są takie same dla wszystkich plikach CPP, które używają typu.) W tym przypadku konsolidator nie powiedzie się, raportowanie nazwę symbolu i nazwę drugiego pliku OBJ, w którym zdefiniowano typ. Często jest to przydatne do obracania zamówienia, że pliki OBJ są wysyłane do konsolidatora do odnalezienia lokalizacji inna wersja tego typu.

### <a name="loader-lock-deadlock"></a>Zakleszczenie blokady modułu ładującego

"Zakleszczenia blokady modułu ładującego" może wystąpić, ale jest deterministyczna i jest wykrywanych i zgłaszanych w czasie wykonywania. Zobacz [inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md) szczegółowe tła, wskazówki i rozwiązań.

### <a name="data-exports"></a>Eksportowanie danych

Eksportowanie danych biblioteki DLL są podatne na błędy i nie jest zalecane. Jest to spowodowane sekcji danych biblioteki DLL nie jest gwarantowane do zainicjowania część zarządzanej biblioteki DLL zostały wykonane. Odwołuj się do metadanych z [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).

### <a name="type-visibility"></a>Widoczność typów

Typy natywne są domyślnie prywatny. Może to spowodować, że typ natywny nie są widoczne w bibliotece DLL. Rozwiązać ten problem, dodając `public` do tych typów.

### <a name="floating-point-and-alignment-issues"></a>Zmiennoprzecinkowe punktu i wyrównanie problemów

`__controlfp` nie jest obsługiwana w środowisku uruchomieniowym języka wspólnego (zobacz [_control87 —, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) Aby uzyskać więcej informacji). Środowisko CLR również nie są uwzględniane [wyrównać](../cpp/align-cpp.md).

### <a name="com-initialization"></a>Zainicjowanie modelu COM

Środowisko uruchomieniowe języka wspólnego inicjuje automatycznie COM, podczas inicjowania modułu (gdy COM jest inicjowany automatycznie wystąpiło to jako MTA). Jawne inicjowanie modelu COM daje w wyniku kody powrotne wskazujący, że COM jest już zainicjowany. Podjęto próbę jawnie zainicjować modelu COM za pomocą jednego modelu wątkowości, gdy środowisko CLR już zainicjowany do innego modelu wątkowości COM może spowodować awarię aplikacji.

Środowisko uruchomieniowe języka wspólnego rozpoczyna się COM jako MTA domyślnie; Użyj [/CLRTHREADATTRIBUTE (Ustaw wątku atrybut CLR)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) Aby zmodyfikować to ustawienie.

### <a name="performance-issues"></a>Problemy z wydajnością

Mogą być widoczne obniżenie wydajności natywnego języka C++ wygenerowany na język MSIL są wywoływane pośrednio (wywołania funkcji wirtualnej lub za pomocą wskaźników funkcji). Aby dowiedzieć się więcej na ten temat, zobacz [podwójna](../dotnet/double-thunking-cpp.md).

Podczas przenoszenia z natywnego na język MSIL, można zauważyć wzrost rozmiaru zestawu roboczego. Jest to spowodowane środowiska uruchomieniowego języka wspólnego udostępnia wiele funkcji, aby upewnić się, że programy działać poprawnie. Jeśli Twoje **/CLR** aplikacja nie działa poprawnie, możesz chcieć umożliwić ze C4793 (funkcja domyślnie wyłączona), zobacz [ostrzeżenie kompilatora (poziom 1 i 3) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) Aby uzyskać więcej informacji.

### <a name="program-crashes-on-shutdown"></a>Program awarii podczas zamykania

W niektórych przypadkach CLR można zamykania przed zakończeniem zarządzanego kodu uruchamiania. Za pomocą `std::set_terminate` i `SIGTERM` może to spowodować. Zobacz [stałe sygnałów](../c-runtime-library/signal-constants.md) i [set_terminate](../c-runtime-library/abnormal-termination.md) Aby uzyskać więcej informacji.

## <a name="using-new-visual-c-features"></a>Za pomocą nowych funkcji Visual C++

Po kompiluje aplikację, łączy i działa, możesz rozpocząć korzystanie z funkcji platformy .NET w każdy moduł skompilowany z **/CLR**. Aby uzyskać więcej informacji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).

Jeśli używasz zarządzanych rozszerzeń języka C++, można przekonwertować kodu, aby użyć nowej składni. Aby uzyskać szczegółowe informacje dotyczące konwertowania zarządzanych rozszerzeń języka C++, zobacz [C + +/ CLI Podręcznik migracji](../dotnet/cpp-cli-migration-primer.md).

Aby uzyskać informacje na temat programowania w języku Visual C++ .NET, zobacz:

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)

- [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>Zobacz też

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
