---
title: Struktura plików vcxproj i props
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: a24349980e9395257f20fcfcc0987883060a7c1d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303141"
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura plików vcxproj i props

[MSBuild](../msbuild-visual-cpp.md) jest domyślnym systemem projektu w programie Visual Studio; Po wybraniu opcji **plik** > **Nowy projekt** w C++ wizualizacji tworzysz projekt MSBuild, którego ustawienia są przechowywane w pliku projektu XML, który ma `.vcxproj`rozszerzenia. Plik projektu może również importować. props pliki i pliki. targets, w których można przechowywać ustawienia. W większości przypadków nie trzeba ręcznie edytować pliku projektu i w rzeczywistości nie należy edytować go ręcznie, chyba że masz dobre zrozumienie programu MSBuild. Za każdym razem, gdy to możliwe, należy użyć stron właściwości programu Visual Studio do modyfikowania ustawień projektu (zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md). Jednak w niektórych przypadkach może być konieczne ręczne zmodyfikowanie pliku projektu lub arkusza właściwości. W tych scenariuszach ten artykuł zawiera podstawowe informacje o strukturze pliku.

**Ważne:**

Jeśli zdecydujesz się ręcznie edytować plik. vcxproj, weź pod uwagę następujące fakty:

1. Struktura pliku musi być zgodna z określonym formularzem, który opisano w tym artykule.

1. System projektu programu C++ Visual Studio obecnie nie obsługuje symboli wieloznacznych w elementach projektu. Na przykład nie jest to obsługiwane:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. System projektu programu C++ Visual Studio aktualnie nie obsługuje makr w ścieżkach elementów projektu. Na przykład nie jest to obsługiwane:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "Nieobsługiwane" oznacza, że makra nie są gwarantowane do pracy w przypadku wszystkich operacji w IDE. Makra, które nie zmieniają ich wartości w różnych konfiguracjach, powinny działać, ale mogą nie być zachowywane, jeśli element zostanie przeniesiony do innego filtru lub projektu. Makra, które zmieniają ich wartości dla różnych konfiguracji, spowodują problemy, ponieważ IDE nie oczekuje, że ścieżki elementów projektu różnią się w zależności od konfiguracji projektu.

