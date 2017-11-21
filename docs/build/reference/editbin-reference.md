---
title: "Odwołanie EDITBIN | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: editbin
dev_langs: C++
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7532a9b2bb0b04b1d56b92551df17e7c7466c8f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="editbin-reference"></a>Odwołanie EDITBIN
Edytor plików binarnych Microsoft COFF (polecenia EDITBIN. Wywołanie pliku EXE) modyfikuje pliki binarne wspólnej obiektu pliku formatu (COFF). Aby zmodyfikować plików obiektów, plików wykonywalnych i bibliotek dołączanych (dynamicznie DLL), można użyć polecenia EDITBIN.  
  
> [!NOTE]
>  Można uruchomić to narzędzie tylko z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] wiersza polecenia. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.  
  
 Polecenia EDITBIN nie jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora. Wszelkie modyfikacje plików binarnych utworzone z opcją /GL musi zostać osiągnięty przy ponownej kompilacji, a następnie połączenie.  
  
-   [Wiersz polecenia EDITBIN](../../build/reference/editbin-command-line.md)  
  
-   [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)