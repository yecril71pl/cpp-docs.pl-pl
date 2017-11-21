---
title: "Określanie niestandardowych narzędzi kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs: C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c65664e6c09028f1f15ded917a59ad013868f841
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-custom-build-tools"></a>Określanie niestandardowych narzędzi kompilacji
A *niestandardowego narzędzia kompilacji* zapewnia system kompilacji potrzebnych do tworzenia plików wejściowych określonych informacji. Narzędzie niestandardowej kompilacji Określa polecenie do uruchomienia, listę plików wejściowych, lista plików wyjściowych, które są generowane przez polecenie i opcjonalny opis narzędzia.  
  
 Aby uzyskać ogólne informacje o niestandardowych narzędzi kompilacji i niestandardowe kroki procesu kompilacji, zobacz [niestandardowych krokach kompilacji zrozumienia i tworzenie zdarzenia](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### <a name="to-specify-a-custom-build-tool"></a>Aby określić niestandardowe narzędzie kompilacji  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **właściwości konfiguracji** umożliwiające **konfiguracji** pole. W **konfiguracji** wybierz konfigurację, dla której ma zostać określone narzędzia kompilacji niestandardowej.  
  
3.  W **Eksploratora rozwiązań**, wybierz plik wejściowy dla niestandardowego narzędzia kompilacji.  
  
     Jeśli **niestandardowe narzędzia kompilacji** folder nie jest wyświetlana, rozszerzenie pliku wybrany plik jest skojarzony z domyślnym narzędziem. Na przykład domyślnego narzędzia dla plików .c i .cpp jest kompilatora. Aby zastąpić domyślne ustawienie narzędzia w **właściwości konfiguracji** węzła w **ogólne** folderu w **typu elementu** właściwości, kliknij przycisk **niestandardowej kompilacji Narzędzie**. Kliknij przycisk **Zastosuj** i **niestandardowe narzędzia kompilacji** węzeł jest wyświetlany.  
  
4.  W **niestandardowe narzędzia kompilacji** węzła w **ogólne** folderu, określ właściwości skojarzone z niestandardowe narzędzie kompilacji:  
  
    -   W **dodatkowe zależności**, określ wszelkie dodatkowe pliki poza jednym, dla którego jest definiowany niestandardowego narzędzia kompilacji (pliku skojarzone z niestandardowego narzędzia kompilacji jest niejawnie uznane za dane wejściowe do narzędzia). O dodatkowe pliki wejściowe nie jest wymagane dla narzędzia kompilacji niestandardowej. Jeśli masz więcej niż jeden dodatkowych danych wejściowych, oddziel je średnikami.  
  
         Jeśli **dodatkowe zależności** pliku Data jest późniejsza niż pliku wejściowego, a następnie uruchomienie narzędzia kompilacji niestandardowej. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż pliku wejściowego i pliku wejściowego jest starsza niż **dane wyjściowe** właściwości pliku, a następnie niestandardowego narzędzia kompilacji nie zostało uruchomione.  
  
         Załóżmy na przykład narzędzie niestandardowej kompilacji, która przyjmuje MyInput.x jako dane wejściowe i generuje MyInput.cpp i że MyInput.x zawiera plik nagłówka, MyHeader.h. MyHeader.h można określić jako zależność od MyInput.x wejściowych, a system kompilacji zostanie skompilowany MyInput.cpp, gdy jest nieaktualne względem MyInput.x lub MyHeader.h.  
  
         Wejściowy zależności zapewni, że Twoje niestandardowe narzędzia kompilacji są uruchamiane w kolejności potrzebnych im. W powyższym przykładzie załóżmy, że MyHeader.h jest rzeczywiście dane wyjściowe narzędzia kompilacji niestandardowej. Ponieważ MyHeader.h zależność MyInput.x, system kompilacji najpierw utworzyć przed uruchomieniem tego narzędzia niestandardowej kompilacji na MyInput.x Myheader.h.  
  
    -   W **wiersza polecenia**, określić polecenie, tak jakby był on określenie w wierszu polecenia. Określ prawidłowy polecenia lub pliku wsadowego, a wszelkie wymagane dane wejściowe lub plików wyjściowych. Określ **wywołać** partii polecenia przed nazwą pliku wsadowego, aby zagwarantować, że wszystkie kolejne polecenia są wykonywane.  
  
         Wiele plików wejściowych i wyjściowych można określić symbolicznie z makra programu MSBuild. [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]Określanie lokalizacji plików lub nazw zestawów plików, zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Ponieważ znak "%" jest zarezerwowany przez program MSBuild, jeśli określisz zmienną środowiskową Zastąp każdego  **%**  ucieczki znaku o **% 25** szesnastkowa sekwencja unikowa. Na przykład zastąpić **% WINDIR %** z **25WINDIR % 25**. MSBuild zastępuje wszystkie **% 25** sekwencji z  **%**  znak przed uzyskuje dostęp do zmiennej środowiskowej.  
  
    -   W **opis**, wpisz opisową komunikat dotyczący tego narzędzia kompilacji niestandardowej. Komunikat jest drukowana **dane wyjściowe** okna, jeśli system kompilacji przetwarza tego narzędzia.  
  
    -   W **dane wyjściowe**, określ nazwę pliku wyjściowego. Jest to wymagane wpis; Narzędzie niestandardowej kompilacji bez wartości dla tej właściwości, nie będzie działać. Jeśli narzędzie niestandardowej kompilacji ma więcej niż jedno wyjście, Rozdziel nazwy plików średnikami.  
  
         Nazwę pliku wyjściowego powinny być takie same, jak określono w **wiersza polecenia** właściwości. System kompilacji projektu Szukaj pliku, a następnie sprawdź daty. Jeśli plik wyjściowy jest nowszy niż plik wejściowy lub jeśli plik wyjściowy nie zostanie znaleziony, uruchomienie narzędzia kompilacji niestandardowej. Jeśli wszystkie z **dodatkowe zależności** pliki są starsze niż pliku wejściowego i pliku wejściowego jest starsza niż określona w pliku **dane wyjściowe** właściwości niestandardowego narzędzia kompilacji nie zostało uruchomione.  
  
 Jeśli chcesz, aby system kompilacji do działania na plik wyjściowy wygenerowany przez narzędzie niestandardowej kompilacji, użytkownik musi ręcznie dodać do projektu. Narzędzie niestandardowej kompilacji spowoduje zaktualizowanie pliku podczas kompilacji.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że chcesz dołączyć do projektu pliku o nazwie parser.l. Ma leksykalne analizatora do przetworzenia parser.l w celu utworzenia pliku .c, który ma taką samą nazwę podstawową (parser.c).  
  
 Najpierw należy dodać parser.l i parser.c do projektu. Jeśli pliki jeszcze nie istnieją, po prostu Dodaj odwołanie do plików. Tworzenie niestandardowego narzędzia kompilacji dla parser.l i wpisz następujące polecenie w **polecenia** właściwości:  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 To polecenie uruchamiania analizatora leksykalne na parser.l i dane wyjściowe parser.c do katalogu projektu.  
  
 W **dane wyjściowe** właściwości, wpisz następujące polecenie:  
  
```  
.\%(Filename).c  
```  
  
 Podczas kompilowania projektu system kompilacji porównuje sygnatury czasowe parser.l i parser.c. Jeśli parser.l jest nowsza, lub Jeśli parser.c nie istnieje, system kompilacji uruchamia wartość **wiersza polecenia** właściwości można wyświetlić parser.c aktualne. Ponieważ parser.c również został dodany do projektu, system kompilacji następnie kompiluje parser.c.  
  
## <a name="see-also"></a>Zobacz też  
 [Typowe makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md)   
 [Rozwiązywanie problemów z dostosowaniami kompilacji](../ide/troubleshooting-build-customizations.md)