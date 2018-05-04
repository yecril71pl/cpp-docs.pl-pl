---
title: -ZW (kompilacja środowiska uruchomieniowego systemu Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fce6c6825ed4ae715a2f4cde6b0e1ffa8b3b6733
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Kompilacja środowiska wykonawczego systemu Windows)
Kompiluje źródła kodu do obsługi [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) do tworzenia aplikacji uniwersalnych platformy systemu Windows (UWP).  
  
 Jeśli używasz **/ZW** skompilować, należy zawsze podać **/ehsc** również.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>Argumenty  
 nostdlib  
 Wskazuje tym Platform.winmd, Windows.Foundation.winmd i inne pliki metadanych (.winmd) dla systemu Windows nie są automatycznie uwzględniona w kompilacji domyślnego. Zamiast tego należy użyć [/FU (nazwij wymuszone #using)](../../build/reference/fu-name-forced-hash-using-file.md) opcję kompilatora, aby jawnie określić pliki metadanych systemu Windows.  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu **/ZW** opcja, kompilator obsługuje te funkcje:  
  
-   Wymagane metadane plików, przestrzenie nazw, typy danych i funkcje wymagane przez aplikację do wykonania w środowisku wykonawczym systemu Windows.  
  
-   Automatyczne liczenie odwołań obiektów środowiska wykonawczego systemu Windows i automatyczne odrzucanie obiektu po jego liczebności referencyjnej przechodzi od zera.  
  
 Ponieważ konsolidatora przyrostowego nie obsługuje metadanych systemu Windows, uwzględniane w plikach .obj przy użyciu **/ZW** opcji [/GM ponowną (Włącz minimalnego odbudować)](../../build/reference/gm-enable-minimal-rebuild.md) opcja jest niezgodna z **/ZW** .  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie do języka Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)