1. W celu poprawnego dodania, usunięcia lub zmodyfikowania właściwości projektu w oknie dialogowym **właściwości projektu** , plik musi zawierać oddzielne grupy dla każdej konfiguracji projektu, a warunki muszą być w tej formie:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Każda właściwość musi być określona w grupie z poprawną etykietą, jak określono w pliku reguły właściwości. Aby uzyskać więcej informacji, zobacz [pliki reguł XML na stronie właściwości](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>vcxproj — elementy pliku

Zawartość pliku. vcxproj można sprawdzić przy użyciu dowolnego edytora tekstu lub XML. Możesz wyświetlić go w programie Visual Studio, klikając prawym przyciskiem myszy projekt w Eksplorator rozwiązań, wybierając pozycję **Zwolnij projekt** , a następnie wybierając pozycję **Edytuj foo. vcxproj**.

Pierwszy należy zauważyć, że elementy najwyższego poziomu pojawiają się w określonej kolejności. Na przykład:

- Większość grup właściwości i grup definicji elementów występuje po imporcie dla elementu Microsoft. cpp. default. props.

- Wszystkie elementy docelowe są importowane na końcu pliku.

- Istnieje wiele grup właściwości, z których każda ma unikatową etykietę i pojawia się w określonej kolejności.

Kolejność elementów w pliku projektu jest bardzo ważna, ponieważ MSBuild bazuje na modelu oceny sekwencyjnej.  Jeśli plik projektu, w tym wszystkie pliki zaimportowane. props i. targets, składa się z wielu definicji właściwości, ostatnia definicja przesłania poprzednie. W poniższym przykładzie wartość "XYZ" zostanie ustawiona podczas kompilacji, ponieważ aparat MSBUild napotka go jako ostatni podczas jego oceny.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Poniższy fragment kodu przedstawia plik o minimalnej vcxproj. Każdy plik. vcxproj wygenerowany przez program Visual Studio będzie zawierać te elementy programu MSBuild najwyższego poziomu, które będą wyświetlane w tej kolejności (chociaż mogą zawierać wiele kopii każdego takiego elementu najwyższego poziomu). Należy pamiętać, że atrybuty `Label` są dowolnymi tagami, które są używane tylko przez program Visual Studio jako oznaki do edycji; nie mają żadnej innej funkcji.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

W poniższych sekcjach opisano przeznaczenie każdego z tych elementów i przyczyny ich uporządkowania:

### <a name="project-element"></a>Element projektu

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` jest węzłem głównym. Określa wersję programu MSBuild, która ma być używana, a także domyślny cel do wykonania, gdy ten plik jest przesyłany do programu MSBuild. exe.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations element elementu

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` zawiera opis konfiguracji projektu. Przykłady są debugowaniem | Win32, wydanie | Win32, Debuguj | ARM i tak dalej. Wiele ustawień projektu jest specyficznych dla danej konfiguracji. Na przykład prawdopodobnie trzeba będzie ustawić właściwości optymalizacji dla kompilacji wydania, ale nie dla kompilacji debugowania.

Grupa elementów `ProjectConfigurations` nie jest używana w czasie kompilacji. Środowisko IDE programu Visual Studio wymaga, aby można było załadować projekt. Tę grupę elementów można przenieść do pliku. props i zaimportować do pliku. vcxproj. Jednak w takim przypadku, jeśli trzeba dodać lub usunąć konfiguracje, należy ręcznie edytować plik. props; nie można używać środowiska IDE.

### <a name="projectconfiguration-elements"></a>Elementy ProjectConfiguration

Poniższy fragment kodu przedstawia konfigurację projektu. W tym przykładzie "Debugowanie | x64" jest nazwą konfiguracji. Nazwa konfiguracji projektu musi mieć format $ (Configuration) | $ (platforma). Węzeł konfiguracji projektu może mieć dwie właściwości: konfigurację i platformę. Te właściwości zostaną automatycznie ustawione z wartościami określonymi w tym miejscu, gdy konfiguracja jest aktywna.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE oczekuje na znalezienie konfiguracji projektu dla dowolnej kombinacji wartości konfiguracji i platformy używanych we wszystkich elementach ProjectConfiguration. Często oznacza to, że projekt może mieć bez znaczenia konfiguracje projektu, aby spełnić to wymaganie. Na przykład, jeśli projekt ma następujące konfiguracje:

- Debug|Win32

- Retail|Win32

- Specjalna 32-bitowa Optymalizacja | System

następnie musi również mieć te konfiguracje, chociaż "Specjalna Optymalizacja 32-bitowa" ma znaczenie dla architektury x64:

- Debug|x64

- Retail|x64

- Specjalna 32-bitowa Optymalizacja | x64

Polecenia Kompiluj i Wdróż można wyłączyć dla każdej konfiguracji w **Configuration Manager rozwiązania**.

### <a name="globals-propertygroup-element"></a>Globals — element właściwości

```xml
<PropertyGroup Label="Globals" />
```

`Globals` zawiera ustawienia na poziomie projektu, takie jak ProjectGuid, RootNamespace i ApplicationType/ApplicationTypeRevision. Ostatnie dwa często definiują docelowy system operacyjny. Projekt może dotyczyć tylko pojedynczego systemu operacyjnego ze względu na fakt, że odwołania i elementy projektu nie mogą obecnie mieć warunków. Te właściwości nie są zwykle zastępowane w innym miejscu w pliku projektu. Ta grupa nie jest zależna od konfiguracji i dlatego zwykle w pliku projektu istnieje tylko jedna grupa Globals.

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft. cpp. default. props — element importu

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

Arkusz właściwości **Microsoft. cpp. default. props** jest dostarczany z programem Visual Studio i nie można go modyfikować. Zawiera ustawienia domyślne dla projektu. Wartości domyślne mogą się różnić w zależności od typu ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Elementy właściwości konfiguracji

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` grupy właściwości ma dołączony warunek konfiguracji (na przykład `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`) i znajduje się w wielu kopiach, jeden na konfigurację. Ta grupa właściwości zawiera właściwości, które są ustawione dla określonej konfiguracji. Właściwości konfiguracji obejmują PlatformToolset oraz kontrolują dołączenie systemowych arkuszy właściwości do **Microsoft. cpp. props**. Na przykład, jeśli zdefiniujesz Właściwość `<CharacterSet>Unicode</CharacterSet>`, to systemowy arkusz właściwości **Microsoft. Zostaną uwzględnione cpp. unicodesupport. props** . W przypadku inspekcji **Microsoft. cpp. props**zobaczysz wiersz: `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />`.

### <a name="microsoftcppprops-import-element"></a>Microsoft. cpp. props — element importu

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

Arkusz właściwości **Microsoft. cpp. props** (bezpośrednio lub za pośrednictwem importu) definiuje wartości domyślne dla wielu właściwości specyficznych dla narzędzia, takich jak właściwości optymalizacji i poziomu ostrzeżeń kompilatora, właściwość TYPELIBRARYNAME narzędzia MIDL i tak dalej. Importuje również różne systemowe arkusze właściwości, na podstawie których właściwości konfiguracji są zdefiniowane w grupie właściwości bezpośrednio powyżej.

### <a name="extensionsettings-importgroup-element"></a>Poprawny ExtensionSettings element obiektu

```xml
<ImportGroup Label="ExtensionSettings" />
```

Grupa `ExtensionSettings` zawiera Importy dla arkuszy właściwości, które są częścią dostosowania kompilacji. Dostosowanie kompilacji jest definiowane przez maksymalnie trzy pliki: plik. targets, plik. props i plik. XML. Ta grupa importu zawiera Importy dla pliku. props.

### <a name="propertysheets-importgroup-elements"></a>PropertySheets elementy obiektu

```xml
<ImportGroup Label="PropertySheets" />
```

Grupa `PropertySheets` zawiera Importy dla arkuszy właściwości użytkownika. Są to arkusze właściwości, które można dodać za pomocą widoku Menedżer właściwości w programie Visual Studio. Kolejność, w której wymienione są te Importy, jest ważna i jest odzwierciedlana w Menedżer właściwości. Plik projektu zwykle zawiera wiele wystąpień tego rodzaju grupy importowania, po jednej dla każdej konfiguracji projektu.

### <a name="usermacros-propertygroup-element"></a>UserMacros — element właściwości

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` zawiera właściwości tworzone jako zmienne, które są używane do dostosowywania procesu kompilacji. Na przykład można zdefiniować makro użytkownika, aby zdefiniować niestandardową ścieżkę wyjściową jako $ (CustomOutputPath) i użyć jej do zdefiniowania innych zmiennych. Ta grupa właściwości przechowuje takie właściwości. Należy pamiętać, że w programie Visual Studio ta grupa nie jest wypełniona w pliku projektu C++ , ponieważ Wizualizacja nie obsługuje makr użytkownika dla konfiguracji. Makra użytkownika są obsługiwane w arkuszach właściwości.

### <a name="per-configuration-propertygroup-elements"></a>Elementy właściwości dla każdej konfiguracji

```xml
<PropertyGroup />
```

Istnieje wiele wystąpień tej grupy właściwości, jedną dla każdej konfiguracji dla wszystkich konfiguracji projektu. Każda grupa właściwości musi mieć dołączony jeden warunek konfiguracji. W przypadku braku konfiguracji okno dialogowe **właściwości projektu** nie będzie działało poprawnie. W przeciwieństwie do powyższych grup właściwości, ten element nie ma etykiety. Ta grupa zawiera ustawienia na poziomie konfiguracji projektu. Te ustawienia mają zastosowanie do wszystkich plików, które są częścią określonej grupy elementów. Metadane definicji elementu dostosowania kompilacji są inicjowane w tym miejscu.

Ta właściwość musi znajdować się po `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` i nie może istnieć żadna inna Właściwość bez etykiety (w przeciwnym razie Edytowanie właściwości projektu nie będzie działać poprawnie).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Elementy ItemDefinitionGroup na konfigurację

```xml
<ItemDefinitionGroup />
```

Zawiera definicje elementów. Muszą one być zgodne z tymi samymi regułami, co elementy z właściwością co najmniej etykieta dla każdej konfiguracji.

### <a name="itemgroup-elements"></a>Elementy elementu

```xml
<ItemGroup />
```

Zawiera elementy (pliki źródłowe itp.) w projekcie. Warunki nie są obsługiwane dla elementów projektu (oznacza to, że typy elementów, które są traktowane jako elementy projektu według definicji reguł).

Metadane powinny mieć warunki konfiguracji dla każdej konfiguracji, nawet jeśli są takie same. Na przykład:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

System projektu programu C++ Visual Studio obecnie nie obsługuje symboli wieloznacznych w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

System projektu programu C++ Visual Studio aktualnie nie obsługuje makr w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Odwołania są określone w elemencie Items i mają następujące ograniczenia:

- Odwołania nie obsługują warunków.

- Metadane odwołań nie obsługują warunków.

### <a name="microsoftcpptargets-import-element"></a>Element Imports Microsoft. cpp. targets

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definiuje elementy wizualne C++ (bezpośrednio lub za pośrednictwem importu), takie jak kompilacja, czyszczenie itp.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets element obiektu

```xml
<ImportGroup Label="ExtensionTargets" />
```

Ta grupa zawiera Importy dla plików docelowych dostosowywania kompilacji.

## <a name="impact-of-incorrect-ordering"></a>Wpływ nieprawidłowej kolejności

Środowisko IDE programu Visual Studio zależy od pliku projektu, który został opisany powyżej. Na przykład po zdefiniowaniu wartości właściwości na stronach właściwości środowisko IDE zazwyczaj umieści definicję właściwości w grupie właściwości z pustą etykietą. Gwarantuje to, że wartości domyślne wprowadzone w arkuszach właściwości systemu zostaną przesłonięte przez wartości zdefiniowane przez użytkownika. Podobnie pliki docelowe są importowane na końcu, ponieważ wykorzystują właściwości zdefiniowane powyżej i ponieważ zazwyczaj nie definiują samych właściwości. Podobnie arkusze właściwości użytkownika są importowane po arkuszach właściwości systemu (zawartych w **Microsoft. cpp. props**). Dzięki temu użytkownik może zastąpić wszystkie wartości domyślne, które są wprowadzane przez systemowe arkusze właściwości.

Jeśli plik. vcxproj nie jest zgodny z tym układem, wyniki kompilacji mogą nie być oczekiwane. Na przykład w przypadku błędnego zaimportowania systemowego arkusza właściwości po arkuszu właściwości zdefiniowanym przez użytkownika ustawienia użytkownika zostaną przesłonięte przez systemowe arkusze właściwości.

Nawet środowisko projektowania IDE jest zależne od pewnego zakresu od prawidłowej kolejności elementów. Na przykład, jeśli plik. vcxproj nie ma grupy importu `PropertySheets`, IDE może nie być w stanie określić, gdzie umieścić nowy arkusz właściwości utworzony przez użytkownika w **Menedżer właściwości**. Może to spowodować przesłanianie arkusza użytkownika przez arkusz systemowy. Chociaż algorytm heurystyczny używany przez IDE może tolerować niewielkie niespójności w układzie pliku. vcxproj, zdecydowanie zaleca się, aby nie odróżnić od struktury pokazanej wcześniej w tym artykule.

## <a name="how-the-ide-uses-element-labels"></a>Jak środowisko IDE używa etykiet elementów

W środowisku IDE, gdy właściwość **UseOfAtl** jest ustawiana na stronie właściwości ogólne, jest zapisywana w grupie Właściwości konfiguracji w pliku projektu, podczas gdy właściwość **TargetName** na tej samej stronie właściwości jest zapisywana w grupie Właściwości "Less" dla określonej konfiguracji. Program Visual Studio analizuje plik XML strony właściwości, aby uzyskać informacje o tym, gdzie należy napisać każdą właściwość. Na stronie właściwości **Ogólne** (przy założeniu, że masz angielską wersję programu Visual Studio 2019 Enterprise Edition), ten plik jest `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Plik reguł XML strony właściwości definiuje statyczne informacje o regule i jej właściwości. Jedną z tych informacji jest preferowane położenie właściwości reguły w pliku docelowym (plik, w którym zostanie zapisywana jego wartość). Preferowana pozycja jest określana przez atrybut Label dla elementów pliku projektu.

## <a name="property-sheet-layout"></a>Układ arkusza właściwości

Poniższy fragment kodu XML jest minimalnym układem pliku arkusza właściwości (. props). Jest on podobny do pliku. vcxproj, a funkcje elementów. props można wywnioskować na podstawie wcześniejszej dyskusji.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Aby utworzyć własny arkusz właściwości, skopiuj jeden z plików. props w folderze VCTargets i zmodyfikuj go do własnych potrzeb. W przypadku programu Visual Studio 2019 Enterprise Edition domyślną ścieżką VCTargets jest `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Zobacz także

[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)<br/>
[Pliki XML strony właściwości](property-page-xml-files.md)
