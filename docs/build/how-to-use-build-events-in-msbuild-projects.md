---
title: 'Porady: Korzystanie ze zdarzeń kompilacji w projektach MSBuild | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.usebuildevents
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdc5ea4c2cd1e02e6894d2dedf8470641021f0b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214472"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild
To zdarzenie kompilacji jest polecenia, który program MSBuild wykonuje na określonym etapie w procesie kompilacji. *Prekompilacji* wystąpi zdarzenie, przed rozpoczęciem kompilacji; *prekonsolidacyjnego* wystąpi zdarzenie przed uruchomieniem kroku łącze; i *po kompilacji* wystąpi zdarzenie po kompilacji kończy się pomyślnie. To zdarzenie kompilacji występuje tylko wtedy, gdy występuje w kroku skojarzonej kompilacji. Na przykład zdarzenia prekonsolidacyjnego nie występuje krokiem link nie zostanie uruchomione.  
  
 Wszystkich zdarzeń kompilacji trzy jest reprezentowana w grupie definicji elementów przez command element (`<Command>`) które jest wykonywane i message element (`<Message>`) oznacza to wyświetlane, **MSBuild** wykonuje zdarzeń kompilacji. Każdy element jest opcjonalny, a jeśli określisz tego samego elementu wielokrotnie ostatniego wystąpienia ma pierwszeństwo.  
  
 Opcjonalny *Użyj kompilacji* — element (`<`*zdarzenia kompilacji*`UseInBuild>`) można określić w grupie właściwości, aby wskazać, czy zdarzenie kompilacji jest wykonywany. Wartość zawartości *Użyj kompilacji* jest element `true` lub `false`. Domyślnie to zdarzenie kompilacji jest wykonywane, chyba że odpowiadającymi mu dostawcami *Użyj kompilacji* element jest ustawiony na wartość `false`.  
  
 Poniższa tabela zawiera listę każdego zdarzenia kompilacji — element XML:  
  
|— Element XML|Opis|  
|-----------------|-----------------|  
|`PreBuildEvent`|To zdarzenie jest wykonywany przed rozpoczęciem kompilacji.|  
|`PreLinkEvent`|To zdarzenie jest wykonywany przed rozpoczęciem kroku łączenia.|  
|`PostBuildEvent`|To zdarzenie jest wykonywany po zakończeniu kompilacji.|  
  
 W poniższej tabeli wymieniono każdy *Użyj kompilacji* elementu:  
  
|— Element XML|Opis|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|Określa, czy można wykonać *prekompilacji* zdarzeń.|  
|`PreLinkEventUseInBuild`|Określa, czy można wykonać *prekonsolidacyjnego* zdarzeń.|  
|`PostBuildEventUseInBuild`|Określa, czy można wykonać *postkompilacyjnego* zdarzeń.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład można dodać wewnątrz elementu projektu myProject.vcxproj za elementem pliku utworzonego w [Instruktaż: przy użyciu programu MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). A *prekompilacji* zdarzeń sprawia, że kopia main.cpp; *prekonsolidacyjnego* zdarzeń sprawia, że kopia main.obj; a co *po kompilacji* zdarzeń tworzy kopię myproject.exe. Jeśli projekt jest kompilowany przy użyciu konfiguracji wydania, wykonywane są zdarzeń kompilacji. Jeśli projekt jest kompilowany przy użyciu konfiguracji debugowania, zdarzeń kompilacji nie zostaną wykonane.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Program MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)   
 [Przewodnik: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)