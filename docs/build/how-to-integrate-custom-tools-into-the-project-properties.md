---
title: "Porady: integrowanie narzędzi niestandardowych we właściwościach projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/27/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.integratecustomtools
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 128b19c1175fb5f39599a9ccaeae66d1fc53fdab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Porady: integrowanie narzędzi niestandardowych we właściwościach projektu
Opcje narzędzia niestandardowego można dodać do programu Visual Studio **strony właściwości** okna, tworząc bazowe pliki schematu XML.  
  
 **Właściwości konfiguracji** sekcji **strony właściwości** okno wyświetla grupy ustawień, które są nazywane *reguły*. Każda reguła zawiera ustawienia dla narzędzia lub grupy funkcji. Na przykład **konsolidatora** reguła zawiera ustawienia dla narzędzia konsolidatora. Ustawienia w regule można podzielić na *kategorii*.  
  
 Tym dokumencie wyjaśniono, jak utworzyć plik w katalogu zestawu, który zawiera właściwości własnych narzędzi niestandardowych, dzięki czemu właściwościach są ładowane podczas uruchamiania programu Visual Studio. Aby uzyskać informacje na temat sposobu modyfikowania pliku, zobacz [platformy Extensibilty część 2](http://go.microsoft.com/fwlink/?LinkID=191489) na blogu zespołu programu Visual Studio.  
  
### <a name="to-add-or-change-project-properties"></a>Aby dodać lub zmienić właściwości projektu  
  
1.  W edytorze XML Utwórz plik XML.  
  
2.  Zapisz plik w programie Visual Studio 2017 `VCTargets\1033` folderu. Będzie mieć inną ścieżkę dla każdej wersji programu Visual Studio 2017, jest zainstalowana i każdego języka. Na przykład ścieżka folderu dla programu Visual Studio Enterprise edition w języku angielskim jest `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Dostosuj ścieżki dla języka i wersji Visual Studio. Każda reguła w **strony właściwości** okna jest reprezentowana przez plik XML w tym folderze. Upewnij się, unikatowej nazwie pliku w folderze.  
  
3.  Skopiuj zawartość `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, zamknij go bez zapisywania zmian, a następnie wklej zawartość w nowym pliku XML. Można użyć dowolnego pliku schematu XML — jest to tylko jeden, który może służyć, aby uruchomić przy użyciu szablonu.  
  
4.  W nowym pliku XML należy zmodyfikować zawartość zgodnie z wymaganiami. Upewnij się zmienić **Nazwa reguły** i **Rule.DisplayName** w górnej części pliku.  
  
5.  Zapisz zmiany i zamknij plik.  
  
6.  Pliki XML `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` są ładowane podczas uruchamiania programu Visual Studio. W związku z tym aby przetestować nowy plik, ponownie uruchom Visual Studio.  
  
7.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**. W **strony właściwości** okna, w okienku po lewej stronie, sprawdź, czy jest nowy węzeł z nazwą reguły.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
