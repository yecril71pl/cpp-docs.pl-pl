---
title: Pliki reguł XML strony właściwości
ms.date: 04/27/2017
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 17b89f00b2e51c960ed7d3219427b56d92851b81
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823269"
---
# <a name="property-page-xml-rule-files"></a>Pliki reguł XML strony właściwości

Strony właściwości projektu w IDE, są konfigurowane przez pliki XML w folderze VCTargets. Dokładnej ścieżki zależy od tego, której wersji programu Visual Studio są instalowane i język produktu. Visual Studio 2017 Enterprise Edition w języku angielskim, ścieżka jest `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Pliki XML opisują nazwy reguły, kategorie, a poszczególne właściwości, typ danych, wartości domyślne i jak są wyświetlane. Gdy właściwość jest ustawiona w IDE, nowa wartość są przechowywane w pliku projektu.

Tylko scenariusze, w których należy zrozumieć wewnętrzne działanie tych plików i środowisku IDE programu Visual Studio czy () ma zostać utworzona niestandardowa strona właściwości lub (b) który chcesz dostosować właściwości projektu za pomocą środków innych niż za pomocą programu Visual Studio IDE.

Najpierw Przyjrzyjmy Otwórz strony właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie Właściwości):

![Właściwości projektu Visual C++](../media/cpp-property-page-2017.png)

Każdy węzeł w węźle **właściwości konfiguracji** nosi nazwę reguły. Reguła reprezentuje czasami jednego narzędzia, takie jak kompilator, ale ogólnie rzecz biorąc termin odnosi się do zasobu, który ma właściwości, który wykonuje i który może generować pewne dane wyjściowe. Każda reguła jest wypełniana z pliku xml w folderze VCTargets. Na przykład reguła C/C++, która jest wyświetlana powyżej jest wypełniana przez "cl.xml".

Jak wspomniano powyżej, każda reguła ma zestaw właściwości, które są podzielone na kategorie. Każdy węzeł podrzędny w obszarze reguła reprezentuje kategorię. Na przykład węźle Optymalizacja C/C++ zawiera wszystkie powiązane optymalizacji właściwości narzędzia kompilatora. Właściwości i ich wartości są renderowane w postaci siatki w okienku po prawej stronie.

Możesz otworzyć cl.xml w Notatniku lub w dowolnym edytorze XML (patrz poniżej. Tworzenie migawki). Węzeł główny wywołuje regułę, która ma tej samej listy właściwości zdefiniowane w nim, jak są wyświetlane w interfejsie użytkownika, oraz dodatkowe metadane, zostanie wyświetlony.

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

Istnieje jeden plik XML odpowiadający każdy węzeł w obszarze właściwości konfiguracji na stronach właściwości interfejsu użytkownika. Można dodać lub usunąć reguły w interfejsie użytkownika, w tym lub usuwając lokalizacje na odpowiadające im pliki XML w projekcie. Na przykład jest to, jak Microsoft.CppBuild.targets (jeden poziom wyżej z folderu 1033) obejmuje cl.xml:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Jeśli możesz oddzielić cl.xml wszystkie dane, możesz ostatecznie następujący szkielet:

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

W poniższej sekcji opisano każdej głównych elementów, a niektóre metadanych, który można dołączyć do nich.

1. **Reguła:**  Reguła jest zazwyczaj węzła głównego w pliku xml. może mieć wiele atrybutów:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Nazwa:** Atrybut Name jest identyfikatorem reguły. Musi być unikatowa wśród wszystkich właściwości strony pliki xml dla projektu.

   b. **PageTemplate:** Wartość tego atrybutu jest używana przez interfejs użytkownika z kolekcji szablonów interfejsu użytkownika. Szablon "narzędzia" powoduje wyświetlenie właściwości w postaci standardowych siatki. Inne wbudowane wartości dla tego atrybutu to "debugera" i "generic". Zobacz węzła debugowanie i ogólne węzła, odpowiednio do sprawdzenia formatu interfejsu użytkownika, wynikające z określenie tych wartości. W interfejsie użytkownika dla szablonu strony "debugera" używa pole listy rozwijanej, aby przełączać się między właściwości inne debugery, natomiast szablon "generic" przedstawia kategorie inną właściwość wszystko to w przeciwieństwie posiadanie wielu kategorii podrzędne węzły regułę po jednej stronie węzeł. Ten atrybut jest po prostu sugestię w interfejsie użytkownika; plik xml została zaprojektowana jako niezależnie od interfejsu użytkownika. Inny interfejs użytkownika może użyć tego atrybutu do różnych celów.

   c. **SwitchPrefix:** Jest to prefiks używany w wierszu polecenia na potrzeby przełączników. Wartość "/" spowodowałoby przełączników, które mają postać/zi, / nologo, / W3, itp.

   d. **Kolejność:** Jest to sugestię do potencjalnego klienta interfejsu użytkownika na położenie tej reguły w porównaniu do innych reguł w systemie.

   e. **xmlns:** Jest to standardowy element XAML. Zobaczysz trzy obszary nazw na liście. Odpowiadają one przestrzenie nazw do deserializacji XAML klasy, XAML systemu i schematu przestrzeni nazw, odpowiednio.

   f. **Właściwość DisplayName:** Jest to nazwa, która jest wyświetlana na stronie właściwości interfejsu użytkownika dla węzła reguły. Ta wartość jest zlokalizowana. Utworzyliśmy DisplayName jako element podrzędny, reguły, a nie jako atrybutu (np. nazwę lub SwitchPrefix) z powodu lokalizacji wewnętrznych wymagań narzędzia. Zarówno z perspektywy firmy XAML są równoważne. Tak możesz po prostu przekształcić ją w atrybutu zbędnych elementów lub pozostaw to pole, ponieważ jest.

   g. **Źródło danych:** Jest to bardzo ważne właściwość, która informuje system projektu, lokalizacji, z której należy wartość właściwości odczytywane i zapisywane do, a jego grupowania (opisana poniżej). Aby uzyskać cl.xml te wartości są:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` informuje system projektu, że wszystkie właściwości reguły mają być zapisywane w pliku projektu lub pliku arkusza właściwości (w zależności od węzła użyto się na stronach właściwości). Możliwa wartość to "UserFile", która będzie zapisywała wartość w pliku .user.

   - `ItemType="ClCompile"` mówi, że właściwości zostaną zapisane w formie ItemDefinition metadanych lub metadane elementu (ten ostatni tylko wtedy, gdy strony właściwości zostały zduplikowany z węzła pliku w Eksploratorze rozwiązań) tego typu elementu. Jeśli to pole nie jest ustawiona, właściwości są zapisywane jako wspólnej właściwości w PropertyGroup.

   - `Label=""` Wskazuje, że po właściwości są zapisywane w postaci `ItemDefinition` metadane, etykieta ItemDefinitionGroup — element nadrzędny będzie pusty (każdego elementu MSBuild może mieć etykietę). Program Visual Studio 2017 korzysta z etykietami grup można przejść do pliku projektu .vcxproj. Należy zauważyć, że grup, które zawierają większość właściwości reguły pusty ciąg jako etykiety.

   - `HasConfigurationCondition="true"` informuje system projektu, aby umieścić warunek konfiguracji na wartość tak, aby działa tylko dla bieżącej konfiguracji projektu (warunek może zostać umieszczona w grupie nadrzędnej lub samą wartość). Na przykład, otwórz strony właściwości węzła projektu i ustaw wartość właściwości **traktowanie ostrzeżeń jako błędów** w obszarze **właściwości konfiguracji > C/C++ General** "Yes". Następujące wartości są zapisywane do pliku projektu. Zwróć uwagę, warunek konfiguracji dołączony do ItemDefinitionGroup — element nadrzędny.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Jeśli tę wartość ustawiono na stronie właściwości dla określonego pliku, takie jak stdafx.cpp, wartość właściwości powinny być zapisane w obszarze element stdafx.cpp w pliku projektu, jak pokazano poniżej. Zwróć uwagę, jak warunek konfiguracji jest podłączony bezpośrednio do samego metadanych.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Innym atrybucie **DataSource** niewymienionego powyżej jest **PersistedName**. Ten atrybut służy do reprezentowania właściwości w pliku projektu, używając innej nazwy. Domyślnie ten atrybut jest ustawiony na wartość właściwości **nazwa**.

   Pojedynczej właściwości można zastąpić reguł elementu nadrzędnego źródła danych. W takiej sytuacji lokalizacji dla tej właściwości wartości będzie różnić się od innych właściwości w regule.

   h. Istnieją inne atrybuty reguły, takie jak opis, SupportsFileBatching itp, które nie są wyświetlane w tym miejscu. Pełny zestaw atrybutów, które są stosowane do reguły lub w innym elemencie można uzyskać, przeglądając dokumentację dla tych typów. Alternatywnie można sprawdzić właściwości publiczne dla typów w `Microsoft.Build.Framework.XamlTypes` przestrzeni nazw w `Microsoft.Build.Framework .dll` zestawu.

   i. **DisplayName**, **PageTemplate**, i **kolejności** względami są związane z interfejsem użytkownika właściwości, które znajdują się w tym modelu danych niezależnie od interfejsu użytkownika. Te właściwości są prawie pewne, który będzie używany przez wszystkie interfejs użytkownika, który służy do wyświetlania na stronach właściwości. **DisplayName** i **opis** są dwie właściwości, które znajdują się w przypadku niemal wszystkich elementów w pliku xml. A Oto tylko dwie właściwości, które są zlokalizowane (lokalizacja tych ciągów zostaną wyjaśnione w nowszym post).

