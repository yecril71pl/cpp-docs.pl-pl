---
title: -link (przebiegu opcje do konsolidatora) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b22e21022162a0f9f75e41e3e0bfdce348947e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="link-pass-options-to-linker"></a>/link (Przepuść opcje do konsolidatora)
Przekazuje jedną lub więcej opcji konsolidatora do konsolidatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>Argumenty  
 `linkeroptions`  
 — Opcja konsolidatora lub opcje do przekazania do konsolidatora.  
  
## <a name="remarks"></a>Uwagi  
 **/Link** opcja i jego opcje konsolidatora muszą występować po dowolnej nazwy pliku i opcji CL. Odstęp jest wymagany między **/link** i `linkeroptions`. Aby uzyskać więcej informacji, zobacz [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk strony właściwości konsolidatora.  
  
4.  Zmodyfikuj co najmniej jednej właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Nie można zmienić tej opcji kompilatora programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)