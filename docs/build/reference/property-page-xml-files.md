---
title: Pliki reguł XML na stronie właściwości
ms.date: 05/06/2019
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: da9fa72419dc6971e90124b061da48493d7ca017
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303163"
---
# <a name="property-page-xml-rule-files"></a>Pliki reguł XML na stronie właściwości

Strony właściwości projektu w IDE są konfigurowane przy użyciu plików XML w folderze VCTargets. Dokładna ścieżka zależy od tego, które wersje programu Visual Studio są zainstalowane, i języka produktu. W przypadku programu Visual Studio 2019 Enterprise Edition w języku angielskim ścieżka jest `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033`. Pliki XML opisują nazwy reguł, kategorii i poszczególnych właściwości, ich typ danych, wartości domyślne i sposób ich wyświetlania. Po ustawieniu właściwości w IDE, Nowa wartość jest przechowywana w pliku projektu.

Jedyne scenariusze, w których należy zrozumieć wewnętrzne działania tych plików i środowisko IDE programu Visual Studio, to (a) chcesz utworzyć niestandardową stronę właściwości lub (b), aby dostosować właściwości projektu za pomocą pewnych metod innych niż za pośrednictwem środowiska IDE programu Visual Studio.

Najpierw Otwórz strony właściwości dla projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie Właściwości):

![Właściwości projektu C++ programu Visual Studio](../media/cpp-property-page-2017.png)

Każdy węzeł we **właściwościach konfiguracji** jest nazywany regułą. Reguła czasami reprezentuje pojedyncze narzędzie, takie jak kompilator, ale ogólnie termin odnosi się do elementu, który ma właściwości, które wykonuje i który może generować niektóre dane wyjściowe. Każda reguła jest wypełniana z pliku XML w folderze VCTargets. Na przykład, pokazana powyżejC++ reguła C/jest wypełniona "CL. xml".

Jak pokazano powyżej, Każda reguła ma zestaw właściwości, które są pogrupowane w kategorie. Każdy podwęzeł w ramach reguły reprezentuje kategorię. Na przykład węzeł optymalizacji w obszarze C/C++ zawiera wszystkie właściwości związane z optymalizacją narzędzia kompilatora. Właściwości i ich wartości są renderowane w formacie siatki w okienku po prawej stronie.

