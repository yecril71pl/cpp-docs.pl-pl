---
title: 'Instrukcje: Tworzenie aplikacji konsoli środowiska CLR (C + +/ CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: ba0fa81aa42f946dbaf005c00380573e44312c5a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816363"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Instrukcje: Tworzenie aplikacji konsoli środowiska CLR (C + +/ CLI)

Szablon aplikacji Konsolowej do tworzenia projektu aplikacji konsoli, który ma już odwołania do projektu podstawowych i plików.

Zazwyczaj Aplikacja konsoli jest skompilowany w autonomicznego pliku wykonywalnego, ale nie ma graficznego interfejsu użytkownika. Użytkownik uruchamia aplikację konsoli w wierszu polecenia i korzysta z wiersza polecenia, aby problem instrukcje uruchomionej aplikacji. W wierszu polecenia aplikacji zawiera również informacje w danych wyjściowych. Natychmiastowości aplikacji konsoli sprawia, że doskonały sposób, aby dowiedzieć się więcej technik programowania, bez obawy dotyczące implementowania interfejsu użytkownika.

Gdy używasz szablonu aplikacji konsoli, aby utworzyć projekt, jego automatycznie dodaje tych plików i odwołań do:

- Odwołania do tych przestrzeni nazw .NET Framework:

   - <xref:System.AppDomainManager>— Zawiera klasy podstawowe i klas bazowych, które definiują często używanymi wartościami i odwołania do typów danych, zdarzenia i procedury obsługi zdarzeń, interfejsy, atrybuty i przetwarzanie wyjątków.

   - mscorlib — zestawu biblioteki DLL, która obsługuje programowanie .NET Framework.

- Pliki źródłowe:

   - W konsoli (plik .cpp) — główne źródło pliku i punktu wejścia do aplikacji, który został utworzony. Identyfikuje plik .dll projektu i przestrzeni nazw projektu. Podaj własny kod w tym pliku.

   - Atrybuty AssemblyInfo.cpp—Contains, pliki, zasoby, typów, informacji o wersji, informacje o podpisywaniu i tak dalej, używanej do zmodyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [zawartość zestawu](/dotnet/framework/app-domains/assembly-contents).

   - Stdafx.cpp—Used tworzenie prekompilowany plik nagłówka o nazwie Win32.pch i plik wstępnie skompilowane typy, o nazwie StdAfx.obj.

- Pliki nagłówkowe:

   - Stdafx.h—Used tworzenie prekompilowany plik nagłówka o nazwie Win32.pch i plik wstępnie skompilowane typy, o nazwie StdAfx.obj.

   - wygenerowany Resource.h—A obejmują app.rc w pliku.

- Pliki zasobów:

   - plik skryptu zasobu App.RC—the programu.

   - Plik ikony App.ico—the programu.

- ReadMe.txt—Describes pliki w projekcie.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Do utworzenia projektu aplikacji konsoli środowiska uruchomieniowego (języka wspólnego CLR) w usłudze common language

1. Na pasku menu wybierz **pliku**, **New**, **projektu**.

1. W **nowy projekt** okno dialogowe, w obszarze **zainstalowane szablony**, wybierz opcję **Visual C++** węzeł **CLR** węzłem, a następnie wybierz pozycję Szablon Aplikacja konsoli.

1. W **nazwa** wprowadź unikatową nazwę aplikacji.

   Można określić inne ustawienia projektu i rozwiązania, ale nie są wymagane.

1. Wybierz **OK** przycisku.

## <a name="see-also"></a>Zobacz także

[Projekty CLR](../build/reference/files-created-for-clr-projects.md)

