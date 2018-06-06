---
title: Pliki reguł XML strony właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcee2c416fba6a959785826781aefd96b0d06d75
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339647"
---
# <a name="property-page-xml-rule-files"></a>Pliki reguł XML strony właściwości
Strony właściwości projektu w środowisku IDE są konfigurowane przez pliki XML w folderze VCTargets. Dokładnej ścieżki zależy od tego, które edition(s) programu Visual Studio są zainstalowane, a język produktu. Dla programu Visual Studio 2017 Enterprise Edition w języku angielskim, ścieżka jest `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Pliki XML opisują nazwy reguły, kategorii i poszczególnych właściwości, typ danych, wartości domyślne i jak mają być wyświetlane. Po ustawieniu właściwości w IDE nowa wartość jest przechowywane w pliku projektu.

Tylko scenariusze, w których trzeba wiedzieć, że wewnętrzne działanie tych plików i środowiska IDE programu Visual Studio (), konieczne jest utworzenie niestandardowej strony właściwości lub (b) chcesz dostosować właściwości projektu niektórych metod innych niż za pomocą środowiska IDE programu Visual Studio. 

Po pierwsze umożliwia otwieranie stron właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie Właściwości):
   
![Właściwości projektu w programie Visual C++](media/cpp-property-page-2017.png)

Każdy węzeł w węźle **właściwości konfiguracji** nosi nazwę reguły. Reguła reprezentuje czasami jednego narzędzia, takiego jak kompilator, ale ogólnie termin odnosi się do zasobu, który ma właściwości, która wykonuje i który może powodować pewne dane wyjściowe. Każda reguła pochodzą z pliku xml w folderze VCTargets. Na przykład reguła C/C++, która jest wyświetlana powyżej jest wypełniana "cl.xml".

Jak pokazano powyżej, każda reguła ma zestaw właściwości, które są pogrupowane w kategorie. Każdy węzeł podrzędny w regule reprezentuje kategorię. Na przykład do węzła Optymalizacja C/C++ zawiera wszystkie powiązane optymalizacji właściwości narzędzia kompilatora. Właściwości i ich wartości, same są renderowane w formacie siatki w okienku po prawej stronie.

Możesz otworzyć cl.xml w Notatniku lub w dowolnym edytorze XML (patrz migawki poniżej). Zostanie wyświetlone węzła głównego o nazwie regułę, która ma tę samą listę właściwości zdefiniowane w nim, jak są wyświetlane w interfejsie użytkownika wraz z dodatkowych metadanych.

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

Istnieje jeden plik XML odpowiadający każdy węzeł w obszarze właściwości konfiguracji na stronach właściwości interfejsu użytkownika. Można dodać lub usuń reguły w interfejsie użytkownika przez dodanie lub usunięcie lokalizacje odpowiadające im pliki XML w projekcie. Na przykład jest to, jak Microsoft.CppBuild.targets (jeden poziom wyżej w folderze 1033) zawiera cl.xml:

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
Jeśli paska cl.xml wszystkie dane, spowoduje utworzenie z następującą szkieletową:
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

W poniższej sekcji opisano każdy główne elementy, a niektóre metadanych, który można dołączyć do nich.

1. **Reguła:** reguła jest zazwyczaj węzła głównego w pliku xml; może mieć wiele atrybutów:

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **Nazwa:** atrybut Name jest identyfikatorem reguły. Musi być unikatowa wśród wszystkich właściwości strony pliki xml dla projektu.

   b. **PageTemplate:** wartość tego atrybutu jest używany przez interfejs użytkownika do wyboru w kolekcji szablonów interfejsu użytkownika. Szablon "narzędzia" renderuje właściwości w formacie standardowych siatki. Inne wartości w utworzony dla tego atrybutu to "debugera" i "Ogólne". Zapoznaj się z węzła debugowanie i ogólne węzła, odpowiednio, aby wyświetlić format interfejsu użytkownika, wynikające z określenie tych wartości. Interfejs użytkownika dla szablonu strony "debugera" korzysta z listy rozwijanej można zmieniać właściwości debugery różnych natomiast szablon "Ogólne" przedstawia kategorie inną właściwość w jedną stronę o wiele kategorii węzły podrzędne w obszarze reguły w przeciwieństwie węzeł. Ten atrybut jest tylko uwag do interfejsu użytkownika; plik xml zaprojektowano w sposób niezależny interfejsu użytkownika. Inny interfejs użytkownika może używać tego atrybutu do różnych celów.

  c. **SwitchPrefix:** jest to element prefix używany w wierszu polecenia dla przełączników. Wartość "/" spowoduje powstanie przełączników, które mają postać/zi, / nologo, /W3 itp.

  d. **Kolejność:** to sugestię potencjalnego klienta interfejsu użytkownika na względne położenie tej reguły w porównaniu do innych reguł w systemie.

  e. **xmlns:** jest to standardowy element XAML. Trzy obszary nazw na liście jest widoczny. Odpowiadają one przestrzeni nazw do deserializacji XAML klasy, systemu i schematu przestrzeń nazw XAML, odpowiednio.

  f. **Nazwa wyświetlana:** jest to nazwa, który jest wyświetlany na stronie właściwości interfejsu użytkownika dla węzła reguły. Ta wartość jest zlokalizowana. Utworzyliśmy Nazwa wyświetlana jako element podrzędny reguły, a nie jako atrybut (np. nazwę lub SwitchPrefix) z powodu wewnętrznego lokalizacji narzędzia wymagania. Zarówno z perspektywy w języku XAML, są równoważne. Tak można tylko tworzyć i atrybutu, aby zwiększyć czytelność, lub pozostaw to pole, ponieważ jest on.

  g. **Źródło danych:** jest bardzo ważne właściwość, która informuje system projektu w lokalizacji, w którym wartość właściwości musi odczytywane i zapisywane, a jego grupowania (co omówiono poniżej). Dla cl.xml te wartości są następujące:

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile` Określa, że system projektu, że wszystkie właściwości reguły mają być zapisywane do pliku projektu lub pliku arkusza właściwości (w zależności od węzła użyto wywołania strony właściwości). Możliwe wartości to "UserFile", która będzie zapisywała wartość plik .user.

   - `ItemType="ClCompile"` informuje, że właściwości będą przechowywane jako ItemDefinition ani elementu metadanych (drugie tylko wtedy, gdy strony właściwości zostały zduplikowany z węzła plików w Eksploratorze rozwiązań) tego typu elementu. Jeśli to pole nie jest ustawiona, właściwości są zapisywane jako wspólne właściwości w PropertyGroup.

   - `Label=""` Wskazuje, że podczas właściwości są zapisywane jako `ItemDefinition` metadanych, etykiety dominującego ItemDefinitionGroup będzie pusty (każdego elementu MSBuild może mieć etykietę). Visual Studio 2017 korzysta z etykietą grup można przejść do pliku .vcxproj projektu. Należy pamiętać, że grup, które zawierają większość właściwości reguły mieć ciągu pustego jako etykieta.

   - `HasConfigurationCondition="true"` informuje system projektu, aby umieścić warunek konfiguracji wartość tak, aby obowiązuje tylko dla bieżącej konfiguracji projektu (warunek może zostać umieszczona w grupie nadrzędnej albo samą wartość). Na przykład otwieranie stron właściwości węzła projektu i ustawić wartość właściwości **Traktuj ostrzeżenia jako błąd** w obszarze **właściwości konfiguracji > Ogólne C/C++** "Yes". Następujące wartości są zapisywane w pliku projektu. Zwróć uwagę, warunek konfiguracji dołączony do obiektu nadrzędnego ItemDefinitionGroup.

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   Jeśli tę wartość ustawiono na stronie właściwości dla określonego pliku, takie jak stdafx.cpp, wartość właściwości powinny być zapisane w pozycji stdafx.cpp w pliku projektu, jak pokazano poniżej. Zwróć uwagę, jak warunek konfiguracji jest podłączony bezpośrednio do samej siebie metadanych.

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   Innym atrybucie **źródła danych** nie są wymienione powyżej jest **PersistedName**. Ten atrybut służy do reprezentowania właściwość w pliku projektu, używając innej nazwy. Domyślnie ten atrybut ma ustawioną właściwość **nazwa**. 

   Wybranej właściwości można zastąpić regułę elementu nadrzędnego źródła danych. W takim przypadku będą inne niż inne właściwości reguły lokalizacji dla tej właściwości wartości.

   h. Istnieją inne atrybuty reguły, takie jak opis, SupportsFileBatching itp, które nie są wyświetlane tutaj. Pełny zestaw atrybutów, które są stosowane do reguły lub innych elementów można uzyskać, przeglądając dokumentację dla tych typów. Alternatywnie można sprawdzić właściwości publiczne dla typów w `Microsoft.Build.Framework.XamlTypes` przestrzeni nazw w `Microsoft.Build.Framework .dll` zestawu.

   i. **Nazwa wyświetlana**, **PageTemplate**, i **kolejności** są w przeciwnym razie właściwości związanych z interfejsu użytkownika, które znajdują się w tym modelu danych niezależny od interfejsu użytkownika. Te właściwości są prawie niektórych mają być używane przez elementów interfejsu użytkownika, który służy do wyświetlania strony właściwości. **Nazwa wyświetlana** i **opis** są dwie właściwości, które znajdują się na prawie wszystkie elementy w pliku xml. I są tylko dwie właściwości, które są zlokalizowane (lokalizacja tych ciągów opisano w późniejszym post).

