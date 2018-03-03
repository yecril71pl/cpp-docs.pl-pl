---
title: -V (numer wersji) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a940000b5330c4eccdcabcc5a31f0c3e3e74d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="v-version-number"></a>/V (Numer wersji)
Przestarzałe. W pliku obj. osadzony ciąg tekstowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>Argumenty  
 `string`  
 Ciąg określający numer wersji lub informacje o prawach autorskich do osadzenia w pliku .obj.  
  
## <a name="remarks"></a>Uwagi  
 Etykieta stringcan plik .obj z numeru wersji lub informacje o prawach autorskich. Znaków spację lub tabulator musi być ujęta w znaki cudzysłowu ("), jeśli są one częścią ciąg. Ukośnik odwrotny (\\) musi poprzedzać wszystkie znaki cudzysłowu, jeśli są one częścią ciąg. Odstęp między **/V** i `string` jest opcjonalna.  
  
 Można również użyć [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md) z argumentem typu komentarza kompilatora, aby umieścić nazwę i numer wersji kompilatora w pliku obj.  
  
 **/V** opcji jest przestarzały, począwszy od programu Visual Studio 2005; **/V** został głównie używane do obsługi tworzenia sterowniki urządzeń wirtualnych urządzenia (vxd) i tworzenia urządzenia vxd nie jest już obsługiwana przez zestaw narzędzi Visual C++. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)