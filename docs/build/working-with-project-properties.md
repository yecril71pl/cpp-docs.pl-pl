---
title: Ustaw kompilator języka C++ i właściwości w programie Visual Studio kompilacji
description: Użyj środowiska IDE programu Visual Studio, aby zmienić opcje kompilatora i konsolidatora C++ i inne ustawienia kompilacji.
ms.date: 03/27/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: ab5456bfc8a1b8305813f4ee4a4399091de15aee
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564921"
---
# <a name="set-compiler-and-build-properties"></a>Ustaw kompilatora i właściwości kompilacji

W środowisku IDE, wszystkie informacje, które są potrzebne do tworzenia projektu jest przedstawiany jako *właściwości*. Informacje te obejmują nazwę aplikacji, rozszerzenie (np. biblioteki DLL, LIB i EXE), opcje kompilatora, opcje konsolidatora, ustawienia debugera, niestandardowych kroków kompilacji i wielu innych rzeczy. Zazwyczaj można użyć *stron właściwości* ( **projektu &#124; właściwości**) aby wyświetlić i zmodyfikować te właściwości. Aby uzyskać dostęp do strony właściwości, wybierz opcję **Projekt > \<Nazwa projektu > właściwości** z menu głównego, lub kliknij prawym przyciskiem myszy na węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Właściwości**.

## <a name="default-properties"></a>Właściwości domyślne

Podczas tworzenia projektu, system przypisuje wartości różnych właściwości. Wartości domyślne, różnią się nieco w zależności od typu projektu i jakie opcje należy wybrać w Kreatorze aplikacji. Na przykład Projekt ATL ma właściwości związanych z plikami MIDL, ale są nieobecne w podstawowa Aplikacja konsoli. Domyślne właściwości są wyświetlane w okienku ogólne na stronach właściwości:

![Program Visual C&#43; &#43; projektu domyślne](media/visual-c---project-defaults.png "domyślne ustawienia projektu Visual C++")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Stosowanie właściwości, aby tworzyć konfiguracje i platformy docelowej

Niektóre właściwości, takie jak nazwa aplikacji, dotyczą wszystkich zmian kompilacji, niezależnie od platformy docelowej i czy jest on kompilację debugowania lub wydania. Jednak większość właściwości jest zależne od konfiguracji. Jest to spowodowane kompilator musi wiedzieć, jakie określonej platformy, program będzie uruchamiany na i jakie kompilatora określone opcje do użycia, aby generować poprawny kod. W związku z tym po ustawieniu właściwości jest zwrócenie uwagi, konfiguracji i platformy, które dotyczą nową wartość. Powinna ona dotyczą tylko kompilacje Debug Win32 lub powinien on dotyczą również debugować ARM i debugowanie x64? Na przykład **optymalizacji** właściwość, domyślnie jest ustawiona na **Maksymalizuj prędkość (/ O2)** w konfiguracji wydania, ale jest wyłączone w konfiguracji debugowania.

Strony właściwości zaprojektowano tak, aby zawsze możesz zobaczyć, a jeśli potrzeby zmodyfikować, których konfiguracja i platforma wartość właściwości stosuje się do. Poniższa ilustracja przedstawia strony właściwości z konfiguracją i informacje o platformie w polach listy u góry. Gdy **optymalizacji** właściwość jest ustawiona w tym miejscu, będzie stosowana tylko do kompilacji Debug Win32, które akurat jest aktywnej konfiguracji przedstawione przez czerwony strzałki.

![Program Visual C&#43; &#43; stron właściwości przedstawiający aktywnej konfiguracji](media/visual-c---property-pages-showing-active-configuration.png "stron właściwości w usłudze Visual C++ przedstawiający aktywnej konfiguracji")

Na poniższej ilustracji przedstawiono na tej samej stronie właściwości projektu, ale konfiguracja została zmieniona do wydania. Należy pamiętać, inną wartość dla właściwości optymalizacji. Należy również zauważyć, że aktywnej konfiguracji jest nadal debugowania. Można ustawić właściwości dla wszystkich konfiguracji, w tym miejscu; nie musi być aktywne.

![Program Visual C&#43; &#43; konfiguracji wydania przedstawiający stron właściwości](media/visual-c---property-pages-showing-release-config.png "konfiguracji wydania przedstawiający stron właściwości w usłudze Visual C++")

## <a name="target-platforms"></a>Platformy docelowe

*Platforma docelowa* odwołuje się do typu urządzenia i/lub uruchamianego pliku wykonywalnego w systemie operacyjnym. Możesz tworzyć projekt służący do więcej niż jedną platformę. Platformy docelowe dostępne dla projektów C++ zależą od rodzaju projektu. obejmują, ale nie są ograniczone do Win32, x64, ARM, Android i iOS.     **X86** platformę docelową, które można napotkać w **programu Configuration Manager** jest taka sama jak **Win32** w natywnych projektów w języku C++. Oznacza Win32, Windows 32-bitowe i **x64** oznacza Windows 64-bitowych. Aby uzyskać więcej informacji na temat tych dwóch platform, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).

**Dowolny Procesor** wartość platformy, które można napotkać w docelowa **programu Configuration Manager** nie ma wpływu na natywnych projektów w języku C++; dotyczy C + +/ interfejsu wiersza polecenia i .NET innych typów projektów. Aby uzyskać więcej informacji, zobacz [/clrimagetype (określenie typu z obrazu CLR)](reference/clrimagetype-specify-type-of-clr-image.md).


Aby uzyskać więcej informacji na temat ustawiania właściwości kompilacji debugowania zobacz:

- [Ustawienia projektu dla konfiguracji debugowania w języku C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Ustawienia debugera i przygotowanie](/visualstudio/debugger/debugger-settings-and-preparation)
- [Przygotowanie debugowania: Typy projektów Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Określanie plików symboli (pdb) i plików źródłowych w debugerze programu Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Opcje kompilatora i konsolidatora C++

Opcje kompilatora i konsolidatora C++ znajdują się w obszarze **C/C++** i **konsolidatora** węzłów w lewym okienku w obszarze **właściwości konfiguracji**. Te wykonuje translację elementu bezpośrednio do opcji wiersza polecenia, które zostaną przekazane do kompilatora. Aby uzyskać dokumentację dotyczącą określonej opcji, wybierz opcję w środkowym okienku i naciśnij klawisz **F1**. Lub możesz przeglądać dokumentacji dla wszystkich opcji w [opcje kompilatora MSVC](reference/compiler-options.md) i [opcje konsolidatora MSVC](reference/linker-options.md). 

**Stron właściwości** wyświetlane okno dialogowe strony właściwości, które mają zastosowanie do bieżącego projektu. Na przykład, jeśli projekt nie ma pliku .idl, nie zostanie wyświetlona strona właściwości MIDL. Aby uzyskać więcej informacji o ustawieniu na poszczególnych stronach właściwości, zobacz [strony właściwości (C++)](reference/property-pages-visual-cpp.md). 

## <a name="directory-and-path-values"></a>Wartości katalogu i ścieżki

Program MSBuild obsługuje stałe kompilacji o nazwie "makrami" dla niektórych wartości ciągu obejmują katalogi i ścieżki. Te są widoczne na stronach właściwości, w którym można znaleźć i zmodyfikuj je za pomocą [Edytor właściwości](#property_editor). 

Poniższa ilustracja przedstawia strony właściwości dla projektu Visual C++. W okienku po lewej stronie **katalogi VC ++** *reguły* jest zaznaczone, a w okienku po prawej stronie zawiera listę właściwości, które są skojarzone z tą regułą. `$(...)` Wartości są nazywane *makra*. A *— makro* jest stałą czasu kompilacji, która może odnosić się do wartości, który jest zdefiniowany przez Visual Studio lub MSBuild system lub wartości zdefiniowanej przez użytkownika. Za pomocą makr zamiast jednoznacznie ustalonych wartości, takich jak ścieżki katalogów, można łatwo udostępniać ustawienia właściwości między komputerami oraz między wersjami programu Visual Studio i lepiej zagwarantować, że ustawienia projektu poprawnie w programie uczestniczyć [ dziedziczenie właściwości](project-property-inheritance.md). 

![Strony właściwości projektu](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Edytor właściwości służy do wyświetlania wartości wszystkich dostępnych makr.

### <a name="predefined-macros"></a>Wstępnie zdefiniowane makra

*makra globalne*<br/>
Dotyczy wszystkich elementów w konfiguracji projektu. Ma składnię `$(name)`. Przykładem globalnego makro jest `$(VCInstallDir)`, które przechowuje katalog główny instalacji programu Visual Studio. Makro globalne odpowiada `PropertyGroup` w programie MSBuild.

*makra elementów*<br/>
Ma składnię `%(name)`. Dla pliku makro elementu dotyczy tylko tego pliku — na przykład, można użyć `%(AdditionalIncludeDirectories)` do określenia Dołącz katalogi, które są stosowane tylko do określonego pliku. Tego rodzaju makro elementu odpowiada `ItemGroup` metadanych w programie MSBuild. Gdy jest używane w kontekście konfiguracji projektu, makro elementu stosuje się do wszystkich plików określonego typu. Na przykład C/C++ **definicje preprocesora** właściwość konfiguracji może potrwać `%(PreprocessorDefinitions)` makro elementu, który ma zastosowanie do wszystkich plików .cpp w projekcie. Tego rodzaju makro elementu odpowiada `ItemDefinitionGroup` metadanych w programie MSBuild. Aby uzyskać więcej informacji, zobacz [definicje elementu](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Makra zdefiniowane przez użytkownika

Możesz utworzyć *zdefiniowane przez użytkownika makra* do wykorzystania jako zmienne w kompilacjach projektu. Na przykład, można utworzyć makro zdefiniowane przez użytkownika, które udostępnia wartość do niestandardowego kroku kompilacji lub niestandardowego narzędzia kompilacji. Makro zdefiniowane przez użytkownika to para nazwa/wartość. W pliku projektu użyj **$(**<em>nazwa</em>**)** Notacja do uzyskania dostępu do wartości.

Makro zdefiniowane przez użytkownika jest przechowywane w arkuszu właściwości. Jeśli projekt nie zawiera jeszcze arkusza właściwości, można utworzyć jeden, wykonując kroki opisane w temacie [udziału lub ponowne użycie ustawienia projektu programu Visual Studio](create-reusable-property-configurations.md).

#### <a name="to-create-a-user-defined-macro"></a>Aby utworzyć makro zdefiniowane przez użytkownika

1. W **Menedżer właściwości** okna (na pasku menu wybierz **widoku**, **Menedżer właściwości**), otwórz menu skrótów dla arkusza właściwości (jego nazwa kończy się na .user), a następnie wybierz Właściwości. **Stron właściwości** zostanie otwarte okno dialogowe dla tego arkusza właściwości.

1. W lewym okienku okna dialogowego wybierz **makra użytkownika**. W okienku po prawej stronie wybierz **Dodaj makro** przycisk, aby otworzyć **Dodaj makro użytkownika** okno dialogowe.

1. W oknie dialogowym określ nazwę i wartość dla makra. Opcjonalnie można zaznaczyć **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji** pole wyboru.

## <a name="property_editor">Edytor właściwości</a>

Edytor właściwości służy do modyfikowania niektórych właściwości ciągów i zaznaczania makr jako wartości. Aby otworzyć Edytor właściwości, zaznacz właściwość na stronie właściwości, a następnie wybierz strzałkę w dół po prawej stronie. Jeśli zawiera listy rozwijanej  **\<Edytuj >**, a następnie wybierz pozycję go, aby wyświetlić Edytor właściwości dla tej właściwości.

![Property&#95;Editor&#95;Dropdown](media/property_editor_dropdown.png "Property_Editor_Dropdown")

W edytorze właściwości można wybrać **makra** przycisk w celu wyświetlenia dostępnych makr oraz ich bieżących wartości. Poniższa ilustracja przedstawia Edytor właściwości dla **dodatkowe katalogi dołączenia** właściwości po **makra** został wybrany przycisk. Gdy **Dziedzicz po elemencie nadrzędnym lub domyślnych wartościach projektu** pole wyboru jest zaznaczone i Dodaj nową wartość, jest ona dołączana do dowolnych wartości, które obecnie są dziedziczone. Jeśli usuniesz zaznaczenie pola wyboru, nowa wartość zamieni wartości dziedziczone. W większości przypadków pozostaw zaznaczone pole wyboru.

![Property editor, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Dodawanie katalogu plików dołączonych do zestawu katalogów domyślnych

Podczas dodawania katalogu plików dołączonych do projektu jest ważne, aby nie zastąpić domyślnych katalogów. Poprawny sposób dodania katalogu to dołączenie nowej ścieżki, na przykład "C:\MyNewIncludeDir\", a następnie dołączenie **$(IncludePath)** do wartości właściwości.

## <a name="quickly-browse-and-search-all-properties"></a>Szybko przeglądać i wyszukiwać wszystkie właściwości

**Wszystkie opcje** strony właściwości (w obszarze **właściwości konfiguracji &#124; C/C++** w węźle **stron właściwości** okno dialogowe) zapewnia szybki sposób przeglądania i wyszukiwania właściwości, które są dostępne w bieżącym kontekście. Ma specjalne pole wyszukiwania i prostą składnię, aby pomóc w filtrowaniu wyników:

Brak prefiksu:<br/>
Wyszukiwanie tylko w nazwach właściwości (podciąg bez uwzględniania wielkości liter).

'/' lub '-' :<br/>
Wyszukiwanie tylko w przełącznikach kompilatora (prefiks bez uwzględniania wielkości liter)

v:<br/>
Wyszukiwanie tylko w wartościach (podciąg bez uwzględniania wielkości liter).

## <a name="set-environment-variables-for-a-build"></a>Ustawianie zmiennych środowiskowych dla kompilacji

Kompilator MSVC (cl.exe) rozpoznaje pewne zmienne środowiskowe, w szczególności LIB, LIBPATH, PATH lub INCLUDE. Podczas kompilowania za pomocą środowiska IDE, właściwości, które są ustawiane w [VC ++ Directories Property Page](reference/vcpp-directories-property-page.md) strona właściwości są używane do ustawiania tych zmiennych środowiskowych. Jeśli wartości LIB, LIBPATH i INCLUDE zostały już ustawione, na przykład przez wiersz polecenia programistów, zostaną zastąpione wartościami odpowiednich właściwości programu MSBuild. Następnie kompilacja dołącza wartość właściwości katalogów plików wykonywalnych Katalogi VC++ do PATH. Można ustawić zmienną środowiskową zdefiniowanych przez użytkownika utworzyć makro zdefiniowane przez użytkownika, a następnie zaznaczając pole wyboru, które mówi **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Ustawianie zmiennych środowiskowych dla sesji debugowania

W okienku po lewej stronie projektu **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **debugowanie**.

W okienku po prawej stronie Zmień **środowiska** lub **Scal środowisko** ustawienia projektu, a następnie wybierz **OK** przycisku.

## <a name="in-this-section"></a>W tej sekcji

[Udostępnianie lub ponowne używanie ustawień projektów programu Visual Studio](create-reusable-property-configurations.md)<br/>
Jak utworzyć plik .props za pomocą ustawień niestandardowej kompilacji, które mogą być udostępniane lub resused.

[Dziedziczenie właściwości projektu](project-property-inheritance.md)<br/>
W tym artykule opisano kolejność obliczania, .props, .targets, pliki.vcxproj i zmiennych środowiskowych w procesie kompilacji.

[Modyfikowanie właściwości i obiektów docelowych bez zmieniania pliku projektu](modify-project-properties-without-changing-project-file.md)<br/>
Jak utworzyć ustawienia tymczasowego kompilacji bez konieczności modyfikowania pliku projektu. 

## <a name="see-also"></a>Zobacz także

[Projekty programu Visual Studio — C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Struktura plików vcxproj i props](reference/vcxproj-file-structure.md)<br/>
[Pliki XML strony właściwości](reference/property-page-xml-files.md)<br/>