Można otworzyć plik CL. XML w Notatniku lub dowolnym edytorze XML (zobacz migawka poniżej). Zobaczysz węzeł główny o nazwie Rule, który ma tę samą listę właściwości, które są zdefiniowane w interfejsie użytkownika, wraz z dodatkowymi metadanymi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
```

Istnieje jeden plik XML odpowiadający każdemu węzłowi we właściwościach konfiguracji w interfejsie użytkownika stron właściwości. Możesz dodawać lub usuwać reguły w interfejsie użytkownika, dołączając lub usuwając lokalizacje do odpowiednich plików XML w projekcie. Na przykład jest to sposób, w jaki Microsoft. CppBuild. targets (jeden poziom z folderu 1033) zawiera plik CL. XML:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Jeśli połączymy plik CL. XML wszystkich danych, zostanie on zakończony następującym szkieletem:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

W poniższej sekcji opisano poszczególne główne elementy i niektóre z metadanych, które można do nich dołączyć.

1. **Reguła:**  Reguła jest ogólnie węzłem głównym w pliku XML; może mieć wiele atrybutów:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Nazwa:** Atrybut name jest identyfikatorem reguły. Musi być unikatowa wśród wszystkich plików XML strony właściwości projektu.

   b. **PageTemplate:** Wartość tego atrybutu jest używana przez interfejs użytkownika do wybierania z kolekcji szablonów interfejsu użytkownika. Szablon "Narzędzie" renderuje właściwości w standardowym formacie siatki. Inne wbudowane wartości tego atrybutu to "Debugger" i "Generic". Zobacz odpowiednio węzeł Debugowanie i węzeł ogólny, aby zobaczyć format interfejsu użytkownika wynikający z określenia tych wartości. Interfejs użytkownika dla szablonu strony "debuger" używa pola listy rozwijanej, aby przełączać się między właściwościami różnych debugerów, podczas gdy szablon "ogólny" wyświetla różne kategorie właściwości wszystkie na jednej stronie, w przeciwieństwie do wielu węzłów podrzędnych kategorii w ramach reguły większości. Ten atrybut jest tylko sugestią interfejsu użytkownika; plik XML został zaprojektowany jako niezależny od interfejsu użytkownika. Inny interfejs użytkownika może używać tego atrybutu do różnych celów.

   c. **SwitchPrefix:** Jest to prefiks używany w wierszu polecenia dla przełączników. Wartość "/" spowoduje, że przełączniki wyglądają podobnie jak/ZI,/nologo,/W3 itd.

   d. **Kolejność:** Jest to sugestia klienta potencjalnego interfejsu użytkownika dla względnej lokalizacji tej reguły w porównaniu z innymi regułami w systemie.

   e. **xmlns:** Jest to standardowy element XAML. Widoczne są trzy obszary nazw. Odpowiadają one przestrzeniom nazw dla klas deserializacji XAML, schematu XAML i systemowej przestrzeni nazw, odpowiednio.

   f. **Nazwa wyświetlana:** Jest to nazwa wyświetlana w interfejsie użytkownika strony właściwości węzła reguły. Ta wartość jest zlokalizowana. Utworzyliśmy jako element podrzędny reguły, a nie jako atrybut (na przykład Name lub SwitchPrefix) z powodu wymagań narzędzia lokalizacji wewnętrznej. Z perspektywy języka XAML obie są równoważne. Dzięki temu można po prostu wprowadzić atrybut, aby zmniejszyć jego czytelność lub pozostawić go w taki sam sposób.

   g. **Źródło danych:** Jest to bardzo ważna właściwość, która informuje system projektu o lokalizacji, z której wartość właściwości powinna odczytywać i zapisywać, oraz grupowanie (wyjaśniono poniżej). W przypadku CL. XML te wartości są następujące:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` informuje system projektu, że wszystkie właściwości reguły powinny być zapisywane do pliku projektu lub pliku arkusza właściwości (w zależności od tego, który węzeł został użyty do duplikowania stron właściwości). Druga możliwa wartość to "UserFile", która pisze wartość do pliku. User.

   - `ItemType="ClCompile"` informuje o tym, że właściwości będą przechowywane jako metadane ItemDefinition lub metadane elementu (tylko wtedy, gdy strony właściwości zostały zduplikowane z węzła pliku w Eksploratorze rozwiązań) tego typu elementu. Jeśli to pole nie jest ustawione, właściwość jest zapisywana jako wspólna właściwość w liście właściwości.

   - `Label=""` wskazuje, że gdy właściwości są zapisywane jako metadane `ItemDefinition`, etykieta nadrzędnego ItemDefinitionGroup będzie pusta (każdy element MSBuild może mieć etykietę). Program Visual Studio 2017 lub nowszy używa grup oznaczonych jako do nawigowania w pliku projektu. vcxproj. Należy zauważyć, że grupy zawierające większość właściwości reguły mają pusty ciąg jako etykietę.

   - `HasConfigurationCondition="true"` instruuje system projektu, aby dołączył warunek konfiguracji do wartości, aby obowiązywał tylko dla bieżącej konfiguracji projektu (warunek może być dołączany do grupy nadrzędnej lub sama sama wartość). Na przykład Otwórz strony właściwości poza węzłem projektu i ustaw wartość właściwości **Traktuj ostrzeżenia jako błąd** we **właściwościach konfiguracji > C/C++ ogólne** do "tak". Następująca wartość jest zapisywana w pliku projektu. Zwróć uwagę na warunek konfiguracji dołączony do elementu nadrzędnego ItemDefinitionGroup.

      ```xml
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Jeśli ta wartość została ustawiona na stronie właściwości dla określonego pliku, na przykład stdafx. cpp, wartość właściwości zostanie zapisywana w elemencie *stdafx. cpp* w pliku projektu, jak pokazano poniżej. Zwróć uwagę, jak warunek konfiguracji jest bezpośrednio dołączony do samych metadanych.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Innym atrybutem **źródła danych** , który nie jest wymieniony powyżej, jest **persistedname**. Ten atrybut służy do reprezentowania właściwości w pliku projektu przy użyciu innej nazwy. Domyślnie ten atrybut jest ustawiony na **nazwę**właściwości.

   Poszczególne właściwości mogą przesłonić swoje źródło danych reguły nadrzędnej. W takim przypadku lokalizacja tej właściwości będzie różna od innych właściwości w regule.

   h. Istnieją inne atrybuty reguły, w tym opis i SupportsFileBatching, które nie są tutaj wyświetlane. Pełny zestaw atrybutów dotyczących reguły lub dowolnego innego elementu można uzyskać, przeglądając dokumentację dla tych typów. Alternatywnie można przeanalizować właściwości publiczne dla typów w przestrzeni nazw `Microsoft.Build.Framework.XamlTypes` w zestawie `Microsoft.Build.Framework .dll`.

   i. **DisplayName**, **PageTemplate**i **Order** są właściwościami związanymi z interfejsem użytkownika, które znajdują się w tym modelu danych niezależnym od interfejsu użytkownika. Te właściwości są prawie określone do użycia przez każdy interfejs użytkownika, który jest używany do wyświetlania stron właściwości. **Nazwa wyświetlana** i **Opis** to dwie właściwości, które znajdują się w prawie wszystkich elementach w pliku XML. Są to jedyne dwie właściwości, które są zlokalizowane (lokalizacja tych ciągów zostanie omówiona w późniejszym wpisie).

1. **Kategoria:** Reguła może mieć wiele kategorii. Kolejność, w której kategorie są wymienione w pliku XML jest sugestią interfejsu użytkownika do wyświetlania kategorii w tej samej kolejności. Na przykład kolejność kategorii w węźle C/C++ Node widzianym w interfejsie użytkownika — ogólne, optymalizacja, preprocesor,...  — jest taka sama jak w CL. XML. Przykładowa Kategoria wygląda następująco:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   Powyższy fragment kodu przedstawia atrybuty **name** i **DisplayName** , które zostały opisane wcześniej. Jeszcze raz istnieją inne atrybuty, których **kategorii** nie można użyć powyżej. Informacje o nich można uzyskać, odczytując dokumentację lub badając zestawy za pomocą Ildasm. exe.

1. **Właściwości:** Jest to mięso pliku XML i zawiera listę wszystkich właściwości w tej regule. Każda właściwość może być jednym z pięciu możliwych typów, które przedstawiono w powyższym szkieletzie XAML. Oczywiście w pliku może być tylko kilka z tych typów. Właściwość ma wiele atrybutów, które umożliwiają rozbudowane. Wyjaśnię tylko **StringProperty** tutaj. Pozostałe są bardzo podobne.

    ```xml
    <StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
      <StringProperty.DisplayName>
        <sys:String>Object File Name</sys:String>
      </StringProperty.DisplayName>
      <StringProperty.Description>
        <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
      </StringProperty.Description>
    </StringProperty>
    ```

   Większość atrybutów w fragmencie kodu została opisana przed. Nowe są podtype, Category i switch.

   a. **Podtyp** jest atrybutem dostępnym tylko dla **StringProperty** i **StringListProperty**; zapewnia informacje kontekstowe. Na przykład wartość "plik" wskazuje, że właściwość reprezentuje ścieżkę pliku. Takie informacje kontekstowe służą do ulepszania środowiska edycji przez udostępnienie Eksploratora Windows jako edytora właściwości, który umożliwia użytkownikowi wizualne Wybieranie pliku.

   b. **Kategoria:** Deklaruje kategorię, w której znajduje się ta właściwość. Spróbuj znaleźć tę właściwość w kategorii **pliki wyjściowe** w interfejsie użytkownika.

   c. **Przełącznik:** Gdy reguła reprezentuje narzędzie, takie jak narzędzie kompilatora w tym przypadku — większość właściwości reguły jest przenoszona jako przełączniki do pliku wykonywalnego narzędzia podczas kompilacji. Wartość tego atrybutu wskazuje literał przełącznika, który ma być używany. Powyższa Właściwość określa, że jej przełącznik powinien mieć wartość **fo**. W połączeniu z atrybutem **SwitchPrefix** reguły nadrzędnej ta właściwość jest przenoszona do pliku wykonywalnego jako **/fo "Debug\"** (widoczne w wierszu polecenia dla C/C++ w interfejsie użytkownika strony właściwości).

   Inne atrybuty właściwości obejmują:

   d. **Widoczne:** Jeśli z jakiegoś powodu nie chcesz, aby właściwość była wyświetlana na stronach właściwości (ale prawdopodobnie nadal jest dostępna w czasie kompilacji), ustaw dla tego atrybutu wartość false.

   e. **Tylko do odczytu:** Jeśli chcesz udostępnić widok tylko do odczytu wartości tej właściwości na stronach właściwości, ustaw dla tego atrybutu wartość true.

   f. **IncludeInCommandLine:** Niektóre właściwości mogą nie być przesyłane do narzędzia w czasie kompilacji. Ustawienie tego atrybutu na wartość false uniemożliwi przekazanie go.
