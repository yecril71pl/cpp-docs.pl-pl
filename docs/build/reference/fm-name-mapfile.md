---
title: -Fm (nazwa Mapfile) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fm
dev_langs:
- C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a499b943fcd3213aa76876c65c3aac2dd79060
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374287"
---
# <a name="fm-name-mapfile"></a>/Fm (Nazwa Mapfile)
Informuje konsolidator, aby utworzyć plik mapowania zawierającego listę segmentów w kolejności, w jakiej występują w odpowiedniego pliku .exe lub DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie mapfile podano nazwę podstawową odpowiadający mu plik źródłowy języka C lub C++ z. MAPOWANIA rozszerzenia.  
  
 Określanie **/Fm** działa tak samo jak gdyby była określona [/map (Generowanie Mapfile)](../../build/reference/map-generate-mapfile.md) — opcja konsolidatora.  
  
 Jeśli określisz [/c (Kompiluj bez konsolidacji)](../../build/reference/c-compile-without-linking.md) do pomijania łączenia **/Fm** nie ma wpływu.  
  
 Symbole globalne w pliku mapowania zwykle mają co najmniej jeden wiodące znaki podkreślenia, ponieważ kompilator dodaje podkreśleniem początku do nazwy zmiennej. Wiele symboli globalne, które pojawiają się w pliku mapowania jest używana wewnętrznie przez kompilator i biblioteki standardowe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)