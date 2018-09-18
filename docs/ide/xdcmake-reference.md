---
title: Xdcmake — dokumentacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- xdcmake
dev_langs:
- C++
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf28f01778bea31bc84a57fa74fed3221673dec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039962"
---
# <a name="xdcmake-reference"></a>XDCMake — odwołanie
xdcmake.exe to program, który kompiluje pliki .xdc w pliku XML. Plik .xdc jest tworzony przez kompilator języka Visual C++ dla każdego pliku kodu źródłowego, podczas kompilowania kodu źródłowego za pomocą [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) i kiedy plik kodu źródłowego zawiera komentarze dokumentacji oznaczone tagów XML.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Aby użyć xdcmake.exe w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  Otwórz **właściwości konfiguracji** folderu.  
  
3.  Kliknij przycisk **komentarzy dokumentu XML** stronę właściwości.  
  
> [!NOTE]
>  Opcje xdcmake.exe w wierszu polecenia różnią się od opcji, gdy xdcmake.exe jest używany w środowisku programistycznym (strony właściwości). Uzyskać informacji na temat używania xdcmake.exe w środowisku programistycznym, zobacz [strony właściwości narzędzia generowania dokumentów XML](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Składnia  
 xdcmake — `input_filename options`  
  
## <a name="parameters"></a>Parametry  
  
*input_filename*<br/>
Nazwa pliku plików xdc używany jako dane wejściowe xdcmake.exe. Określ jeden lub więcej plików xdc lub użyj *.xdc wszystkich plików xdc w bieżącym katalogu.  
  
*Opcje*<br/>
Zero lub więcej z następujących czynności:  
  
|Opcja|Opis|  
|------------|-----------------|  
|/?, / help|Wyświetla Pomoc dla xdcmake.exe.|  
|/ Assembly:*nazwy pliku*|Umożliwia określenie wartości \<zestawu > tagu w pliku XML.  Domyślnie wartość \<zestawu > tag jest taka sama jak nazwa pliku XML.|  
|/nologo|Pomiń komunikat o prawach autorskich.|  
|/ out:*nazwy pliku*|Pozwala określić nazwę pliku XML.  Domyślnie nazwa pliku XML, który jest nazwa pierwszego pliku .xdc przetwarzane przez xdcmake.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio będzie automatycznie wywoływać xdcmake.exe podczas kompilowania projektu. Można również wywołać xdcmake.exe w wierszu polecenia.  
  
 Zobacz [tagi zalecane dla komentarzy do dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) Aby uzyskać więcej informacji na temat dodawania komentarzy do dokumentacji do plików kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)