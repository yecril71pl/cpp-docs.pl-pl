---
title: Strona właściwości NMake (Windows C++) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: c0dbe537635fe6698f814f3d8456f0caa9c8c796
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823600"
---
# <a name="nmake-property-page"></a>Strona właściwości NMake

**NMake** właściwość umożliwia określenie ustawień kompilacji dla projektów NMake. (NMAKE jest implementacja firmy Microsoft [wprowadzić](https://wikipedia.org/wiki/Make_(software)).)

Aby uzyskać więcej informacji na temat projektów NMake zobacz [Tworzenie projektu pliku reguł programu make](creating-a-makefile-project.md). W przypadku projektów plików reguł programu make innych niż - Windows zobacz [właściwości projektu pliku reguł programu make (Linux C++)](../../linux/prop-pages/makefile-linux.md), [ogólne właściwości projektu (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) lub [właściwości narzędzia NMake (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page).

**NMake** strona właściwości zawiera następujące właściwości.

## <a name="uielement-list"></a>Lista elementów UI

- **Wiersz polecenia kompilacji**

   Określa polecenie do uruchomienia po **kompilacji** jest kliknięty **kompilacji** menu.

- **Wiersz poleceń rekompilacji wszystkiego**

   Określa polecenie do uruchomienia po **Kompiluj wszystko ponownie** jest kliknięty **kompilacji** menu.

- **Wiersz polecenia Wyczyść**

   Określa polecenie do uruchomienia po **czysty** jest kliknięty **kompilacji** menu.

- **Output**

   Określa nazwę pliku, który będzie zawierał dane wyjściowe wiersza polecenia. Domyślnie ta nazwa pliku opiera się na nazwę projektu.

- **Definicje preprocesora**

   Określa wszystkie definicje preprocesora, użycia plików źródłowych. Wartość domyślna zależy od bieżącej platformy i konfiguracji.

- **Ścieżka wyszukiwania plików dołączanych**

   Określa katalog, w którym kompilator wyszukuje pliki dołączane.

- **Wymuszone obejmuje**

   Określa pliki, które preprocesor przetwarza automatycznie, nawet wtedy, gdy nie są uwzględniane w plikach projektu.

- **Ścieżka wyszukiwania zestawu**

   Określa katalog, gdzie programu .NET Framework wyszukiwania, kiedy go próbuje rozpoznać zestawów platformy .NET.

- **Wymuszone za pomocą zestawów**

   Określa zestawy, które automatycznie przetwarza programu .NET Framework.

- **Dodatkowe opcje**

   Określa wszelkie dodatkowe przełączniki kompilatora dla funkcji IntelliSense do użycia podczas jej analizuje pliki języka C++.

Aby uzyskać informacje o tym, jak uzyskać dostęp do **NMake** strony właściwości, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

Aby uzyskać informacje na temat programowego dostępu do elementów członkowskich tego obiektu, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja strony właściwości projektu C++](property-pages-visual-cpp.md)<br>
