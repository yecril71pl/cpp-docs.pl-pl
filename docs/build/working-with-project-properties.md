---
title: Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio
description: Użyj środowiska IDE programu Visual Studio, aby zmienić opcje kompilatora i konsolidatora języka C++ oraz inne ustawienia kompilacji.
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 6c05dd00324113819dd145e46bf10dfeb96a66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078236"
---
# <a name="set-compiler-and-build-properties"></a>Ustawianie właściwości kompilatora i Build

W środowisku IDE wszystkie informacje, które są konieczne do skompilowania projektu, są ujawniane jako *Właściwości*. Te informacje obejmują nazwę aplikacji, rozszerzenie (na przykład DLL, LIB, EXE), opcje kompilatora, Opcje konsolidatora, ustawienia debugera, niestandardowe kroki kompilacji i wiele innych rzeczy. Zazwyczaj można używać *stron właściwości* do wyświetlania i modyfikowania tych właściwości. Aby uzyskać dostęp do stron właściwości, wybierz pozycję **Project** > **_ProjectName_ Properties (właściwości** projektu) z menu głównego lub kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.

## <a name="default-properties"></a>Właściwości domyślne

Podczas tworzenia projektu system przypisuje wartości dla różnych właściwości. Wartości domyślne różnią się w zależności od rodzaju projektu i opcji wybranych w Kreatorze aplikacji. Na przykład Projekt ATL ma właściwości powiązane z plikami MIDL, ale nie są one obecne w podstawowej aplikacji konsolowej. Właściwości domyślne są wyświetlane w okienku ogólne na stronach właściwości:

