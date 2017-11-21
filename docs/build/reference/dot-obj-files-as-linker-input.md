---
title: ". Pliki obj jako wejście konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca8346f9ff29d097450eda4d8bfbfee7f7a3f522
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="obj-files-as-linker-input"></a>Pliki .Obj — Wejście konsolidatora
Narzędzia konsolidatora (łącze. Wywołanie pliku EXE) akceptuje pliki obj w typowych obiektu pliku formatu (COFF).  
  
## <a name="remarks"></a>Uwagi  
 Firma Microsoft udostępnia dokument do pobrania, który definiuje wspólne format pliku obiektu. Aby uzyskać więcej informacji, należy pobrać poprawkę 8.1 lub nowszy z [Microsoft przenośny plik wykonywalny i wspólne specyfikacją formatu pliku obiektu](http://go.microsoft.com/fwlink/?LinkId=93292).  
  
## <a name="unicode-support"></a>Obsługa formatu Unicode  
 Począwszy od programu Visual Studio 2005, kompilator Microsoft Visual C++ obsługuje znaki Unicode w identyfikatorach zgodnie z definicją ISO/IEC C i C++ standardów. Poprzednie wersje kompilatora obsługiwane tylko znaki ASCII w identyfikatorach. Do obsługi standardu Unicode w nazwach funkcji, klasy i statyczne, kompilatorze i konsolidatorze Użyj kodowania Unicode UTF-8 dla symboli COFF w plikach .obj. Kodowanie UTF-8 jest upwardly zgodny z kodowaniem ASCII używane we wcześniejszych wersjach programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat kompilatorze i konsolidatorze, zobacz [obsługi formatu Unicode w kompilatorze i Konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [Unicode](http://go.microsoft.com/fwlink/?LinkId=37123) organizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Obsługa formatu Unicode](../../text/support-for-unicode.md)   
 [Obsługa standardu Unicode w kompilatorze i Konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Unicode standard](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [Typowe specyfikacją formatu pliku obiektu](http://go.microsoft.com/fwlink/?LinkId=93292)