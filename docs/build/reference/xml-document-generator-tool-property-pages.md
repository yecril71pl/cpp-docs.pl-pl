---
title: Strony właściwości narzędzia generowania dokumentów XML
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: d17913909532c5bebcac712937af00be3ad98712
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335766"
---
# <a name="xml-document-generator-tool-property-pages"></a>Strony właściwości narzędzia generowania dokumentów XML

Strona właściwości Narzędzia generatora dokumentów XML udostępnia funkcje pliku xdcmake.exe. xdcmake.exe scala pliki xdc z plikiem xml, gdy kod źródłowy zawiera komentarze do dokumentacji i [/doc (Process Documentation Comments) (C/C++)](doc-process-documentation-comments-c-cpp.md) jest określony,. Zobacz [Zalecane tagi dla uwag dokumentacji, aby](recommended-tags-for-documentation-comments-visual-cpp.md) uzyskać informacje na temat dodawania komentarzy dokumentacji do kodu źródłowego.

> [!NOTE]
> Opcje xdcmake.exe w środowisku programistycznym (strony właściwości) różnią się od opcji, gdy xdcmake.exe jest używany w wierszu polecenia. Aby uzyskać informacje na temat używania pliku xdcmake.exe w wierszu polecenia, zobacz [XDCMake Reference](xdcmake-reference.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Pomijanie banera startowego**

   Pomiń wiadomości dotyczące praw autorskich.

- **Dodatkowe pliki dokumentów**

   Dodatkowe katalogi, w których system projektu ma wyszukać pliki .xdc. xdcmake zawsze będzie szukać plików .xdc generowanych przez projekt. Można określić wiele katalogów.

- **Wyjściowy plik dokumentu**

   Nazwa i lokalizacja katalogu pliku wyjściowego xml. Aby uzyskać informacje na temat używania makr do określania lokalizacji katalogów, zobacz [Typowe makra dla poleceń kompilacji i właściwości.](common-macros-for-build-commands-and-properties.md)

- **Zależności biblioteki dokumentów**

   Jeśli projekt ma zależność od projektu lib w rozwiązaniu, można przetworzyć pliki xdc z projektu .lib do plików xml dla bieżącego projektu.

## <a name="see-also"></a>Zobacz też

[Odwołanie do strony właściwości projektu języka C++](property-pages-visual-cpp.md)
