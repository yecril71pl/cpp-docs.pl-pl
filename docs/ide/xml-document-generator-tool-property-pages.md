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
ms.openlocfilehash: 3e97aa61715f0cda8e339a1aabc8e947170b2e90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594236"
---
# <a name="xml-document-generator-tool-property-pages"></a>Strony właściwości narzędzia generowania dokumentów XML

Strona właściwości narzędzie generowania dokumentów XML udostępnia funkcję xdcmake.exe. xdcmake.exe scala plików xdc do pliku XML, gdy kod źródłowy zawiera komentarzy do dokumentacji i [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) jest określony. Zobacz [tagi zalecane dla komentarzy do dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) informacji dotyczących dodawania komentarzy do dokumentacji do kodu źródłowego.

> [!NOTE]
>  Opcje xdcmake.exe w środowisku programistycznym (strony właściwości) różnią się od opcji, gdy xdcmake.exe jest używany w wierszu polecenia. Aby uzyskać informacje na temat używania xdcmake.exe w wierszu polecenia, zobacz [xdcmake — dokumentacja](../ide/xdcmake-reference.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Pomijaj transparent startowy**

   Pomiń komunikat o prawach autorskich.

- **Pliki dodatkowe dokumentów**

   Dodatkowe katalogi, w których chcesz, aby system projektu będzie szukał plików xdc. xdcmake — zawsze będzie szukał plików xdc wygenerowany przez projekt. Można określić wiele katalogów.

- **Wynikowy plik dokumentu**

   Nazwy i lokalizacji katalogu wyjściowego pliku XML. Zobacz [typowe makra dla poleceń i właściwości kompilacji](../ide/common-macros-for-build-commands-and-properties.md) informacji na temat korzystania z makr do określenia lokalizacji w katalogu.

- **Zależności biblioteki dokumentów**

   Jeśli projekt zależny od .lib projektu w rozwiązaniu, może przetwarzać plików xdc z projektu lib w plikach XML dla bieżącego projektu.

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../ide/property-pages-visual-cpp.md)<br>
[Strony właściwości](../ide/property-pages-visual-cpp.md)