2.  **Kategoria:** reguła może mieć wiele kategorii. Kolejność, w którym kategorie są wymienione w pliku xml jest uwag do interfejsu użytkownika można wyświetlić kategorii w tej samej kolejności. Na przykład kolejność kategorii w węźle C/C++, jak pokazano w interfejsie użytkownika — ogólne, optymalizacja, preprocesora,...  — jest taki sam jak ten w cl.xml. Kategoria próbki wygląda następująco:

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
Powyżej fragment kodu przedstawia **nazwa** i **DisplayName** atrybuty, które zostały opisany wcześniej. Ponownie, istnieją inne atrybuty **kategorii** może mieć, które nie są używane powyżej. Można określić o nich przeczytaj dokumentację lub analizowania zestawów przy użyciu ildasm.exe.

3. **Właściwości:** jest rodzaje pliku xml i zawiera listę wszystkich właściwości w tej regule. Każda właściwość może być jednego z pięciu typów możliwych pokazano powyżej szkielet XAML. Oczywiście można mieć tylko niektóre z tych typów w pliku. Właściwość ma wiele atrybutów umożliwiających Bogato opisana. Będzie opisano tylko **StringProperty** tutaj. Pozostałe są bardzo podobne.

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
Przed opisano większość atrybutów we fragmencie. Te nowe są podtyp, kategorii i przełącznika.

   a. **Podtyp** jest dostępna tylko dla atrybutu **StringProperty** i **StringListProperty**; udostępnia informacje kontekstowe. Na przykład wartość "file" oznacza, że właściwość reprezentuje ścieżkę do pliku. Takie informacje kontekstowe służy do edytowania udoskonalenie zapewniając Eksploratora Windows jako edytora właściwości, która umożliwia użytkownikom wizualne wybrać plik.

   b. **Kategoria:** to deklaruje kategorii, pod którym znajduje się ta właściwość. Próbuje znaleźć tej właściwości, w obszarze **pliki wyjściowe** kategorii w interfejsie użytkownika.

   c. **Przełącznik:** gdy reguła reprezentuje narzędzia — takiego jak narzędzie kompilatora w takim przypadku — większość właściwości reguły są przekazywane jako przełączników do narzędzia do pliku wykonywalnego w czasie kompilacji. Wartość tego atrybutu wskazuje literału używanego przełącznika. Właściwość powyżej Określa, że jego przełącznika powinna być **Fo**. Połączone z **SwitchPrefix** atrybutu nadrzędnego reguły, ta właściwość jest przekazywana do pliku wykonywalnego jako **/Fo "Debug\"**  (widoczne w wierszu polecenia dla C/C++ w interfejsie użytkownika strony właściwości).

   Inne atrybuty właściwości obejmują:

   d. **Widoczny:** Jeśli jakiegoś powodu nie chcesz z właściwości wyświetlane na stronach właściwości (ale nadal prawdopodobnie jest dostępny w czasie kompilacji), ten atrybut jest ustawiony na wartość false.

   e. **Tylko do odczytu:** Jeśli chcesz podać wartości tej właściwości na stronach właściwości widoku tylko do odczytu, ten atrybut ustawiony na wartość true.

   f. **IncludeInCommandLine:** niektórych właściwości nie może być konieczne przekazane do narzędzia w czasie kompilacji. Ustawienie wartości false dla tego atrybutu będą zapobiegać jej przekazywany.


