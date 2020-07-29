---
title: 'Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 7c35abbcabe62da2e60fbc2393c575e7c3872cf3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224009"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild

Zdarzenie kompilacji to polecenie, które program MSBuild wykonuje na określonym etapie procesu kompilacji. Zdarzenie *przed kompilacją* występuje przed rozpoczęciem kompilacji; zdarzenie *poprzedzające konsolidację* występuje przed uruchomieniem kroku linku; zdarzenie *po kompilacji* występuje po pomyślnym zakończeniu kompilacji. Zdarzenie kompilacji występuje tylko wtedy, gdy występuje skojarzony krok kompilacji. Na przykład zdarzenie poprzedzające połączenie nie występuje, jeśli krok łącza nie zostanie uruchomiony.

Każde z trzech zdarzeń kompilacji jest reprezentowane w grupie definicji elementu przez element polecenia ( `<Command>` ), który jest wykonywany, i element Message ( `<Message>` ), który jest wyświetlany, gdy **MSBuild** wykonuje zdarzenie kompilacji. Każdy element jest opcjonalny, a jeśli określisz ten sam element wielokrotnie, ostatnie wystąpienie ma pierwszeństwo.

Do grupy właściwości można określić opcjonalny element *use-in-Build* ( `<` *kompilacja-zdarzenie* `UseInBuild>` ), aby wskazać, czy zdarzenie kompilacji jest wykonywane. Wartość zawartości elementu *use-in-Build* jest albo **`true`** **`false`** . Domyślnie zdarzenie kompilacji jest wykonywane, chyba że jego odpowiadający element *use-in-Build* jest ustawiony na **`false`** .

W poniższej tabeli wymieniono każdy element XML zdarzenia kompilacji:

|Element XML|Opis|
|-----------------|-----------------|
|`PreBuildEvent`|To zdarzenie jest wykonywane przed rozpoczęciem kompilacji.|
|`PreLinkEvent`|To zdarzenie jest wykonywane przed rozpoczęciem kroku linku.|
|`PostBuildEvent`|To zdarzenie jest wykonywane po zakończeniu kompilacji.|

Poniższa tabela zawiera listę wszystkich elementów *użytych w kompilacji* :

|Element XML|Opis|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Określa, czy ma zostać wykonane zdarzenie *poprzedzające kompilację* .|
|`PreLinkEventUseInBuild`|Określa, czy ma zostać wykonane zdarzenie *poprzedzające połączenie* .|
|`PostBuildEventUseInBuild`|Określa, czy ma zostać wykonane zdarzenie *po kompilacji* .|

## <a name="example"></a>Przykład

Poniższy przykład może być dodany wewnątrz elementu projektu pliku VCXPROJ. WebProject. Web, który został utworzony w [instruktażu: przy użyciu programu MSBuild do utworzenia projektu języka C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Zdarzenie *sprzed kompilacji* tworzy kopię głównego programu. cpp; zdarzenie *poprzedzające konsolidację* tworzy kopię Main. obj; a zdarzenie *po kompilacji* wykonuje kopię myproject.exe. Jeśli projekt został skompilowany przy użyciu konfiguracji wydania, zdarzenia kompilacji są wykonywane. Jeśli projekt został skompilowany przy użyciu konfiguracji debugowania, zdarzenia kompilacji nie są wykonywane.

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz także

[MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)<br/>
[Przewodnik: Tworzenie projektu C++ przy użyciu programu MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
