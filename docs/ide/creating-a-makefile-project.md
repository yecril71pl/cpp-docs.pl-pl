---
title: "Tworzenie projektu pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f487126b58dddc0243646ebce7faa2754ffa7053
ms.sourcegitcommit: 4e01d36ffa64ea11bacf589f79d2f1df947e2510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="creating-a-makefile-project"></a>Tworzenie projektu pliku reguł programu make

Jeśli masz istniejący projekt kodu źródłowego kompilacji z wiersza polecenia przy użyciu pliku reguł programu make środowisko projektowe Visual Studio ma kilka sposobów włączania go do projektu, który mogą w pełni korzystać z funkcji programu Visual Studio IDE. W tym artykule opisano sposób tworzenia projektu pliku reguł programu make w Visual Studio, która korzysta z istniejącego pliku reguł programu make w celu skompilowania kodu w środowisku IDE. Alternatywnie można użyć **Utwórz nowy projekt z istniejących plików kodu** kreatora, aby utworzyć natywnego projektu programu MSBuild w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu C++ z istniejącego kodu](how-to-create-a-cpp-project-from-existing-code.md). Począwszy od programu Visual Studio 2017 r, można również użyć **Otwórz Folder** funkcja, której można użyć kilku istniejących systemów kompilacji, tak jakby były natywnego projektów programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projekty w programie Visual C++](non-msbuild-projects.md).

Do otwierania i tworzenia kodu źródłowego przy użyciu z istniejącego pliku reguł programu make, należy użyć programu Visual Studio, najpierw utworzyć nowy projekt, wybierając szablon projektu pliku reguł programu make. Kreator pomaga określić polecenia i używane przez Twojego pliku reguł programu make środowiska. Korzystać z tego projektu, do tworzenia kodu w środowisku programowania Visual Studio.

Domyślnie projektu pliku reguł programu make są wyświetlane żadne pliki w Eksploratorze rozwiązań. Projektu pliku reguł programu make określa ustawienia kompilacji, które są uwzględniane na stronie właściwości projektu.

Plik wyjściowy określany w projekcie nie ma wpływu na nazwę, którą generuje skrypt kompilacji; deklaruje tylko zamiar. Pliku reguł programu make nadal kontroluje proces kompilacji i określa elementy docelowe kompilacji.

## <a name="to-create-a-makefile-project"></a>Aby utworzyć projekt Makefile

1. Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu za pomocą Kreatora aplikacji Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).

1. W **nowy projekt** okna dialogowego rozwiń **Visual C++** > **ogólne** , a następnie wybierz **projektu pliku reguł programu make** w W okienku szablonów, aby otworzyć Kreator projektu.

1. W [ustawienia aplikacji](../ide/application-settings-makefile-project-wizard.md) Podaj czyszczenia danych wyjściowych polecenia i Odbuduj informacji debugowania i detaliczne kompilacje.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otwórz nowo utworzony projekt w **Eksploratora rozwiązań**.

Możesz przeglądać i modyfikować właściwości projektu na stronie właściwości. Zobacz [Ustawianie właściwości projektu Visual C++](../ide/working-with-project-properties.md) informacje dotyczące wyświetlania strony właściwości.

## <a name="see-also"></a>Zobacz też

[Kreator projektu pliku reguł programu make](../ide/makefile-project-wizard.md)<br/>
[Znaki specjalne w pliku reguł programu Make](../build/special-characters-in-a-makefile.md)<br/>
[Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)<br/>
