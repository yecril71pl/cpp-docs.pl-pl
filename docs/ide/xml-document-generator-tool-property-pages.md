---
title: Strony właściwości narzędzia generowania dokumentów XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 772e9dc6a296873ef27171676ebca0c185c1771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-generator-tool-property-pages"></a>Strony właściwości narzędzia generowania dokumentów XML
Strona właściwości narzędzie generowania dokumentu XML ujawniającą funkcjonalność xdcmake.exe. xdcmake.exe scala plikach xdc w pliku XML, gdy kod źródłowy zawiera komentarzy do dokumentacji i [/doc (przetwarzanie komentarzy dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) jest określona. Zobacz [tagi zalecane dla komentarzy do dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) informacji na temat dodawania komentarzy do dokumentacji do kodu źródłowego.  
  
> [!NOTE]
>  Opcje xdcmake.exe w środowisku programistycznym (strony właściwości) różnią się od opcji, gdy xdcmake.exe jest używany w wierszu polecenia. Aby uzyskać informacje na temat używania xdcmake.exe w wierszu polecenia, zobacz [xdcmake — odwołanie](../ide/xdcmake-reference.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Pomiń Baner startowy**  
 Pomiń komunikat o prawach autorskich.  
  
 **Pliki dodatkowe**  
 Dodatkowe katalogi, w których ma szukać plików xdc system projektu. xdcmake — zawsze będzie szukać plików xdc wygenerowany przez projekt. Można określić wiele katalogów.  
  
 **Wynikowy plik dokumentu**  
 Nazwy i lokalizacji katalogu wyjściowego pliku XML. Zobacz [wspólnej makra dla poleceń kompilacji oraz właściwości](../ide/common-macros-for-build-commands-and-properties.md) informacji przy użyciu makra w celu określenia lokalizacji katalogu.  
  
 **Zależności biblioteki dokumentów**  
 Jeśli projekt zawiera zależności w projekcie lib w rozwiązaniu, można przetwarzać plików xdc z projektu .lib do plików XML dla bieżącego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../ide/property-pages-visual-cpp.md)   
 [Strony właściwości](../ide/property-pages-visual-cpp.md)