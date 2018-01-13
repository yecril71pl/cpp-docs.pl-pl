---
title: -link (przebiegu opcje do konsolidatora) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /link
dev_langs: C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6732f5a2b144172939e23af4addb37b7605de11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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