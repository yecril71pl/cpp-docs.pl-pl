---
title: Praca z właściwościami projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c33a18ff0d492ef3a870a342c9d8ff292007748
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339946"
---
# <a name="working-with-project-properties"></a>Praca z właściwościami projektu
W środowisku IDE, wszystkie informacje niezbędne do utworzenia projektu jest ujawniona jako *właściwości*. Informacje te obejmują nazwę aplikacji, rozszerzenia (takie jak biblioteki DLL, LIB EXE) — opcje kompilatora, opcje konsolidatora, ustawienia debugera, niestandardowe kroki procesu kompilacji i inne czynności. Zazwyczaj *strony właściwości* ( **projektu &#124; właściwości**) do wyświetlania i modyfikowania tych właściwości. 
  
 Podczas tworzenia projektu systemu przypisuje wartości różnych właściwości. Wartości domyślne różnią się w zależności od rodzaju projektu i opcje wybrać w Kreatorze aplikacji. Na przykład Projekt ATL ma właściwości związane z plikami MIDL, ale są nieobecne w aplikacji konsoli podstawowe. Domyślne właściwości są wyświetlane w okienku ogólne na stronach właściwości:  
  
 ![Visual C&#43; &#43; projektu domyślne](../ide/media/visual-c---project-defaults.png "domyślne projektów Visual C++")  
  
 Niektóre właściwości, takie jak nazwa aplikacji, dotyczą wszystkich zmian kompilacji, niezależnie od platformy docelowej i czy jest kompilację debugowania lub wersji. Jednak większość właściwości są zależne od konfiguracji. Jest to spowodowane kompilator musi wiedzieć, program będzie uruchamiany na określonej platformy i jakie kompilatora określonych opcji Użyj, aby wygenerować prawidłowego kodu. W związku z tym podczas ustawiania właściwości jest zwrócenie uwagi na nową wartość stosuje się do platformy i konfiguracji. Należy również stosować tylko do kompilacji debugowania Win32 lub jego stosuje się również do debugowania ARM i debugowania x64? Na przykład **optymalizacji** właściwość domyślnie jest ustawiona **Maksymalizuj szybkość (/ O2)** w wersji konfiguracji, ale jest wyłączone w konfiguracji debugowania.  
  
 Strony właściwości są zaprojektowane tak, aby zawsze można zobaczyć i zmodyfikowania konieczne, których konfiguracja i platforma wartość właściwości dotyczą. Na poniższej ilustracji przedstawiono strony właściwości configuration i platform informacje w polach listy u góry. Gdy **optymalizacji** właściwość jest ustawiona w tym miejscu, zostanie zastosowana tylko do kompilacji debugowania Win32, które odbywa się za aktywnej konfiguracji, jak to przedstawiono Czerwone strzałki.  
  
 ![Visual C&#43; &#43; strony właściwości przedstawiający aktywnej konfiguracji](../ide/media/visual-c---property-pages-showing-active-configuration.png "aktywnej konfiguracji przedstawiający stron właściwości w usłudze Visual C++")  
  
 Na poniższej ilustracji przedstawiono tej samej stronie właściwości projektu, ale zmieniono konfigurację do wydania. Należy pamiętać różnych wartości dla właściwości optymalizacji. Należy również zauważyć, że aktywnej konfiguracji jest nadal debugowania. Można ustawić właściwości dla żadnej konfiguracji nie musi być aktywne.  
  
 ![Visual C&#43; &#43; strony właściwości przedstawiający wersji konfiguracji](../ide/media/visual-c---property-pages-showing-release-config.png "config wersji przedstawiający stron właściwości w usłudze Visual C++")  
  
 System projektu opiera się na MSBuild, który definiuje formaty plików i reguł do tworzenia projektów dowolnego rodzaju. MSBuild zarządza znacznie złożoność budynku dla wielu platform i konfiguracje, ale należy zrozumieć nieco dotyczące sposobu działania. Jest to szczególnie ważne, jeśli chcesz zdefiniować konfiguracje niestandardowe lub Utwórz wielokrotnego użytku zestawy właściwości, które można udostępniać i zaimportować do wielu projektów.  
  
 Właściwości projektu są przechowywane bezpośrednio w pliku projektu (*.vcxproj) lub w innych plikach XML lub .props, że importuje plik projektu, które dostarczają wartości domyślne. Jak pokazano wcześniej, tę samą właściwość dla tej samej konfiguracji można przypisać inną wartość w różnych plikach. Podczas kompilowania projektu aparat MSBuild ocenia pliku projektu i wszystkich importowanych plików w dobrze zdefiniowanej kolejności (opisanych poniżej). Ponieważ każdy z plików jest obliczane, wszystkie wartości właściwości zdefiniowane w tym pliku zastępują istniejące wartości. Wartości, które nie są określone są dziedziczone z plików, które zostały ocenione wcześniej. W związku z tym podczas ustawiania właściwości ze strony właściwości, należy również należy zwrócić uwagę na których wartość. Jeśli wartość właściwości "X" w pliku .props, ale właściwość jest ustawiona na "Y" w pliku projektu, projekt zostanie utworzona z właściwością ustawioną wartość "Y". Jeśli tej samej właściwości jest równa "Z" w elemencie projektu, takich jak plik .cpp, aparat MSBuild użyje wartość "Z". Aby uzyskać więcej informacji, zobacz [dziedziczenia](#bkmkPropertyInheritance) dalszej części tego artykułu.  
  
## <a name="build-configurations"></a>Konfiguracje kompilacji  
 Konfiguracja jest tylko dowolnego grupy właściwości, które podano nazwę. Program Visual Studio udostępnia konfiguracje Debug i Release i każdego ustawia różne właściwości odpowiednio do kompilacji debugowania lub kompilacji wydania. Można użyć **programu Configuration Manager** Aby zdefiniować konfiguracje niestandardowe jako wygodny sposób właściwości grupy dla określonej wersji kompilacji. Służy Menedżer właściwości zaawansowane pracy z właściwościami, ale wprowadzeniu go tutaj ponieważ pomaga zwizualizować właściwości konfiguracji. Możesz uzyskać do niego dostęp z **widoku &#124; Menedżer właściwości** lub **widoku &#124; inne okna &#124; Menedżer właściwości** w zależności od ustawienia. Ma ona węzłów dla każdej pary konfiguracji/platform w projekcie. W każdej z tych węzłów są węzły arkusze właściwości (pliki .props), które ustawić niektórych właściwości specyficzne dla danej konfiguracji.  
  
 ![Menedżer właściwości](../ide/media/property-manager.png "Menedżer właściwości")  
  
 Jeśli przejdź do okienka ogólne na stronach właściwości (patrz na ilustracji powyżej) i ustaw właściwość zestawu znaków na "Nie Ustawianie" zamiast "Użyj Unicode" i kliknij polecenie **OK**, Menedżer właściwości będą wyświetlane nie **obsługi formatu Unicode** arkusz właściwości dla bieżącej konfiguracji, ale nadal będą dostępne dla innych ustawień.  
  
 Aby uzyskać więcej informacji na temat Menedżera właściwości i arkusze właściwości, zobacz [tworzenia konfiguracji wielokrotnego użytku właściwości](#bkmkPropertySheets) dalszej części tego artykułu.  
  
> [!TIP]
>  Plik .user jest funkcją starszych i firma Microsoft zaleca, usuń go, aby zachować właściwości poprawnie pogrupowane według konfiguracji/platformy.  
  
## <a name="target-platforms"></a>Platformy docelowe  
 *Platforma docelowa* odwołuje się do typu urządzenia i/lub systemu operacyjnego, uruchamianego pliku wykonywalnego. Można utworzyć projektu dla więcej niż jedną platformę. Na platformach docelowych dostępne dla projektów C++ są zależne od typu projektu. obejmują, ale nie są ograniczone do systemu Win32, x64, ARM, Android i iOS.     **X86** platformy docelowej, które można napotkać w **programu Configuration Manager** jest taka sama jak **Win32** w projektach C++ macierzystego. Win32 oznacza 32-bitowego systemu Windows i **x64** oznacza 64-bitowego systemu Windows. Aby uzyskać więcej informacji o te dwie platformy, zobacz [uruchomiona 32-bitowych aplikacji](https://msdn.microsoft.com/library/windows/desktop/aa384249\(v=vs.85\).aspx).  
  
 **Any CPU** wartość platformy, które można napotkać w docelowa **programu Configuration Manager** nie ma wpływu na projektów C++ natywnych; jest istotny dla języka C + +/ CLI i innych .NET typy projektów. Aby uzyskać więcej informacji, zobacz [clrimagetype (określenie typu z obrazu CLR)](../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
## <a name="property-pages"></a>Strony właściwości  
 Jak już wspomniano wcześniej, system projektu Visual C++ jest oparty na [MSBuild](/visualstudio/msbuild/msbuild-properties) i wartości są przechowywane w pliku projektu XML, domyślne pliki .props i .targets. Dla programu Visual Studio 2015, te pliki znajdują się w **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Dla programu Visual Studio 2017 r, te pliki znajdują się w  **\\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\_wersji_\\Common7\\ IDE\\VC\\VCTargets**, gdzie _wersji_ jest zainstalowanej wersji programu Visual Studio. Właściwości są także przechowywane w plikach .props niestandardowych, które można dodać do własnego projektu. Zdecydowanie zaleca się czy nie ręcznie edytować pliki, a zamiast tego użyć strony właściwości w IDE można zmodyfikować wszystkie właściwości, zwłaszcza tych, które uczestniczyć w dziedziczeniu, chyba że masz bardzo dobrą znajomością programu MSBuild.  
  
 Poniższa ilustracja przedstawia strony właściwości dla projektu Visual C++. W okienku po lewej stronie **katalogi VC ++ *** reguły* jest zaznaczona, i w okienku po prawej stronie listy właściwości, które są skojarzone z tej reguły. `$(...)` Wartości Niestety są nazywane *makra*. Są to *nie* makr C/C++, ale po prostu kompilacji stałe. Makra zostały omówione w [makra strony właściwości](#bkmkPropertiesVersusMacros) sekcji w dalszej części tego artykułu.)  
  
 ![Strony właściwości projektu](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")  
  
> [!WARNING]
>  **Wspólne właściwości** konfiguracje we wcześniejszych wersjach programu Visual Studio zostały usunięte. Aby dodać odwołanie do projektu, można teraz używać **Dodaj odwołanie do** okna dialogowego w taki sam sposób jak w przypadku języków zarządzanych. Zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).  
  
#### <a name="to-set-a-property-for-a-project"></a>Aby ustawić właściwość dla projektu  
  
1.  W przypadku większości scenariuszy można ustawić właściwości na poziomie projektu bez tworzenia arkusza właściwości niestandardowej. W menu głównym wybierz **projektu &#124; właściwości**, lub kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**.  
  
2.  Użyj **konfiguracji** i **platformy** Lista pól w górnej części okna dialogowego, aby określić, które właściwości grupy należy zastosować zmiany. W wielu przypadkach **wszystkich platform** i **wszystkie konfiguracje** są właściwie. Można ustawić właściwości tylko do niektórych konfiguracji wielokrotnego wyboru w **Menedżer właściwości**, a następnie otwórz menu skrótów i wybierz **właściwości**.  
  
 **Strony właściwości** wyświetlane okno dialogowe strony właściwości, które mają zastosowanie do bieżącego projektu. Na przykład, jeśli projekt nie ma pliku .idl, nie zostanie wyświetlona strona właściwości MIDL.  
  
 Po wybraniu właściwości na stronie właściwości, można nacisnąć klawisz **F1** aby przejść do tematu odwołania, aby uzyskać więcej informacji na temat odpowiedniego przełącznika kompilatora lub konsolidatora.  
  
 Więcej informacji na temat każdej strony właściwości można znaleźć w tych tematach:  
  
-   [Strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md)  
  
-   [Strona właściwości ogólnych (plik)](../ide/general-property-page-file.md)  
  
-   [Strony właściwości wiersza polecenia](../ide/command-line-property-pages.md)  
  
-   [Ustawienia projektu dla konfiguracji debugowania z C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)  
  
-   [Strona właściwości NMake](../ide/nmake-property-page.md)  
  
-   [Strony właściwości konsolidatora](../ide/linker-property-pages.md)  
  
-   [Strony właściwości zasobów](../ide/resources-property-pages.md)  
  
-   [Strony właściwości MIDL](../ide/midl-property-pages.md)  
  
-   [Strona właściwości Odwołania sieci Web](../ide/web-references-property-page.md)  
  
-   [Strona właściwości Narzędzie generowania danych XML](../ide/xml-data-generator-tool-property-page.md)  
  
## <a name="to-quickly-browse-and-search-all-properties"></a>Aby szybko przeglądać i wyszukiwanie wszystkich właściwości  
 **Wszystkie opcje** strony właściwości (w obszarze **właściwości konfiguracji &#124; C/C++** w węźle **strony właściwości** okno dialogowe) umożliwia szybkie przeglądania i wyszukiwania właściwości, które są dostępne w bieżącym kontekście. Ma specjalne pole wyszukiwania i prostą składnię, aby pomóc w filtrowaniu wyników:  
  
 Brak prefiksu:  
 Wyszukiwanie tylko w nazwach właściwości (podciąg bez uwzględniania wielkości liter).  
  
 '/' lub '-' :  
 Wyszukiwanie tylko w przełącznikach kompilatora (prefiks bez uwzględniania wielkości liter)  
  
 v:  
 Wyszukiwanie tylko w wartościach (podciąg bez uwzględniania wielkości liter).  
  
##  <a name="bkmkPropertiesVersusMacros"></a> Makra strony właściwości  
 A *makro* jest stałą kompilacji, który może odnosić się wartość, która jest definiowana za pomocą programu Visual Studio lub system programu MSBuild lub wartości zdefiniowanej przez użytkownika. Za pomocą makr zamiast jednoznacznie ustalonych wartości, takich jak ścieżki katalogów, można łatwo udostępniać ustawienia właściwości między komputerami oraz między poszczególnymi wersjami programu Visual Studio, i lepiej zagwarantować, że ustawienia projektu poprawnie uczestniczą w dziedziczeniu właściwości. Edytor właściwości służy do wyświetlania wartości wszystkich dostępnych makr.  
  
### <a name="predefined-macros"></a>Wstępnie zdefiniowane makra  
 makra globalne  
 Dotyczy wszystkich elementów w konfiguracji projektu. Ma składnię `$(name)`. Przykładem globalne makro jest `$(VCInstallDir)`, która przechowuje katalog główny instalacji programu Visual Studio. Globalne makro odpowiada `PropertyGroup` w programie MSBuild.  
  
 makra elementów  
 Ma składnię `%(name)`. Dla pliku makro element ma zastosowanie tylko do tego pliku — na przykład można użyć `%(AdditionalIncludeDirectories)` do określenia Dołącz katalogi, które mają zastosowanie tylko do określonego pliku. Ten rodzaj elementu makro odpowiada `ItemGroup` metadanych w programie MSBuild. Gdy jest używane w kontekście konfiguracji projektu, makro elementu stosuje się do wszystkich plików określonego typu. Na przykład C/C++ **definicje preprocesora** właściwości konfiguracji może potrwać `%(PreprocessorDefinitions)` makra elementu, która ma zastosowanie do wszystkich plików .cpp w projekcie. Ten rodzaj elementu makro odpowiada `ItemDefinitionGroup` metadanych w programie MSBuild. Aby uzyskać więcej informacji, zobacz [definicje elementów](/visualstudio/msbuild/item-definitions).  
  
### <a name="user-defined-macros"></a>Makra zdefiniowane przez użytkownika  
 Można utworzyć *makra zdefiniowane przez użytkownika* do użycia jako zmiennych w kompilacji projektu. Na przykład, można utworzyć makro zdefiniowane przez użytkownika, które udostępnia wartość do niestandardowego kroku kompilacji lub niestandardowego narzędzia kompilacji. Makro zdefiniowane przez użytkownika to para nazwa/wartość. W pliku projektu za pomocą **$(***nazwa***)** notacji do uzyskania dostępu do wartości.  
  
 Makro zdefiniowane przez użytkownika jest przechowywane w arkuszu właściwości. Jeśli projekt nie zawiera już arkusz właściwości, można go utworzyć, wykonując kroki opisane w temacie [tworzenia konfiguracji wielokrotnego użytku właściwości](#bkmkPropertySheets).  
  
##### <a name="to-create-a-user-defined-macro"></a>Aby utworzyć makro zdefiniowane przez użytkownika  
  
1.  W **Menedżer właściwości** okna (na pasku menu wybierz **widoku**, **Menedżer właściwości**), otwórz menu skrótów dla arkusza właściwości (jego nazwa kończy się w .user), a następnie wybierz pozycję Właściwości. **Strony właściwości** zostanie otwarte okno dialogowe dla tego arkusza właściwości.  
  
2.  W lewym okienku w oknie dialogowym wybierz **makra użytkownika**. W okienku po prawej stronie wybierz **Dodaj makro** przycisk, aby otworzyć **Dodaj makro użytkownika** okno dialogowe.  
  
3.  W oknie dialogowym określ nazwę i wartość dla makra. Opcjonalnie wybierz **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji** pole wyboru.  
  
## <a name="property-editor"></a>Edytor właściwości  
 Edytor właściwości służy do modyfikowania niektórych właściwości ciągów i zaznaczania makr jako wartości. Aby otworzyć Edytor właściwości, zaznacz właściwość na stronie właściwości, a następnie wybierz strzałkę w dół po prawej stronie. Jeśli na liście rozwijanej znajdują się  **\<Edytuj >**, a następnie wybierz pozycję go, aby wyświetlić Edytor właściwości dla tej właściwości.  
  
 ![Właściwość&#95;edytor&#95;listy rozwijanej](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")  
  
 W edytorze właściwości można wybrać **makra** przycisk, aby wyświetlić dostępne makra i ich wartości. Na poniższej ilustracji przedstawiono edytora właściwości **dodatkowe katalogi dołączenia** właściwości po **makra** wybrano przycisku. Gdy **Dziedzicz po elemencie nadrzędnym lub domyślnych wartościach projektu** pole wyboru jest zaznaczone i Dodaj nową wartość, zostanie ono dodane do wartości, które obecnie są dziedziczone. Jeśli usuniesz zaznaczenie pola wyboru, nowa wartość zamieni wartości dziedziczone. W większości przypadków pozostaw zaznaczone pole wyboru.  
  
 ![Edytor właściwości, Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")  
  
##  <a name="bkmkPropertySheets"></a> Tworzenie konfiguracji właściwości wielokrotnego użytku  
 Chociaż możesz ustawiać właściwości „globalne” dla poszczególnych użytkowników i komputerów, nie zalecamy tego. Zamiast tego zaleca się używanie **Menedżer właściwości** utworzyć *arkusza właściwości* do przechowywania ustawień dla każdego rodzaju projektu, który chcesz mieć możliwość ponownego użycia lub udostępniać innym osobom. Arkusze właściwości również sprawiają, że jest mniej prawdopodobne, że ustawienia właściwości dla innych typów projektów zostaną przypadkowo zmienione. Arkusze właściwości omówiono bardziej szczegółowo [tworzenia konfiguracji wielokrotnego użytku właściwości](#bkmkPropertySheets).  
  
> [!IMPORTANT]
>  **pliki .user i dlaczego mogą powodować problemy**  
>   
>  Arkusze właściwości globalne, ma rozszerzenie nazwy pliku .user, które znajdowały się w używane poprzednich wersji programu Visual Studio \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ folderu. Firma Microsoft nie zaleca już używania tych plików, ponieważ ustawiają one właściwości konfiguracji projektu dla poszczególnych użytkowników i konkretnych komputerów. Takie ustawienia „globalne” mogą zakłócać kompilacje, zwłaszcza gdy są one ukierunkowane na więcej niż jedną platformę na komputerze kompilacji. Na przykład, jeśli masz zarówno projekt MFC, jak i projekt Windows Phone, właściwości .user byłyby nieprawidłowe dla jednego z nich. Arkusze właściwości wielokrotnego użytku są bardziej elastyczne i bardziej niezawodne.  
>   
>  Pomimo tego, że pliki .user są nadal instalowane przez Visual Studio i uczestniczą w dziedziczeniu właściwości, są one domyślnie puste. Najlepszym rozwiązaniem jest, aby usunąć odwołania do nich w **Menedżer właściwości** w celu zapewnienia, że projekty działają niezależnie od dowolnego użytkownika, ustawienia to ważne jest, aby zapewnić poprawne zachowanie SCC (kodu źródłowego środowisko kontrola).  
  
 Aby wyświetlić **Menedżer właściwości**, na pasku menu wybierz **widoku**, **inne okna**, **Menedżer właściwości**.  
  
 Jeśli masz wspólnego, często używanych zbiór właściwości, które chcesz zastosować do wielu projektów, możesz użyć **Menedżer właściwości** uzyskanie je do ponownego użycia *arkusza właściwości* pliku, który ma Konwencja rozszerzenie nazwy pliku .props. Arkusz (lub arkusze) można stosować do nowych projektów, aby nie było konieczne ustawianie ich właściwości od podstaw. Aby uzyskać dostęp do **Menedżer właściwości**, na pasku menu wybierz **widoku**, **Menedżer właściwości**.  
  
 ![Menu skrótów Menedżer właściwości](../ide/media/sharingnew.png "SharingNew")  
  
 W każdym węźle konfiguracji zobaczysz węzłów dla każdego arkusza właściwości, która ma zastosowanie do tej konfiguracji. System dodaje arkuszy właściwości, które ustawić wartości na podstawie opcji wybranych w Kreatorze aplikacji, podczas tworzenia projektu. Kliknij prawym przyciskiem myszy dowolny węzeł i wybierz polecenie Właściwości, aby wyświetlić właściwości, które są stosowane do tego węzła. Wszystkie arkusze właściwości są automatycznie importowane do arkusza właściwości "główny" projektu (ms.cpp.props) i są oceniane w kolejności, w jakiej występują w Menedżerze właściwości. Można przenieść je, aby zmienić kolejność obliczania. Arkusze właściwości, które są oceniane później spowoduje zmianę wartości w arkuszach wcześniej obliczone.  
  
 Jeśli wybierzesz **dodać nowy projekt arkusza właściwości** i wybierz opcję, na przykład MyProps.props arkusza właściwości, okno dialogowe właściwości strony pojawi się. Należy zauważyć, że ma ona zastosowanie do arkusza właściwości MyProps; wszelkie wprowadzone zmiany są zapisywane w arkuszu, a nie w pliku projektu (.vcxproj).  
  
 Właściwości w arkuszu właściwości zostaną zastąpione, jeśli ustawiono tę samą właściwość bezpośrednio w pliku .vcxproj.  
  
 Można importować arkusz własności tak często, jak jest to wymagane. Wiele projektów w rozwiązaniu może dziedziczyć ustawienia z tego samego arkusza właściwości, a projekt może mieć wiele arkuszy. Arkusz właściwości może dziedziczyć ustawienia z innego arkusza właściwości.  
  
 Można również utworzyć jeden arkusz właściwości dla wielu konfiguracji. W tym celu należy utworzyć arkusz właściwości dla każdej konfiguracji, otwórz menu skrótów dla jednego z nich, wybierz pozycję **Dodaj istniejący arkusz właściwości**, a następnie dodaj arkuszy programu. Jednak jeśli używasz jednego wspólnego arkusza właściwości, należy pamiętać, że po ustawieniu właściwości jest ona ustawiana dla wszystkich konfiguracji, których dotyczy arkusz, a środowisko IED nie pokazuje, które projekty lub inne arkusze właściwości dziedziczą z danego arkusza właściwości.  
  
 W dużych rozwiązaniach, które będą miały wiele projektów, może być przydatne utworzenie arkusza właściwości na poziomie rozwiązania. Po dodaniu projektu do rozwiązania, użyj **Menedżer właściwości** do dodania do projektu tego arkusza właściwości. Jeśli jest to wymagane na poziomie projektu, można dodać nowy arkusz właściwości do ustawiania wartości specyficznych dla projektu.  
  
> [!IMPORTANT]
>  Domyślnie plik .props nie uczestniczy w kontroli źródła, ponieważ nie jest utworzony jako element projektu. Można ręcznie dodać plik jako element rozwiązania, jeżeli chce się go włączyć do kontroli źródła.  
  
#### <a name="to-create-a-property-sheet"></a>Aby utworzyć arkusz właściwości  
  
1.  Na pasku menu wybierz **widoku**, **Menedżer właściwości**. **Menedżer właściwości** otwiera.  
  
2.  Aby zdefiniować zakres arkusza właściwości, wybierz element, do którego ma to zastosowanie. Może to być określona konfiguracja lub inny arkusz właściwości. Otwórz menu skrótów dla tego elementu, a następnie wybierz pozycję **dodać nowy projekt arkusza właściwości**. Określ nazwę i lokalizację.  
  
3.  W **Menedżer właściwości**, otwórz nowy arkusz właściwości, a następnie ustaw właściwości, które chcesz dołączyć.  
  
##  <a name="bkmkPropertyInheritance"></a> Dziedziczenie właściwości  
 Właściwości projektu są warstwowe. Każda warstwa dziedziczy wartości poprzedniej warstwy, ale dziedziczone wartości mogą być zastąpione przez ustawienie właściwości w sposób jawny. Oto podstawowe drzewo dziedziczenia:  
  
1.  Domyślne ustawienia z zestawu narzędzi CPP MSBuild (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.cpp.default.props, który jest importowany przez plik .vcxproj.)  
  
2.  Arkusze właściwości  
  
3.  Plik .vcxproj. (Można zastąpić ustawienia domyślne i ustawienia arkusza właściwości.)  
  
4.  Metadane elementów  
  
> [!TIP]
>  Na stronie właściwości, właściwość `bold` jest zdefiniowana w bieżącym kontekście. Właściwość czcionką normalną jest dziedziczona.  
  
 Plik projektu (.vcxproj) importuje inne arkusze właściwości podczas procesu kompilacji. Po zaimportowaniu wszystkich arkuszy właściwości, plik projektu jest oceniany i ostatnia definicja dowolnej wartości właściwości jest tą, która będzie używana. Czasami warto wyświetlić plik rozszerzony w celu stwierdzenia, jak jest dziedziczona dana wartość właściwości. Aby wyświetlić rozszerzoną wersję, wprowadź następujące polecenie w wierszu polecenia Visual Studio. (Zastąp nazwy plików zastępczych nazwami, których chcesz używać.)  
  
 **MSBUILD /pp:** *temp* **.txt** *moja_aplikacja* **.vcxproj**  
  
 Rozwinięte pliki projektu mogą być duże i trudne do zrozumienia, chyba że znasz MSBuild. Oto podstawowa struktura pliku projektu:  
  
1.  Podstawowe właściwości projektu, które nie są udostępniane w środowisku IDE.  
  
2.  Import pliku Microsoft.cpp.default.props, który określa pewne właściwości podstawowe, niezależne od zestawu narzędzi.  
  
3.  Globalne właściwości konfiguracji (udostępniany jako **jest zestaw narzędzi platformy** i **projektu** domyślnej właściwości na **ogólne konfiguracji** strony. Te właściwości określają, który zestaw narzędzi i które wewnętrzne arkusze właściwości są importowane w pliku Microsoft.cpp.props w następnym kroku.  
  
4.  Import pliku Microsoft.cpp.props, który określa większość ustawień domyślnych projektu.  
  
5.  Import wszystkich arkuszy właściwości, w tym plików .user. Arkusze właściwości można zastąpić wszystkie elementy z wyjątkiem **jest zestaw narzędzi platformy** i **projektu** domyślnej właściwości.  
  
6.  Pozostałe właściwości konfiguracji projektu. Te wartości mogą zastąpić to, co ustawiono w arkuszach właściwości.  
  
7.  Elementy (pliki) wraz z ich metadanymi. To jest zawsze ostateczny wynik, jeśli chodzi o reguły oceny MSBuild, nawet jeśli występują one przed innymi właściwościami i importami.  
  
 Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>Dodawanie katalogu plików dołączonych do zestawu katalogów domyślnych  
 Podczas dodawania katalogu plików dołączonych do projektu jest ważne, aby nie zastąpić domyślnych katalogów. Prawidłowy sposób, aby dodać katalog są dołączane nowej ścieżki, na przykład "C:\MyNewIncludeDir\", a następnie dołącz **$(IncludePath)** makra w wartości właściwości.  
  
## <a name="setting-environment-variables-for-a-build"></a>Ustawianie zmiennych środowiskowych dla kompilacji  
 Kompilator języka Visual C++ (cl.exe) rozpoznaje pewne zmienne środowiskowe, w szczególności LIB, LIBPATH, PATH i INCLUDE. Podczas budowania z IDE, właściwości, które są ustawione w [strona właściwości katalogów VC ++](../ide/vcpp-directories-property-page.md) strony właściwości używanych do ustawiania tych zmiennych środowiskowych. Jeśli wartości LIB, LIBPATH i INCLUDE zostały już ustawione, na przykład przez wiersz polecenia programistów, zostaną zastąpione wartościami odpowiednich właściwości programu MSBuild. Następnie kompilacja dołącza wartość właściwości katalogów plików wykonywalnych Katalogi VC++ do PATH. Można ustawić zmienną środowiskową użytkownika utworzone makra zdefiniowane przez użytkownika, a następnie zaznaczając pole **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji**.  
  
## <a name="setting-environment-variables-for-a-debugging-session"></a>Ustawianie zmiennych środowiskowych dla sesji debugowania  
 W okienku po lewej stronie projektu **strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **debugowanie**. 
  
 W okienku po prawej stronie Zmień **środowiska** lub **Scal środowisko** projektu ustawienia, a następnie wybierz pozycję **OK** przycisku.  

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>Modyfikowanie właściwości i elementów docelowych bez zmiany pliku projektu
Można zastąpić właściwości projektu i obiektów docelowych w wierszu polecenia programu MSBuild bez zmiany pliku projektu. Jest to przydatne, gdy chcesz zastosować niektórych właściwości tymczasowo lub co pewien czas. Zakłada się pewna znajomość programu MSBuild. Aby uzyskać więcej informacji, zobacz [MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Edytor XML w Visual Studio lub dowolnego edytora tekstu, służy do tworzenia pliku .props lub .targets. Nie używaj **Menedżer właściwości** w tym scenariuszu ponieważ dodaje właściwości do pliku projektu.

*Aby zastąpić właściwości projektu:*
- Utwórz plik .props, który określa właściwości, które chcesz zastąpić. 
- W wierszu polecenia: Ustaw ForceImportBeforeCppTargets="C:\sources\my_props.props"
 
*Aby zastąpić obiekty docelowe projektu:*
1) Utwórz plik .targets z ich realizacji lub określonej lokalizacji docelowej
2) W wierszu polecenia: Ustaw ForceImportAfterCppTargets = "C:\sources\my_target.targets"
 
Można też ustawić jedną z tych opcji w wierszu polecenia programu msbuild przy użyciu opcji/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props" 
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets" 
```  

Zastępowanie właściwości i elementów docelowych w ten sposób jest odpowiednikiem dodając następujące instrukcje importu do wszystkich plików .vcxproj w rozwiązaniu:

```cmd 
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```  

## <a name="see-also"></a>Zobacz też  
 [Tworzenie i zarządzanie projektami Visual C++](../ide/creating-and-managing-visual-cpp-projects.md) [struktury plików .vcxproj i .props](vcxproj-file-structure.md) [pliki XML strony właściwości](property-page-xml-files.md)