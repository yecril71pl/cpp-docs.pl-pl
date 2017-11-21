---
title: "-CLRIMAGETYPE (określenie typu obrazu CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs: C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f11684f71e874d2dbb439ed1f9dfc46b543a63e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Określenie typu obrazu CLR)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator akceptuje obiektów macierzystych i również MSIL obiekty, które są kompilowane przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), / CLR: pure, lub/CLR: Safe. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015. Gdy mieszanych obiektów w tej samej kompilacji są przekazywane, możliwość weryfikacji wynikowego pliku wyjściowego jest, domyślnie równa najniższa możliwość wprowadzania modułów weryfikacji. Na przykład w przypadku przekazania zarówno w sejfie, jak i czysty modułu do konsolidatora plik wyjściowy będzie czysty. W przypadku przekazania obrazu macierzystego i obraz trybu mieszanego (skompilowana przy użyciu **/CLR**), obraz wynikowy będzie obrazu w trybie mieszanym.  
  
 Umożliwia clrimagetype Określ niższej możliwość weryfikacji, jeżeli jest to, co jest potrzebne.  
  
 W programie .NET 4.5 clrimagetype obsługuje opcję SAFE32BITPREFERRED. To ustawienie — w nagłówku PE obrazu — flagi, które wskazują, że obiekt MSIL są bezpieczne i może być uruchamiany na wszystkich platformach, ale wykonanie 32-bitowego środowiska są preferowane. Ta opcja umożliwia aplikacji do uruchamiania na platformach ARM i określa również, czy ma być uruchamiany w emulatorze WOW64 na 64-bitowych systemach operacyjnych zamiast środowiska wykonawczego 64-bitowych.  
  
 Gdy .exe skompilowanego za pomocą **/CLR** lub **/CLR: pure** jest uruchamiany w 64-bitowym systemie operacyjnym, aplikacja działa w emulatorze WOW64, dzięki czemu 32-bitowej aplikacji na 64-bitowym systemie operacyjnym. Domyślnie, który ma być kompilowana przy użyciu .exe **/CLR: Safe** jest uruchamiana Obsługa 64-bitowego systemu operacyjnego. Jednak jest możliwe, że bezpieczne aplikacji ładuje składnika 32-bitowego. W takim przypadku obraz bezpiecznego uruchamiania Obsługa 64-bitowego systemu operacyjnego zakończy się niepowodzeniem, ładuje 32-bitowej aplikacji. Aby upewnić się, że obraz bezpieczne kontynuuje działanie ładuje składnika 32-bitowych na 64-bitowym systemie operacyjnym, użyj opcji /CLRIMAGETYPE:SAFE32BITPREFERRED. Jeśli kod ma działać na platformach ARM, można określić clrimagetype: PURE możliwość zmiany metadanych (.corflags), oznaczając je do uruchomienia w emulatorze WOW64 (i podstawiając własne symbol wejścia):  
  
 **Cl/CLR: Safe t.cpp/Link clrimagetype: pure /entry:?main@@$$HYMHXZ opcji**  
  
 Aby uzyskać informacje o tym, jak można ustalić typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **typu obrazu CLR** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)