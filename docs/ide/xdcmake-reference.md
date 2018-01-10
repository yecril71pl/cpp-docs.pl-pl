---
title: "Xdcmake — odwołanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xdcmake
dev_langs: C++
helpviewer_keywords: xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea635d701b4dea2471067072083d9568f11f3d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="xdcmake-reference"></a>XDCMake — odwołanie
xdcmake.exe to program, który kompiluje plikach xdc do pliku XML. Plik .xdc jest tworzony przez kompilator języka Visual C++ dla każdego pliku źródła kodu, podczas kompilowania kodu źródłowego z [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) i gdy pliku kodu źródłowego zawiera komentarzy do dokumentacji oznaczonych tagów XML.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Aby użyć xdcmake.exe w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  Otwórz **właściwości konfiguracji** folderu.  
  
3.  Kliknij przycisk **komentarzy dokumentu XML** strony właściwości.  
  
> [!NOTE]
>  Opcje xdcmake.exe w wierszu polecenia różnią się od opcji, gdy xdcmake.exe jest używany w środowisku programistycznym (strony właściwości). Informacje na temat używania xdcmake.exe w środowisku programistycznym, zobacz [strony właściwości narzędzia generowania dokumentów XML](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Składnia  
 xdcmake —`input_filename options`  
  
## <a name="parameters"></a>Parametry  
 gdzie:  
  
 `input_filename`  
 Nazwa pliku plikach xdc używane jako dane wejściowe xdcmake.exe. Określ co najmniej jeden plik .xdc lub służy *.xdc do Użyj wszystkich plików xdc w bieżącym katalogu.  
  
 `options`  
 Zero lub więcej z następujących czynności:  
  
|Opcja|Opis|  
|------------|-----------------|  
|/?, / help|Wyświetla Pomoc dla xdcmake.exe.|  
|/ Assembly:*filename*|Umożliwia określenie wartości \<zestawu > znacznika w pliku XML.  Domyślnie wartość \<zestawu > tag jest taka sama jak nazwa pliku XML.|  
|/nologo|Pomiń komunikat o prawach autorskich.|  
|/ out:*filename*|Pozwala określić nazwę pliku XML.  Domyślnie nazwa pliku XML jest nazwa pierwszego pliku .xdc przetworzone przez xdcmake.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio wywoła xdcmake.exe automatycznie podczas kompilowania projektu. Można także wywoływać xdcmake.exe w wierszu polecenia.  
  
 Zobacz [tagi zalecane dla komentarzy do dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) Aby uzyskać więcej informacji na temat dodawania komentarzy do dokumentacji do plików kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)