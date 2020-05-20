---
title: Określanie niestandardowych narzędzi kompilacji
ms.date: 06/05/2018
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
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314757"
---
# <a name="specify-custom-build-tools"></a>Określanie niestandardowych narzędzi kompilacji

*Niestandardowe narzędzie kompilacji* zapewnia systemowi kompilacji informacje potrzebne do tworzenia określonych plików wejściowych. Niestandardowe narzędzie kompilacji Określa polecenie do uruchomienia, listę plików wejściowych, listę plików wyjściowych, które są generowane przez polecenie, oraz opcjonalny opis tego narzędzia.

Aby uzyskać ogólne informacje na temat niestandardowych narzędzi kompilacji i niestandardowych kroków kompilacji, zobacz [Opis niestandardowych kroków kompilacji i zdarzeń kompilacji](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Aby określić niestandardowe narzędzie kompilacji

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** , aby włączyć pole **Konfiguracja** . W polu **Konfiguracja** wybierz konfigurację, dla której chcesz określić niestandardowe narzędzie kompilacji.

1. W **Eksplorator rozwiązań**wybierz plik wejściowy dla niestandardowego narzędzia kompilacji.

   Jeśli folder **niestandardowego narzędzia kompilacji** nie jest wyświetlany, rozszerzenie pliku wybranego pliku jest skojarzone z domyślnym narzędziem. Na przykład domyślne narzędzie dla plików. c i. cpp jest kompilatorem. Aby zastąpić domyślne ustawienie narzędzia, w węźle **Właściwości konfiguracji** , w folderze **Ogólne** , we właściwości **Typ elementu** wybierz **niestandardowe narzędzie kompilacji**. Wybierz **Zastosuj** i zostanie wyświetlony węzeł **Narzędzie kompilacji niestandardowej** .

1. W węźle **narzędzia kompilacji niestandardowej** w folderze **Ogólne** Określ właściwości skojarzone z niestandardowym narzędziem kompilacji:

   - W obszarze **dodatkowe zależności**określ wszelkie dodatkowe pliki wykraczające poza plik, dla którego zdefiniowano narzędzie do kompilacji niestandardowej (plik skojarzony z narzędziem kompilacji niestandardowej jest niejawnie traktowany jako dane wejściowe narzędzia). Posiadanie dodatkowych plików wejściowych nie jest wymagane dla niestandardowego narzędzia kompilacji. Jeśli masz więcej niż jedno dodatkowe dane wejściowe, oddziel je średnikami.

      Jeśli dla **pliku** wejściowego jest późniejsza data, to narzędzie kompilacji niestandardowej zostanie uruchomione. Jeśli wszystkie pliki **zależności dodatkowych** są starsze niż plik wejściowy, a plik wejściowy jest starszy niż **plik właściwości Output** , narzędzie kompilacji niestandardowej nie zostanie uruchomione.

      Załóżmy na przykład, że masz niestandardowe narzędzie do kompilowania, które pobiera obiekt. x jako dane wejściowe i generuje plik. cpp, a element. x zawiera pliku nagłówkowego. Można określić plik. h jako zależność wejściową do elementu wsadowego. x, a system kompilacji utworzy plik. cpp, gdy jest nieaktualny, w odniesieniu do elementu wsadowego. x lub. h.

      Zależności wejściowe mogą także zapewnić, że niestandardowe narzędzia kompilacji działają w kolejności, w jakiej są potrzebne. W poprzednim przykładzie Załóżmy, że element. h jest w rzeczywistości wyjściem z niestandardowego narzędzia kompilacji. Ze względu na to, że element webnagłówker. h jest zależnością obiektu Input. x, system kompilacji najpierw kompiluje obiekt. h przed uruchomieniem niestandardowego narzędzia kompilacji na wejściu. x.

   - W **wierszu polecenia**określ polecenie tak, jakby było ono określane w wierszu polecenia. Określ prawidłowe polecenie lub plik wsadowy oraz wszystkie wymagane pliki wejściowe lub wyjściowe. Określ polecenie **call** Batch przed nazwą pliku wsadowego, aby zagwarantować, że wszystkie kolejne polecenia są wykonywane.

      Wiele plików wejściowych i wyjściowych można określić symbolicznie przy użyciu makr MSBuild. Aby uzyskać informacje na temat sposobu określania lokalizacji plików lub nazw zestawów plików, zobacz [Common MACROS for Build Commands and Properties](reference/common-macros-for-build-commands-and-properties.md).

      Ponieważ znak "%" jest zastrzeżony przez MSBuild, w przypadku określenia zmiennej środowiskowej Zamień każdy **%** znak ucieczki na **%25** szesnastkową sekwencję ucieczki. Na przykład Zamień **% windir%** na **% 25WINDIR %25**. MSBuild zastępuje każdą sekwencję **%25** **%** znakiem przed uzyskaniem dostępu do zmiennej środowiskowej.

   - W polu Opis wprowadź komunikat **opisujący**to niestandardowe narzędzie kompilacji. Komunikat jest drukowany w oknie **danych wyjściowych** , gdy system kompilacji przetwarza to narzędzie.

   - W **obszarze dane wyjściowe określ**nazwę pliku wyjściowego. Jest to wymagany wpis; bez wartości dla tej właściwości narzędzie kompilacji niestandardowej nie zostanie uruchomione. Jeśli niestandardowe narzędzie kompilacji ma więcej niż jedno wyjście, oddziel nazwy plików średnikami.

      Nazwa pliku wyjściowego powinna być taka sama jak określona we właściwości **wiersza polecenia** . System kompilacji projektu będzie szukać pliku i sprawdzić jego datę. Jeśli plik wyjściowy jest starszy niż plik wejściowy lub nie można odnaleźć pliku wyjściowego, zostanie uruchomione narzędzie kompilacji niestandardowej. Jeśli wszystkie pliki **zależności dodatkowych** są starsze niż plik wejściowy, a plik wejściowy jest starszy niż plik określony **we właściwości Output** , narzędzie kompilacji niestandardowej nie zostanie uruchomione.

Jeśli system kompilacji ma działać na pliku wyjściowym wygenerowanym przez niestandardowe narzędzie kompilacji, musisz ręcznie dodać go do projektu. Narzędzie kompilacji niestandardowej zaktualizuje plik podczas kompilacji.

## <a name="example"></a>Przykład

Załóżmy, że chcesz dołączyć plik o nazwie parser. l do projektu. W ścieżce pliku wykonywalnego znajduje się Analizator leksykalny **Analizator leksykalny. exe**. Chcesz użyć go do przetworzenia pliku. c, który ma taką samą nazwę bazową (parser. c).

Najpierw Dodaj parser. l i parser. c do projektu. Jeśli pliki jeszcze nie istnieją, Dodaj odwołanie do tych plików. Utwórz niestandardowe narzędzie kompilacji dla parsera. l i wprowadź następujące polecenie we właściwości **Commands** :

> **Analizator leksykalny% (FullPath). \% (Filename). c**

To polecenie powoduje uruchomienie analizatora leksykalnego na analizatorze. l i wyjście parser. c do katalogu projektu.

We właściwości **Outputs** Outputs wprowadź następujące polecenie:

> **.\% (Filename). c**

Podczas kompilowania projektu, system kompilacji porównuje sygnatury czasowe analizatora składni. l i parser. c. Jeśli parser. l jest nowszy lub jeśli parser. c nie istnieje, system kompilacji uruchamia wartość właściwości **wiersza polecenia** , aby uzyskać analizator składni. c. Ponieważ parser. c został również dodany do projektu, system kompilacji kompiluje parser. c.

## <a name="see-also"></a>Zobacz także

[Typowe makra dla właściwości i poleceń kompilacji](reference/common-macros-for-build-commands-and-properties.md)<br>
[Rozwiązywanie problemów z dostosowaniami kompilacji](troubleshooting-build-customizations.md)
