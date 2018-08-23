---
title: -ZW (kompilacja środowiska uruchomieniowego Windows) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 97a97158dda886a09fb6ccb00898a8c518d8e250
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602265"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Kompilacja środowiska wykonawczego systemu Windows)
Kompiluje źródła kod obsługujący rozszerzenia składnik Visual C++ C + +/ CX do tworzenia aplikacji uniwersalnych platformy Windows (UWP).  
  
 Kiedy używasz **/ZW** skompilować, należy zawsze określić **/ehsc** także.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>Argumenty  
 nostdlib  
 Wskazuje, że Platform.winmd Windows.Foundation.winmd i inne domyślne, które pliki metadanych (.winmd) Windows nie są automatycznie uwzględniane w kompilacji. Zamiast tego należy użyć [/FU (nazwij wymuszone #using)](../../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora jawnie określić pliki metadanych Windows.  
  
## <a name="remarks"></a>Uwagi  
 Po określeniu **/ZW** opcja, kompilator obsługuje te funkcje:  
  
-   Pliki wymagane metadane, przestrzenie nazw, typów danych i funkcje wymagane przez aplikację do środowiska wykonawczego Windows.  
  
-   Automatyczne zliczanie odwołań obiektów Windows Runtime i automatyczne odrzucanie obiektu podczas jego licznik odwołań zbliża się do zera.  
  
 Ponieważ konsolidatora przyrostowego nie obsługuje metadanych Windows dołączona do plików .obj przy użyciu **/ZW** opcji [/Gm (Włącz minimalną ponowną kompilację)](../../build/reference/gm-enable-minimal-rebuild.md) opcja jest niezgodna z **/ZW** .  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie językowe Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)