![Domyślne ustawienia projektu w programie Visual C&#43;&#43; ](media/visual-c---project-defaults.png "Visual C++ wartości domyślne projektu")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Stosowanie właściwości do konfiguracji kompilacji i platform docelowych

Niektóre właściwości, takie jak nazwa aplikacji, mają zastosowanie do wszystkich wariantów kompilacji, niezależnie od platformy docelowej lub do kompilacji debugowania lub wydania. Ale większość właściwości jest zależna od konfiguracji. Wynika to z faktu, że kompilator musi wiedzieć, jaka konkretna platforma zostanie uruchomiona, i jakie opcje kompilatora mają być używane w celu wygenerowania poprawnego kodu. W związku z tym podczas ustawiania właściwości należy zwrócić uwagę na to, której konfiguracji i platformy ma dotyczyć nowa wartość. Czy ma zastosowanie tylko do debugowania systemu Win32 lub czy ma również zastosowanie do aktywacji ARM i debugowania x64? Na przykład właściwość **optymalizacji** domyślnie ustawia wartość **maksymalizuj szybkość (/O2)** w konfiguracji wydania, ale jest wyłączona w konfiguracji debugowania.

Strony właściwości są zaprojektowane tak, aby zawsze widzieć, i w razie potrzeby zmodyfikować, do której konfiguracji i platformy ma być stosowana wartość właściwości. Poniższa ilustracja przedstawia strony właściwości z informacjami o konfiguracji i platformie w polach listy u góry. Gdy właściwość **optymalizacji** jest ustawiona w tym miejscu, będzie stosowana tylko do debugowania Win32, która stanie się aktywną konfiguracją, jak pokazano na czerwono.

![Strony właściwości&#43;&#43; Visual C pokazujące aktywną konfigurację](media/visual-c---property-pages-showing-active-configuration.png "Visual C++ strony właściwości pokazujące aktywną konfigurację")

Na poniższej ilustracji przedstawiono tę samą stronę właściwości projektu, ale konfiguracja została zmieniona na Release. Zwróć uwagę na różne wartości właściwości Optymalizacja. Należy również pamiętać, że aktywna konfiguracja nadal jest debugowana. W tym miejscu możesz ustawić właściwości dla dowolnej konfiguracji; nie musi ona być aktywna.

![&#43;&#43; strony właściwości programu Visual C przedstawiające konfigurację wydania](media/visual-c---property-pages-showing-release-config.png "Visual C++ strony właściwości pokazujące konfigurację wydania")

## <a name="target-platforms"></a>Platformy docelowe

*Platforma docelowa* odnosi się do rodzaju urządzenia i/lub systemu operacyjnego, na którym będzie uruchamiany plik wykonywalny. Można skompilować projekt dla więcej niż jednej platformy. Dostępne platformy docelowe dla projektów C++ zależą od rodzaju projektu; obejmują one, ale nie są ograniczone do Win32, x64, ARM, Android i iOS.     Platforma docelowa **x86** , która może być widoczna w **Configuration Manager** jest taka sama jak **Win32** w natywnych projektach C++. Win32 oznacza 32-bitowe systemy Windows i **x64** oznaczają 64-bitowe okna. Aby uzyskać więcej informacji na temat tych dwóch platform, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/win32/WinProg64/running-32-bit-applications).

Dowolna wartość platformy docelowej **procesora CPU** , która może być widoczna w **Configuration Manager** nie ma wpływu na natywne projekty C++; dotyczy to C++/CLI i innych typów projektów .NET. Aby uzyskać więcej informacji, zobacz [/CLRIMAGETYPE (Określ typ obrazu CLR)](reference/clrimagetype-specify-type-of-clr-image.md).

Aby uzyskać więcej informacji na temat ustawiania właściwości dla kompilacji debugowania, zobacz:

- [Ustawienia projektu dla konfiguracji debugowania w języku C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Ustawienia debugera i przygotowanie](/visualstudio/debugger/debugger-settings-and-preparation)
- [Przygotowanie debugowania: typy projektów Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Określanie plików symboli (pdb) i plików źródłowych w debugerze programu Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Opcje kompilatora i konsolidatora języka C++

Opcje kompilatora i konsolidatora języka C++ znajdują się w węzłach **C/C++** i **konsolidatora** w lewym okienku w obszarze **Właściwości konfiguracji**. Są one tłumaczone bezpośrednio do opcji wiersza polecenia, które zostaną przesłane do kompilatora. Aby zapoznać się z dokumentacją dotyczącą konkretnej opcji, wybierz opcję w środkowym okienku i naciśnij klawisz **F1**. Można też przejrzeć dokumentację dotyczącą wszystkich opcji w [opcjach kompilatora MSVC](reference/compiler-options.md) i [MSVC Opcje konsolidatora](reference/linker-options.md).

Okno dialogowe **strony właściwości** pokazuje tylko strony właściwości, które mają zastosowanie w bieżącym projekcie. Na przykład, jeśli projekt nie ma pliku .idl, nie zostanie wyświetlona strona właściwości MIDL. Aby uzyskać więcej informacji na temat ustawienia na każdej stronie właściwości, zobacz [strony właściwości (C++)](reference/property-pages-visual-cpp.md).

## <a name="directory-and-path-values"></a>Wartości katalogu i ścieżki

MSBuild obsługuje użycie stałych czasu kompilacji o nazwie "MACROS" dla niektórych wartości ciągów, takich jak katalogi i ścieżki. Są one widoczne na stronach właściwości, w których można odwoływać się do i modyfikować przy użyciu [edytora właściwości](#property_editor).

Poniższa ilustracja przedstawia strony właściwości dla projektu Visual Studio C++. W lewym okienku jest zaznaczona reguła **katalogów VC + +** *rule* , a w prawym okienku zostaną wyświetlone właściwości skojarzone z tą regułą. `$(...)` Wartości są nazywane *makrami*. *Makro* jest stałą czasu kompilacji, która może odwoływać się do wartości zdefiniowanej przez program Visual Studio lub system MSBuild lub do wartości zdefiniowanej przez użytkownika. Za pomocą makr zamiast zakodowanych wartości, takich jak ścieżki katalogów, można łatwo udostępniać ustawienia właściwości między komputerami i między wersjami programu Visual Studio, a także lepiej upewnić się, że ustawienia projektu poprawnie uczestniczą w [dziedziczeniu właściwości](project-property-inheritance.md).

![Strony właściwości projektu](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Aby wyświetlić wartości wszystkich dostępnych makr, można użyć edytora właściwości.

### <a name="predefined-macros"></a>Wstępnie zdefiniowane makra

*makra globalne*<br/>
Dotyczy wszystkich elementów w konfiguracji projektu. Ma składnię `$(name)`. Przykładem makra globalnego jest `$(VCInstallDir)`, który przechowuje katalog główny instalacji programu Visual Studio. Makro globalne odnosi się do `PropertyGroup` w programie MSBuild.

*makra elementu*<br/>
Ma składnię `%(name)`. Dla pliku, makro elementu dotyczy tylko tego pliku — na przykład można użyć `%(AdditionalIncludeDirectories)` , aby określić katalogi dołączania, które mają zastosowanie tylko do określonego pliku. Tego rodzaju makro elementu odpowiada `ItemGroup` metadanych w programie MSBuild. Gdy jest używane w kontekście konfiguracji projektu, makro elementu stosuje się do wszystkich plików określonego typu. Na przykład właściwość konfiguracji **Definicje preprocesora** języka C/C++ może przyjmować makro `%(PreprocessorDefinitions)` elementu, które ma zastosowanie do wszystkich plików. cpp w projekcie. Tego rodzaju makro elementu odpowiada `ItemDefinitionGroup` metadanych w programie MSBuild. Aby uzyskać więcej informacji, zobacz [definicje elementu](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Makra zdefiniowane przez użytkownika

Można utworzyć *makra zdefiniowane przez użytkownika* , które będą używane jako zmienne w kompilacjach projektu. Na przykład, można utworzyć makro zdefiniowane przez użytkownika, które udostępnia wartość do niestandardowego kroku kompilacji lub niestandardowego narzędzia kompilacji. Makro zdefiniowane przez użytkownika to para nazwa/wartość. W pliku projektu Użyj notacji **$ (**<em>name</em>**)** , aby uzyskać dostęp do wartości.

Makro zdefiniowane przez użytkownika jest przechowywane w arkuszu właściwości. Jeśli projekt nie zawiera jeszcze arkusza właściwości, można go utworzyć, wykonując czynności opisane w sekcji [udostępnianie lub ponowne używanie ustawień projektu programu Visual Studio](create-reusable-property-configurations.md).

#### <a name="to-create-a-user-defined-macro"></a>Aby utworzyć makro zdefiniowane przez użytkownika

1. Otwórz okno **Menedżer właściwości** . (Na pasku menu wybierz polecenie **Wyświetl** > **Menedżer właściwości** lub **Wyświetl** > **inne Menedżer właściwości systemu Windows** > **Property Manager**). Otwórz menu skrótów dla arkusza właściwości (jego nazwa jest zakończona w. user), a następnie wybierz polecenie **Właściwości**. Zostanie otwarte okno dialogowe **strony właściwości** dla tego arkusza właściwości.

1. W lewym okienku okna dialogowego wybierz opcję **makra użytkownika**. W prawym okienku wybierz przycisk **Dodaj makro** , aby otworzyć okno dialogowe **Dodaj makro użytkownika** .

1. W oknie dialogowym określ nazwę i wartość dla makra. Opcjonalnie zaznacz pole wyboru **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji** .

## <a name=""></a><a name="property_editor">Edytor właściwości</a>

Edytor właściwości służy do modyfikowania niektórych właściwości ciągów i zaznaczania makr jako wartości. Aby otworzyć Edytor właściwości, zaznacz właściwość na stronie właściwości, a następnie wybierz strzałkę w dół po prawej stronie. Jeśli lista rozwijana zawiera ** \<>edycji **, możesz wybrać ją, aby wyświetlić Edytor właściwości dla tej właściwości.

![Lista rozwijana&#95;edytora&#95;właściwości](media/property_editor_dropdown.png "Property_Editor_Dropdown")

W edytorze właściwości można wybrać przycisk **makra** w celu wyświetlenia dostępnych makr i ich bieżących wartości. Na poniższej ilustracji przedstawiono Edytor właściwości dla właściwości **Dodatkowe katalogi dołączane** po wybraniu przycisku **makra** . Gdy pole wyboru **Dziedzicz z wartości nadrzędnych lub domyślnych projektu** jest zaznaczone i dodawana jest nowa wartość, jest ona dołączana do dowolnych wartości, które są obecnie dziedziczone. Jeśli usuniesz zaznaczenie pola wyboru, nowa wartość zamieni wartości dziedziczone. W większości przypadków pozostaw zaznaczone pole wyboru.

![Edytor właściwości, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Dodaj katalog dołączania do zestawu katalogów domyślnych

Podczas dodawania katalogu plików dołączonych do projektu jest ważne, aby nie zastąpić domyślnych katalogów. Poprawny sposób dodania katalogu to dołączenie nowej ścieżki, na przykład "C:\MyNewIncludeDir\", a następnie dołączenie makra **$ (IncludePath)** do wartości właściwości.

## <a name="quickly-browse-and-search-all-properties"></a>Szybko Przeglądaj i Przeszukaj wszystkie właściwości

Strona właściwości **wszystkie opcje** (w obszarze **Właściwości konfiguracji &#124; w węźle C/C++** w oknie dialogowym **strony właściwości** ) zapewnia szybki sposób przeglądania i wyszukiwania właściwości, które są dostępne w bieżącym kontekście. Ma specjalne pole wyszukiwania i prostą składnię, aby pomóc w filtrowaniu wyników:

Brak prefiksu:<br/>
Wyszukiwanie tylko w nazwach właściwości (podciąg bez uwzględniania wielkości liter).

'/' lub '-' :<br/>
Wyszukiwanie tylko w przełącznikach kompilatora (prefiks bez uwzględniania wielkości liter)

v:<br/>
Wyszukiwanie tylko w wartościach (podciąg bez uwzględniania wielkości liter).

## <a name="set-environment-variables-for-a-build"></a>Ustawianie zmiennych środowiskowych dla kompilacji

Kompilator MSVC (CL. exe) rozpoznaje pewne zmienne środowiskowe, w tym LIB, LIBPATH, PATH i INCLUDE. Podczas kompilowania przy użyciu środowiska IDE właściwości, które są ustawione na stronie właściwości [katalogów VC + +](reference/vcpp-directories-property-page.md) , są używane do ustawiania tych zmiennych środowiskowych. Jeśli wartości LIB, LIBPATH i INCLUDE zostały już ustawione, na przykład przez wiersz polecenia programistów, zostaną zastąpione wartościami odpowiednich właściwości programu MSBuild. Następnie kompilacja dołącza wartość właściwości katalogów plików wykonywalnych Katalogi VC++ do PATH. Można ustawić zmienną środowiskową zdefiniowaną przez użytkownika, tworząc makro zdefiniowane przez użytkownika, a następnie zaznaczając pole wyboru Dodaj **to makro jako zmienną środowiskową w środowisku kompilacji**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Ustawianie zmiennych środowiskowych dla sesji debugowania

W lewym okienku okna dialogowego **strony właściwości** projektu rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.

W prawym okienku zmodyfikuj ustawienia projektu **środowisko** lub **Scal środowisko** , a następnie wybierz przycisk **OK** .

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie lub ponowne używanie ustawień projektów programu Visual Studio](create-reusable-property-configurations.md)<br/>
Jak utworzyć plik. props z niestandardowymi ustawieniami kompilacji, które mogą być udostępniane lub ponownie używane.

[Dziedziczenie właściwości projektu](project-property-inheritance.md)<br/>
Opisuje kolejność obliczeń dla plików. props,. Target,. vcxproj i zmiennych środowiskowych w procesie kompilacji.

[Modyfikowanie właściwości i obiektów docelowych bez zmieniania pliku projektu](modify-project-properties-without-changing-project-file.md)<br/>
Jak utworzyć ustawienia kompilacji tymczasowej bez konieczności modyfikowania pliku projektu.

## <a name="see-also"></a>Zobacz też

[Projekty programu Visual Studio — C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Struktura plików vcxproj i props](reference/vcxproj-file-structure.md)<br/>
[Pliki XML strony właściwości](reference/property-page-xml-files.md)<br/>
