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
ms.openlocfilehash: 460cc5fbca12d433f807d3c19603ba606be514c8
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42464857"
---
# <a name="working-with-project-properties"></a>Praca z właściwościami projektu
W środowisku IDE, wszystkie informacje, które są potrzebne do tworzenia projektu jest przedstawiany jako *właściwości*. Informacje te obejmują nazwę aplikacji, rozszerzenie (np. biblioteki DLL, LIB i EXE), opcje kompilatora, opcje konsolidatora, ustawienia debugera, niestandardowych kroków kompilacji i wielu innych rzeczy. Zazwyczaj można użyć *stron właściwości* ( **projektu &#124; właściwości**) aby wyświetlić i zmodyfikować te właściwości. 
  
 Podczas tworzenia projektu, system przypisuje wartości różnych właściwości. Wartości domyślne, różnią się nieco w zależności od typu projektu i jakie opcje należy wybrać w Kreatorze aplikacji. Na przykład Projekt ATL ma właściwości związanych z plikami MIDL, ale są nieobecne w podstawowa Aplikacja konsoli. Domyślne właściwości są wyświetlane w okienku ogólne na stronach właściwości:  
  
 ![Program Visual C&#43; &#43; projektu domyślne](../ide/media/visual-c---project-defaults.png "domyślne ustawienia projektu Visual C++")  
  
 Niektóre właściwości, takie jak nazwa aplikacji, dotyczą wszystkich zmian kompilacji, niezależnie od platformy docelowej i czy jest on kompilację debugowania lub wydania. Jednak większość właściwości jest zależne od konfiguracji. Jest to spowodowane kompilator musi wiedzieć, jakie określonej platformy, program będzie uruchamiany na i jakie kompilatora określone opcje do użycia, aby generować poprawny kod. W związku z tym po ustawieniu właściwości jest zwrócenie uwagi, konfiguracji i platformy, które dotyczą nową wartość. Powinna ona dotyczą tylko kompilacje Debug Win32 lub powinien on dotyczą również debugować ARM i debugowanie x64? Na przykład **optymalizacji** właściwość, domyślnie jest ustawiona na **Maksymalizuj prędkość (/ O2)** w konfiguracji wydania, ale jest wyłączone w konfiguracji debugowania.  
  
 Strony właściwości zaprojektowano tak, aby zawsze możesz zobaczyć, a jeśli potrzeby zmodyfikować, których konfiguracja i platforma wartość właściwości stosuje się do. Poniższa ilustracja przedstawia strony właściwości z konfiguracją i informacje o platformie w polach listy u góry. Gdy **optymalizacji** właściwość jest ustawiona w tym miejscu, będzie stosowana tylko do kompilacji Debug Win32, które akurat jest aktywnej konfiguracji przedstawione przez czerwony strzałki.  
  
 ![Program Visual C&#43; &#43; stron właściwości przedstawiający aktywnej konfiguracji](../ide/media/visual-c---property-pages-showing-active-configuration.png "stron właściwości w usłudze Visual C++ przedstawiający aktywnej konfiguracji")  
  
 Na poniższej ilustracji przedstawiono na tej samej stronie właściwości projektu, ale konfiguracja została zmieniona do wydania. Należy pamiętać, inną wartość dla właściwości optymalizacji. Należy również zauważyć, że aktywnej konfiguracji jest nadal debugowania. Można ustawić właściwości dla wszystkich konfiguracji, w tym miejscu; nie musi być aktywne.  
  
 ![Program Visual C&#43; &#43; konfiguracji wydania przedstawiający stron właściwości](../ide/media/visual-c---property-pages-showing-release-config.png "konfiguracji wydania przedstawiający stron właściwości w usłudze Visual C++")  
  
 Sam system projektu zależy od platformy MSBuild definiuje formaty plików i reguł do tworzenia projektów wszelkiego rodzaju. Program MSBuild zarządza wiele trudności, ponieważ tworzenie dla wielu platform i konfiguracje, ale trzeba nieco wiedzieć o tym, jak działa. Jest to szczególnie ważne, jeśli chcesz zdefiniować konfiguracje niestandardowe lub Utwórz wielokrotnego użytku zestawy właściwości, które można udostępniać i zaimportować do wielu projektów.  
  
 Właściwości projektu są przechowywane bezpośrednio w pliku projektu (*.vcxproj) lub w innych plikach XML lub .props, że import pliku projektu, które dostarczają wartości domyślne. Jak pokazano wcześniej, tę samą właściwość dla taką samą konfigurację można przypisać inną wartość w różnych plikach. Podczas tworzenia projektu, aparat MSBuild oblicza plik projektu i wszystkie zaimportowane pliki w dobrze zdefiniowanej kolejności (opisanych poniżej). Zgodnie z każdego pliku jest oceniany, wszystkie wartości właściwości zdefiniowane w tym pliku spowoduje zastąpienie istniejących wartości. Wszelkie wartości, które nie zostały określone są dziedziczone z plików, które zostały ocenione wcześniej. W związku z tym podczas ustawiania właściwości na stronach właściwości warto również zwrócić uwagę na gdzie ustawić. Jeśli właściwość jest ustawiona na "X" w pliku .props, ale właściwości jest równa "Y" w pliku projektu, projekt zostanie skompilowany z właściwością "Y". Jeśli w tej samej właściwości jest równa "Z" dla elementu projektu, np. plik .cpp, aparat MSBuild będzie używać wartości "Z". Aby uzyskać więcej informacji, zobacz [dziedziczenia właściwości](#bkmkPropertyInheritance) w dalszej części tego artykułu.  
  
## <a name="build-configurations"></a>Konfiguracje kompilacji  
 Konfiguracja jest po prostu dowolne grupy właściwości, które są określone nazwy. Program Visual Studio oferuje konfiguracje Debug i Release, i każdy ustawia różne właściwości odpowiednio do kompilacji debugowania lub kompilacji wydania. Możesz użyć **programu Configuration Manager** konfiguracje niestandardowe jest definiowana jako wygodny sposób właściwości grupy dla określonej wersji kompilacji. Menedżer właściwości służy do zaawansowanych Praca z właściwościami, ale wprowadzeniu go w tym miejscu, ponieważ ułatwia wizualizowanie konfiguracji właściwości. Możesz uzyskać do niego dostęp z **widoku &#124; Menedżer właściwości** lub **widoku &#124; Windows inne &#124; Menedżer właściwości** w zależności od ustawień. W projekcie ma węzły dla każdej pary konfiguracji i platformy. W każdym z tych węzłów są węzły arkusze właściwości (pliki .props), które ustawić niektóre określonych właściwości dla tej konfiguracji.  
  
 ![Menedżer właściwości](../ide/media/property-manager.png "Menedżer właściwości")  
  
 Jeśli przejdź do okienka ogólne na stronach właściwości (patrz ilustracja powyżej) i ustaw właściwość zestawu znaków na "Nieustawione" zamiast "Użyj Unicode" i kliknij **OK**, wyświetli się Menedżer właściwości nie **obsługi standardu Unicode** arkusz właściwości dla bieżącej konfiguracji, ale nadal będą dostępne dla innych konfiguracji.  
  
 Aby uzyskać więcej informacji o Menedżerze właściwości i arkuszach właściwości, zobacz [tworzenia konfiguracji właściwości wielokrotnego użytku](#bkmkPropertySheets) w dalszej części tego artykułu.  
  
> [!TIP]
>  Plik .user, odnoszący jest funkcją starszej wersji, a firma Microsoft zaleca, Usuń Aby zachować właściwości poprawnie pogrupowane według konfiguracji i platformy.  
  
## <a name="target-platforms"></a>Platformy docelowe  
 *Platforma docelowa* odwołuje się do typu urządzenia i/lub uruchamianego pliku wykonywalnego w systemie operacyjnym. Możesz tworzyć projekt służący do więcej niż jedną platformę. Platformy docelowe dostępne dla projektów C++ zależą od rodzaju projektu. obejmują, ale nie są ograniczone do Win32, x64, ARM, Android i iOS.     **X86** platformę docelową, które można napotkać w **programu Configuration Manager** jest taka sama jak **Win32** w natywnych projektów w języku C++. Oznacza Win32, Windows 32-bitowe i **x64** oznacza Windows 64-bitowych. Aby uzyskać więcej informacji na temat tych dwóch platform, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 **Dowolny Procesor** wartość platformy, które można napotkać w docelowa **programu Configuration Manager** nie ma wpływu na natywnych projektów w języku C++; dotyczy C + +/ interfejsu wiersza polecenia i .NET innych typów projektów. Aby uzyskać więcej informacji, zobacz [/clrimagetype (określenie typu z obrazu CLR)](../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
## <a name="property-pages"></a>Strony właściwości  
 Jak wspomniano wcześniej, system projektów języka Visual C++ opiera się na [MSBuild](/visualstudio/msbuild/msbuild-properties) i wartości są przechowywane w pliku XML projektu domyślne pliki .props i .targets. Dla programu Visual Studio 2015, te pliki znajdują się w **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Dla programu Visual Studio 2017, te pliki znajdują się w  **\\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\_wersji_\\Common7\\ IDE\\VC\\VCTargets**, gdzie _wersji_ jest zainstalowanej wersji programu Visual Studio. Właściwości są także przechowywane w plikach .props niestandardowych, które można dodać do własnego projektu. Zdecydowanie zalecamy czy nie ręcznie edytować tych plików, a zamiast tego użyć strony właściwości w środowisku IDE, aby zmodyfikować wszystkie właściwości, zwłaszcza tych, które uczestniczą w dziedziczeniu, chyba że masz bardzo dobre Omówienie programu MSBuild.  
  
 Poniższa ilustracja przedstawia strony właściwości dla projektu Visual C++. W okienku po lewej stronie **katalogi VC ++ *** reguły* jest zaznaczone, a w okienku po prawej stronie zawiera listę właściwości, które są skojarzone z tą regułą. `$(...)` Wartości Niestety są nazywane *makra*. Są to *nie* makra języka C/C++, ale po prostu kompilacji stałe. Makra są omówione w [makra strony właściwości](#bkmkPropertiesVersusMacros) sekcję w dalszej części tego artykułu.)  
  
 ![Strony właściwości projektu](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")  
  
> [!WARNING]
>  **Wspólne właściwości** konfiguracje we wcześniejszych wersjach programu Visual Studio zostały usunięte. Aby dodać odwołanie do projektu, możesz teraz używać **Dodaj odwołanie** okna dialogowego w taki sam sposób jak w przypadku języków zarządzanych. Zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).  
  
#### <a name="to-set-a-property-for-a-project"></a>Aby ustawić właściwość dla projektu  
  
1.  W przypadku większości scenariuszy można ustawić właściwości na poziomie projektu, bez tworzenia arkusz właściwości niestandardowych. W menu głównym wybierz **projektu &#124; właściwości**, lub kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**.  
  
2.  Użyj **konfiguracji** i **platformy** listy pól w górnej części okna dialogowego, aby określić, które właściwości grupy należy zastosować zmiany. W wielu przypadkach **wszystkich platform** i **wszystkie konfiguracje** są właściwym wyborem. Aby ustawić właściwości tylko niektórych konfiguracji, zaznacz je w oknie **Menedżer właściwości**, a następnie otwórz menu skrótów i wybierz **właściwości**.  
  
 **Stron właściwości** wyświetlane okno dialogowe strony właściwości, które są stosowane do bieżącego projektu. Na przykład, jeśli projekt nie ma pliku .idl, nie zostanie wyświetlona strona właściwości MIDL.  
  
 Po wybraniu właściwości na stronie właściwości, możesz nacisnąć przycisk **F1** można przejść do tematu odwołania, aby uzyskać więcej informacji na temat odpowiedni przełącznik kompilator lub konsolidator.  
  
 Więcej informacji na temat każdej strony właściwości można znaleźć w następujących tematach:  
  
-   [Strona właściwości ogólnych (projekt)](../ide/general-property-page-project.md)  
  
-   [Strona właściwości ogólnych (plik)](../ide/general-property-page-file.md)  
  
-   [Strony właściwości wiersza polecenia](../ide/command-line-property-pages.md)  
  
-   [Ustawienia projektu dla konfiguracji debugowania języka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)  
  
-   [Strona właściwości NMake](../ide/nmake-property-page.md)  
  
-   [Strony właściwości konsolidatora](../ide/linker-property-pages.md)  
  
-   [Strony właściwości zasobów](../ide/resources-property-pages.md)  
  
-   [Strony właściwości MIDL](../ide/midl-property-pages.md)  
  
-   [Strona właściwości Odwołania sieci Web](../ide/web-references-property-page.md)  
  
-   [Strona właściwości Narzędzie generowania danych XML](../ide/xml-data-generator-tool-property-page.md)  
  
## <a name="to-quickly-browse-and-search-all-properties"></a>Aby szybko przeglądać i wyszukiwać wszystkie właściwości  
 **Wszystkie opcje** strony właściwości (w obszarze **właściwości konfiguracji &#124; C/C++** w węźle **stron właściwości** okno dialogowe) zapewnia szybki sposób przeglądania i wyszukiwania właściwości, które są dostępne w bieżącym kontekście. Ma specjalne pole wyszukiwania i prostą składnię, aby pomóc w filtrowaniu wyników:  
  
 Brak prefiksu:  
 Wyszukiwanie tylko w nazwach właściwości (podciąg bez uwzględniania wielkości liter).  
  
 '/' lub '-' :  
 Wyszukiwanie tylko w przełącznikach kompilatora (prefiks bez uwzględniania wielkości liter)  
  
 v:  
 Wyszukiwanie tylko w wartościach (podciąg bez uwzględniania wielkości liter).  
  
##  <a name="bkmkPropertiesVersusMacros"></a> Makra strony właściwości  
 A *— makro* jest stałą czasu kompilacji, która może odnosić się do wartości, który jest zdefiniowany przez Visual Studio lub MSBuild system lub wartości zdefiniowanej przez użytkownika. Za pomocą makr zamiast jednoznacznie ustalonych wartości, takich jak ścieżki katalogów, można łatwo udostępniać ustawienia właściwości między komputerami oraz między poszczególnymi wersjami programu Visual Studio, i lepiej zagwarantować, że ustawienia projektu poprawnie uczestniczą w dziedziczeniu właściwości. Edytor właściwości służy do wyświetlania wartości wszystkich dostępnych makr.  
  
### <a name="predefined-macros"></a>Wstępnie zdefiniowane makra  
 makra globalne  
 Dotyczy wszystkich elementów w konfiguracji projektu. Ma składnię `$(name)`. Przykładem globalnego makro jest `$(VCInstallDir)`, które przechowuje katalog główny instalacji programu Visual Studio. Makro globalne odpowiada `PropertyGroup` w programie MSBuild.  
  
 makra elementów  
 Ma składnię `%(name)`. Dla pliku makro elementu dotyczy tylko tego pliku — na przykład, można użyć `%(AdditionalIncludeDirectories)` do określenia Dołącz katalogi, które są stosowane tylko do określonego pliku. Tego rodzaju makro elementu odpowiada `ItemGroup` metadanych w programie MSBuild. Gdy jest używane w kontekście konfiguracji projektu, makro elementu stosuje się do wszystkich plików określonego typu. Na przykład C/C++ **definicje preprocesora** właściwość konfiguracji może potrwać `%(PreprocessorDefinitions)` makro elementu, który ma zastosowanie do wszystkich plików .cpp w projekcie. Tego rodzaju makro elementu odpowiada `ItemDefinitionGroup` metadanych w programie MSBuild. Aby uzyskać więcej informacji, zobacz [definicje elementu](/visualstudio/msbuild/item-definitions).  
  
### <a name="user-defined-macros"></a>Makra zdefiniowane przez użytkownika  
 Możesz utworzyć *zdefiniowane przez użytkownika makra* do wykorzystania jako zmienne w kompilacjach projektu. Na przykład, można utworzyć makro zdefiniowane przez użytkownika, które udostępnia wartość do niestandardowego kroku kompilacji lub niestandardowego narzędzia kompilacji. Makro zdefiniowane przez użytkownika to para nazwa/wartość. W pliku projektu użyj **$(***nazwa***)** Notacja do uzyskania dostępu do wartości.  
  
 Makro zdefiniowane przez użytkownika jest przechowywane w arkuszu właściwości. Jeśli projekt nie zawiera jeszcze arkusza właściwości, można utworzyć jeden, wykonując kroki opisane w temacie [tworzenia konfiguracji właściwości wielokrotnego użytku](#bkmkPropertySheets).  
  
##### <a name="to-create-a-user-defined-macro"></a>Aby utworzyć makro zdefiniowane przez użytkownika  
  
1.  W **Menedżer właściwości** okna (na pasku menu wybierz **widoku**, **Menedżer właściwości**), otwórz menu skrótów dla arkusza właściwości (jego nazwa kończy się na .user), a następnie wybierz Właściwości. **Stron właściwości** zostanie otwarte okno dialogowe dla tego arkusza właściwości.  
  
2.  W lewym okienku okna dialogowego wybierz **makra użytkownika**. W okienku po prawej stronie wybierz **Dodaj makro** przycisk, aby otworzyć **Dodaj makro użytkownika** okno dialogowe.  
  
3.  W oknie dialogowym określ nazwę i wartość dla makra. Opcjonalnie można zaznaczyć **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji** pole wyboru.  
  
## <a name="property-editor"></a>Edytor właściwości  
 Edytor właściwości służy do modyfikowania niektórych właściwości ciągów i zaznaczania makr jako wartości. Aby otworzyć Edytor właściwości, zaznacz właściwość na stronie właściwości, a następnie wybierz strzałkę w dół po prawej stronie. Jeśli zawiera listy rozwijanej  **\<Edytuj >**, a następnie wybierz pozycję go, aby wyświetlić Edytor właściwości dla tej właściwości.  
  
 ![Właściwość&#95;edytora&#95;listy rozwijanej](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")  
  
 W edytorze właściwości można wybrać **makra** przycisk w celu wyświetlenia dostępnych makr oraz ich bieżących wartości. Poniższa ilustracja przedstawia Edytor właściwości dla **dodatkowe katalogi dołączenia** właściwości po **makra** został wybrany przycisk. Gdy **Dziedzicz po elemencie nadrzędnym lub domyślnych wartościach projektu** pole wyboru jest zaznaczone i Dodaj nową wartość, jest ona dołączana do dowolnych wartości, które obecnie są dziedziczone. Jeśli usuniesz zaznaczenie pola wyboru, nowa wartość zamieni wartości dziedziczone. W większości przypadków pozostaw zaznaczone pole wyboru.  
  
 ![Edytor właściwości, Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")  
  
##  <a name="bkmkPropertySheets"></a> Tworzenie konfiguracji właściwości wielokrotnego użytku  
 Chociaż możesz ustawiać właściwości „globalne” dla poszczególnych użytkowników i komputerów, nie zalecamy tego. Zamiast tego zaleca się używanie **Menedżer właściwości** utworzyć *arkusza właściwości* do przechowywania ustawień dla każdego rodzaju projektu, który chcesz mieć możliwość ponownego użycia lub udostępnienia innym osobom. Arkusze właściwości również sprawiają, że jest mniej prawdopodobne, że ustawienia właściwości dla innych typów projektów zostaną przypadkowo zmienione. Arkusze właściwości są szczegółowo omówione w [tworzenia konfiguracji właściwości wielokrotnego użytku](#bkmkPropertySheets).  
  
> [!IMPORTANT]
>  **pliki .user i kwestia ich problematyczności**  
>   
>  Poprzednich wersji programu Visual Studio używały arkuszy właściwości globalnych, które miały rozszerzenie nazwy pliku .user i znajdowały się w \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ folder. Firma Microsoft nie zaleca już używania tych plików, ponieważ ustawiają one właściwości konfiguracji projektu dla poszczególnych użytkowników i konkretnych komputerów. Takie ustawienia „globalne” mogą zakłócać kompilacje, zwłaszcza gdy są one ukierunkowane na więcej niż jedną platformę na komputerze kompilacji. Na przykład, jeśli masz zarówno projekt MFC, jak i projekt Windows Phone, właściwości .user byłyby nieprawidłowe dla jednego z nich. Arkusze właściwości wielokrotnego użytku są bardziej elastyczne i bardziej niezawodne.  
>   
>  Pomimo tego, że pliki .user są nadal instalowane przez Visual Studio i uczestniczą w dziedziczeniu właściwości, są one domyślnie puste. Najlepszym rozwiązaniem jest usunięcie odwołania do nich w **Menedżer właściwości** w celu zapewnienia, że projekty będą działać niezależnie od dowolnego użytkownika, ustawienia to ważne jest zapewnienie poprawnego zachowania w SCC (kod źródłowy środowisko Control).  
  
 Aby wyświetlić **Menedżer właściwości**, na pasku menu wybierz **widoku**, **Windows inne**, **Menedżer właściwości**.  
  
 Jeśli masz wspólny, często używany zestaw właściwości, które chcesz zastosować do wielu projektów, możesz użyć **Menedżer właściwości** aby uchwycić je w do ponownego użycia *arkusza właściwości* pliku, który zwyczajowo ma rozszerzenie nazwy pliku .props. Arkusz (lub arkusze) można stosować do nowych projektów, aby nie było konieczne ustawianie ich właściwości od podstaw. Aby uzyskać dostęp do **Menedżer właściwości**, na pasku menu wybierz **widoku**, **Menedżer właściwości**.  
  
 ![Menu skrótów Menedżer właściwości](../ide/media/sharingnew.png "SharingNew")  
  
 W każdym węźle konfiguracji zobaczysz węzłów dla każdego arkusza właściwości, która ma zastosowanie do konfiguracji. System dodaje arkuszy właściwości, które ustawić wartości na podstawie opcji wybranych w Kreatorze aplikacji, podczas tworzenia projektu. Kliknij prawym przyciskiem myszy dowolny węzeł, a następnie wybierz polecenie Właściwości, aby wyświetlić właściwości, które są stosowane do tego węzła. Wszystkie arkusze właściwości są automatycznie importowane do arkusza właściwości "główną" projektu (ms.cpp.props) i są obliczane w kolejności, w jakiej znajdują się w Menedżerze właściwości. Możesz przenieść je, aby zmienić kolejność oceny. Arkusze właściwości, które zostaną później ocenione spowoduje zastąpienie wartości w arkuszach wcześniej obliczane.  
  
 Jeśli wybierzesz **Dodaj nowy arkusz właściwości projektu** i następnie wybierzesz na przykład arkusz właściwości MyProps.props, okno dialogowe strony właściwości jest wyświetlana. Należy zauważyć, że ma ona zastosowanie do arkusza właściwości MyProps; wszelkie wprowadzone zmiany są zapisywane w arkuszu, a nie w pliku projektu (.vcxproj).  
  
 Właściwości w arkuszu właściwości zostaną zastąpione, jeśli ustawiono tę samą właściwość bezpośrednio w pliku .vcxproj.  
  
 Można importować arkusz własności tak często, jak jest to wymagane. Wiele projektów w rozwiązaniu może dziedziczyć ustawienia z tego samego arkusza właściwości, a projekt może mieć wiele arkuszy. Arkusz właściwości może dziedziczyć ustawienia z innego arkusza właściwości.  
  
 Można również utworzyć jeden arkusz właściwości dla wielu konfiguracji. W tym celu należy utworzyć arkusz właściwości dla każdej konfiguracji, otwórz menu skrótów dla jednej z nich, wybierz polecenie **Dodaj istniejący arkusz właściwości**, a następnie dodaj inne arkusze. Jednak jeśli używasz jednego wspólnego arkusza właściwości, należy pamiętać, że po ustawieniu właściwości jest ona ustawiana dla wszystkich konfiguracji, których dotyczy arkusz, a środowisko IED nie pokazuje, które projekty lub inne arkusze właściwości dziedziczą z danego arkusza właściwości.  
  
 W dużych rozwiązaniach, które będą miały wiele projektów, może być przydatne utworzenie arkusza właściwości na poziomie rozwiązania. Po dodaniu projektu do rozwiązania, użyj **Menedżer właściwości** Dodaj arkusz właściwości do projektu. Jeśli jest to wymagane na poziomie projektu, można dodać nowy arkusz właściwości do ustawiania wartości specyficznych dla projektu.  
  
> [!IMPORTANT]
>  Domyślnie plik .props nie uczestniczy w kontroli źródła, ponieważ nie jest utworzony jako element projektu. Można ręcznie dodać plik jako element rozwiązania, jeżeli chce się go włączyć do kontroli źródła.  
  
#### <a name="to-create-a-property-sheet"></a>Aby utworzyć arkusz właściwości  
  
1.  Na pasku menu wybierz **widoku**, **Menedżer właściwości**. **Menedżer właściwości** zostanie otwarty.  
  
2.  Aby zdefiniować zakres arkusza właściwości, wybierz element, do którego ma to zastosowanie. Może to być określona konfiguracja lub inny arkusz właściwości. Otwórz menu skrótów dla tego elementu, a następnie wybierz **Dodaj nowy arkusz właściwości projektu**. Określ nazwę i lokalizację.  
  
3.  W **Menedżer właściwości**, otwórz nowy arkusz właściwości, a następnie ustaw właściwości, które chcesz dołączyć.  
  
##  <a name="bkmkPropertyInheritance"></a> Dziedziczenie właściwości  
 Właściwości projektu są warstwowe. Każda warstwa dziedziczy wartości poprzedniej warstwy, ale dziedziczone wartości mogą być zastąpione przez ustawienie właściwości w sposób jawny. Oto podstawowe drzewo dziedziczenia:  
  
1.  Domyślne ustawienia z zestawu narzędzi CPP MSBuild (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.cpp.default.props, który jest importowany przez plik .vcxproj.)  
  
2.  Arkusze właściwości  
  
3.  Plik .vcxproj. (Można zastąpić ustawienia domyślne i ustawienia arkusza właściwości.)  
  
4.  Metadane elementów  
  
> [!TIP]
>  Na stronie właściwości, właściwość w `bold` jest zdefiniowany w bieżącym kontekście. Właściwość czcionką normalną jest dziedziczona.  
  
 Plik projektu (.vcxproj) importuje inne arkusze właściwości podczas procesu kompilacji. Po zaimportowaniu wszystkich arkuszy właściwości, plik projektu jest oceniany i ostatnia definicja dowolnej wartości właściwości jest tą, która będzie używana. Czasami warto wyświetlić plik rozszerzony w celu stwierdzenia, jak jest dziedziczona dana wartość właściwości. Aby wyświetlić rozszerzoną wersję, wprowadź następujące polecenie w wierszu polecenia Visual Studio. (Zastąp nazwy plików zastępczych nazwami, których chcesz używać.)  
  
 **Program MSBuild /pp:** *temp* **.txt** *myapp* **.vcxproj**  
  
 Rozwinięte pliki projektu mogą być duże i trudne do zrozumienia, chyba że znasz MSBuild. Oto podstawowa struktura pliku projektu:  
  
1.  Podstawowe właściwości projektu, które nie są udostępniane w środowisku IDE.  
  
2.  Import pliku Microsoft.cpp.default.props, który określa pewne właściwości podstawowe, niezależne od zestawu narzędzi.  
  
3.  Globalne właściwości konfiguracji (udostępniane jako **PlatformToolset** i **projektu** właściwości domyślnych na **ogólne ustawienia konfiguracji** strony. Te właściwości określają, który zestaw narzędzi i które wewnętrzne arkusze właściwości są importowane w pliku Microsoft.cpp.props w następnym kroku.  
  
4.  Import pliku Microsoft.cpp.props, który określa większość ustawień domyślnych projektu.  
  
5.  Import wszystkich arkuszy właściwości, w tym plików .user. Arkusze właściwości można zastąpić wszystkim, z wyjątkiem **PlatformToolset** i **projektu** właściwości domyślnych.  
  
6.  Pozostałe właściwości konfiguracji projektu. Te wartości mogą zastąpić to, co ustawiono w arkuszach właściwości.  
  
7.  Elementy (pliki) wraz z ich metadanymi. To jest zawsze ostateczny wynik, jeśli chodzi o reguły oceny MSBuild, nawet jeśli występują one przed innymi właściwościami i importami.  
  
 Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>Dodawanie katalogu plików dołączonych do zestawu katalogów domyślnych  
 Podczas dodawania katalogu plików dołączonych do projektu jest ważne, aby nie zastąpić domyślnych katalogów. Poprawny sposób dodania katalogu to dołączenie nowej ścieżki, na przykład "C:\MyNewIncludeDir\", a następnie dołączenie **$(IncludePath)** do wartości właściwości.  
  
## <a name="setting-environment-variables-for-a-build"></a>Ustawianie zmiennych środowiskowych dla kompilacji  
 Kompilator języka Visual C++ (cl.exe) rozpoznaje pewne zmienne środowiskowe, w szczególności LIB, LIBPATH, PATH i INCLUDE. Podczas kompilowania za pomocą środowiska IDE, właściwości, które są ustawiane w [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md) strona właściwości są używane do ustawiania tych zmiennych środowiskowych. Jeśli wartości LIB, LIBPATH i INCLUDE zostały już ustawione, na przykład przez wiersz polecenia programistów, zostaną zastąpione wartościami odpowiednich właściwości programu MSBuild. Następnie kompilacja dołącza wartość właściwości katalogów plików wykonywalnych Katalogi VC++ do PATH. Można ustawić zmienną środowiskową zdefiniowanych przez użytkownika utworzyć makro zdefiniowane przez użytkownika, a następnie zaznaczając pole wyboru, które mówi **Ustaw to makro jako zmienną środowiskową w środowisku kompilacji**.  
  
## <a name="setting-environment-variables-for-a-debugging-session"></a>Ustawianie zmiennych środowiskowych dla sesji debugowania  
 W okienku po lewej stronie projektu **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **debugowanie**. 
  
 W okienku po prawej stronie Zmień **środowiska** lub **Scal środowisko** ustawienia projektu, a następnie wybierz **OK** przycisku.  

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>Modyfikowanie właściwości i obiektów docelowych bez wprowadzania zmian w pliku projektu
Bez wprowadzania zmian w pliku projektu, można zastąpić właściwości projektu i obiekty docelowe w wierszu polecenia programu MSBuild. Jest to przydatne, gdy użytkownik chce zastosować niektórych właściwości tymczasowo lub od czasu do czasu. Zakłada się pewną wiedzę na temat programu MSBuild. Aby uzyskać więcej informacji, zobacz [MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Aby utworzyć plik .props i .targets, można użyć edytora XML w Visual Studio lub dowolnego edytora tekstów. Nie używaj **Menedżer właściwości** w tym scenariuszu, ponieważ dodaje właściwości do pliku projektu.

*Aby zastąpić właściwości projektu:*
- Utwórz plik .props, który określa właściwości, które chcesz zastąpić. 
- W wierszu polecenia: Ustaw ForceImportBeforeCppTargets="C:\sources\my_props.props"
 
*Aby zastąpić cele projektu:*
1) Tworzenie pliku .targets z ich implementacji lub określonej lokalizacji docelowej
2) W wierszu polecenia: Ustaw ForceImportAfterCppTargets = "C:\sources\my_target.targets"
 
Można również ustawić jedną z opcji w wierszu polecenia programu msbuild, przy użyciu opcji/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props" 
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets" 
```  

Zastępowanie właściwości i obiektów docelowych w ten sposób jest odpowiednikiem dodając następujące instrukcje importu do wszystkich plików vcxproj w rozwiązaniu:

```cmd 
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```  

## <a name="see-also"></a>Zobacz też  
 [Tworzenie i zarządzanie projektami Visual C++](../ide/creating-and-managing-visual-cpp-projects.md) [vcxproj i props pliku struktury](vcxproj-file-structure.md) [pliki XML strony właściwości](property-page-xml-files.md)