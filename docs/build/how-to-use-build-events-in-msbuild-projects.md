---
title: "Porady: Korzystanie ze zdarzeń kompilacji w projektach MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.usebuildevents
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebbccf147cc45ce5e3dab512e13a8b059f104cdd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Porady: korzystanie ze zdarzeń kompilacji w projektach MSBuild
To zdarzenie kompilacji jest polecenie który [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] wykonuje określonego etapu w procesie kompilacji. *Prekompilacyjnego* zdarzenie przed rozpoczęciem kompilacji; *prekonsolidacyjnego* zdarzenie przed uruchomieniem kroku łącze; i *postkompilacyjnego* zdarzenie po kompilacji kończy się pomyślnie. Zdarzenia kompilacji występuje tylko wtedy, gdy występuje kroku kompilacji. Zdarzenia prekonsolidacyjnego nie występuje na przykład, jeśli krok łącze nie działa.  
  
 Każda zdarzeń trzy kompilacji jest reprezentowana w grupie definicji elementu przez command element (`<Command>`) który jest wykonywany i elementu komunikatu (`<Message>`) czyli wyświetlane **MSBuild** wykonuje zdarzeń kompilacji. Każdy element jest opcjonalny, i podanie tego samego elementu wiele razy, pierwszeństwo ma ostatniego wystąpienia.  
  
 Opcjonalny *Użyj kompilacji* elementu (`<`*zdarzenie kompilacji***UseInBuild**`>`) można określić w grupie właściwości, aby wskazać, czy Zdarzenie kompilacji jest wykonywana. Wartość zawartości *Użyj kompilacji* jest element `true` lub `false`. Domyślnie to zdarzenie kompilacji jest wykonywany, chyba że odpowiednie *Użyj kompilacji* element jest ustawiony na wartość `false`.  
  
 W poniższej tabeli wymieniono każdego zdarzenia kompilacji — element XML:  
  
|XML Element|Opis|  
|-----------------|-----------------|  
|`PreBuildEvent`|To zdarzenie jest wykonywany przed rozpoczęciem kompilacji.|  
|`PreLinkEvent`|To zdarzenie jest wykonywany przed rozpoczęciem kroku łącza.|  
|`PostBuildEvent`|To zdarzenie jest wykonywana po zakończeniu kompilacji.|  
  
 Poniższa tabela zawiera listę *Użyj kompilacji* elementu:  
  
|XML Element|Opis|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|Określa, czy można wykonać *prekompilacyjnego* zdarzeń.|  
|`PreLinkEventUseInBuild`|Określa, czy można wykonać *prekonsolidacyjnego* zdarzeń.|  
|`PostBuildEventUseInBuild`|Określa, czy można wykonać *postkompilacyjnego* zdarzeń.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład można dodać wewnątrz elementu projektu utworzonych w pliku myproject.vcxproj [wskazówki: przy użyciu programu MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). A *prekompilacyjnego* sprawia, że zdarzenie kopię main.cpp; *prekonsolidacyjnego* sprawia, że zdarzenie kopię main.obj; a co *postkompilacyjnego* zdarzeń tworzy kopię myproject.exe. Jeśli projekt został zbudowany przy użyciu konfiguracji wydanie, wykonywane są zdarzeń kompilacji. Jeśli projekt został zbudowany przy użyciu konfiguracji debugowania, zdarzeń kompilacji nie zostaną wykonane.  
  
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
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)   
 [Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)