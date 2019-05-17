---
title: 'Instrukcje: Integrowanie narzędzi niestandardowych we właściwościach projektu'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837030"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Instrukcje: Integrowanie narzędzi niestandardowych we właściwościach projektu

Można dodać opcje niestandardowego narzędzia w programie Visual Studio **stron właściwości** okna, tworząc bazowe pliki schematu XML.

**Właściwości konfiguracji** części **stron właściwości** okno wyświetla grupy ustawień, które są znane jako *reguły*. Każda reguła zawiera ustawienia dla narzędzia lub grupy funkcji. Na przykład **konsolidatora** reguła zawiera ustawienia dla narzędzia konsolidatora. Ustawienia w regule można podzielić na *kategorie*.

W tym dokumencie wyjaśniono, jak utworzyć plik w katalogu zestawu, który zawiera właściwości dla własnych narzędzi niestandardowych właściwości są ładowane podczas uruchamiania programu Visual Studio. Aby uzyskać informacje o sposobie modyfikowania pliku, zobacz [platformy Extensibilty część 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) na blogu zespołu projektu usługi Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Aby dodać lub zmienić właściwości projektu

1. W edytorze XML należy utworzyć plik XML.

1. Zapisz plik w programie Visual Studio `VCTargets\1033` folderu. Będziesz mieć inną ścieżkę dla każdej wersji programu Visual Studio, który jest zainstalowany i każdego z języków. Na przykład domyślna ścieżka folderu dla programu Visual Studio 2019 Community edition w języku angielskim jest `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Dostosuj ścieżkę dla swojego języka i wersji programu Visual Studio. Każda reguła w **stron właściwości** okna jest reprezentowany przez plik XML, w tym folderze. Upewnij się, że plik ma unikatową nazwę w folderze.

1. Skopiuj zawartość `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (lub niezależnie od ścieżki), zamknij je bez zapisywania zmian, a następnie wklej zawartość w nowym pliku XML. Można użyć dowolnego pliku schematu XML — jest to tylko jedna, który może służyć, tak więc zaczynasz przy użyciu szablonu.

1. W nowym pliku XML zmodyfikuj zawartość zgodnie z wymaganiami. Upewnij się, że zmiana **Nazwa reguły** i **Rule.DisplayName** w górnej części pliku.

1. Zapisz zmiany i zamknij plik.

1. Pliki XML `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (lub zapisać wszędzie tam, gdzie) są ładowane podczas uruchamiania programu Visual Studio. W związku z tym aby przetestować nowy plik, uruchom ponownie program Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**. W **stron właściwości** okna, w okienku po lewej stronie, sprawdź, czy nowy węzeł z nazwą reguły.

## <a name="see-also"></a>Zobacz także

[Program MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)