1. **Kategoria:** Reguła może mieć wiele kategorii. Kolejność, w jakiej kategorii są wymienione w pliku xml jest sugestię w interfejsie użytkownika do wyświetlania kategorii w tej samej kolejności. Na przykład kolejność kategorii w węźle C/C++, jak pokazano w interfejsie użytkownika — ogólne, optymalizacja, Preprocesor,...  — jest taki sam jak ten w cl.xml. Kategoria przykładowe wygląda następująco:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   Powyższe fragment kodu przedstawia **nazwa** i **DisplayName** atrybutów, które został opisany wcześniej. Jeszcze raz istnieją inne atrybuty **kategorii** może mieć, które nie są używane powyżej. Możesz sprawdzać ich temat, zapoznając się z dokumentacją i analizując zestawy za pomocą ildasm.exe.

1. **Właściwości:** To jest rodzaje pliku xml i zawiera listę wszystkich właściwości w tej regule. Każda właściwość może być jednego z pięciu typów możliwych pokazano w powyższym szkielet XAML. Oczywiście może mieć tylko kilka z tych typów w pliku. Właściwość ma wiele atrybutów, które zezwalała na graficznie opisane. Wyjaśnię to tylko **StringProperty** tutaj. Pozostałe są bardzo podobne.

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

   Zanim zostały opisane większość atrybutów, w tym fragmencie kodu. Te nowe są podtypu, kategorii i przełącznika.

   a. **Podtyp** jest dostępna tylko dla atrybutu **StringProperty** i **StringListProperty**; zapewnia informacje kontekstowe. Na przykład wartość "file" wskazuje, że właściwość reprezentuje ścieżkę do pliku. Takie informacje kontekstowe jest używana do podwyższenia środowisko edytowania, zapewniając Eksploratora Windows jako Edytor właściwości, który umożliwia użytkownikowi wybrać plik wizualnie.

   b. **Kategoria:** Deklaruje to kategoria, pod którym znajduje się ta właściwość. Spróbuj znaleźć tę właściwość w ramach **pliki wyjściowe** kategorii w interfejsie użytkownika.

   c. **Przełącznik:** Jeśli reguła reprezentuje narzędzie — takiego jak narzędzie kompilatora w tym przypadku — większość właściwości reguły są przekazywane jako przełączników do narzędzia pliku wykonywalnego w czasie kompilacji. Wartość tego atrybutu wskazuje literału używanego przełącznika. Powyższej właściwości określa, że jego przełącznika powinna być **Fo**. W połączeniu z **SwitchPrefix** atrybutu nadrzędnego reguły, ta właściwość jest przekazywana do pliku wykonywalnego jako **/Fo "debugowanie\"**  (widoczne w wierszu polecenia języka C/c++ w interfejsie użytkownika strony właściwości).

   Inne atrybuty właściwości obejmują:

   d. **Widoczny:** Jeśli z jakiegoś powodu nie mają swoje właściwości wyświetlane na stronach właściwości (ale nadal prawdopodobnie jest ona dostępna w czasie kompilacji), ten atrybut jest ustawiony na wartość false.

   e. **Tylko do odczytu:** Jeśli chcesz przedstawić widok tylko do odczytu wartości tej właściwości na stronach właściwości, ustaw ten atrybut na wartość true.

   f. **IncludeInCommandLine:** Niektóre właściwości nie może być konieczne do przekazania do narzędzia, w czasie kompilacji. Ustawienie tego atrybutu na false uniemożliwi jej przekazywana.
