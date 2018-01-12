---
title: "Porady: tworzenie aplikacji konsoli środowiska CLR (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ccb46ca7cd9cb7e1999a0be684eccf712006618e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Porady: tworzenie aplikacji do konsoli środowiska CLR (C++/CLI)
Szablon aplikacji konsoli można utworzyć projekt aplikacji konsoli, która ma już odwołań projektu podstawowych oraz pliki.  
  
 Zazwyczaj aplikacji konsoli jest kompilowany do autonomicznego pliku wykonywalnego, ale nie ma graficznego interfejsu użytkownika. Użytkownik uruchamia aplikację konsoli w wierszu polecenia i używa instrukcji problem do uruchomionej aplikacji w wierszu polecenia. W wierszu polecenia aplikacji zawiera także informacje w danych wyjściowych. Natychmiastowości aplikacji konsoli ułatwia doskonałym sposobem poznawania technik programowania bez obawy dotyczące implementowania interfejsu użytkownika.  
  
 Gdy używasz szablonu aplikacji konsoli, aby utworzyć projekt, automatycznie dodaje to, te odwołania i pliki:  
  
-   Odwołania do tych przestrzeni nazw .NET Framework:  
  
    -   [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx)— zawiera podstawowe klasy i klasy podstawowej, które definiują powszechnie używane wartości i odwołania do typów danych, zdarzeń i procedury obsługi zdarzeń, interfejsów, atrybuty i przetwarzanie wyjątków.  
  
    -   mscorlib — zestawu DLL, która obsługuje programowanie .NET Framework.  
  
-   Pliki źródłowe:  
  
    -   W konsoli (plik .cpp) — główne źródło pliku i punktu wejścia do aplikacji, który został właśnie utworzony. Identyfikuje plik dll projektu i przestrzeń nazw projektu. Podaj kod w tym pliku.  
  
    -   Atrybuty AssemblyInfo.cpp—Contains, plików, zasobów, typów, informacje na temat wersji, podpisywania informacji i tak dalej, używanej do zmodyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [zawartość zestawu](/dotnet/framework/app-domains/assembly-contents).  
  
    -   Stdafx.cpp—Used tworzenie prekompilowanego pliku nagłówkowego o nazwie Win32.pch i plik wstępnie skompilowane typy o nazwie StdAfx.obj.  
  
-   Pliki nagłówkowe:  
  
    -   Stdafx.h—Used tworzenie prekompilowanego pliku nagłówkowego o nazwie Win32.pch i plik wstępnie skompilowane typy o nazwie StdAfx.obj.  
  
    -   wygenerowany Resource.h—A Uwzględnij plik dla app.rc.  
  
-   Pliki zasobów:  
  
    -   plik skryptu zasobu App.RC—the programu.  
  
    -   Plik ikony App.ico—the programu.  
  
-   ReadMe.txt—Describes pliki w projekcie.  
  
## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Aby utworzyć projekt aplikacji konsoli środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **zainstalowane szablony**, wybierz pozycję **Visual C++** węzła, wybierz opcję **CLR** węzeł, a następnie wybierz szablon aplikacji konsoli.  
  
3.  W **nazwa** wprowadź unikatową nazwę aplikacji.  
  
     Można określić innych ustawień projektu i rozwiązania, ale nie są wymagane.  
  
4.  Wybierz **OK** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekty CLR](../ide/files-created-for-clr-projects.md)   


