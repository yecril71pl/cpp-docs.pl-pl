---
title: pliki. vcxproj i symbole wieloznaczne
description: Jak natywne pliki Project System. vcxproj języka C++ obsługują symbole wieloznaczne.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 23d36a63f328e14cca59d1d57838173b4dcb0954
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662883"
---
# <a name="vcxproj-files-and-wildcards"></a>`.vcxproj` pliki i symbole wieloznaczne

Środowisko IDE programu Visual Studio nie obsługuje niektórych konstrukcji elementów projektu w *`.vcxproj`* plikach. Te nieobsługiwane konstrukcje obejmują symbole wieloznaczne, listy rozdzielane średnikami lub makra MSBuild, które rozszerzają się do wielu plików. `.vcxproj`System projektu dla kompilacji C++ jest bardziej restrykcyjny niż MSBuild. Każdy element projektu musi mieć własny element MSBuild. Aby uzyskać więcej informacji na temat `.vcxproj` formatu pliku, zobacz [ `.vcxproj` i `.props` Struktura pliku](vcxproj-file-structure.md).

Te przykłady konstrukcji nie są obsługiwane przez środowisko IDE:

```xml
<ItemGroup>
  <None Include="*.txt">
  <ClCompile Include="a.cpp;b.cpp"/>
  <ClCompile Include="@(SomeItems)" />
</ItemGroup>
```

Jeśli `.vcxproj` plik projektu zawierający te konstrukcje są ładowane w środowisku IDE, projekt może wydawać się w pierwszej kolejności. Problemy są jednak prawdopodobnie zaraz po zmodyfikowaniu projektu przez program Visual Studio, a następnie zapisaniu go na dysku. Mogą wystąpić przypadkowe awarie i niezdefiniowane zachowanie.

W programie Visual Studio 2019 w wersji 16,7, gdy program Visual Studio ładuje `.vcxproj` plik projektu, automatycznie wykrywa nieobsługiwane wpisy w elementach projektu. Podczas ładowania rozwiązania zobaczysz ostrzeżenia w oknie danych wyjściowych.

Program Visual Studio 2019 w wersji 16,7 również dodaje obsługę projektu tylko do odczytu. Obsługa tylko do odczytu umożliwia środowisku IDE używanie ręcznie utworzonych projektów, które nie mają dodatkowych ograniczeń projektów, które można edytować w środowisku IDE.

Jeśli masz `.vcxproj` plik, który korzysta z co najmniej jednego nieobsługiwanego konstrukcje, możesz go załadować bez ostrzeżeń w IDE przy użyciu jednej z następujących opcji:

- Wyświetl wszystkie elementy jawnie
- Oznacz swój projekt jako tylko do odczytu
- Przenoszenie elementów symboli wieloznacznych do treści docelowej

## <a name="list-all-items-explicitly"></a>Wyświetl wszystkie elementy jawnie

Obecnie nie ma możliwości, aby elementy rozszerzające symbole wieloznaczne były widoczne w oknie Eksplorator rozwiązań w projekcie nietylko do odczytu. Eksplorator rozwiązań oczekuje, że projekty mają jawnie listę wszystkich elementów.

Aby `.vcxproj` projekty były automatycznie rozszerzane o symbole wieloznaczne w programie Visual Studio 2019 w wersji 16,7 lub nowszej, należy ustawić `ReplaceWildcardsInProjectItems` Właściwość na `true` . Zalecamy utworzenie *`Directory.Build.props`* pliku w katalogu głównym i użycie tej zawartości:

```xml
<Project>
  <PropertyGroup>
    <ReplaceWildcardsInProjectItems>true</ReplaceWildcardsInProjectItems>
  </PropertyGroup>
</Project>
```

## <a name="mark-your-project-as-read-only"></a>Oznacz swój projekt jako tylko do odczytu

W programie Visual Studio 2019 w wersji 16,7 lub nowszej można oznaczyć projekty jako *tylko do odczytu*. Aby oznaczyć projekt jako tylko do odczytu, Dodaj następującą właściwość do *`.vcxproj`* pliku lub do któregokolwiek z importowanych plików:

```xml
<PropertyGroup>
    <ReadOnlyProject>true</ReadOnlyProject>
</PropertyGroup>
```

`<ReadOnlyProject>`Ustawienie uniemożliwia programowi Visual Studio edytowanie i zapisywanie projektu, dzięki czemu można używać dowolnych z nich konstrukcji programu MSBuild, w tym symboli wieloznacznych.

Ważne jest, aby wiedzieć, że pamięć podręczna projektu nie jest dostępna, jeśli program Visual Studio wykryje symbole wieloznaczne w elementach projektu w *`.vcxproj`* pliku lub dowolnym z jego importów. Czasy ładowania rozwiązań w IDE są znacznie dłuższe w przypadku wielu projektów, które używają symboli wieloznacznych.

## <a name="move-wildcard-items-to-a-target-body"></a>Przenoszenie elementów symboli wieloznacznych do treści docelowej

Możesz chcieć użyć symboli wieloznacznych, aby zebrać zasoby, dodać wygenerowane źródła i tak dalej. Jeśli nie są one potrzebne w oknie Eksplorator rozwiązań, można użyć tej procedury w zamian:

1. Zmień nazwę grupy elementów, aby dodać symbole wieloznaczne. Na przykład zamiast:

   ```xml
   <Image Include="*.bmp" />
   <ClCompile Include="*.cpp" />
   ```

   Zmień na:

   ```xml
   <_WildCardImage Include="*.bmp" />
   <_WildCardClCompile Include="*.cpp" />
   ```

1. Dodaj tę zawartość do  *`.vcxproj`* pliku.Lub Dodaj go do *`Directory.Build.targets`* pliku w katalogu głównym, aby mieć wpływ na wszystkie projekty w tym katalogu głównym:

   ```xml
   <Target Name="AddWildCardItems"
       AfterTargets="BuildGenerateSources">
     <ItemGroup>
       <Image Include="@(_WildCardImage)" />
       <ClCompile Include="@(_WildCardClCompile)" />
     </ItemGroup>
   </Target>
   ```

   Ta zmiana powoduje, że kompilacja zobaczy elementy, które są zdefiniowane w  *`.vcxproj`* pliku. Jednak teraz nie są one widoczne w oknie Eksplorator rozwiązań i nie będą powodowały problemów w środowisku IDE.

1. Aby wyświetlić poprawną funkcję IntelliSense dla  `_WildCardClCompile`   elementów po otwarciu tych plików w edytorze, Dodaj następującą zawartość:

   ```xml
   <PropertyGroup>
     <ComputeCompileInputsTargets>
       AddWildCardItems
       $(ComputeCompileInputsTargets)
     </ComputeCompileInputsTargets>
   </PropertyGroup>
   ```

Efektywnie można używać symboli wieloznacznych dla każdego elementu w treści docelowej. Można również użyć symboli wieloznacznych w  `ItemGroup`   , które nie są zdefiniowane jako element projektu przez [`ProjectSchemaDefinition`](https://devblogs.microsoft.com/cppblog/vc-MSBuild-extensibility-example/) .

> [!NOTE]
> Jeśli przeniesiesz symbol wieloznaczny z *`.vcxproj`* pliku do zaimportowanego pliku, nie będą one widoczne w oknie Eksplorator rozwiązań. Ta zmiana umożliwia również załadowanie projektu w środowisku IDE bez modyfikacji. Nie zaleca się jednak, aby ta metoda została wyłączona, ponieważ powoduje wyłączenie pamięci podręcznej projektu.

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)<br/>
[Pliki XML strony właściwości](property-page-xml-files.md)
